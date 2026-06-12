---
title: "Ubuntu 9.04 Freezes"
date: 2009-10-11
forum: Hardware
---

### Post by Pvt_Beeano on 2009-10-11
Appologies for cross-posting ([http://ubuntuforums.org/showthread.php?t=1288231](http://ubuntuforums.org/showthread.php?t=1288231)) - thought this forum may be more relevant;

Just made the switch from XP to Ubuntu but I'm having a few issues. I'll try and be a clear as possible but I am new to Linux so appologies in advance if I'm missing something obvious, I have been searching the forums and trying to fix this myself.

Initially I did a clean install of 9.04 and can boot to the desktop but after a minute or two the GUI locked up. I did some searching around and found that adding this to grub's boot options helped as the problem may lie with the wrong tasks being sent to the wrong core in a multi-core cpu;

```
noapic nolapic pci=noacpi 
```

The problem with this is that I only get one core of my cpu working so I took out all but;

```
pci=noacpi 
```

The system now boots and works for a seemingly random period of time, although launching synaptic, add/remove... or apt from the command line results in an instant freeze.

Here is /var/log/dmesg with only pci=noacpi in the boot options;

[http://www.sendspace.com/file/wgx3mu]("http://www.sendspace.com/file/wgx3mu")

And here it is with all three options;

[http://www.sendspace.com/file/tn19rk]("http://www.sendspace.com/file/tn19rk")

Hope sendspace is okay, let me know if I should use something else.

The only other things I've done since installation is to add VLC and install some drivers to OSS working with my X-Fi card. I'd really like to be able to use both cores of my cpu.

Thanks in advance for any help.

Hardware specs for info;

Shuttle SD32G5 with 2Gb of RAM, Intel C2D@2.13, Nvidia 7600GT and Creative X-Fi

---

### Post by Pvt_Beeano on 2009-10-11
Bump

---

### Post by Pvt_Beeano on 2009-10-11
Bump

---

### Post by mi_were on 2009-10-21
I feel your pain ](*,), my laptop synaptic and add/remove keep freeze whenever I try starting either of them.

I am still trolling the web trying to find a solution to this hiccup.

---

### Post by mi_were on 2010-02-04
Gave in and reinstalled ubuntu!

---

### Post by umechanism on 2010-02-04
You should install 9.10 which is the latest stable release.

---

### Post by jenaniston on 2010-02-04
> **Pvt_Beeano said:**
> . . . can boot to the desktop but after a minute or two the GUI locked up. 

I am working on the same problem with a Sharp AL27 laptop . . .
but I am running a 8GB USB pendrive full install (live versions won't work on the laptop) as my operating system -
but I do fully use the Ubuntu9.04 kernel root terminal in recovery mode for all troubleshooting and file and config changes.

I am now just a few fstab and menu.lst changes away from having a full gnome desktop (or so I* think* I am) -
but I'll try lighter weight Xfce desktop or** X**ubuntu if I have to.

But I will say, the Debian distros of linux are ***much*** kinder to these unsupported laptop/hardware driver problems
than any other linux I know of  - this*** is*** fixable.

But ***the exact same occurence*** - 1-2 minutes when on the jaunty desktop - and the mouse/keyboard and desktop screen freezes up.
Now I just use the desktop to shut down normally . . .
but only after a couple hours in the recovery mode root terminal.

---

