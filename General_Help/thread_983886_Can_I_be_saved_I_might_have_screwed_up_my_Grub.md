---
title: "Can I be saved? I might have screwed up my Grub"
date: 2008-11-16
forum: General Help
---

### Post by slapshot2205 on 2008-11-16
So there is no need to search, I really did screw this one up. Originally I had wubi and i was trying to move it to a seperate partition and it worked but didnt load up because some kind of error. So i thought i would do the unetboot or whatever its called so i did that and what i thought what a good idea was, was to reformat my ext3 drive. I think that is were I went wrong because I believe my grub was on it. So now when I boot up it goes straight to Grub error 15, which means no ubuntu no windows so technically no anything

So my question really is, If I get a live cd and then install it in the ext3 partition will I be ok? Since it would technically install Grub with it?

Thank you and any help would be amazing. I am a total n00b when it comes to ubuntu so I am sure this was just a lack of common sense  problem. I just need to get back to my OS's.

---

### Post by Peter09 on 2008-11-16
If its just grub that you have screwed it is possible to recover from the LiveCD. Search here for grub recovery stuff.

---

### Post by slapshot2205 on 2008-11-16
Yeh, I forgot my standard forum mentality in a panic so i just kind of posted. I think I may have figured out a few things to do. One would be just uninstall Grub with the Super Grub disk or whatever I just need to get the disk and burn it and I think while I am out getting disks. Ill pick up a copy of retail Ubuntu live CD. I am at a college and just dont know anyone who has one themselves. Oh well at least mine will look professional.

---

### Post by Peter09 on 2008-11-16
Yeah, this may help.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by slapshot2205 on 2008-11-16
well I dont have ubuntu installed at all and actually reformatted the partition that it was on. But Windows is still intact and so is my Wubi install. I just cant get to it because Grub is blocking me from selecting any OS. 

Some stuff that you sent me might work. The only problem is that no place is open untill 11 that I could get stuff from. 

Im just stressed because If i lose everything It would be bad. I have most of my personal stuff backed up but I dont have windows itself backed up and the comp is 3 years old so I dont have the disk anymore. Yeh I know thats dumb but I have a bad habit of being impatient and I thought I could at least get ubuntu installed and then I would just figure everything else out later.

---

### Post by Peter09 on 2008-11-16
You may find that installing Ubuntu (dual Boot) will recover your windows O/S. Might be the best way to do it - sort of personal decision really, in this case lots of ways to go.

---

### Post by caljohnsmith on 2008-11-16
OK, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo fdisk -lu
```
And we can work from there if you want. :)

---

### Post by slapshot2205 on 2008-11-16
yeh Im going to make one of those here in a sec first I am going to try and delete grub since its the only thing thats left of my old install and if that doesnt work I am going to try and install ubuntu to the partition and hopefully it will all reset itself.

and well if that doesnt work I will just be like my computer is dying and prolly just wipe the drive and do a full on ubuntu install

---

### Post by slapshot2205 on 2008-11-16
so I just put in the super grub disk and everything has booted up so far
this is just the test run more tests to come soon 

Ill let you know if I need anymore help!

---

