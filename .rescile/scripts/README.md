# Rescile Controller CE - Initialization Scripts

These scripts automate the setup of the `rescile-controller-ce` binary for your local environment. They will download the correct binary for your operating system, verify its integrity, and add it to your shell's `PATH` for the current session.

The scripts are idempotent: if the binary is already installed, they will simply ensure it's available in your `PATH` without re-downloading.

## Prerequisites

- **Linux/macOS**: `curl` and `jq` must be installed.
- **Windows**: `PowerShell` and `curl` (included in modern versions of Windows 10/11) are required.
- **NixOS**: Make sure `programs.nix-ld.enable = true` is configured (https://search.nixos.org/options?channel=unstable&show=programs.nix-ld.enable)

## Usage

### Linux and macOS (bash, zsh, etc.)

The `init.sh` script is designed to be evaluated by your shell. This allows it to modify your current shell's environment.

1.  Make the script executable:
    ```sh
    chmod +x init.sh
    ```
2.  Run the script using `eval`:
    ```sh
    eval "$(./init.sh)"
    ```

After running this command, the `.bin` directory will be prepended to your `PATH`, and you can run the `rescile-controller-ce` command directly.

### Windows (PowerShell)

The `init.ps1` script should be run directly within a PowerShell terminal.

1.  You may need to adjust your execution policy to run local scripts:
    ```powershell
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process
    ```
2.  Run the script:
    ```powershell
    .\init.ps1
    ```

This will download the binary and add its location to the `PATH` for your current PowerShell session.

### Windows (Command Prompt - `cmd.exe`)

The `init.bat` script is a standard batch file.

1.  Simply run it from the command prompt:
    ```cmd
    init.bat
    ```

This will set up the binary and update the `PATH` for the current `cmd.exe` session.
