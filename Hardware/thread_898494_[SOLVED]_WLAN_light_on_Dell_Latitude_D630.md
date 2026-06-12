---
title: "[SOLVED] WLAN light on Dell Latitude D630"
date: 2008-08-23
forum: Hardware
---

### Post by MicheleZ on 2008-08-23
Hello,

I have just installed Ubuntu on a Dell Latitude D630 equipped with this Intel WLAN card:
Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

The WLAN works fine, however the LED is not lit even if the WLAN is on.  
This is a very minor thing, still something I wouldn't mind to have fixed.

A single switch operates both the bluetooth and the WLAN and the bluetooth light works as it should.

I looked into /etc/acpi and the wireless script points to 
/usr/share/acpi-support/state-funcs 
where there's a function specific for asus-laptops and for ibm-thinkpads but nothing for dells.

Anybody knows how to get the LED light to come on?

Cheers,

Michele

---

### Post by rmaultz on 2008-09-21
To get  the  wlan  light  you have to use the  dell driver  or  follow  these instructions  

===============================
Here is the instructions to instal the 1490  and the 1505  agn Dell wireless in kubuntu   this  can be technicial  but this is what i found works  

 

Here is the best write up on using ndis wrapper.

 

IF you need more like the whole extracting it..let me know.

 

3.4. Installing Windows driver 3.4.1. Installing Windows driver using ndisgtk (ndiswrapper graphical interface)
·         If you chose to install ndisgtk, the graphical interface for ndiswrapper, after installation click on System | Administration | Windows wireless drivers and follow the instructions on-screen. For an idea of what to expect, some screenshots of ndisgtk can be found here.

If this works, and you have a network connection, then you can skip to Automatically loading at Startup - ndisgtk will load the driver if it installs correctly.

3.4.2. Installing Windows driver using command line
In a Terminal, run the following command:

·           sudo ndiswrapper -i ~/drivers/drivername.inf
(assuming the driver is in a directory in your home folder called drivers, and is named drivername.inf)

ndiswrapper then copies the .inf and sys files into /etc/ndiswrapper/.... Don't forget that the filename you type in is case-sensitive.

3.4.2.1. Check to make sure the driver was installed correctly
Run the following command from a Terminal:
  ndiswrapper -l
If the driver is installed correctly, you should see the following output:

  Installed ndis drivers:
  {name of driver} driver present, hardware present
or

  {name of driver} : driver installed
       device ({Chipset ID}) present
If you don't see this message:

a.       Try a different driver such as the drivers for Windows 2000, or another driver matching the PCI ID on the ndiswrapper list.

b.      This document has a troubleshooting section which may provide an answer.

c.       Look for additional help. Read HowToGetHelp for more information.

3.5. Load the new driver module
If ndiswrapper correctly associates the driver to the wireless adapter, you are now ready to load the driver into memory, and try to establish a network connection. Open a Terminal and run the following commands:
·           sudo depmod -a
  sudo modprobe ndiswrapper
Then, also in a Terminal, check for error messages:

  tail /var/log/messages
Alternatively, open a Terminal and try the commands ifconfig and iwconfig. Your wireless card should appear with an interface name of wlan0. If it doesn't appear here, then the driver is not working properly. If no errors are given, you should now be able to configure the network connection.

---

### Post by IntuitiveNipple on 2008-09-21
I've built the iwl3945 driver with LED support and created a DKMS package, see the thread "[iwl3945/iwl4965 with LED support, Hardy DKMS package](http://ubuntuforums.org/showthread.php?t=924629)" for details of how to install it.
Please report in that thread if it works (or doesn't) with that system.

---

### Post by MicheleZ on 2008-09-24
Hello TJ,

Since posting I installed the backports and the WLAN LED started to work so I am now a bit reluctant to change things again. 

As I am not an expert I have a question: If I try to install iwl-led-dkms and discover that it does not work, is it sufficient to uninstall to revert to the current configuration?

Will mark the thread as solved as soon as I find out how :-)

Cheers,

Michele

---

