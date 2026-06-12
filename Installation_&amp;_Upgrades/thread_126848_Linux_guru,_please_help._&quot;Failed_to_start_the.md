---
title: "Linux guru, please help. &quot;Failed to start the X server&quot;"
date: 2006-02-07
forum: Installation &amp; Upgrades
---

### Post by PandaToledo on 2006-02-07
I'm a novice in Linux world. I just received the free install CD from ubuntu and tried to install a dual boot system to my Toshiba A105-S101 laptop in addition to the current operating Windows XP Home system.

After successfully installed the ubuntu system, I can only run the system in command line mode because of the following problems occured before I logged into the system:

- "[COLOR="Red"]Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?[/COLOR] <Yes> <No>"

After choosing <Yes>, the following shows up:

- "X Windows System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux panda 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
Before reporting problems, check [http://wiki.X.org](http://wiki.X.org) to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8 )) #1 Mon Oct 10 13:14:36 BST 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
<Ok>"

After click <Ok>, it asks:

- "Would you like to view the detailed X server output as well? <Yes> <No>"

Selection of <Yes> gives the same response as above:

- "X Windows System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux panda 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
Before reporting problems, check [http://wiki.X.org](http://wiki.X.org) to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8 )) #1 Mon Oct 10 13:14:36 BST 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
<Ok>"

And then it shows:

- "[COLOR="red"]The X server is now disabled. Restart GDM when it is configured correctly[/COLOR]. <Ok>"

After that, I can only see the command line interface:

- "Ubuntu 5.10 "Breezy Badger" panda tty1
panda login: _"

I have checked ubuntu's website, but cannot find the solution to this problem. Please help! TIA!

PS: The laptop specification:
- Processor: Intel Celeron M 1.6GHz
- Display Type WXGA widescreen active-matrix TFT-LCD with TruBrite technology (1280 x 800)
- Screen Size 15.4"
- System Bus 400MHz
- Cache Memory 1MB on die Level 2
- System Memory (RAM) 256MB + 512MB (added) PC4200 DDR2 SDRAM
- Hard Drive Type SATA (5400 rpm) 60GB
- Optical Drive DVD-ROM/CD-RW
- Graphics ATI Mobility RADEON XPRESS
- Video Memory 64-128MB (shared)
- Modem 56 Kbps* ITU V.90 *Capable of receiving 56 Kbps downloads. However, current regulations limit download speed to 53 Kbps.
- Networking Built-in 10/100Base-TX Ethernet LAN (RJ-45 connector); V.90 high-speed modem
- Wireless Networking Built-in Atheros high-speed wireless LAN (802.11b/g)
- Operating System Windows XP Home

---

### Post by kaamos on 2006-02-07
Hello!

Login and try this -> [http://ubuntuforums.org/showpost.php?p=710762&postcount=2](http://ubuntuforums.org/showpost.php?p=710762&postcount=2)
The "vesa" driver is a backup solution and hopefully "ati" could work for you as well.

Good luck.

---

### Post by PandaToledo on 2006-02-07
Then I have followed these 2 posts to upgrade the ATI driver:

[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

[http://www.ubuntuforums.org/showthread.php?t=75378](http://www.ubuntuforums.org/showthread.php?t=75378)

I used the following codes in the command line interface

```
sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg
```

It successfully removed the old drivers and downloaded the new drivers using the autodetected internet connection. However, another problem occurs when I reconfigure the xserver, I used all the defaults values, except specified [COLOR="royalblue"]**64000K**[/COLOR] in Video RAM, and **[COLOR="royalblue"]No[/COLOR] **to monitor autodetection.

When I choose the color depth, no matter what I choose, (choices are: 1, 4, 8, 15, 16, 24 bits), the configuration stops and jumped back to command line interface, and showing an error message of:

[COLOR="Red"]"xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.200602071512[/COLOR]

If I restart from here, the problem in the first post is still there.

Please help.

Thanks in advance.

---

### Post by PandaToledo on 2006-02-07
[QUOTE=kaamos]Hello!

Login and try this -> [http://ubuntuforums.org/showpost.php?p=710762&postcount=2](http://ubuntuforums.org/showpost.php?p=710762&postcount=2)
The "vesa" driver is a backup solution and hopefully "ati" could work for you as well.

Good luck.[/QUOTE]

Hi kaamos, thanks for your reply.

I tried your suggestion, and tried both "ati" and "vesa" as the video driver.

However, the new problem happens, as stated in my second post.

When come to reconfigure color depth, no matter what I choose, the configuration halted with an error message:

[COLOR="Red"]"xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.200602071512"[/COLOR]

P.T.

---

### Post by tseliot on 2006-02-07
> **PandaToledo][COLOR="Red"]"xserver-xorg postinst warning: overwriting possibly-customised configuration file said:**
> 
This just warns you that it's overwriting your xorg.conf. In other words it's not a problem.

Do this:
sudo nano /etc/X11/xorg.conf

then scroll down the file and get to the Section "Device"
and set the driver to "vesa" like in the following example:
```
Driver		"vesa"
```

Press:
CTRL+O to save the file (yes, overwrite it)
CTRL+X to exit

then type:
sudo /etc/init.d/gdm stop (or "kdm stop" if you use Kubuntu)
sudo /etc/init.d/gdm start (or "kdm start" if you use Kubuntu)

---

### Post by arckeda on 2006-02-07
Try vesa or the other v one then after selecting type:
startx

---

### Post by PandaToledo on 2006-02-07
[QUOTE=tseliot]This just warns you that it's overwriting your xorg.conf. In other words it's not a problem.

Do this:
sudo nano /etc/X11/xorg.conf

then scroll down the file and get to the Section "Device"
and set the driver to "vesa" like in the following example:
```
Driver		"vesa"
```

Press:
CTRL+O to save the file (yes, overwrite it)
CTRL+X to exit

then type:
sudo /etc/init.d/gdm stop (or "kdm stop" if you use Kubuntu)
sudo /etc/init.d/gdm start (or "kdm start" if you use Kubuntu)[/QUOTE]

Hi tseliot, thanks for your reply. 

The reason I thought the overwriting message is an error message is because the same problem as stated in post #1 still exist after I restart. (Using Ctrl + Alt + Del)

I followed the steps in your post:

After putting the code:

sudo nano /etc/X11/xorg.conf

I can read the entire file, however the Driver is already set as "vesa" in the "Device" Section as follows:
Identifier "ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
Driver "vesa"
BusID "PCI:1:5:0"

So I saved the file using Ctrl + X.

Then, 
sudo /etc/init.d/gdm stop 

got response:
* Stopping GNOME Display Manager... [ok]

However, the next line of code
sudo /etc/init.d/gdm start 

cause the similar problem as in post #1, the difference is, now it first showing error message:

- "[COLOR="Red"]The X server is now disabled. Restart GDM when it is configured correctly.[/COLOR] <Ok>"

Then showing the following:
- "[COLOR="red"]Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?[/COLOR] <Yes> <No>"

Is there any other alternatives to change in the configuration files? If needed, I can post the entire configuration file in text format.

Thanks.

P.T.

---

### Post by PandaToledo on 2006-02-07
[QUOTE=arckeda]Try vesa or the other v one then after selecting type:
startx[/QUOTE]

Hi arckeda, thanks for your reply.

I don't know if I understand your suggestions correct? Should I use other display driver starts with "v", such as, "vga", "via", "vmware"?

Once configuration files is saved, using "startx" to load the X server?

P.T.

---

