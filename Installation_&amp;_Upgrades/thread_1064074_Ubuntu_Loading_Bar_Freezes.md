---
title: "Ubuntu Loading Bar Freezes"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by ZiggyFry on 2009-02-08
I've been trying to install Ubuntu on my desktop. I installed it on my laptop without problems. When I try to install/boot from cd, the loading bar with the Ubuntu logo starts, but freezes just before 3 bars. I tried giving it time (about a half hour) but still nothing.

I tried the cd on a different computer and it worked. The same thing has happened with other versions of Ubuntu.

Does anybody have an idea of what's wrong?

Sin.Ziggy.

---

### Post by Partyboi2 on 2009-02-09
Try booting without the splash screen. When you are at the main menu press F6 and change the word splash to nosplash, then press enter to boot.

---

### Post by ZiggyFry on 2009-02-12
Ok. I tried that. It gives me a dozen errors. One of them says "[	252.654867] SQUASHFS error: Unable to read directory block [2a22ab2e:15c4]"  and the others are slightly different. One of the times I tried, it continued after that to say something about ports and failing. (It only happened once and I don't know what that means.) 

I hope that is helpful. I know almost nothing about this os.

Sin.Ziggy.

---

### Post by Partyboi2 on 2009-02-13
Make sure you have checked the md5sum''s that they match.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Try burning the iso at x4 or less speed and check the cd for defects afterward (One of the options at the main menu of the ubuntu live cd)

Another thing you could try is to add some boot options at boot. When you are at the main menu press F6 and at the end of the line add
```
ide=nodma
``` then press enter. If that does not work then try using```
acpi=off
``` as a boot option.

---

### Post by Anger 2 on 2009-02-13
Take a look at your laptop whilst it is loading Ubuntu. Does the point at which the bar freezes on your desktop coinside with the point at which the message 'checking partitions on hard disk' appears on the laptop?

---

### Post by ZiggyFry on 2009-02-13
md5sums are the same, I've tried burning cds at max, 8x 4x and 1x, no defects.

I tried entering ide=nodma/acpi=off and neither seemed to do anything.

Anger - It gives me a bunch of "SQUASHFS" errors when it freezes.

I don't know if this would help, either, but I've tried resetting the BIOS and reformatting without luck.

Thanks for the help/suggestions. 

Sin.Ziggy.

---

### Post by ZiggyFry on 2009-02-19
Last night I was trying different things that I thought might work. I didn't wait until it froze/stopped this time, and it said "This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip" "Try the 8139too driver instead"

I googled this and when somebody else had this problem, they told that person to go to [http://en.opensuse.org/SDB:Realtek_8139_Driver_Problem](http://en.opensuse.org/SDB:Realtek_8139_Driver_Problem)

[QUOTE=OpenSuse]First get the information about the network card

hwinfo --netcard[/quote]

I don't know what to do with this. I'm assuming that I type this somewhere, but I don't know where.

Sin.Ziggy.

Update/edit: I removed my network card and the 8139 driver errors stopped. Now, the only errors I have are a dozen of "squashfs" errors.

---

