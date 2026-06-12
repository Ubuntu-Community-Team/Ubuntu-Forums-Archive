---
title: "poweroff problem"
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by astrotzky on 2007-07-19
Hello,

I recently started using Ubuntu (I'm on Feisty - 7.04 now) and I had some beginner's problems, but this one I can't solve myself.
Basically, the computer refuses to poweroff when shutting down. I removed the splash kernel parameter in order to see some stuff, and the last message is "[numbers dot numbers] Power off" and that's it. It locks there.
It worked when I had Dapper Drake instead of Feisty.

Facts:
- "shutdown -P now" does the same (no poweroff)
- the problem only appears if I login into Gnome/KDE (i.e. no problem if I choose to shutdown at the login screen); I read a thread that blamed the integrated Intel sound card but it didn't indicated a solution
- the problem does not appear when choosing to hibernate
- I tried acpi=force kernel parameter in my /boot/grub/menu.lst as sugested in other thread but that didn't worked

Some more info.
```

uname -a
Linux mistere-desktop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux


lspci

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:04.0 Mass storage controller: <pci_lookup_name: buffer too small> (rev 13)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
04:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)

```

I hope there is someone that can help me as this problem drives me mad :(

---

### Post by kngunn on 2007-07-20
I'm having similar problems on a Dell Optiplex 745.  I'm also seeing that lots of people are having power-down problems -- not just with Ubuntu and not just on Dells.

Here's the funny thing:  you've prompted me to try and solve this annoyance, so I went to my BIOS settings and toggled a couple of settings.  No more problem!  I toggled them back -- still no more problem!  I can no longer reproduce the issue.

Does this mean toggling the settings (virtualization and hard drive acoustic mode) had an effect?  Maybe, maybe not.  Could it be that there is some program or process that I run sometimes (or the system runs) that causes the problem to manifest?  Who knows!  I thought MAYBE it was VMWare, so I fired up my XP virtual machine, but I can still shut down correctly, so it's a mystery.

Try a cold boot of Ubuntu.  Don't log in -- shut down immediately.  Does it work correctly?  If not, try toggling those BIOS settings and see what happens.  Maybe it won't appear until after the system runs for a while.

In any case, I would love to get to the bottom of this.  Let's figure it out!

---

### Post by astrotzky on 2007-07-20
As I said, I can shutdown correctly (i.e. poweroff) if I don't login into KDE/Gnome.
And you're right. This problem isn't specific to Ubuntu.
There are quite a few bug reports regarding this on launchpad. The guys there said it might be a problem with the kernel (and I think they might be right).
I also understood this issue is very difficult to debug because by the time it happens, the filesystems have been unmounted and all services stopped so there's nowhere to log some info.

Got it. It was the sound card after all.
I need to do "sudo rmmod snd_hda_intel" before shutting down. After that, the system powers off correctly.
Which leaves me with another problem.
**How can I do this automatically?**
I don't feel like typing a command + my password every time I want to do a shutdown.

I think about replacing the shutdown command with a script which does the rmmod and after that, a "shutdown -P now".
The thing is, I don't know where can I modify the command executed at shutdown (when I click shutdown) and how to make a script to run as root (so it doesn't require me to type my password as sudo does).
Help with these 2 issues is highly appreciated.

Of course, if you have a better solution (new kernel, whatever), don't hesitate.

For the others: if you have this problem (no poweroff), try adding "acpi=force" in your /boot/grub/menu.lst as a parameter to the kernel you're booting. This might help you even though it hasn't helped me.

---

### Post by frufo on 2007-08-27
Hello astroztky,

although on Debian Etch I had exactly the same problem while powerinf off with the snd_hta_intel on an ASUS P5GD1Pro. 

I have created a file:
/etc/rc0.d/K85hda_snd

with the following lines:

#!/bin/sh
echo "unloading snd_hda_intel"
/sbin/modprobe -r snd_hda_intel

Do no forget to make it executable with:

chmod a+x /etc/rc0.d/K85hda_snd

---

### Post by vicky1984 on 2007-08-28
i've tried doing the rmmod thing, and i get an error saying the module is in use. i've tried the acpi=force thing before and it never works. any suggestions?

---

### Post by havencruise on 2007-09-01
I seem to have different kind of poweroff problem here.
The problem arises when i type in the command "poweroff" in the terminal, whether in CUI or GUI.
The system fails to poweroff, instead goes ahead with a system halt, and leaves me high n dry with the statement "System Halted".
Have been trying to find a fix. 
Help Please!!

---

### Post by astrotzky on 2007-09-02
Hello frufo,

Thank you, that did the trick.
For the record, my motherboard is P5GD2 Basic.

---

