---
title: "Kodak essp 5250 does print but does not scan, what to do?"
date: 2014-04-14
forum: Hardware
---

### Post by 171742 on 2014-04-14
Hello,

thats the exact problem. Simplescan does not get it. Tried all google puts out, nothing works:

[http://forums.linuxmint.com/viewtopic.php?f=42&t=113757](http://forums.linuxmint.com/viewtopic.php?f=42&t=113757)
[http://ubuntuforums.org/showthread.php?t=1711141](http://ubuntuforums.org/showthread.php?t=1711141)
[http://askubuntu.com/questions/182421/kodak-esp-aio-prints-good-on-ubuntu-12-04-butnothing-finds-the-scanner-any-ide](http://askubuntu.com/questions/182421/kodak-esp-aio-prints-good-on-ubuntu-12-04-butnothing-finds-the-scanner-any-ide)

I have ubuntu 12.4 on asus a6rp.

Any idea?

Thanks!

---

### Post by paulnewall on 2014-04-16
You may get suggestions to install the sane backend kodakaio from the sane site or from sourceforge. Don't do this except as a last resort because it is difficult to install sane-backends correctly and ubuntu 12.04 should have a working version of sane-backends that includes kodakaio.

It could be useful to know how you are connecting the printer, USB or network?

First try to debug the sane-backends that you already have.
Try the ideas below:
How to set up Kodak ESP scanning in Ubuntu 12.10  version 1, 15 jan 2013

I am using a live DVD to be sure I do not have anything that does not come with an initial installation of Ubuntu 12.10

My printer is a Kodak ESP 5250 using the WiFi network connection.

1. Check the necessary packages are installed as follows. This step is not needed if you have not installed or removed any package listed here.

Start Ubuntu Software Center
Type sane into the search box
Click show xx technical items
Check that the following packages have a tick showing they are installed:
Simple Scan
libsane-common
sane-utils
libsane

Close Ubuntu Software Center.

2. Connect and switch on your printer.

If you use the network connection you need to set up the connection to your wireless network using the printer front panel. You need to know the IP address of the printer, which you should be able to get via the front panel.
If you use usb go straight to step 4.

3. (If you have the printer connected via usb you can ignore this step)
Now we will edit the configuration file for the scanner backend (kodakaio)
Start Dash Home
type terminal into the search box
run terminal
at the prompt in terminal type 
sudo gedit /etc/sane.d/kodakaio.conf
In the text editor gedit scroll down to the bottom of the kodakaio.conf file and find the usb id for your printer, for example my ESP 5250 has id 0x4041
Then scroll up to a line like:
#net 192.168.1.17 0x4067
Add a similar line, omitting the # at the start, and giving your IP adress and usb id for example:
net 192.168.1.3 0x4041
Save the file.
Close gedit.

In terminal you can check that the scanner can be detected by typing
scanimage -L
which should give a response like
device `kodakaio:net:192.168.1.3?model=0x4041' is a Kodak KODAK ESP 5200 Series AiO flatbed scanner
Close terminal

4.
Start Ubuntu Software Center
Type simple into the search box
Run simple-scan
Click on the scan button, and you should get a scan. It will be blank if you have no document on the flatbed.

---

