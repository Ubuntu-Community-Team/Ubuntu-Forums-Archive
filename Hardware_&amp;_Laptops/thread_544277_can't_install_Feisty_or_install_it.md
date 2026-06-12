---
title: "can't install Feisty or install it"
date: 2007-09-06
forum: Hardware &amp; Laptops
---

### Post by papa6 on 2007-09-06
I've posted this at launchpad with no responses in awhile so I'll try here.

[https://answers.launchpad.net/ubuntu/+question/12712](https://answers.launchpad.net/ubuntu/+question/12712)

and 

[https://answers.launchpad.net/ubuntu/+question/12828](https://answers.launchpad.net/ubuntu/+question/12828)

question 12712 has a link to my PC's specs. anyhow, my mainboard has the sata ports built-in at the lower right hand side of the mainboard([http://h10025.www1.hp.com/ewfrf-JAVA/Doc/images/c00605782.jpg]("http://h10025.www1.hp.com/ewfrf-JAVA/Doc/images/c00605782.jpg")). I also have standard IDE ports for legacy drives. my drive is in the white sata port. channel 4 master.

So when I try to boot the feisty livecd, it hangs up on an error about sata2. but during livecd boot-ups, if i hit ctrl+alt+del, i can by pass the hang-up and get into livecd eventually. so i try gparted one time, it can't find my sata drive, the next livecd bootup, i try to regular install and when it gets to the partition stuff, it too can't find my drive.

any advice?

---

### Post by be4truth on 2007-09-06
Your sata drive is the only harddrive in your box? CD/DVD is IDE? It looks to me that your computer boots the sata drive as ide. There is a setting in the bios which lets you choose to handle sata as sata or ide. Can you check that? You will find this probably somewhere under ADVANCED.

---

### Post by papa6 on 2007-09-06
yes there is in Bios. my only fear would be that if I disabled the IDE DVD/CD roms, i won't be able to use them for installation. but i can select ide primary/secondary or both. I think I have it set for both.

my legacy IDE channels are 1 and 2 while the sata are 3 and 4,being that the sata drive is on 4 primary channel.

---

