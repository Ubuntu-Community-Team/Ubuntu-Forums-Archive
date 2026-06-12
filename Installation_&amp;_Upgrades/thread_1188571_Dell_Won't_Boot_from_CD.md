---
title: "Dell Won't Boot from CD"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by PaulTR on 2009-06-15
Couldn't find a solution in the forums, so figured I'd post. Friends Dell won't boot because of a corrupt biosinfo.inf, so I got a copy of the file and am trying to use Ubuntu to boot up and use on her computer so I can move the file over. Thing is, the Dell won't boot off of the Ubuntu CD. Any suggestions on how to get it to? It's a Jaunty CD, and the Dell is from '03. I forget the model type, or I'd post it and I'm not at the machine right now. Thanks.

---

### Post by merlinus on 2009-06-15
Check the bios to make sure booting from cd comes before hdd.  Also, perhaps the cd is bad, or the .iso has errors.

---

### Post by jflaker on 2009-06-15
> **PaulTR said:**
> Couldn't find a solution in the forums, so figured I'd post. Friends Dell won't boot because of a corrupt biosinfo.inf, so I got a copy of the file and am trying to use Ubuntu to boot up and use on her computer so I can move the file over. Thing is, the Dell won't boot off of the Ubuntu CD. Any suggestions on how to get it to? It's a Jaunty CD, and the Dell is from '03. I forget the model type, or I'd post it and I'm not at the machine right now. Thanks.

Watch your bios screen, you may have to hit F12 to get a boot menu...choose which device or the default is to boot from hard disk.

If cd/dvd isn't an option at the boot chooser (after hitting F12), go into BIOS and select the CD/DVD as a boot device, it will show on the boot menu after you boot again and hit F12

I just fixed someone's dell laptop and didn't see the boot option F12 for the first 5 reboots.

---

### Post by philcamlin on 2009-06-15
yeah at the DELL bios screen hit f12 and click boot from cd 

make sure the cd is in the first cd slot:popcorn::popcorn::popcorn:

---

### Post by presence1960 on 2009-06-15
> **PaulTR said:**
> Couldn't find a solution in the forums, so figured I'd post. Friends Dell won't boot because of a corrupt biosinfo.inf, so I got a copy of the file and am trying to use Ubuntu to boot up and use on her computer so I can move the file over. Thing is, the Dell won't boot off of the Ubuntu CD. Any suggestions on how to get it to? It's a Jaunty CD, and the Dell is from '03. I forget the model type, or I'd post it and I'm not at the machine right now. Thanks.

Well first you want to check to see if the CD drive is set to first boot in the boot order in BIOS.

If that is correct then you might want to see if you did an MD5SUM on the iso you burned as an image. Did you burn the CD image at the slowest possible speed. Check to see if the CD boots on another machine.

MD5SUM links : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
               [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If everything checks out it could be the CD drive.

---

### Post by PaulTR on 2009-06-15
Erm, should have included this in the original post. Got into the bios and set it for the CD drive to boot first, but it still won't go for it. Also tried the Ubuntu CD successfully on two other machines, an XP desktop and a Ubuntu running laptop.

---

### Post by PaulTR on 2009-06-15
Burned the CD by right clicking on the .iso in Ubuntu and clicking write to disc. I did it at the default speed option though, so I'll give making another one a shot at the slowest speed, see if that helps. Will also take an extra CD drive with me, though from what I understand her CD drive works fine.

---

### Post by presence1960 on 2009-06-15
> **PaulTR said:**
> Burned the CD by right clicking on the .iso in Ubuntu and clicking write to disc. I did it at the default speed option though, so I'll give making another one a shot at the slowest speed, see if that helps. Will also take an extra CD drive with me, though from what I understand her CD drive works fine.

Hopefully the other CD drive will do the trick. If the CD boots from 2 other machines I seriously doubt the problem is the CD.

---

### Post by jflaker on 2009-06-16
> **PaulTR said:**
> Erm, should have included this in the original post. Got into the bios and set it for the CD drive to boot first, but it still won't go for it. Also tried the Ubuntu CD successfully on two other machines, an XP desktop and a Ubuntu running laptop.

Again, did you watch your bios screen....it should say something about F1 for setup and F12 for boot menu....you need to hit F12 while the BIOS screen flashes up...It should ask you what device to boot from.

---

### Post by Metaljaz on 2009-06-18
Make sure you are using a CD and not a DVD if the drive is a CD drive.

---

### Post by MyR on 2009-06-18
I didn't read the full thread b/c it looked like too many words.  But there's 2 things I can think of.

1. Maybe her optical drive is bad. You could try a bootable Ubuntu USB drive instead.

2. I have a dell laptop and pressing F8 (or something?) during BIOS start up brings up the boot device menu; I would give that a try first. google to find the right button to push.

peace

---

### Post by running_rabbit07 on 2009-06-18
I don't know if it helps but I just loaded Xubuntu on a laptop with an external cd drive. There was an option to help load with cd while booted in windows. I just doulbe clicked cd and it had three options. Clicked the help option and it is loading as I am typing this.

Just an idea.

---

