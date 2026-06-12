---
title: "Verizon Wireless with Kyocera KPC650"
date: 2008-05-31
forum: Hardware
---

### Post by Roy Sanders on 2008-05-31
I am not an Linux expert, just getting started, getting away from MS.  What a relief.  This is in response to EVDO users. Specifically for the KPC650. Should work for other similar data cards as well.  


THE FOLLOWING INSTRUCTIONS ARE FOR THE KPC650 AND VERIZON, OTHER DATA CARDS SHOULD RESPOND THE SAME, ONLY WITH DIFFERENT DEVICE ID CODES. 

 	1. Use Super User mode for the following, otherwise you will not be allowed to save the files:

	roy@xxx-desktop:~$ su root (Enter) 
	Password: xxxxxxx (Enter)

	2. You need to do a 'lsusb' to get the vendor/product id such as:

 
	root@xxx-desktop:/home/xxx# lsusb (Enter)
	Bus 006 Device 001: ID 0000:0000  
	Bus 005 Device 002: ID 0c88:17da Kyocera Wireless Corp. 
	Bus 005 Device 001: ID 0000:0000  
	Bus 004 Device 006: ID 040d:6205 VIA Technologies, Inc. 
	Bus 004 Device 005: ID 046d:c51b Logitech, Inc. 
	Bus 004 Device 004: ID 413c:5103 Dell Computer Corp. 
	Bus 004 Device 003: ID 046e:52c4 Behavior Tech. Computer Corp. 
	Bus 004 Device 002: ID 2001:f103 D-Link Corp. [hex] 
	Bus 004 Device 001: ID 0000:0000  
	Bus 003 Device 001: ID 0000:0000  
	Bus 002 Device 001: ID 0000:0000  
	Bus 001 Device 001: ID 0000:0000


	3. Bus 005 Device 002: ID 0c88:17da Kyocera Wireless Corp. (write down the ID xxxx:xxxx)



	4. Next, modprobe your new usbserial module  

	root@xxx-desktop:/home/xxx# modprobe usbserial vendor=0xc88 product=0x17da maxSize=2048 (Enter)


	If modprobe command doesn't create /dev/ttyUSB0 and /dev/ttyUSB1 on it's own, execute the following:


	root@xxx-desktop:/home/xxx#mknod /dev/ttyUSB0 c 188 0 (Enter)

	root@xxx-desktop:/home/xxx#mknod /dev/ttyUSB1 c 188 1 (Enter)
  
	
	5. The /etc/wvdial.conf file needs to be modified to access your KPC 650.
	root@xxx-desktop:/home/xxx#gedit /etc/wvdial.conf (Enter)(Enter) (gedit is gui editor that may be used in Terminal mode)

   	Delete contents of wvdial.conf and enter the following lines and save:

	[Dialer Verizon] 

	Phone = #777 

	Password = xxxxxxx  (your ISP password)

	Username = [email]xxxxxxxxxx@verizon.net[/email] (your ISP username)

	[Dialer prl-update] 

	Password = xxxxxxx  (your ISP password)

	Username = [email]xxxxxxxxxx@verizon.net[/email] (your ISP username)

	[Dialer Defaults] 

	Modem = /dev/ttyUSB0 

	Baud = 115200 

	Init = ATZ 

	Dial Command = ATDT 

	Stupid mode = 1

	6. Create a batch file with the following lines: I located mine on the Desktop for easy access.

	modprobe usbserial vendor=0c88 product=0x17da maxsize=2048
	wvdial Verizon

	7. Save as: 'Verizon", and under file properties/permissions ,select 'Execute: x  Allow executing file as program.'

	This file is used for connection and/or reconnection:

	It can also be placed in System/Preferences/Sessions to connect at system startup.

 	Click on the "Verizon" batch file, select "Run In Terminal", the following code should appear in the Terminal Screen:

	WvDial<*1>: WvDial: Internet dialer version 1.56
	WvModem<*1>: Cannot get information for serial port.
	WvDial<*1>: Initializing modem.
	WvDial<*1>: Sending: ATZ
	WvDial Modem<*1>: ATZ
	WvDial Modem<*1>: OK
	WvDial<*1>: Modem initialized.
	WvDial<*1>: Sending: ATDT#777
	WvDial<*1>: Waiting for carrier.
	WvDial Modem<*1>: ATDT#777
	WvDial Modem<*1>: CONNECT
	WvDial<*1>: Carrier detected.  Starting PPP immediately.
	WvDial<Notice>: Starting pppd at Sat May 31 18:52:07 2008
	WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
	WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
	WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
	WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
	WvDial<Notice>: Pid of pppd: 6957
	WvDial<*1>: Using interface ppp0
	WvDial<*1>: local  IP address 98.132.168.250
	WvDial<*1>: remote IP address 75.116.236.196
	WvDial<*1>: primary   DNS address 166.102.165.11
	WvDial<*1>: secondary DNS address 166.102.165

 	If the above (or similar) is displayed in the terminal screen you should be connected to the web, ignore the errors in the code. When executing in user 	mode, these errors will appear, do not worry about them, Start your browser to see if the connection was completed.


Good luck, let me know if this works for you....

---

### Post by Joeb454 on 2008-05-31
It would if it was 2006 ;)

In all honesty - I doubt the OP is on the forums anymore.

---

### Post by bapoumba on 2008-06-01
Moved to its own thread in the support area. These posts were originally [here]("http://ubuntuforums.org/showthread.php?t=157113"), answering an old thread in the archive section.

---

