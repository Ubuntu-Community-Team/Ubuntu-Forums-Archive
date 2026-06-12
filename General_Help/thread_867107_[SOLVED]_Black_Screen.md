---
title: "[SOLVED] Black Screen"
date: 2008-07-22
forum: General Help
---

### Post by bj218 on 2008-07-22
Ubuntu 8.04 Black screen Problem
This morning I tried to change the screen resolution from640/480 and found that I could not change it?
I then tried to change the screen appearance from None to Normal I then got a window that said I had to enable the NVIDIA driver I clicked ENABLE DRIVER  then I got a window that said  “Please run appearance/desktop effects again after restarting the computer when the new graphics driver is active”. On restart everything looked good  until I entered my ID and PW then the screen went BLACK and that was it!! The last 2 times that I tried to boot Ubuntu I got the Ubuntu logo and a progress bar which seemed to go all the way but then the black screen no request for an ID or PW.  Could Ubuntu have installed my WindowsXP Nvidia driver? What can I do to remove the Nvidia driver if it is the problem I don't know how to overcome the BLACK screen.

---

### Post by pauper on 2008-07-22
Turn your computer on. At GRUB menu press ESC key. Select "(recovery mode)".
Press Enter. Login.

Find out about your video card:

```
lspci | grep -i Display
```

See what driver is currently in use for X session:

```
grep -iC 3 pci /etc/X11/xorg.conf
```

All available video drivers are here:

```
ls /lib/modules/`uname -r`/kernel/drivers/video
```

Backup your current xorg.conf

```
sudo cp /etc/X11/xorg.conf{,.bak}
```

Create new xorg.conf, choose another video driver.
Note: Usually the name of the video driver corresponds to the name of the card,
i.e. select "intel" for "Intel Corporation Mobile GM965..." You may try some
other generic drivers (vesa, vga...).

```
sudo dpkg-reconfigure xserver-xorg
```

Reboot:

```
sudo shutdown -r now
```

---

### Post by bj218 on 2008-07-23
> **pauper said:**
> Turn your computer on. At GRUB menu press ESC key. Select "(recovery mode)".
Press Enter. Login.

Find out about your video card:

```
lspci | grep -i Display
```

See what driver is currently in use for X session:

```
cat /etc/X11/xorg.conf | grep -iC 3 pci
```

All available video drivers are here:

```
ls /lib/modules/`uname -r`/kernel/drivers/video
```

Backup your current xorg.conf

```
sudo cp /etc/X11/xorg.conf{,.bak}
```

Create new xorg.conf, choose another video driver.
Note: Usually the name of the video driver corresponds to the name of the card,
i.e. select "intel" for "Intel Corporation Mobile GM965..." You may try some
other generic drivers (vesa, vga...).

```
sudo dpkg-reconfigure xserver-xorg
```

Reboot:

```
sudo shutdown -r now
```
Something I should have included in my original post is that I know almost nothing about the Linux  OS. I know a little about grub and that is it. Also on my computer I have 2 SATA drives, 1 has WindowsXP prof. The other has Mint and Ubuntu 8.04.Mint is root. 

I have a question about the commands you gave me shouldn't they all begin with sudo?

Here is what I did this morning. MY boot sequence is Mint/Windows/Ubuntu. AT boot up I highlited Ubuntu 8.04 and pressed ENTER when it started to boot Ubuntu I pressed ESC and I got a window that said EXITING  under neath this was the following &#8220;You are leaving the graphical boot menu and
starting the text mode interface&#8221; I clk OK. The next window I got was blue and it listed 3 Mint options 1 windows and 5Ubuntu options, I highlighted the Ubuntu 8.04 recovery mode and pressed ENTER 
then a number screens went by very fast at the end I got a screen called RECOVERY MENU I highlighted the  &#8220;Try to fix X server&#8221; and pressed ENTER. The next window said &#8220;the X server
reconfiguration is now running&#8221; your screen may flicker during autodetection, in a few seconds it came back to the Recovery Menu this time I selected RESUME NORMAL BOOT and pressed ENTER. I am not sure why I made the above decisions maybe you can tell me what went on!!
After I pressed that last enter it did just that it booted to Ubuntu8.04 and every thing looked great.
I can now even set the screen resolution on boot up it was set at 1024x768. I restarted it 2 more times today and every thing worked. I do not understand how doing the above things fixed my problem,but I am not complaining.
I sure appreciate your help.  THANKS bj218

---

### Post by pauper on 2008-07-23
> I have a question about the commands you gave me shouldn't they all
begin with sudo?
As long as you have permission to access (ls) and read (cat, grep) you run them
as a regular user. See "man chmod".

```
ls -l /etc/X11/xorg.conf
-rw-r--r-- ...
```

Now in this case only root is permitted to write to /etc/X11 directory, i.e.
"sudo cp /etc/X11/xorg.conf{,.bak}"

```
ls -l /etc | grep X11
drwxr-xr-x ...
```  

"lspci" and "uname" are both informational (but this does not state that it
applies to all: sudo lshw, sudo dmidecode, etc.)  and run as regular user.

"dpkg-reconfigure" and "shutdown" are always run as a root.

> ...highlighted the "Try to fix X server..."

Here you let the system to recover itself up, i.e. to set any offending custom
settings back to default. I just provided a manual way to deal with it.

---

### Post by bj218 on 2008-07-24
I went to the Nvidia site and they have a Linux driver for my video card.
How can I get Ubuntu to install it? I have made copies of your ommands
for my future ref. I think they may come in handy someday. It was realy nice that you explaied the purpose of each one. Thank You bj218
PS I certanily did learn a few things in this exercise.

---

### Post by pauper on 2008-07-24
You can get all the detailed information about installation and running
routines from the NVidia website.

---

