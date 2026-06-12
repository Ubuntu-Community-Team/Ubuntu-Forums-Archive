---
title: "Kernel oops on FS Amilo M3438G"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by r0bert on 2005-10-13
Hello All,

I succesfully installed Ubuntu 5.10 on my laptop, but after booting I get a kernel oops caused by 'modprobe'. It is giving lots of output (stacktraces) but it's would be a hell of a job to type it here again :rolleyes: . What i have figured out so far, is that is has something to do with my Sound Card. My questions are:

Can I enable some kind of logging in grub so that i can save the stacktraces somewhere? I am able to read my ext3 partition under Windows XP, but all logs in /var/log are empty.

Does anybody have the same problems with this soundcard:
```
lspci -v: 0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
lspci -v: 	Subsystem: Unknown device 1734:107c
lspci -v: 	Flags: bus master, fast devsel, latency 0, IRQ 10
lspci -v: 	Memory at febf8000 (64-bit, non-prefetchable) [size=16K]
lspci -v: 	Capabilities: [50] Power Management version 2
lspci -v: 	Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
lspci -v: 	Capabilities: [70] #10 [0091]
```

Under Hoary I did not have these problems, and I succesfully used the [Realtek ACL880]("http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True") drivers.

Thanks in advance :D

edit:
I tried passing acpi=off noapic nolapic while booting, but it didnt help

---

### Post by tucoz on 2005-10-14
I am not sure we have the same sound card (I have a FSC m1437g), but I experienced something similar. This was not in modprobe, but when loading the hotplug subsystem. I added snd_hda_intel, and snd_hda_codec to /etc/hotplug/blacklist. It booted fine after that, so I installed the Realtek drivers (I ran the install script), and removed the lines I had added to blacklist. After a reboot, sound is working just fine.

Martin

---

### Post by r0bert on 2005-10-14
[QUOTE=tucoz]I am not sure we have the same sound card (I have a FSC m1437g), but I experienced something similar. This was not in modprobe, but when loading the hotplug subsystem. I added snd_hda_intel, and snd_hda_codec to /etc/hotplug/blacklist. It booted fine after that, so I installed the Realtek drivers (I ran the install script), and removed the lines I had added to blacklist. After a reboot, sound is working just fine.

Martin[/QUOTE]

You're right, i did some research (hooray for the SysRQ key :cool: ) and hotplug seems to be the problem. I just disabled hotplug but this is a little too drastic for me, so I'll try your solution :) 

Could you tell me how you blacklisted the modules? When I reboot right after the installation process, it locks up so I can only blacklist them using the alt + sysRQ + e, and then do some editing, but perhaps there is an other (more friendly way ;) ) of doing this?

Thanks for your help!

---

### Post by tucoz on 2005-10-14
Hi,
you can probably bypass hotplug in the boot by just pressing ctrl+c when you see that loading. When the system is loaded, open up a terminal and:
```
sudo nano -w /etc/hotplug/blacklist
``` and add snd_hda_intel, and snd_hda_codec to the bottom of that file.

Otherwise you could always edit your grub boot parameters to just boot into a simple shell and do your changes from there. That is when grub loads, press e to edit a boot line
e.g.
```
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/sda3 ro quiet splash
```
change this to
```
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/sda3 rw init=/bin/bash
```
Then, you just press b to boot with that line. You do not need to sudo stuff in that bash shell, as you have login as root.
This will only change the boot parameters temporarily.

Martin

---

### Post by r0bert on 2005-10-14
[QUOTE=tucoz]Hi,
you can probably bypass hotplug in the boot by just pressing ctrl+c when you see that loading.
[/QUOTE]

I already tried, but it didn't work (don't know why, but i guess it cannot be aborted due to the kernel oops or something).

[QUOTE=tucoz]
When the system is loaded, open up a terminal and:
```
sudo nano -w /etc/hotplug/blacklist
``` and add snd_hda_intel, and snd_hda_codec to the bottom of that file.
[/QUOTE]

Thanks, i will try this!

Last question: since this seems to be a (serious?) bug, I should send a bugreport to someone, right? I have absolutely no experience with this, so if somebody could point me in the right direction I would appreciate it :D

---

### Post by Liverman on 2005-10-14
I'm having the same problem of freezing when the boot gets to the hotplug thingy. I've managed to blacklist snd_hda_intel and snd_hda_codec. 

**tucoz**, do you have a link for the driver you downloaded :confused:  - i'm not getting the drivers i've tried to worked.

Appreciate it.

---

### Post by shenki on 2005-10-14
Here are some bugs relating to your issue:

[15465](http://bugzilla.ubuntu.com/show_bug.cgi?id=15465) Hotplug hangs on boot trying to load snd-hda-intel
[15031](http://bugzilla.ubuntu.com/show_bug.cgi?id=15031) ALC880 + Intel 915GM - ICH6 results in Kernel panic

From what I gathered after reading through the comments, the bug has been known about for a while, however, the patch to fix it was considered to risky to ass to the kernel close to the stable release. There is a patch, and a kernel with the patch itegrated, in the comments to bug 15031.

This [kernel](http://www.sh.nu/~crimsun/linux-image-2.6.12-9-386_2.6.12-9.22_i386.deb) contains the said patch. I gave it a go myself (LG LW40 Express, with intel HD audio (ICH6) sound), and didn't have any luck, but it seems others have.

---

### Post by iNerdSure on 2005-10-15
[QUOTE=shenki]Here are some bugs relating to your issue:

[15465](http://bugzilla.ubuntu.com/show_bug.cgi?id=15465) Hotplug hangs on boot trying to load snd-hda-intel
[15031](http://bugzilla.ubuntu.com/show_bug.cgi?id=15031) ALC880 + Intel 915GM - ICH6 results in Kernel panic

From what I gathered after reading through the comments, the bug has been known about for a while, however, the patch to fix it was considered to risky to ass to the kernel close to the stable release. There is a patch, and a kernel with the patch itegrated, in the comments to bug 15031.

This [kernel](http://www.sh.nu/~crimsun/linux-image-2.6.12-9-386_2.6.12-9.22_i386.deb) contains the said patch. I gave it a go myself (LG LW40 Express, with intel HD audio (ICH6) sound), and didn't have any luck, but it seems others have.[/QUOTE]
Thanks. The solution suggested appears rather technical for me, a Linux newbie. I hope some Ubuntu users out there have a simpler fix.

---

### Post by tucoz on 2005-10-15
[QUOTE=Liverman]I'm having the same problem of freezing when the boot gets to the hotplug thingy. I've managed to blacklist snd_hda_intel and snd_hda_codec. 

**tucoz**, do you have a link for the driver you downloaded :confused:  - i'm not getting the drivers i've tried to worked.

Appreciate it.[/QUOTE]
Liverman, check out the link posted by r0bert in the first message in this thread. That is the driver I am using. You simply download that driver, extract it, and run sudo ./install and it should install the drivers for you.

---

### Post by shenki on 2005-10-15
nah, not techincal at all:

```
wget [http://www.sh.nu/~crimsun/linux-image-2.6.12-9-386_2.6.12-9.22_i386.deb](http://www.sh.nu/~crimsun/linux-image-2.6.12-9-386_2.6.12-9.22_i386.deb)
sudo dpkg -i linux-image-2.6.12-9-386_2.6.12-9.22_i386.deb
```

and then reboot your computer.

---

### Post by savale on 2005-10-17
[QUOTE=shenki]nah, not techincal at all:

```
wget [http://www.sh.nu/~crimsun/linux-image-2.6.12-9-386_2.6.12-9.22_i386.deb](http://www.sh.nu/~crimsun/linux-image-2.6.12-9-386_2.6.12-9.22_i386.deb)
sudo dpkg -i linux-image-2.6.12-9-386_2.6.12-9.22_i386.deb
```

and then reboot your computer.[/QUOTE]

ahh nice. Did you compiled that kernel?

---

### Post by a_dejot on 2005-10-17
thanks very much for the info about the drivers, but when i run ./install it terminates with the (final) message:

alsaconf: command not found

any ideas?

---

### Post by Liverman on 2005-10-17
[QUOTE=a_dejot]thanks very much for the info about the drivers, but when i run ./install it terminates with the (final) message:

alsaconf: command not found

any ideas?[/QUOTE]
You can download the alsaconf source code here [http://www.alsa-project.org/alsa/ftp/driver/alsaconf/](http://www.alsa-project.org/alsa/ftp/driver/alsaconf/)

I have tried the exact same thing and i get an error compiling the driver - quite anoying.

I also tried the patch suggested and got an error running /etc/init.d/pcmcia, but the sound worked :rolleyes: - i think i'll stick to finding a driver.

---

### Post by Liverman on 2005-10-18
Finally got it to work - i only needed to install some additional packages in order to compile. 
Thanks for the help...;)

---

