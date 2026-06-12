---
title: "Hanging on post install reboot"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by Joe Z on 2009-04-08
I just got an Appro 1U server (Dual Opterons 2 ghz, 4gb ram, 120gb IDE HD, NO CD), and am trying to install Ubuntu on it. 
The installation process seems to go fine, and after all is done it'll go to reboot. Once it reboots, it just sits on a blinking cursor and never loads the OS. 

I've tried to reinstall Ubuntu a couple times now, all with the same results. 

I'm sure I'm booting from the proper device, as I am able to select the device by pressing F11. Once the HD is selected (or by default), the cursor just blinks. 

I have several flash drives, but only my smallest 512mb one is recognized by the server's bios which is what I've used to load up the Net Install. I just purchased a brand new one this morning too, and it is not recognized by the bios. 

I can load up Slax as a mini OS, so the server is functioning properly...there just seems to be an issue with the install and I can't get a flash drive to be recognized that is large enough to store the entire ubuntu cd. When Slax is open, I can view the other flash drives. 

Any reason that one flash drive would work with the bios, but my other two (1gb, 4gb) won't? All are formatted FAT32. 

Please help! 

Thanks, 
Joe Z

---

### Post by upchucky on 2009-04-08
dont panic,its all still there, just need to do a few things

boot the pc using the ubuntu live cd then

download this

[http://sourceforge.net/project/platf...roup_id=250055](http://sourceforge.net/project/platf...roup_id=250055)

then do this in a terminal.


```
sudo bash ~/Desktop/boot_info_script*.sh

```

post the results of the file here so we know the drive geometry.

also download this and create the supergrub repair utility cd,

Supergrub

Get Supergrub to set up/repair Grub here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

after you have downloaded and created the supergrub disk boot from it then use it to fix grub.

you must read the instructions carefully and understand them, google what you do not understand. You will not hurt anything with this but can get very confused if you do not understand what it does.

there are people here that can tell you exactly what to do to fix your system based on the info the above file reports, however supergrub will also fix it, as long as you understand what it does and how it works.

---

### Post by Joe Z on 2009-04-08
Thanks for the fast reply.  Only issue is that I don't have a CD drive on this server. I can boot into Slax.  However, both of your links are not showing the full URL and have the ... in the href.  I'm sure I can find the Supergrub file, but what was the first one?  Also, which version of Ubuntu do you suggest?

---

### Post by upchucky on 2009-04-08
the first one is a small program that gets the drive geometry information from your machine and creates a file on your desktop that you can post here.

I checked my link, it did bring me to their site, but I think that sourceforge may be doing maintenance on the server, try again later, same for the supergrub link.

you could try searching their site for something like get bootleader or drive information.

if the site does not come back up soon you could ask in a new thread what the commands are to find what your drive information is so you can post the drive information here.

ubuntu 8.04 is the current long term supported release.

---

### Post by Joe Z on 2009-04-08
Ok,
I was able to run the info program, but I cannot figure out how to install supergrub.  At any rate, attached is the results.txt file from the info program. What should my next step be?

---

### Post by Joe Z on 2009-04-08
So a buddy suggested something is wrong with the MBR, but neither of us know how to adjust it.  Please Help!

---

### Post by upchucky on 2009-04-09
The site in my previous post where i linked to get supergrub is broken go to the folllowing link sorry. this site has comprehensive instructions with samples on how to fix grub. grub is what sets up the mbr, supergrub is what is used to fix grub when it gets confused.

Supergrub

Get Supergrub to set up/repair Grub here:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

after you have downloaded and created the supergrub disk, boot from it then use it to fix grub.

you must read the instructions carefully and understand them, google what you do not understand. You will not hurt anything with this but can get very confused if you do not understand what it does.

---

### Post by Joe Z on 2009-04-09
I have grub installed now, but it is throwing this:
Error 21: Selected disk does not exist

Attached is the new results.txt file.

---

### Post by upchucky on 2009-04-09
super grub is trying to set up on the wrong disk or partition, you need to tell it to set up the disk that has ubuntu on it,

you should see something like hda1 ext3  which is the filesystem type for ubuntu.

for some reason i can not open the files you are posting,they claim to be txt files but properties shows them as gif file.

so I cant tell you the exact steps to do

---

