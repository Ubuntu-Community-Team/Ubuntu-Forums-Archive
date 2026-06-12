---
title: "Cant install ubuntu at all"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by Psyphre on 2009-04-30
Hi, Ive been using ubuntu since edgy eft and never had any real issues with installing. Except with this "errno 5 input/output error". 

It first started with hardy. I burnted 10cds, at slow speeds, both 32 and 64 bit. But I kept getting errno5 at roughly the same spot in the install with each one. Eventually I gave up and reinstalled gutsy. Waiting till intrepid came out. Intrepid installed brilliantly.

Now its Jaunty's turn and once again the ugly errno5 rears it face. Same spot. 23%/24%.
Burnt another CD, and same thing. Even switched in a different Harddrive to eliminate Hardrive as a possible cause. Still same (27% this time). Changed CDrom drive. Same thing.

I even downloaded intrepid, and burnt it, and tried installing. Guess what? Same thing!

My pc is completely and utterly useless now :( 
I cant install linux at all. I thought the hardy issue was a one-off but I guess not.

Have searched forums but no satisfactory answer beyond 'burn cd at lower speed', 'burn cd not DVD' etc etc.

Im lost, I'm linuxless and im exhausted :(


PS: Errno5 is:

```
This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD lens, to check whether the harddisk is old and in need of replacement, or to move the system to a cooler environment
```

---

### Post by Psyphre on 2009-04-30
FIXED IT!!!

I took out all ram sticks apart from 1.
Worked perfectly. Then just put in the extra sticks afterwards.

---

### Post by elitenoobboy on 2009-05-03
I am also having this problem. It's on a dell inspiron 1525, so for me, it's probably just easier to try to install intrepid first rather than open it up to remove ram sticks. Does anybody know what causes this? Bad ram? Weird ram config?

---

### Post by ahashim on 2009-05-13
i have the exact same problem. i have an hp pavillion 6500. i know for a fact that my hard drive is fine and my cd-rom is not faulty. ive burned several copies of it now and just doesnt work.

come on linux, i stand up for you when people wonder why i bother... gimme a bone here.

---

### Post by upchucky on 2009-05-13
the definition of insanity is doing the same thing over and over and expecting different results.

try a few different versions of linux live cd's, perhaps Knoppix?
try the alternate version.

you do realize the hardy is the last long term supported release.

intrepid and jaunty are beta.

you also should realize that 99% of issues are because of hardware, not linux. the reason it is hardware is because manufacturers are not letting linux developers have the hardware specs to create drivers, they are still brainwashed by the microsoft way of doing things.

---

### Post by Psyphre on 2009-05-14
On the laptop its defintely not worth taking out sticks of ram. 

I'm not convinced that uphucky is right in blaming the hardware. If it were the hardware then how come previous versions of ubuntu work but not jaunty?

Another solution that has worked for me was using a windowsxp CD to reformat, then delete the partitions in the windows xp cd and then start fresh with ubuntu.
If you dont have a windows XP cd, some people have had success with using Gparted on ubuntu's cd (Although when I tried it didnt work for me).

Hope it works for you guys.

PS: Even though Hardy is supposedly long term support its the one I've had the most issues with.

---

### Post by ahashim on 2009-05-14
so i downloaded ubuntu 8.04 and burned the iso to a cd and decided i'll just run the updater and get on to 9.04 that way... and guess what... i check the cd for defects from the boot-cd menu and it finds errors on it AGAIN.

what on earth is going on??

---

### Post by ahashim on 2009-05-14
how do i create a bootable usb-flash drive from the iso? because burning them just doesnt seem to work.

---

### Post by Psyphre on 2009-05-14
Sounds like the exact same issue I had with Hardy. Once it messes up, it seems to mess up any other ubuntu/linux install you do afterwards.

I sorted it out by wiping the harddrive by reformatting, installing windows XP, then wiping that clean and installing ubuntu again. I honestly don't think its your CD drive because I tried swapping drives before, but still had the same issue. Im afraid I dont know how to create a LiveUSB.

---

### Post by ahashim on 2009-05-14
just thought i'd update this thread. i managed to fix the problem.

i made a bootable usb-stick using the downloaded iso. this was done using the instructions provided here:

[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)

well it seems to be working fine... except i have no sound. and when i use the live-cd, i get sound. small driver issue which i'll work towards figuring out, but at least the installation is done.

---

### Post by Psyphre on 2009-05-14
good to hear you solved it. I'll try that USB trick in future if I get the same issue.

Altho I find it strange you need a windows pc to create a LiveUSB. Can it not be done natively in ubuntu?

---

### Post by Sierra 99 on 2009-05-14
When trying to install ubuntu, I'm receiving the following message and then the system hangs. [COLOR=Red]0.0556244 Pci: Bios bug #0 (00000031) Found[/COLOR]
I've tried upgrading/downgrading my bios without success. The cd works fine in other computers and installs fine as well. 

i have an Asus P5QL - Pro motherboard with the latest bios update. 

Any suggestions?

---

### Post by Psyphre on 2009-05-14
> **Sierra 99 said:**
> When trying to install ubuntu, I'm receiving the following message and then the system hangs. [COLOR=Red]0.0556244 Pci: Bios bug #0 (00000031) Found[/COLOR]
I've tried upgrading/downgrading my bios without success. The cd works fine in other computers and installs fine as well. 

i have an Asus P5QL - Pro motherboard with the latest bios update. 

Any suggestions?

Hi sierra, I'm afraid I dont have any suggestions on your problem, however I think it would be a good idea to you make your own thread. Hopefully it will allow more people to see your post as this thread mostly deals with CD install issues and may be overlooked by people who have the answer to your BIOS issue.

---

