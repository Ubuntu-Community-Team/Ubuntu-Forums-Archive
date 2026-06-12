---
title: "Black Screen White Cursor"
date: 2008-11-23
forum: General Help
---

### Post by Oliverl on 2008-11-23
Hey

I Installed Ubuntu using the Wubi installer on to a partitioned part of my HardDrive.

It all went well...downloaded and all. And it asked to restart. So it did. Then I chose Ubuntu on the dual boot screen. But it just leaves me with a black screen and a flashing cursor. I can get to the Grub menu but no further. And I can still boot up vista fine.

Thanks
Oliver!

---

### Post by shadow01 on 2008-11-24
Hi,

simmilar problem for me. I get the Ubuntu-logo, after this my screen turns green. In safe graphics mode everything seems to be allright till:

starting Ubiquity
ret = dm.run (sys.argu[3:])
File "/usr/bin/ubiquity-dm", line 113, in run
raise xStartupError, 'x server failed to start after 60 seconds.'
--main--.xstartuperror : xserver failed to load after 60 seconds

Tried the amd64 version as well as i386.
Also tried the 8.04 version, same problem here just that it seems as Ubuntu would actually install, reboots itself after ~15 min but all I get is the green screen and the login sound.

I'm using a MSI GX610, AMD Athlon X2, Ati M76M (HD2600), 2 GB RAM, runing Windows Vista.

Some time ago I used to run Ubuntu 7.x on it if this may help.


Any help would be appreciated, thanks in advance.

---

### Post by ago on 2008-11-25
> **Oliverl said:**
> Hey

I Installed Ubuntu using the Wubi installer on to a partitioned part of my HardDrive.

It all went well...downloaded and all. And it asked to restart. So it did. Then I chose Ubuntu on the dual boot screen. But it just leaves me with a black screen and a flashing cursor. I can get to the Grub menu but no further. And I can still boot up vista fine.

Thanks
Oliver!
see this [http://ubuntuforums.org/showthread.php?p=6247944#post6247944](http://ubuntuforums.org/showthread.php?p=6247944#post6247944)

---

### Post by ago on 2008-11-25
> **shadow01 said:**
> Hi,

simmilar problem for me. I get the Ubuntu-logo, after this my screen turns green.
That is a different problem, the above is a grub4dos issue (possibly HDD drivers), yours is likely a video driver issue.

You might need some special boot parameters to go around that. If you search for the make and model of your videocard you might be able to find that (you can use the lspci command). You add boot parameters pressing "e" within the Ubuntu boot menu.

---

### Post by Menorius on 2009-01-29
> **shadow01 said:**
> Hi,
starting Ubiquity
ret = dm.run (sys.argu[3:])
File "/usr/bin/ubiquity-dm", line 113, in run
raise xStartupError, 'x server failed to start after 60 seconds.'
--main--.xstartuperror : xserver failed to load after 60 seconds


I am having the same exact error. I have a 8800GT SLI configuration. When i run the lspci command, the system lists that card last so i assume that it knows about it. I then typed lspci 06:00.0 and it came up with a menu of some other commands. I know what some of them do because i have used ubuntu before but none of them i tried seemed to help.

I would appreciate any help i could get.

---

### Post by Prom1 on 2009-01-29
I'm getting the exact same error!

Wubi v8.10 and Ubuntu 8.10 i386 BOTH in the same folder
C:\Shared Documents\New Apps\Ubuntu - 8_10 
within Windows XP SP3.

My system is:
Dell Optiplex GX260
Pentium 4 2Ghz (first of this series)
266Mhz FSB
250GB HDD half full; 30GB partitioned with Wubi.exe
600+MB RAM
Intel 64MB internal video chipset (AGP slot 4x EMPTY but video chipset uses this bus)
Video buffer in BIOS set to 8MB as I previously had it set to 1MB (Fedora Core 2/3/4 had issues with this thus changed to 8MB)

I NEVER had a problem installing Wubi v8.04 so I'm not sure whats going on. I tried the following after the Ubuntu load error:
```
sudo dpkg-reconfigure xserver-xorg 
```
to try to fix VESA settings but nothing there except US Keyboard which asks me all kinds of bull settings I care nothing for.

---

### Post by Prom1 on 2009-01-29
Ok now this is driving me nuts and really getting me bugged!

I've been reading multiple threads and tried the following:

CTRL+ALT+F2 to get me to the command prompt
then

```
sudo apt-get purge compiz compiz-core
```

This removed some 20MB from the Wubi partition screen kept flickering (VGA to LCD) during me typing. Rebooted after command completed successfully; so so I thought was success.

I figured I'd try another command I saw to insure this compiz was removed hoping that I'd get to a Ubuntu login prompt.

```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

System didn't even realize that the previous command prior to the reboot was supposed to have been completed and compiz was supposed to be removed. Rebooted and tried.

```
http://www.mylittleubuntuguide.com/files/video
sudo chmod +x video
sudo ./video 
```

This command took a while downloading files > found it on another site that was supposedly to download intel gma845 drivers but it too failed when trying to install them; something about a directory not existing. I noticed that fakeroot kept showing up during several of the commands actions that took place. Rebooted SAME old display issue.

Finally I tried:

```
sudo apt-get install xserver-xorg-video-i810
```

nadda same old display junk.

What is going on?! is Ubuntu so completely up to date that anything 5yrs old doesn't run it any longer?? I've got a plain old i386x86 machine. No 64-bit junk imbedded video chipset from Intel thats it.

Intel imbedded video is the "Intel(R) 82845GL Graphics Controller.

---

