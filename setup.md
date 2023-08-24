
---

# Pyenv-Win Installation and Setup Guide

## **1. Download `pyenv-win`**
Visit the official [pyenv-win GitHub page](https://github.com/pyenv-win/pyenv-win) and download `pyenv-win`. You can download by clicking on the **<span style="background-color: green;color:white"> <>Code </span>** button and download zip.



## **2. Create `.pyenv` Folder**
Open a PowerShell instance and execute the following command:
```powershell
mkdir $HOME/.pyenv
```
This creates a `.pyenv` folder in `c:\users\<YourUserName>`.

## **3. Extract and Copy**
Extract the contents of the `pyenv-win` ZIP file you downloaded.

Next, copy both the `pyenv-win` folder and the `.version` file from the `pyenv-win-master` folder into the `.pyenv` folder you created in the previous step.

## **4. Set Environment Variables**
In the same PowerShell instance, execute the following commands:

```powershell

[System.Environment]::SetEnvironmentVariable('PYENV',$env:USERPROFILE + "\.pyenv\pyenv-win\","User")


[System.Environment]::SetEnvironmentVariable('PYENV_HOME',$env:USERPROFILE + "\.pyenv\pyenv-win\","User")

[System.Environment]::SetEnvironmentVariable('path', $env:USERPROFILE + "\.pyenv\pyenv-win\bin;" + $env:USERPROFILE + "\.pyenv\pyenv-win\shims;" + [System.Environment]::GetEnvironmentVariable('path', "User"),"User")

```

## **5. Update Execution Policy**
Close the current PowerShell instance and open a new one as an **administrator**. Run:
```powershell
Set-ExecutionPolicy unrestricted
```
once prompted withe the message click **A** on your keyboard.

## **6. Test `pyenv` Installation**
In the PowerShell, execute:
```powershell
pyenv
```

If you encounter any warnings, run:
```powershell
Unblock-File $HOME/.pyenv/pyenv-win/bin/pyenv.ps1
```

## **7. Install Required Python Version**
Execute the following commands to list available Python versions, install Python 3.8.10, and check installed versions:
```powershell
pyenv install -l
pyenv install 3.8.10
pyenv versions
```

## **8. Create a Virtual Environment**
Navigate to your project's folder and run:
```powershell
pyenv local 3.8.10
python -m venv .vs_prj
.vs_prj\Scripts\activate
```

## **9. Open in Visual Studio Code**
Execute the following command to open your project directory in Visual Studio Code:
```powershell
code .
```

## **10. Install Project Requirements**
If you have a `requirements.txt` file with dependencies listed, install them using:
```powershell
pip install -r .\requirements.txt
```

---
