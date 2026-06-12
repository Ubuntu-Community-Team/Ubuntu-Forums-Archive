---
title: "Installing ubuntu"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by mac-doggie on 2009-03-13
Hi,

I'm pretty new to linux and ubuntu and decided to try it, so I downloaded the latest version and tried booting from the CD. Everything worked fine so I thought let's try installing it next to my XP installation. It all looked like it was going to work, only when I came to the reboot part of the installation I was given a bootloader error.

Grub loading please wait.

Error 21

So I googled a bit to try to find an answer to this. I figured out that the error means the disc is not recognised by the BIOS or something like that. I tried some different things in the BIOS but it didn't help. So I thought lets just reboot with the windows cd and choose repair mode so I can do a fdisk /mbr.

I inserted my win xp cd but after some loading I was presented a STOP error window (BSOD) Grrr...

I don't have a floppy drive anymore, so creating a bootfloppy also isn't an option...

I'd realy like to get both ubuntu and win xp running, but at least I need to get my windows installation back to work...
At the moment I can only boot from the Ubuntu CD, but that takes more then 5 minutes to boot (is that normal by the way)

I tried some console commands in grub like:
```

grub> find /boot/grub/stage1
 (hd2,0)

grub> root (hd2,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+16 p (hd2,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

```

but after rebooting it still didn't work. I removed the partition with the partitioning tool and installed the whole thing again. But this time after rebooting the Error 21 was gone. The screeen now just freezes when it reaches the boot from CD prompt. normaly that stays only for a few seconds before continue loading from harddrive...

I pressed ctrl-alt-del a few times but it just wasn't going to work. Windows install cd still doesn't work.

My situation:
 hda1 window partition
 hda2 windows partition
 hdb 
 hdc

I have three 500 Gib SATA discs one contains windows and the other two are a striped raid configuration.

While I am typing this I get a hunch...
wait a minute....
.................

yes... I got it. I turned of all raid settings in the BIOS and now the grub works without any hasitations... And yes my win XP boots again....

now lets try if Ubuntu will also start...

yes that also works. and a lot faster than from CD.. cewl...

Now My final question. How do I make win XP my default startup option in GRUB ? Because after 10 seconds ubuntu will automaticly start and I think my girlfriend won't be happy with that :-) 

I'm glad this long story was all for nothing ... well not really nothing so I hope to get an answer to my one final question...

kind regards,

mac

---

### Post by iKonaK on 2009-03-13
```
gksu gedit /boot/grub/menu.lst
```....and put this before the ubuntu entry :
```
title  Windows 95/98/NT/2000
root        (hd0,0)
makeactive
chainloader    +1
```*(hd2,0) probably in your case....

---

