---
title: "dual boot 2 linux OS's on 2 different drives."
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by 5mattyb5 on 2009-05-31
Hi guys,

I have 2 seperate physical hard drives a 640 and a 320 not a partitioned single drive.  I have Ubuntu jaunty 64 on the 640 which is my primary drive.  I want to put PCLINUXOS on the other drive with it's own grub.  So to be safe I just unplugged the 640 from the motherboard and installed PCLINUXOS normally.  It worked I rebooted awesome. I shutdown hooked up my other drive rebooted to PCLINUXOS, it worked awesome.......but it only worked once now I can only boot to Ubuntu I can mount the 320 in Ubuntu and see that the operating system and all my data is indeed still on that drive but I can't boot to it.  I tried adding that kernel to my Ubuntu GRUB but that didn't work.  Does anybody have any suggestions?  If I instsalled PCLINUXOS with my 640 still plugged in than I have a choice of replacing the Ubuntu GRUB or not installing a boot loader at all, both don't sound safe to me, but what do I know, that's why I'm asking.

---

### Post by ajgreeny on 2009-05-31
Change the first boot device in your BIOS perhaps to get the PCLinuxOS disk as the boot disk.

Actually it is much easier to just let one grub take care of everything.  You can always switch from one OS's grub to the other later if you need to.

What error do you get when trying to boot PCL from ubuntu's grub, and what exactly did you add to the ubuntu grub menu.lst file in your attempt to boot it as normally you can add the stanza from one grub menu to the other to get all OSs bootable.

---

### Post by 5mattyb5 on 2009-06-04
I figured out that grub could't boot the other OS because it was on a different drive, however I did realize that each os gave me an option upon install to put grub where I wanted.  So I actually have Both OS's operating on both drives now with seperate drives, and that is good enough for me but thanx for all your help.

---

### Post by 5mattyb5 on 2009-06-04
I figured out that grub could't boot the other OS because it was on a different drive, however I did realize that each os gave me an option upon install to put grub where I wanted.  So I actually have Both OS's operating on both drives now with seperate grubs, and that is good enough for me but thanx for all your help.

---

