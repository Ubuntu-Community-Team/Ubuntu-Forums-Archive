---
title: "Install problem"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by 0ra1suicid3 on 2009-03-09
Ok so
im trying to install ubuntu on a imac 24" 2008 mode, since my internal hd fail and not work yet is showing up on disk utility but cant do anything on it, so Im am running my mac os X from a external hd which is 750G, one partition which is 425.42g and it running my mac os X the second was a backup and it was 200g but.... i decided otherwise
so i split the 2nd partition into 2 named Home the second is swap as i read in the faqs on this website
 i burned the cd fine, checked the md5 and it matched and i installed Refit,the cd boots fine i see the menu

ok this is where im confused
i enter install ubuntu, i see the ubuntu bar but then takes me to a busy box terminal
since im pretty used to the unix terminal i new where i was,but no matter if i go to install linux or try ubuntu wi partion th unchanged to comp it takes me there i leave it running it say failed to load ata3 or what ever and goes on and on i left running for about 24 hours and it was still doing it

here the question! what do it do to fix it! what did i do wrong! i want to run ubuntu from the external hd home sinse the first one is used by mac os X
how do i install ubuntu?

---

### Post by upchucky on 2009-03-09
search for busybox, master bootloader repair, advanced supergrub disk, and menu.list on these forums, there are hundreds of posts on how to fix boot problems

---

### Post by 0ra1suicid3 on 2009-03-11
ok thank fo that, but that dint help really, i still cant boot the installer

now when i remove the stealh flag to debug,
i get alkind of errors

ata3 device is not ready
or Link to slow and get erno 16 then it hang at sd 4:0:0:0 [sda27]
i tryed with  presing f6 then add all_generic=ide irqpoll but with no succes at all! eny help?? im about to abandon all together re-downloaded 4 time burned 4 time and wasted 4 cd
as far as i know, md5 checks out fine, there same as the website say all but the secound one i dled

eny thought?

aslo in vmware fusion, i can install it fine

also the partition for ubuntu is fat32

---

