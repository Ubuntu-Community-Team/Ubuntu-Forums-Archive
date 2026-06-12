---
title: "Booting help"
date: 2008-10-07
forum: General Help
---

### Post by tekkaman on 2008-10-07
Hello everyone

I have 2 IDE harddrives in my comp. One is the main one with XP. And the secondary one with vista. I decided to try Ubuntu. I created a partition on the secondary drive by making the vista one smaller. Up to that everying is ok. I installed Ubuntu on that partition. I expected that if I select to boot from the second harddrive I would've been presented the options of dual booting with vista. But that's not what happened. Instead I get a grub loading tool that boots before the main drive is able to boot XP. I didn't wanted to make any changes to the first drive. Because I mainly use XP. I verified to see if the boot ini of XP was altered via msconfig. But it seems it's intact. So the question is. Where is the grub loading tool located and why does it boot first than everything else. And how do I restore my main drive the way it was.

---

### Post by tekkaman on 2008-10-08
bump. Help anyone ?

---

### Post by caljohnsmith on 2008-10-08
Most likely what happened is that Grub got installed to the MBR (Master Boot Record) of your Win XP drive, while Grub's files (such as its menu.lst, or the file that lists your OS choices in the Grub menu) is on the other drive. You can restore Win XP's boot loader to the MBR by booting your Windows Install CD, going to the Recovery Console, and running:
```
fixmbr
```
That will let you boot directly into XP when you boot the XP drive on start up; or depending on how you installed Vista, you might instead get the Vista boot loader which will give you a choice of either XP or Vista. I would recommend changing your BIOS so that you first boot the Vista+Ubuntu drive on start up, then you can add Grub to the MBR of that drive, and after that you can configure Grub to boot either Ubuntu, Vista, or XP. Does that sound good? If so, to begin with boot your Live CD, open a terminal (applications > accessories > terminal), and do:
```
sudo fdisk -lu
```
And post the output. We can work from there.

---

