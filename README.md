# Dynare Syntax

This VS Code extension enables syntax highlighting for Dynare files.
MATLAB code within Dynare files is also highlighted.
**Note**: This extension alone does **not** enable running your Dynare code in VS Code.

You can install this extension via the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=shsu.dynare-syntax).

The [syntaxes/dynare.tmLanguage.json](syntaxes/dynare.tmLanguage.json) file was generated using Perplexity with Claude 3.5. Ongoing improvements are being made with the assistance of Claude 3.5 Sonnet.

**NOTE**: This extension is still under development. If you encounter any bugs, please create an [issue](https://github.com/shihhsuanhsu/vscode-dynare-syntax/issues).

## Run Dynare in Terminal

1. **Ensure MATLAB is installed** on your system.

2. **Verify MATLAB can run in headless mode**:
   - Type `matlab -nodesktop` in the terminal or PowerShell
   - MATLAB's copyright information should appear in the terminal
   - If not, please add MATLAB's installation directory to the environment variable `PATH`, or replace `matlab` with the absolute path to your MATLAB installation

3. **Run Dynare code in the terminal** using:
   ```bash
   matlab -nodesktop -nosplash -r \"try, dynare <dynare filename>, catch error, disp(getReport(error,'extended')), exit(1), end, exit(0);\"
   ```

   **Note**: This command exits both Dynare and MATLAB upon code completion. Make sure to store the IRFs in your Dynare code, or alternatively use:
   ```bash
   matlab -nodesktop -nosplash -r \" dynare <dynare filename>;\"
   ```

4. **For Code Runner integration**, add the following to the executor map to use the run button:
   ```json
   "dynare": "cd $dir && matlab -nodesktop -nosplash -r \"try, dynare $fileNameWithoutExt, catch error, disp(getReport(error,'extended')), exit(1), end, exit(0);\""
   ```
