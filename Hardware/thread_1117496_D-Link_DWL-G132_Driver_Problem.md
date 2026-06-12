---
title: "D-Link DWL-G132 Driver Problem"
date: 2009-04-06
forum: Hardware
---

### Post by dasme on 2009-04-06
> **Onay said:**
> This is just a little howto I'm writing for people that have this specific usb wireless card and want to get it working in the Gutsy Gibbon release. This involves getting the ndiswrapper source and compiling it, so a few extra steps will be needed.

Things you need before you start...
[LIST=1]
[*]Gutsy Gibbon Live CD
[*]Computer with working internet (doesn't need to be the one you're installing this on)
[/LIST]

[SIZE="5"]Compile Ndiswrapper[/SIZE]
1. On the computer you have with the internet, download the ndiswrapper-1.47 source (I found that 1.48 causes lock-ups in Gutsy). Link below
[http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=internap&filename=ndiswrapper-1.47.tar.gz&980135](http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=internap&filename=ndiswrapper-1.47.tar.gz&980135)
Store that on an external usb drive and transfer to the dwl-g132 computer's **Desktop**

2. Insert the Gutsy CD into the dwl-g132 computer.

3. Open up Terminal and execute the following to get compiling tools for the source
```
sudo apt-get install build-essential
```
4. Change directory to the desktop, untar ndiswrapper, and change to the ndiswrapper directory
```
cd ~/Desktop
tar zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
```
5. Run the following commands to install ndiswrapper
```
make uninstall
make
sudo make install
```
[SIZE="5"]
Install the drivers
[/SIZE]
6. Download the following drivers on the internet computer from this link
[ftp://ftp.dlink.com/Wireless/dwlg132/Driver/dwlg132_drivers_121.zip](ftp://ftp.dlink.com/Wireless/dwlg132/Driver/dwlg132_drivers_121.zip)

7. Transfer these to the **desktop** of the dwl-g132 computer and unzip them there.

8. Go into the extracted directory and find the "Drivers" directory. Copy this to your desktop. You can delete the other folder if you wish, but keep the "Drivers" directory on your desktop.

9. Install the drivers by executing the following commands
```
cd ~/Desktop/Drivers
sudo ndiswrapper -i athfmwdl.inf
sudo ndiswrapper -i NetA5AGU.inf
sudo depmod -a
sudo modprobe ndiswrapper
```
10. Your little lights on the adapter should be blinking and you can now select your wireless connection in the network manager on your toolbar.

11. If everything worked, save your wlan alias...
```
sudo ndiswrapper -m
```
12. Now make it so that the ndiswrapper module is loaded with the kernel on startup...
```
sudo gedit /etc/modules
```
Add the line "ndiswrapper" (no quotes) at the end of the text file and save it.

That should be it. Let me know if I left out something

Hi 
i followed this tutorial and everything worked, i also added ndiswrapper in last line as mentioned in step 12.

i restarted the system, and after restart it stopped working.

tell me guys what should i do to fix this problem.

Thx

---

### Post by dasme on 2009-04-06
Help pls

---

### Post by dasme on 2009-04-06
Bump!

---

