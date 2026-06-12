---
title: "Ubuntu won't boot at all after removing NVIDIA v. 173 driver"
date: 2011-05-29
forum: Hardware
---

### Post by ekortright on 2011-05-29
Upgraded my Dell Inspiron 5150 from Ubuntu 9.x to 11.04. Graphics card is NVIDIA GeForce FX Go5200.
 
When upgrade complete, got message about graphics not supporting unity, but the classic view seemed fine.
 
However, the computer would never come back from a Suspend/Sleep, however. It seemed to hang with a black screen and I would have to force it to power down by holding the power button.
 
After that, when starting up I would sometimes see all kinds of garbage on the screen and the machine would appear to hang. I could reboot in recovery mode, but still I would see garbage on the screen. By guessing that the recovery menu was being displayed, I could drop into a root shell and type the "reboot" command (without being able to see the characters) and the machine would usually come back up OK.
 
I checked the "Additional Drivers" and the NVIDIA v. 173 driver was reported as "enabled but not in use". To see if I could fix the garbage screens by using the generic video driver, I removed the NVIDIA 173 driver and restarted.
 
Now I cannot boot at all (recovery or normal). I get a series of messages on the screen, the last one of which says: "[ 27.959750] fb: conflicting fb hw usage nouveaufb vs EFI VGA - removing generic driver". The machine hangs after that.
 
I cannot even boot a previous version of Linux; I always get the same message now.
 
The video used to work fine with previous versions of Ubuntu. Is it just that Ubuntu 11 is just not compatible with older hardware?

---

### Post by webofunni on 2011-05-29
mount ubuntu partition in another os/livecd and add the EFI VGA in black list

---

### Post by ekortright on 2011-05-29
> **webofunni said:**
> mount ubuntu partition in another os/livecd and add the EFI VGA in black list

Thanks, but can you tell me how to do that?

I can edit /etc/modprobe.d/blacklist.conf and add a line "blacklist xxx", but what is the name to use in place of "xxx" for EFI VGA?  I can't seem to find anything on the web about how to do this.

---

### Post by webofunni on 2011-05-29
Try this. Reboot the machine. In the grub screen press "e" ( letter e ) to edit it. 

go to the line that looks like

```

linux	/vmlinuz-2.6.38-8-generic root=/dev/mapper/ubuntu--server-root ro   quiet

```

and change that to

```

linux	/vmlinuz-2.6.38-8-generic root=/dev/mapper/ubuntu--server-root ro acpi=off

```

press F10 to boot.

---

### Post by ekortright on 2011-05-30
This lets me log into the system, but no X Windows.

---

### Post by ekortright on 2011-05-30
Also, trying to boot normally seems to write invalid data to the graphics card, so that even if I do get the login prompt I get garbage on the screen (my original problem), so that I can't see what I'm doing.

I have to boot to Windows (it's a dual boot) or using the live CD to get the graphics card back to normal again.

---

### Post by ekortright on 2011-05-30
Well, I figured life's too short to spend it trying to figure this problem out, so I blew away my old installation of Ubuntu (9.x upgraded to 11.04).

So . . .

The computer boots fine with the installation CD.  Video looks good.

Told it to replace the existing 11.04 with a fresh install.

After installation, asked to restart; removed CD and let it restart.

1. Displayed the background after a while.  
2. A long time passed without any login screen, then it started flashing some window that looked like the upgrade manager, but it flickered so much that I could not see very well.  It was as if the monitor refresh rate was wrong.
3. I pressed Alt-Ctrl-F1 to try to log in and shutdown manually, but never saw a prompt.  Instead, after a while it went back into X and displayed the login screen.
4. Logged in, but never got the window manager.  The disk kept working, and the fan came on.  This went on for several minutes.
5. Hit Ctrl-Alt-Delete, and the machine restarted.

The attached screen shot is what I get after rebooting.

---

### Post by drdos2006 on 2011-05-30
Here is how I solved my nvidia problem.

Switch off machine, remove nvidia card....nVidia Corporation G73 [GeForce 7600 GT] (rev a1)
Boot with vga monitor on onboard vga output
Remove : sudo rm /usr/lib/extra-modules/nvidia.so
Shutdown, reinstall video card, re-install nvidia driver

regards

---

### Post by ekortright on 2011-05-30
I also tried booting in recovery mode.

I get a login prompt, but the screen is still garbage.

Not sure if this means anything, but all the characters I type at the terminal are reversed left-to-right, and look like an outline rather than a solid character.

What could be messing up my graphics card, that would survive a completely fresh installation?

---

### Post by webofunni on 2011-05-30
Are you able to boot in to the live cd ? In that case a fresh installation will work.

---

### Post by ekortright on 2011-05-30
Live CD boots fine.  I can "try Ubuntu" and get the classic desktop and everything works perfectly.

Booting from my freshly installed (off of the live CD) 11.04 does not work at all, as explained below.

Booting from the live CD seems to fix the video.  However, even after the video seems to be no longer corrupted, booting from hard disk I never get to see the window manager (I do see the background, disk seems to be doing stuff).  If I power off the machine (my only choice), I get corrupted video on restart from hard disk.

---

### Post by ekortright on 2011-06-04
Well, this has been interesting, to say the least. . . .

First, my console (text-mode) garbage display problem seems to have gone away when I booted from the live CD, mounted the Linux partition, and removed the /etc/X11/xorg.conf file (not sure how it got created.  It looked very strange (including it here in case somebody else has this problem):

```

Section "Device"
        Identifier      "Default Device"
        Option  "NoLogo"        "True"
EndSection


```

Next, when I booted normally, I would get the background, but no toolbars.  The machine would start running something (the CPU fan would come on).

Since the garbage screen was fixed, I could get out of X with Ctrl-Alt-F1, log in, and stop X:

```
sudo service gdm stop
```

Also, I could finally look into the log:

```
vi /var/log/Xorg.0.log
```

This showed an error:

> (EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
...
(EE) Screen(s) found, but none have a usable configuration.


I tried uninstalling and reinstalling the nvidia-current and nvidia-173 drivers using apt-get, but no difference.  I also removed the nouveau driver, with no effect.

Finally, in a fit of desperation, I updated everything that needed updating:

```
sudo apt-get update
sudo apt-get upgrade
```

A bunch of stuff was updated, including xorg stuff.  Somehow, that seems to have fixed whatever was wrong.  I can now boot and see the classic view of the desktop.  The X log looks fine now.

I still don't understand how a brand new installation (erasing the previous one) could fail like this.  The Live CD booted just fine, with no display problems, but booting from the installation that came from that very same Live CD was somehow corrupted.

Oh well.  Maybe this will save somebody else some headaches.

---

### Post by ekortright on 2011-06-05
I feel as if I'm talking to myself, but oh well.

The garbage on the text screen came back (it was probably only temporarily fixed by booting from the Live CD).  The letters were all reversed left-to-right, and looked like outlines or drop shadows.

Anyway, I fixed this problem simply by blacklisting the NVIDIA driver altogether.  I did this by adding one line to the file /etc/modprobe.d/blacklist.conf:

```
blacklist nvidia
```

It seems that the nouveau driver is handling the graphics card in text mode correctly, but loading the proprietary driver (nvidia-173) together with it is somehow corrupting things.

---

### Post by Nrbelex on 2011-07-24
> **ekortright said:**
> I feel as if I'm talking to myself, but oh well.

The garbage on the text screen came back (it was probably only temporarily fixed by booting from the Live CD).  The letters were all reversed left-to-right, and looked like outlines or drop shadows.

Anyway, I fixed this problem simply by blacklisting the NVIDIA driver altogether.  I did this by adding one line to the file /etc/modprobe.d/blacklist.conf:

```
blacklist nvidia
```

It seems that the nouveau driver is handling the graphics card in text mode correctly, but loading the proprietary driver (nvidia-173) together with it is somehow corrupting things.

Just wanted to chime in to say I've been having the same problem. I'm a little less versed in Linux, so if anybody could provide some fool-proof directions to get a fresh install of 11.04 going on a 5150 without garbage text at startup, it would be much appreciated!

---

