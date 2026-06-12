---
title: "Stylus not working Gateway CX210X Tablet PC - Finepoint drivers."
date: 2008-04-30
forum: Hardware
---

### Post by rtandon87 on 2008-04-30
Hi,

I really want to get the tablet PC functionality on my Gateway Tablet PC - CX210X in Ubuntu 8.04... (which used to work perfectly under Windows)

So far, I have tried the following:

I installed xserver-xorg-input-fpit and setserial using Synaptics Package Manager.

Then I added the following to my /etc/xorg.conf file:
Section "InputDevice"
Identifier "Tablet"
Driver "fpit"
Option "Device" "/dev/ttyS0"
Option "AlwaysCore" "on"
Option "InvertY"
Option "MaximumXPosition" "12550"
Option "MaximumYPosition" "7650"
Option "MinimumXPosition" "400"
Option "MinimumYPosition" "400"
Option "SendCoreEvents"
EndSection

InputDevice "Tablet"      ----      to the server layout section

Then I created /etc/serial.conf and added the following to it:
/dev/ttyS0 port 0x03F8 irq 4 baud_base 38400

Also, I went to System->Administration->Services and checked etc-setserial

After that I restarted my computer and noticed that as soon as I touch my stylus to the screen, THE SCREEN GOES BLACK/GRAY.  I have to force shut down the computer at this point..
When I restored my xorg.conf file back to original that problem went away..

PLEASE LET ME KNOW HOW CAN I GET MY STYLUS TO WORK IN GATEWAY CX210X.

Rajat

---

### Post by PerfectSine on 2008-08-31
I've got this tablet as well. I'd be interested in hearing if anyone has been able to get the stylus working...

---

### Post by Aesir on 2008-09-02
I have the CX210X w/ Vista Ultimate.  I've recently considered linux for it but held off completely due to Vista providing better support for this laptop's features (display panel feature buttons, pen stylus, voice and writing recognition, battery/power management, etc.).

However, I've also just discovered wubi at [http://wubi-installer.org/](http://wubi-installer.org/) and have just downloaded/installed it.  I've booted into Ubuntu 8.04.1 and am currently downloading default updates available through Update Manager.  The stylus was not detected yet, but I will see if it is after the updates complete.  [Edited: The key point being that you can work to sort out driver/hardware/software support problems without impacting the windows install.  If, at the end of testing, you decide to stay with Windows, you can just uninstall wubi.]

From there, we can inventory exactly which features aren't available and provide information to help with either locating 3rd party updates/patches or request the features be implemented through ubuntu.

[Update: Google on 'finepoint drivers for linux' nets a ton of links, including:
[http://ubuntuforums.org/showthread.php?t=146279&page=3](http://ubuntuforums.org/showthread.php?t=146279&page=3)
I've not yet followed those instructions or downloaded the linked finepoint drivers, I'm still just applying patches/updates for the current standard install I'm working on.]

---

### Post by dragon_788 on 2008-10-21
I haven't tried again with Ubuntu recently, but I can say under openSuse 10.3 (for sure) and 11 (iirc) my tablet functions work perfectly. I can configure everything through yast and use the pen in Xournal and other applications quite well as a pointing device. I have the CX210X with a pretty standard configuration that I'll probably be going back to openSuSE on again soon as I enjoy having everything working without the Windows bloat.

---

