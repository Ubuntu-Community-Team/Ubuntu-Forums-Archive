---
title: "How-to Install Trendnet TEW-423 PI Wireless Card in XUbuntu"
date: 2007-04-03
forum: Hardware &amp; Laptops
---

### Post by PhillD on 2007-04-03
After jumping through numerous posts on this forum to get my wireless card working, I have decided to write out the steps which worked for me in XUbuntu.  Hopefully this can save someone a lot of time and pain in getting their wireless working.  Before I start though, I just want to let you know that I am pretty new to Linux so any support I can offer will be very limited.

Ok, here we go.

1.  Don’t make the mistake I did, printed on the front of my wireless card is “Rev:A2”.  This is  NOT the card revision number.  Look on the back, there should be a sticky label with something like “TEW-423PI H/W:B1” printed on it.  The characters after H/W: are your revision number and in my case B1.  This is VERY useful for the next step.

2.  Go to the trendnet.com website and download the windows driver for the card.  It will ask you which revision of the card you have.  Select the correct one.

3.  Unzip the downloaded files into a folder in your home directory called tnet.

4.  To make life easier later, we are going to rename a directory.  Using thunar file manager, find the tnet folder you just created and then go to the Drivers directory.  You should see a folder called Windows XP.  Rename this folder to WindowsXP (remove the space).

5.  Next we need to install ndiswrapper for XUbuntu.  Open synaptics packet manager and ensure all the repositories are enabled.  (This is in settings-->repositories.  Remember to hit the reload button after you have enabled them.)

6.  Do a search for ndiswrapper and once found, mark ndiswrapper-utils-1.8 for installation.  Click apply.

7.  Next we will install the Windows Xp wireless card driver.  Open the terminal and type:
```
sudo ndiswrapper -i ~/tnet/Drivers/WindowsXP/Mrv8000c.INF 
```

8.  Check that the driver and hardware is detected by typing:
```
ndiswrapper –l
```

You should get something similar, if not identical to:
```
Installed ndis drivers:
mrv8000c                driver present, hardware present
```
	
9.  Open thunar again this time with root privileges (it saves messing around in the console too much) To do this, type the following into the terminal:
```
gksudo thunar
```

10.  Find the file /etc/network/interfaces and open it.  (Because you are logged in with root privileges you will be able to modify and save this file without problems).  Add the following lines after the comments at the top of the file (if there are any at all):
```
#The Primary network interface	
Iface wlan0 inet dhcp
```

Important!  There may be another wlan0 entry at the bottom of the file listed as
```
auto wlan0
Iface wlan0 inet dhcp
```

If this exists, comment it out by adding a # in front of each line or delete them.

11.  Save the file, close mouse pad and close thunar.

12.  Go back to the terminal and enter the command:
```
sudo modprobe ndiswrapper
```.
This does a bunch of stuff like enabling the device to show up in the Network Settings.

13.  Go to System-->Networking  you should see the wireless card and can begin to configure it for your particular wireless setup.  Once setup, disable any wired connections you have or just unplug the Ethernet cable.

14.  Test the connection by surfing the web.

15.  Next we need to enable the device to run on startup.  Go to the terminal and type:
```
sudo ndiswrapper –m
```

16. Next we need to open thunar again with root privileges (as described in step 8 ).  Find and open the file /etc/modules and add the line:

```
ndiswrapper
```

at the bottom.  Save and close the file.

17.  Restart the computer

18.  Re-test the internet connection and ensure the wireless card is still listed in the Network settings.

That's it, your all done, hopefully this has successfully setup your wireless card.  I went back through this step by step on a fresh install and it worked so there should not be anything missing from the instructions.  The one thing I will note is that once the wireless card is enabled, your boot process may take a little longer.  I don’t know why this is, perhaps it is wireless association and IP address allocation but it’s something I am willing to live with.

Again, I hope this has helped.

Phill D

---

