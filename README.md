<img width="2984" height="1702" alt="emix" src="https://github.com/user-attachments/assets/cd7f9846-e219-4b18-ab3f-a27495d99753" />

# Installation

EMix_reborn requires **Python 3.12**, Tkinter, and `python-rtmidi`.

Using Python 3.12 is recommended because it works reliably with the MIDI libraries used by the editor.

## macOS

### 1. Install Homebrew

If Homebrew is not already installed:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### 2. Install Python 3.12 and Tkinter

```bash
brew install python@3.12
brew install python-tk@3.12
```

### 3. Create a virtual environment

```bash
"$(brew --prefix)/bin/python3.12" -m venv ~/emx-midi-env
```

### 4. Activate the environment

```bash
source ~/emx-midi-env/bin/activate
```

### 5. Install the MIDI libraries

```bash
python -m pip install --upgrade pip
python -m pip install python-rtmidi mido
```

### 6. Verify the installation

```bash
python -c "import tkinter, rtmidi, mido; print('Python / Tk / MIDI OK')"
```

You should see:

```text
Python / Tk / MIDI OK
```

### 7. Run the editor

Example:

```bash
python ~/Downloads/EMix_reborn.py
```

Or launch it directly with the virtual-environment Python:

```bash
~/emx-midi-env/bin/python ~/Downloads/EMix_reborn.py
```

You only need to install the libraries **once**.

For later sessions:

```bash
source ~/emx-midi-env/bin/activate
python ~/Downloads/EMix_reborn.py
```

---

# Windows 10 / 11

### 1. Install Python 3.12

Download and install the **64-bit Python 3.12** installer from:

https://www.python.org/downloads/

During installation:

* Enable **Add Python to PATH**
* Keep **Tcl/Tk and IDLE** enabled

### 2. Verify Python

Open Command Prompt or PowerShell:

```powershell
py -3.12 --version
```

You should see:

```text
Python 3.12.x
```

### 3. Create a virtual environment

Command Prompt:

```cmd
py -3.12 -m venv "%USERPROFILE%\emx-midi-env"
```

PowerShell:

```powershell
py -3.12 -m venv "$env:USERPROFILE\emx-midi-env"
```

### 4. Activate the environment

Command Prompt:

```cmd
%USERPROFILE%\emx-midi-env\Scripts\activate
```

PowerShell:

```powershell
& "$env:USERPROFILE\emx-midi-env\Scripts\Activate.ps1"
```

### 5. Install the MIDI libraries

```powershell
python -m pip install --upgrade pip
python -m pip install python-rtmidi mido
```

### 6. Verify the installation

```powershell
python -c "import tkinter, rtmidi, mido; print('Python / Tk / MIDI OK')"
```

You should see:

```text
Python / Tk / MIDI OK
```

### 7. Run the editor

Example:

```powershell
python "$env:USERPROFILE\Downloads\EMix_reborn.py"
```

---

# MIDI connection

For MIDI communication with the Korg EMX-1:

```text
Computer / MIDI Interface OUT → EMX MIDI IN
EMX MIDI OUT → Computer / MIDI Interface IN
```

The editor can send the selected song to the EMX **edit buffer** over SysEx.

It does **not** automatically write the song permanently to the EMX.

To save the transferred song permanently, use the **WRITE** function directly on the EMX hardware.

---

# Troubleshooting

## `ModuleNotFoundError: No module named 'rtmidi'`

Make sure the editor is running from the virtual environment.

macOS:

```bash
~/emx-midi-env/bin/EMix_reborn.py
```

Windows:

```powershell
%USERPROFILE%\emx-midi-env\Scripts\python.exe EMix_reborn.py
```

If needed, install the library into that environment:

```bash
python -m pip install python-rtmidi
```

## macOS: `No module named '_tkinter'`

Install the matching Tkinter package:

```bash
brew install python-tk@3.12
```

Then recreate the virtual environment:

```bash
rm -rf ~/emx-midi-env
"$(brew --prefix)/bin/python3.12" -m venv ~/emx-midi-env
source ~/emx-midi-env/bin/activate
python -m pip install python-rtmidi mido
```

## `externally-managed-environment`

Do not use `--break-system-packages`.

Create and use the virtual environment described above instead.
