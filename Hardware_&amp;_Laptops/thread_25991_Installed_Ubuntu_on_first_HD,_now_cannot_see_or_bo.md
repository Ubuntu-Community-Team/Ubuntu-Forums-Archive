---
title: "Installed Ubuntu on first HD, now cannot see or boot XP on second HD - Help!"
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by Leigh on 2005-04-11
I have two hard drives in my PC. Originally drive C had Windows 2000, drive D has XP and I could dual boot either version of Windows.

I have just installed Ubuntu on drive C, overwriting the Windows 2000 installation as planned.  Ubuntu loads fine, but now, I cannot boot to XP as the GRUB menu doesn't see the OS.

How can I get the boot loader to see Ubuntu **AND** Windows XP, so I can boot to either?

I am a COMPLETE beginner with Linux, so easy to understand instructions, please.

---

### Post by alastair on 2005-04-11
A GRUB issue i.e. bootloader. You need to configure your bootloader (GRUB) to see XP.

The best thing to do is read a little about GRUB e.g.

[http://www.troubleshooters.com/linux/grub/grub.htm](http://www.troubleshooters.com/linux/grub/grub.htm)

(do some web research)

But, before editing the GRUB config file (e.g. /boot/grub/menu.lst), it might be best to stop at the GRUB menu at boot (ESC), and try some things out. GRUB is good that it gives you a shell mode at boot and you can try things manually. If things work out, you know what sort of things to add to the GRUB config file.

e.g.

ESC at boot -> GRUB shell

Try typing somethings like this :

rootnoverify (hd1,0)
makeactive
chainloader +1
boot

This assumes your XP disk is the SECOND hard drive (hd1) and has a single partition (0).

If this works, look to edit the GRUB config file and add to your menu choices.

Good luck.

---

### Post by Casey on 2005-04-11
I'd try what it says above, but I think I recall an issue where Windows XP refuses to be on the second hard drive if there is not a version of Windows installed on the first.  In that case you might need to switch the order of the hard drives and put grub on the MBR of the first one.  (The easiest way is probably to switch the harddrive order and reinstall hoary onto the second one).

I haven't dual booted in a while (Ubuntu does all that I need) so I am not certain as to whether or not this is true.  It might just be that windows prefers to be at the start of the hard drive (as opposed to a later partition...).  I'm trying to remember - but the second hard drive might be the problem.  I'm sure someone else here who knows better can let you know if this is correct or not.

---

### Post by skoal on 2005-04-11
Try this for your Windows drive (hdb):

```
title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1
makeactive
```

---

### Post by Leigh on 2005-04-12
Thanks for all the replys. Unfortunately, the XP computer in question is my work PC so  I had to get it up and running ASAP. I did read about GRUB when I hit this problem, but being a beginner (to Linux) I really didn't know what to look for.  Ultimately, I did what Casey suggested and switched drives so the Windows drive is now the first one. I then reinstalled Ubuntu on the second drive. All is now well.  I shall be trying to configure Ubuntu to do all my work related stuff.

Many thanks once again. I'm now a little bit closer to being a Linux guru!

---

