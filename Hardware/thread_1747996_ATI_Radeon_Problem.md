---
title: "ATI Radeon Problem"
date: 2011-05-03
forum: Hardware
---

### Post by Dragon6 on 2011-05-03
Hello, 
I have my laptop HP G62 which has a graphic card of ATI Radeon HD 5470 and installed Ubuntu 11.04 on it...
I already tried the following guides to install the Graphics card but no success at all:-
1)[http://ubuntuforums.org/showthread.php?t=1409467](http://ubuntuforums.org/showthread.php?t=1409467)
2)[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

The process ends up with a black screen, or unsuccessful system boot.
Please, any ideas or other successful guides to solve my problem?

---

### Post by mastablasta on 2011-05-03
what version of ubuntu are you using? you should be able to get to "additional drivers" application and you can instal the necessary proprietary ATI drivers though there.

---

### Post by Dragon6 on 2011-05-03
I use Ubuntu 11.04 Natty
yes there is additional drivers application, and I tried it, though no success at all, because black screen hangs when I reboot
thanks for reply

---

### Post by sagarthegreat1 on 2011-05-03
when it hangs, try pressing ctrl+alt+F7
there should be s a stack trace or some errors there...post them here


(btw the same thing happens with my vaio with radeon 6630.Boots the first time after install, never afterwards)

---

### Post by Dragon6 on 2011-05-03
Nothing happens!

---

### Post by sauthess on 2011-05-03
Hi,

Do you have multiple graphics cards ? (intel embedded in core i3/i5 or i7 ?)

I have this kind of hardware and hare to change manually link for libglx and libGL...

(but finally it works)

regards,

---

### Post by Dragon6 on 2011-05-03
Hi, yes it does
Intel HD Graphics embedded in core i3

---

### Post by waspbloke on 2011-05-03
When I install the radeon driver I get a black screen. Simply booting up into recovery mode > failsafe X > create new X configuration then rebooting solves this.

In my case, only the radeon driver will give me Unity and only if I do not use my external monitor. Instead I prefer to use my large monitor so forfeit Unity and use the FGLRX driver - which just boots fine for me.

---

### Post by sauthess on 2011-05-03
Hi,

With this configuration (hybrid) I had some troubles getting it working.

I must change libs to have this :

ls -l /usr/lib/libGL.*
lrwxrwxrwx 1 root root 33 2011-05-03 19:38 /usr/lib/libGL.so -> /usr/lib/fglrx/fglrx-libGL.so.1.2
lrwxrwxrwx 1 root root 33 2011-05-03 19:38 /usr/lib/libGL.so.1 -> /usr/lib/fglrx/fglrx-libGL.so.1.2
lrwxrwxrwx 1 root root 33 2011-05-03 19:38 /usr/lib/libGL.so.1.2 -> /usr/lib/fglrx/fglrx-libGL.so.1.2

ls -l /usr/lib/xorg/modules/extensions/ | grep glx
-rw-r--r-- 1 root root 342568 2011-04-19 17:41 FGL.renamed.libglx.so
lrwxrwxrwx 1 root root     54 2011-05-03 19:38 libglx.so -> /usr/lib/xorg/modules/extensions/fglrx/fglrx-libglx.so

Do not forgot :
- to save situation that you have before modification (in case of ...)
- launch "ldconfig" before restarting X after modifications 
- launch aticonfig --initial if not already done

I have created this script I think do the job (not sure as I've done it by hand...), If it can help.... :

#!/bin/sh

mv /usr/lib/fglrx/xorg/modules/extensions/libglx.so /usr/lib/fglrx/xorg/modules/extensions/libglx.so.save
cp /usr/lib/fglrx/xorg/modules/extensions/fglrx/libglx.so /usr/lib/fglrx/xorg/modules/extensions/libglx.so
mv /usr/lib/libGL.so /usr/lib/libGL.so.save
mv /usr/lib/libGL.so.1 /usr/lib/libGL.so.1.save
mv /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1.2.save
ln -s /usr/lib/fglrx/libGL.so /usr/lib/libGL.so
ln -s /usr/lib/fglrx/libGL.so.1 /usr/lib/libGL.so.1
ln -s /usr/lib/fglrx/libGL.so.1.2 /usr/lib/libGL.so.1.2
ldconfig
aticonfig --initial
service gdm stop
sleep 1
service gdm start

This must be launched from console (or with "sudo nohup script.sh &"....)

Hope this help....

At my side I have not solved one problem :
- lauching fullscreen native 3D applications (chromium-bsu for example) breaks X
If someone have an idea....

---

### Post by Dragon6 on 2011-05-10
Please could someone help? I tried searching everywhere, I asked even in IRC #ubuntu, but no success at all of finding a solution

Again, it's ATI Radeon HD 5470 with Intel HD Graphics embedded in core i3

---

### Post by belltown on 2011-05-10
Do you really need to use the ATI graphics card? Have you tried only using the Intel integrated graphics?

---

### Post by Dragon6 on 2011-05-10
> Have you tried only using the Intel integrated graphics

how to do that?

---

### Post by belltown on 2011-05-10
If you can't get the system to boot at all then when you try to boot the system and get the boot menu, type 'e' to edit the command line for the Ubuntu 11.04 OS. At the very end of the line that starts with "linux" add the following:
```
radeon.modeset=0
``` Then press F10 to boot. That should prevent the radeon driver from running in Kernel Modesetting mode, which seems to cause problems when booting.

Try uninstalling the ATI fglrx proprietary driver. I'm not exactly sure about this part as I haven't used it yet myself, but I do have a switchable graphics system that I have successfully got to run on just the Intel driver.

Next, blacklist the radeon (and fglrx?) drivers. Start a terminal window, then type: ```
sudo gedit /etc/modprobe.d/blacklist.conf
```At the end of this file, add:
```

blacklist radeon
blacklist fglrx

 
```Now, when you re-boot you should be running on the Intel (i915) driver.

If you were able to uninstall the fglrx driver and now only have the radeon and intel drivers present, you can de-power the radeon graphics card to dramatically increase battery life and lower temperatures. To do this you'll need to reload the radeon driver that you had blacklisted to allow a successful boot, then run vgaswitcheroo to de-power the card. Edit the file /etc/rc.local and add the following:
```
 modprobe -i radeon
 echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
 
```

---

### Post by aeronutt on 2011-05-10
> **belltown said:**
> If you can't get the system to boot at all then when you try to boot the system and get the boot menu, type 'e' to edit the command line for the Ubuntu 11.04 OS. At the very end of the line that starts with "linux" add the following:
```
radeon.modeset=0
``` Then press F10 to boot. That should prevent the radeon driver from running in Kernel Modesetting mode, which seems to cause problems when booting.

Try uninstalling the ATI fglrx proprietary driver. I'm not exactly sure about this part as I haven't used it yet myself, but I do have a switchable graphics system that I have successfully got to run on just the Intel driver.

Next, blacklist the radeon (and fglrx?) drivers. Start a terminal window, then type: ```
sudo gedit /etc/modprobe.d/blacklist.conf
```At the end of this file, add:
```

blacklist radeon
blacklist fglrx

 
```Now, when you re-boot you should be running on the Intel (i915) driver.

If you were able to uninstall the fglrx driver and now only have the radeon and intel drivers present, you can de-power the radeon graphics card to dramatically increase battery life and lower temperatures. To do this you'll need to reload the radeon driver that you had blacklisted to allow a successful boot, then run vgaswitcheroo to de-power the card. Edit the file /etc/rc.local and add the following:
```
 modprobe -i radeon
 echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
 
```

Yep, this worked for me too. At least, it works to turn off the AMD Radeon graphics, uses the integrated intel graphics, and boot reliably.  See also here:

[http://ubuntuforums.org/showthread.php?t=1744188](http://ubuntuforums.org/showthread.php?t=1744188)

FYI, to my knowledge, it doesn't appear AMD is working on (hot) switchable graphics for linux. And, I'd love to be able to select at boot, but that doesn't work for me either (neither the AMD fglrx proprietary driver or the opensource AMD driver.)

---

### Post by belltown on 2011-05-15
> **aeronutt said:**
> Yep, this worked for me too. At least, it works to turn off the AMD Radeon graphics, uses the integrated intel graphics, and boot reliably.  See also here:

[http://ubuntuforums.org/showthread.php?t=1744188](http://ubuntuforums.org/showthread.php?t=1744188)

FYI, to my knowledge, it doesn't appear AMD is working on (hot) switchable graphics for linux. And, I'd love to be able to select at boot, but that doesn't work for me either (neither the AMD fglrx proprietary driver or the opensource AMD driver.)

I was able to get the latest proprietary AMD driver (11.5) to work. The instructions are here: [http://ubuntuforums.org/showthread.php?p=10805756](http://ubuntuforums.org/showthread.php?p=10805756)

This will install the Catalyst Control Center under System>Preferences, which allows you to switch between the Intel and AMD cards, although you need to reboot for the change to take effect.

---

### Post by aeronutt on 2011-05-15
> **belltown said:**
> I was able to get the latest proprietary AMD driver (11.5) to work. The instructions are here: [http://ubuntuforums.org/showthread.php?p=10805756](http://ubuntuforums.org/showthread.php?p=10805756)

This will install the Catalyst Control Center under System>Preferences, which allows you to switch between the Intel and AMD cards, although you need to reboot for the change to take effect.

I wish it worked for me, but it doesn't. Which AMD graphics do you have? Mine is HD6630M.

---

### Post by belltown on 2011-05-15
> **aeronutt said:**
> I wish it worked for me, but it doesn't. Which AMD graphics do you have? Mine is HD6630M.

I have the ATI HD5650 card. Sorry it doesn't work for your card.

---

