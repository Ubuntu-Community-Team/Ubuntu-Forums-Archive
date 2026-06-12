---
title: "DVD-Rom not working"
date: 2007-12-02
forum: Hardware &amp; Laptops
---

### Post by esoikie on 2007-12-02
I started to notice the problem when my DVD drive would not automount any CD's at all.

When I try to manually mount a regular CD or DVD the drive starts spinning endlessly and hangs the xterm window, even after ejecting the CD, ctrl-c does not bring the prompt back.
(i.e. mount /dev/dvd /cdrom, mount /dev/cdrom /cdrom, mount -t ufs /dev/dvd/ /cdrom, etc.)

Additionally, when I am shutting down the computer, I see an error "hdd not ready for command" flooding my screen.

The final symptom is that occasionally, when there is a CD in the drive or not, I will get a pop-up window asking me what I want to do with the CD in the drive containing music and image files.

The /etc/fstab line is as follows:
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Any suggestions?

---

### Post by Craigus on 2007-12-02
You need to establish whether or not this is a hardware problem - the drive may simply be failing. Try running a different distro live cd (eg slax, knoppix, mepis, etc) and see if the same sort of errors occur. (I assume here that the machine doesn't dual boot windows.)

---

### Post by esoikie on 2007-12-02
No, this is definately not a hardware problem.  I WAS dual booting win98 with Damn Small Linux up until about a week ago.  I can boot the Xubuntu and DSL live CD's with no problem, or boot with my WinXP CD with ease.  It is most definitely a Ubuntu problem as DSL loaded CD's with no problem.

If it helps in anyway, I need to use the ACPI=force and irqpoll options in the boot command.

---

### Post by esoikie on 2007-12-04
No suggestions?

---

### Post by Craigus on 2007-12-05
I found this : [http://forum.notebookreview.com/showthread.php?t=186062]("http://forum.notebookreview.com/showthread.php?t=186062")


Really not sure if this would apply to your hardware though.

---

