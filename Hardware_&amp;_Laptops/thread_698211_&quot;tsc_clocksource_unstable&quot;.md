---
title: "&quot;tsc clocksource unstable&quot;"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by Strid on 2008-02-16
Hey,

I've been getting random freezes and about every third time I reboot, I get a errormessage and ubuntu boots up to a console where I have to run fsck to correct the errors...

Today I booted up my computer as regularly, but it failed to start Gnome. I pressed Ctrl-Alt-F1 to hit tty1 console and type "sudo reboot now", and saw the following mesage: "tsc clocksource unstable".

What does this mean? Does this suggest that something is seriously wrong with my hardware? Sounds pretty bad to me, but it would explain the random freezes I get.

My computer is basically an AMD FX-60 on a ASUS A8N-E motherboard with OCZ ram. Would I need a new CPU and/or motherboard to get me stable again??

Thanks,
Anders

---

### Post by Yellow Pasque on 2008-02-16
Sounds like a bad motherboard to me. That's where the system clock generating circuit resides. Hopefully, you can find yourself a cheap Socket 939 motherboard. :\

---

### Post by Strid on 2008-02-16
Thanks, that's what I feared. Are you aware of any way to test the system clock stability?

---

### Post by Yellow Pasque on 2008-02-16
I'm not aware of a way to do that without an oscilloscope.

---

### Post by nick_h on 2008-02-17
I also get the "clocksource unstable" message.  This is just a message and not an error.  From what I understand, it is just the kernel detecting that it cannot rely on the clock to be constant - for example in variable speed CPUs - and will use a different timing mechanism.

Random freezes in Gutsy are often caused by "Visual Effects".  Try disabling "Visual Effects" and see if it fixes the problem.

The system asking you to run *fsck* points towards a HDD problem.

---

### Post by Strid on 2008-02-17
Hey, thanks. I could try and disable cool and quiet and see if that was the culprit for this error message.

I've already disabled Visual Effects. The random freezes I get are usually when I press the power off button or when open a program. Actually, I haven't had a freeze for a week, which is rather unusual.

I've run fsck and badblocks on both of my harddrives, nothing found. When the system wants to run fsck at boot up, I can just reboot (without running fsck) and it will boot up normally. Then, when I try and run fsck after the 2nd (and succesful) boot attempt, it will find no errors.
My one harddrive has the following partitions: sda1 = NTFS (For Window XP), sda2 = ext3 (filesystem), then a 5 gb swap partition and a 55 GB Fat32 drive for sharing between windows and linux. I'm not sure if this rather mixed up partitioning could cause any problems with anything?

---

### Post by nick_h on 2008-02-17
> I'm not sure if this rather mixed up partitioning could cause any problems with anything?
I doubt it.  I have 1 NTFS, 2 ext3, 1 FAT and 1 swap partition and it doesn't cause any problems.

When your system freezes, can you reboot using the Magic SysRq keys?  Is there anything in your log files?

I just did a quick google and found that we might be able to use the "notsc" kernel option. I haven't tried it myself yet though.

---

### Post by Strid on 2008-02-18
Thanks! I'll google "notsc", although I'm not sure what it is! I think you're right, my other laptop even runs MS-DOS besides Windows XP and linux and I haven't had a freeze ever on that PC, so that probably rules out the harddrive partitioning at least.

I'm not sure what the magic SysRq trick is .. but it's a pretty hard freeze, I'd say. Not even pressing Caps/Num/Scroll Lock will flash the light indicator on the keyboard. Which logfile(s) should I look in?

---

### Post by nick_h on 2008-02-18
> I'm not sure what the magic SysRq trick is
Have a look [here](http://en.wikipedia.org/wiki/Magic_SysRq_key) in the "Raisng Elephants" section.
> Which logfile(s) should I look in?
System->Administration->System Log and try the kern.log file and perhaps the X log.  If it is like the random freezes I was getting with "Visual Effects" then the "Raisng Elephants" will not work and there will be no log entries, but it is worth a look.

---

### Post by sgiandubh on 2008-03-08
I encountered the "clocksource tsc unstable" freeze during boot. I was actually able to boot Live with "noapic nolapic" added to the boot options. ACPI was enabled. That solution that was insufficient for the permanent installation.  For the permanent installation, I disabled ACPI in the BIOS and added "acpi=off" to the boot options for good measure. Disabling ACPI wasn't enough, so I also set CPU performance in the BIOS from "Recommended" to "Maximum." The previous boot options set for Live were removed. I then successfully booted to the desktop.

---

### Post by ssj3strife on 2008-04-28
I found a launchpad bug related to this issue, and it solved my tsc troubles. Check it out:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190414](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190414)

If you're having trouble, try adding clocksource=hpet to your kernel arguments and see if things improve.

---

### Post by mendieta on 2008-06-10
> **ssj3strife said:**
> 
If you're having trouble, try adding clocksource=hpet to your kernel arguments and see if things improve.

You just made my day. I installed Kubuntu 8.04 Desktop from the live CD to a flash drive in my Kubuntu PC, put it in my eeepc, and essentially got it booting, with a long (10 minute) delay in the middle of the bootup. I found the dreaded "clocksource tsc unstable" message, and then that hpet was installed. Bingo, your post made my day.

I am sure this would have been setup by the installer had I run it from the eeepc, which I didn't. 

Anyway, thank you!

---

### Post by unpredictable on 2008-07-20
hi 

I have this clocksource tsc unstable problem ... 
i recently solved it .. 

I have 1 ide and sata disk  .. with HDMI enabled motherboard ASUS 

in the grub screen I put     

clocksource=hpet acpi=off noacpi

you can do it by ...pressing e .... 

when u are done editing ..enter ... press b 


then make this changes permanent ... got to /boot/grub/menu.list ... 
you can edit the lines like mine .. 


title		Ubuntu 8.04.1, kernel 2.6.24-19-generic My Edition 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a4646 ro quiet splash xforcevesa [COLOR="Red"]clocksource=hpet acpi=off noacpi
[/COLOR]initrd		/boot/initrd.img-2.6.24-19-generic
quiet


title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a4647b17-16c6 ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a4647b8-9846-b7f3a8dd16c6 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

---

