---
title: "Uninstalling Wubi"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by hatecrewdeathroll on 2009-07-25
Alright so i want to uninstall Wubi 9.04 but i have a couple questions.

One, when i uninstall it, does the bootloader disappear? When i was using a partitioned ubuntu system and i deleted the partition, GRUB was still there and i couldn't boot anything, so i just wanted to make sure

Two, I heard that with 9.04 you have to manually remove some files after you uninstall it. If this is true, which files do i have to remove and where are they?

---

### Post by nmaster on 2009-07-25
for wubi, just uninstall from the control panel.  i've done this a few times and nothing bad happened.  no other files to delete.  just do it from the control panel.  that simple.

---

### Post by philcamlin on 2009-07-25
go into windows and control panel and click uninstall :popcorn:

---

### Post by raymondh on 2009-07-25
[Wubiguide]("https://wiki.ubuntu.com/WubiGuide").

After uninstalling Ubuntu and to remove the Ubuntu option from the bootloader, you'll have to edit the boot.ini file and delete the ubuntu instance.  See the Uninstallation paragraph in the wubiguide.

---

### Post by nmaster on 2009-07-25
> **raymondhenson said:**
> [Wubiguide]("https://wiki.ubuntu.com/WubiGuide").

After uninstalling Ubuntu and to remove the Ubuntu option from the bootloader, you'll have to edit the boot.ini file and delete the ubuntu instance.  See the Uninstallation paragraph in the wubiguide.

i never had to do this.  uninstalling from the vista control panel was all it took.

---

### Post by raymondh on 2009-07-25
> **neal.m.master said:**
> i never had to do this.  uninstalling from the vista control panel was all it took.

I had to in XP .... after uninstalling thru add/remove, the option for Ubuntu was still present in the bootloader hence requiring a manual delete in the boot.ini file.

---

