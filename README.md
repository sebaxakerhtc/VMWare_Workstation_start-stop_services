# VMWare_Workstation_start-stop_services
Start/Stop VMWare Workstation Services on Windows
Tested on Windows 10 Pro (x64) | VMware® Workstation 16 Pro

Start-Stop_VMWare.bat (Run as Administrator)

    @echo off
	  sc config "VMware Workstation Server" start= demand
	  sc config "VMware NAT Service" start= demand
	  sc config "VMUSBArbService" start= demand
	  sc config "VMnetDHCP" start= demand
	  sc config "VMAuthdService" start= demand
    echo Start/Stop VMware Workstation services
    echo.
    echo 1. Start
    echo 2. Stop
    echo.
    choice /c:12

    If errorlevel 1 if not errorlevel 2 goto start
    If errorlevel 2 if not errorlevel 3 goto stop

    :start
    echo.
    net start "VMware Workstation Server"
    net start "VMware Authorization Service"
    net start "VMware NAT Service"
    net start "VMware DHCP Service"
    net start "VMware USB Arbitration Service"
    goto end

    :stop
    echo.
    net stop "VMware Workstation Server"
    net stop "VMware Authorization Service"
    net stop "VMware NAT Service"
    net stop "VMware DHCP Service"
    net stop "VMware USB Arbitration Service"
    goto end

    :end
