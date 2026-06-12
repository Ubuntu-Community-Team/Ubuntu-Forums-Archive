---
title: "Solved - GUI Interface for Verizon PC5750"
date: 2008-04-22
forum: Hardware
---

### Post by blakesle on 2008-04-22
I have spent the last 3 days setting up the Verizon PC5750 PCMCIA card to link into their broadband system. I have been very successful and wanted to put together a how to for this since I had to pull bits and pieces together from several posts. 

I used information from the following articles and posts:

[http://www.linux.com/feature/52729](http://www.linux.com/feature/52729)
[http://ubuntuforums.org/showthread.php?t=515922](http://ubuntuforums.org/showthread.php?t=515922)
[http://ubuntuforums.org/showthread.php?t=343989&page=4](http://ubuntuforums.org/showthread.php?t=343989&page=4)
[http://howtoforge.com/connecting-gprs-from-ubuntu-gutsy](http://howtoforge.com/connecting-gprs-from-ubuntu-gutsy)

1. Authorize your PC5750

You need to use the VZAccess software provided with the card to authorize its use. This can be done on a Apple Mac Laptop or a PC Laptop. 

Do not insert the card yet.  

Install the appropriate version of the VZAccess software on the laptop and follow the instructions. When you are finished you will get the message that the card has been authorized for use. This must be done prior to setting up the card on Linux.

2. On your Ubuntu Linux Laptop (mine is an Acer Aspire 3680)

Install Gnome-ppp

go to System -> Administration -> Synaptic Package Manager 

Do a search on GNOME-PPP and install it.

Insert the PC5750 PCMCIA Card.

Run GNOME-PPP from Applications -> Internet
Username = 10 digit phone number provided by Verizon
Password = VZW
Phone Number = #777

For convenience I checked "Remember Password"

Click on Setup

With the card in place click on "Detect"

You should then pick up the device at /dev/ttyACM0 (If you do not go to the information below on setting up ttyACM0.)

Type is Analog Modem

Speed is 460800

Unclick "Wait for Dial Tone"

Click on "Networking".
Should be set to "Dynamic IP Adress"
Should be set to "Automatic DNS"

Click on "Options"

Check "Dock in Notification Area" 

This will provide you with a nice Icon showing that you are connected and blinking blue when data is being transferred. 

Make sure of the following

Uncheck Auto Reconnect
Check Abort Connecting if line is busy
Check Abort Connecting if no dialtone
Uncheck Check Carrier Line
Check Check Default Route
Check Ignore Terminal Strings (stupid mode)
Uncheck Send Custom Reply

Close Setup 

Quit GNOME-PPP

On desktop click in some open area.

Click on "Create Launcher"

Type is "Application"
Give the launcher a Name you like. I use "GNOME-PPP"
**Command is "gksu gnome-ppp" This is very important as it is what allows the command to be launched as Root. VERY IMPORTANT!!!**

If you like type in a comment.

Click on OK and this will create a Launcher on your desktop.

Assuming everything went as stated you should now be able to launch your connection to Verizon Broadband. Very cool!


**How to set up ttyACM0 **

Code:

# mknod /dev/input/ttyACM0 c 166 0

Enoy!

---

