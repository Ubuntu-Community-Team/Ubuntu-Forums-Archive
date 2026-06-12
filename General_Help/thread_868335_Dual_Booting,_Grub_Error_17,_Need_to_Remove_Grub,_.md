---
title: "Dual Booting, Grub Error 17, Need to Remove Grub, Fixmbr not working?"
date: 2008-07-23
forum: General Help
---

### Post by mithbuntu on 2008-07-23
Hello All.

I'm in the middle of replacing my IDE HDDs with SATAS since my new mobo can only support 2 ides (and my cd is one...).

Because of this, I removed ubuntu temporarily from my system, but I am unable to now boot into XP.  I was booting xp/ubuntu previously, but I am now trying a quad boot with hacintosh, ubuntu, xp, and vista.

Right now the only OS I have installed that works is Vista, but XP will work once I remove grub and get rid of the error 17.

My question/what I need help on is that even after a fixmbr in the recovery console for my XP install, I am getting grub error 17.  Shouldn't fixmbr have removed grub from my xp hdd and allowed xp to boot? 

Thanks.

---

### Post by FIONEX on 2008-07-23
depends on what fixmbr is doing actually.  i would try:
fdisk /mbr

error 17 means a bunch of different things in grub.  The last time I got that was a when a configuration script accidentally misdiagnosed my configuration.  It was trying to find my linux partition on my windows partition.  Edit your grub menu file and fix it manually.

---

### Post by logos34 on 2008-07-24
> **mithbuntu said:**
> My question/what I need help on is that even after a fixmbr in the recovery console for my XP install, I am getting grub error 17.  Shouldn't fixmbr have removed grub from my xp hdd and allowed xp to boot? 

fixmbr would have overwritten whatever was on the MBR of the ubuntu/xp hard disk, but that is apparently not the Bios boot drive.  So switch the Bios hard disk boot priority so the ubuntu/xp drive is first, or else boot from the vista drive and get [EasyBCD]("http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home")--add xp entry to that. 



> **FIONEX said:**
> depends on what fixmbr is doing actually.  i would try:
fdisk /mbr

I believe that command only works from the win98 boot floppy, whereas mithbuntu is using the xp install cd, where the usage is 'fixmbr'

---

### Post by inkrypted on 2008-07-24
in the recovery console type fixmbr then press enter then type fixboot and press enter then type quit and press enter.

I dual boot too.:)

---

### Post by louieb on 2008-07-24
> **mithbuntu said:**
> ... Shouldn't fixmbr have removed grub from my xp hdd and allowed xp to boot?

I would think so. Unless it fixed the wrong drives MBR. Did you try unplugging all the hard drives except the XP drive? - don't give fixmbr a choice.  Good Luck.

---

### Post by Setagana on 2009-05-10
Is there any way of pointing fixmbr to a certain drive? As I have a netbook I'm using a live USB stick to access the recovery console but I suspect fixmbr is just trying to fix the boot record of the usb stick as it is the first device in the bios boot priority list. Whenever I remove the disk and try boot from the HDD I continue to get the grub error. But if I change the boot order then I can't get to the recovery console... Any suggestions?

---

