---
title: "Start up - black screen - different context - Toshiba Satellite L670D-11Q"
date: 2010-11-28
forum: Hardware
---

### Post by kris7 on 2010-11-28
Hello friends,

I googled for quite some time but nothing helped. So desperate here I am.

**The problem:**after choosing to boot Ubuntu a black screen with a cursor appears. Unresponsive to any commands.
**The distro:** Ubuntu 10.10 x64
**The machine:** it is Toshiba Satellite L670D-11Q
**Some history:**
While installing ubuntu I had to choose the acpi=no option, only than I got the install screen and I was able to install the OS. After reboot I added to the grub the acpi=no, after crtl+x the system did not load. I succeeded in loading the system from the live CD only after I turned off the acpi. Clearly the problem is there. Anyway I could not succeed in starting the already installed OS.

I am not that into computer architecture and OS design so clearly I miss something. If you have any ideas, or need additional information to help, please say it.

A problem solved is a plus to the whole community :)
Thank you in advance.

---

### Post by kris7 on 2010-11-29
Up, anybody?

---

### Post by Stephen_at on 2010-11-29
do you know what video chipset it has in it?

---

### Post by kris7 on 2010-11-29
ATI Mobility Radeon&#8482; HD 5145

I will try the 32bit version of Ubuntu. I have the strange feeling that it might just work out.

---

### Post by bovent on 2010-11-29
I have the same problem with a Toshiba L670D-11N laptop using U10.10-AMD64, probably an issue with the acpi hardware vs drivers. Please share your results

---

### Post by kris7 on 2010-11-29
**So far only the netbook version works without any obvious problems.**
Anyway no change is observed after the installation of the 32bit version.

---

### Post by bovent on 2010-11-30
Thanks for the update, I'll try the netbook version tonight.
Did you perhaps try the 10.04 LTS? (64 or 32 bits)

I will also update my findings here. 

I bought this laptop especially as an Ubuntu workhorse, and I was so pleased to wipe of that crappy Windows 7 (it already crashed when creating the recovery discs while playing solitaire), so I definitely want it running Linux.

Any guru's out there that can share some tips I can try? 
Obviously the Toshy has some new chipset that doesn't work well with 10.10 at the moment.

---

### Post by kris7 on 2010-11-30
So far I only found that for some reason I can't boot up any windows cds... Tried windows 7 and windows vista.

---

### Post by kris7 on 2010-11-30
> **bovent said:**
> Thanks for the update, I'll try the netbook version tonight.
Did you perhaps try the 10.04 LTS? (64 or 32 bits)

I will also update my findings here. 

I bought this laptop especially as an Ubuntu workhorse, and I was so pleased to wipe of that crappy Windows 7 (it already crashed when creating the recovery discs while playing solitaire), so I definitely want it running Linux.

Any guru's out there that can share some tips I can try? 
Obviously the Toshy has some new chipset that doesn't work well with 10.10 at the moment.

I found a solution. For some reason the netbook version does not have any problems with the acpi. Probably because this "laptop" has netbook chipset.

So basically, install the netbook version. Choose the gnome graphical environment and you will end up with ubuntu looking just like the desktop version but without some software which you can add later :)

---

### Post by bovent on 2010-11-30
Hi Kris,
Thanks for the update.

I've seem to have fixed it. I've never had to get messy with Grub, but there lies the solution. (Google is your friend (is it?))

From the start:
- Boot your Ubuntu installation media
- Press the 'Escape' button during the first graphical screen
- Choose your preferred language
- press 'F6 Other options' and choose acpi=off
- Choose 'Install Ubuntu'
- Do your normal installation wizary routine
- Reboot and press 'Escape' right after your BIOS POST screen: This brings up Grub
- Select the first line (it should already be selected), and press the e button
- move your cursor to 'quiet splash' and after a leading space character you type acpi=off
- now press ctrl-x
- You are now booting your favorite OS! But are not finished yet..
- After the succesfull boot, open up a terminal, and type: sudo gedit /boot/grub/grub.cfg
- find your 'quiet splash' again, and type acpi=off
- save this file, and reboot. You now have a working Ubuntu install on your Toshiba L670D! (at least on my 11N model)

I did this install with U10.10-AMD64, and it seems that most hardware like video and sound is working.

Please share your findings for the 11Q model for the community.

good luck!

---

### Post by kd4dii on 2010-11-30
Hello
     I just got a Toshiba Satellite C655-S5056 and am having similar problems.  I was also having problems with booting cds.  One trick I found with tat problem is when I power up with the cd in the drive I enter the bios and move across to exit and do an exit saving changes and when it restarts the cd boots.  If I don't do this the cd doesn't boot.
     I also have to shut off acpi as if I don't the usb doesn't work.  If you do the way mentioned above by editing the grub config, you should run "sudo update-grub" as the changes will not go into the boot file unless you do.
     This whole thing has been frustrating to me as this is a nice laptop and I want to run Ubuntu in a normal fashion, also I hate to see windoze working better than Linux.
     Good luck, hope I was able to help a bit.

Bob

---

### Post by kris7 on 2010-12-01
I am sorry for the not replying faster. Thank you **bovent** and **kd4dii **for your replys. 

Bovent the first thing I did is what you advised me but it did not work out. Now I use the netbook version of Ubuntu and it works good. Only the mic does not work, sadly...

kd4dii it turned out that windows cds are corrupted. So at least I know I have a healthy laptop.

Anyway a bit offtopic, this machine has an awful bios in terms of options. I gives you no flexibility at all. Sadly for the lazy, you never know until the box arrives at your door :D

Hope this topic will help somebody in future, cheers.

---

