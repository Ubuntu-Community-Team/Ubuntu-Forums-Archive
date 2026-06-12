---
title: "No keyboard or mouse at 9.04 login screen"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by mind0ne on 2009-05-06
I upgraded to 9.04 from 8.10 last night from the update manager. After the update/upgrade completed, I restarted the computer as instructed. When it came to the login screen my keyboard and mouse did not respond. I have tried restarting and using the recovery console to start dbus and hal to no success. I turn the numlock on to see when the keyboard shuts off and it is after Ubuntu is loaded but before the login screen appears. The computer is not frozen so some how 9.04 is disabling my mouse and keyboard. I am using a standard ps/2 keyboard and a 7 button usb mouse.

---

### Post by crom.osec on 2009-05-06
Try Ctrl+Alt+F1

If it goes to console, the keyboard is active.

---

### Post by mind0ne on 2009-05-06
Ok, I tried that and nothing happens.  The cursor is blinking ready for some input but I can not type.  I can use the keyboard in Grub, and in recovery mode at the console.  It seems to be disabling the keyboard after this.  I have toggled the numlock key on while its loading and it comes on.  But right at the end of the load, before the login screen appears, the numlock light turns off and the keyboard is then unusable.

---

### Post by mind0ne on 2009-05-06
Here is an update, I don't know if this will help.  I started in recovery mode and dropped to shell. I then ran sudo /etc/init.d/dbus start and hal start.  Then loaded ubuntu using startx.  This allows ubuntu to load with needing a user and password. My mouse was still unresponsive and so was most of my keyboard.  I have a "power", "sleep" and "wake" key at the top of my keyboard.  When I press the power key it brings up the shutdown box.  When I press sleep i get an error dialog box in the lower right hand corner.  Other than that no other keys do anything.  If I do not run the commands from shell before startx this does not happen.
 
Like I said, not sure if it matters but it is a difference.
 
Any help would be greatly appreciated.

---

### Post by devlin7 on 2009-05-06
I found the same problem this morning upgrading Kubuntu 8.10 to 9.04. PS/2 Keyboard and mouse work at CLI but just before the login screen loads the keyboard and mouse freeze tight.

I dont know if its related but I tried running apt-get update" and apparently it says it can not locate any of the servers it needs.

---

### Post by ububaba on 2009-05-08
> **devlin7 said:**
> I found the same problem this morning upgrading Kubuntu 8.10 to 9.04. PS/2 Keyboard and mouse work at CLI but just before the login screen loads the keyboard and mouse freeze tight.

I dont know if its related but I tried running apt-get update" and apparently it says it can not locate any of the servers it needs.

I have exactly the same problem. Mouse and keyboard freeze. :confused:

---

### Post by frodon on 2009-05-09
Hello,

Please contribute to the bug report confirming this bug and maybe providing more information so that some light can be put on this bug:
[https://bugs.launchpad.net/ubuntu/+bug/371214](https://bugs.launchpad.net/ubuntu/+bug/371214)

Note that the user found a dirty workaround

---

### Post by fatherwilliam on 2009-05-10
I'm having the same problem.  After upgrading from 8.10 to 9.04, if I boot from my old (custom) kernel 2.6.27 the keyboard works until X starts, but at the login screen the keyboard and mouse don't work at all.

If I boot from the 2.6.28-11 generic kernel that was installed with 9.04, the keyboard and mouse work as expected.

I haven't been able to find the cause though.


UPDATE:

I was able to get the keyboard/mouse working on my old kernel by disabling HAL:
I added the following lines to my xorg.conf

Section "ServerFlags"
    Option "AutoAddDevices" "False"
EndSection

and then uncommented the input device sections that were commented out by HAL.
# commented out by update-manager, HAL is now used
Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mice"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

# commented out by update-manager, HAL is now used
Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

I still don't understand the cause of all this though.

---

### Post by frodon on 2009-05-11
Useful thread with useful info and possible workaround there :
[http://ubuntuforums.org/showthread.php?t=901300](http://ubuntuforums.org/showthread.php?t=901300)

---

### Post by theOtherMarino on 2009-05-21
Hello,

Same problem: No keyboard, no mouse at login screen. But, the keyboard works fine when using recovery mode, and both work well when using a live CD. So I guess no hardware issue is involved.

In recovery mode, I tried a dpkg-reconfigure xserver-xorg which worked fine, but nope. No keyboard, no mouse. The "try to repair..." menu item in recovery mode worked the same. Still no keyboard, no mouse.

The I tried a dpkg-reconfigure -phigh xserver-xorg. Here is the output:

```
Gtk-WARNING **: cannot open display:  at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 54.
debconf: unable to initialize frontend: Gnome
debconf: (DISPLAY problem?)
debconf: falling back to frontend: Dialog
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090521233742
```

What the... I tried a 
[LIST]
[*]dpkg --configure debconf
[*]dpkg-reconfigure debconf
[*]dpkg-reconfigure -plow debconf (whatever means the "-plow")
[*]sudo /etc/init.d/hal restart
[/LIST]

... but nope.

There are no broken dependencies on my system. I've xserver-xorg-input-mouse installed.

There are are a few posts about this on this forum, but none of help.

What if I apt-get remove xserver-xorg and apt-get install xserver-xorg ?

Any help appreciated.

Regards,

Marino

---

### Post by theOtherMarino on 2009-05-22
Ok, it's toasted. Reinstalling the whole damn thing.

---

### Post by Nintenduh on 2009-06-08
I had this exact same problem after upgrading from 8.10.

I had display problems which I corrected by going into recovery mode and re-installing nvidia drivers. 

Once I got the video stuff rectified the input devices still didn't work. I found a post about unplugging input devices until after X started. They started working so I backed up my home folder, downloaded and burnt a 9.04 CD to re-install. But stupid me, I forgot to set the bios to boot from CD first. I let it boot. and to my suprise, when X came back up I had KB and mouse! ^^

I hope this helps others who had the same problem.

---

### Post by gopashie on 2009-07-21
I am having the exact same problem, this is my first time installing any form of Linux so i am having a hard time trying to figure out what to do without being able to get into the OS. If anyone has been able to fix this problem and would be willing to give me some pretty dumbed down instructions on how to fix it myself i would be very grateful.

---

### Post by edvar on 2009-09-30
It just happened to me. Hal wasn't loading so I got no mouse, keyboard, sound or network available after I installed an upgrade to kernel 2.28.15.52 in Jaunty.

I tried several things but nothing worked then I realized the folder /etc/hal was empty!

I went to a Linux Mint Gloria VM I had installed on another computer and checked the contents of the folder. The folder structure is basically:

/etc/hal/fdi
/etc/hal/fdi/preprobe
/etc/hal/fdi/policy
/etc/hal/fdi/information

I recreated the folders on my Ubuntu Jaunty box and rebooted. After that I was back in business!

---

### Post by PeaSoup on 2009-10-05
I'm getting the same problem described here but I'm not sure how to fix it.

I have a dual boot setup with Ubuntu 9.04 on its own partition (+ swap partition).
When I first installed Ubuntu the other day it was working fine.

Today I decided to reinstall Ubuntu. Naturally I just wanted to replace the previously existing Ubuntu installation.

I chose manual partitioning options during installation. When I chose to allocate the originally used partitions, I was initially getting an error message saying that "No Root File System is Defined". I solved that by selecting the main Ubuntu partition as the "/ " Mount from the drop-down menu. (I did not click the format box since I was happy for my previous installation to be replaced).

(This explanation of my install process may not account for the problem but it seems strange that the original installation worked fine whereas the replacement one does not.)

Now when I try to log back into Ubuntu my mouse and keyboard are not responding at the login screen, although the cursor flashes. I know the components aren't broken as my Vista boots work fine.

Reading around it seems like some files need to be manually edited. Can somebody explain how to do that in the simplest terms? Since I cannot login to Ubuntu I can't access a terminal. None of my Ctrl+Alt+F? keys work either as I saw some had suggested that. Any suggestions?

---

### Post by PeaSoup on 2009-10-05
I'm not familiar with this stuff but it seems to be related to the kernel edition I was trying to boot from. I found that one of the previous kernel-boots which I could still access from the bootloader worked fine. 

In the end I just reformatted that part of the disk before installing. That was not a problem in my case (nothing to back up) but might not be much use to someone else...

---

