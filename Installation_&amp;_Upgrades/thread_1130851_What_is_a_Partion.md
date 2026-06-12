---
title: "What is a Partion???"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by binglebob on 2009-04-20
When i start up Ubuntu and it goes to the installation screen i can go up to step four which involves partitions. it will not allow me to continue until i select a root system from the partitioning menu but all of the buttons are gray meaning i can't click them and the table is empty. Can someone explain what a partition is and then explain what is happening? Thanks...

-binglebob

---

### Post by upchucky on 2009-04-20
By definition, a partition is a divider, but i think that you want a better definition as it applies to operating systems.

I can only suggest that you do a bit of reading about how computers work as your question suggests that you do not know the basic fundamentals of operating systems. since Linux and windows both need partitions to work and a general idea of some basics is a bare minimum for either operating system administration, you will get very frustrated if you do not understand the replies to questions.

I am not trying to be rude, but there is some basic knowledge required for any operating system administration, and to save you time and get better responses from this forum, it is in your best interest to read about hard drives, partitions, memory, live cds, bootable devices, and basic computer management.

partitions on a hard drive allow for installation of operating systems, file storage, memory management, recovery, and file backups.

---

### Post by binglebob on 2009-04-20
You weren't being rude at all...but  I have a different question. I downloaded the file that you put on a CD yourself to install ubuntu. I selected the first option when I put the disk in which was try ubuntu or full installation. I restarted my computer and booted off the CD and got to step 4 yet again. This time it looked different. There were 2 progress bar like charts that said before and after in front of them. Now I want to install ubuntu and keep Windows, but I want the full installation of ubuntu. I need to know which option to choose when I get to that step.

Options:
1. guided - resize SCS|1 (0,0,0), partition#2 (sda) and use freed space
                    Microsoft Windows XP Home Edition| Ubuntu 8.10
New partition size: 60% (63.9 GBs)                   |40% (42.1 GBS)

2.guided - use entire disk
 * SCS|1 (0,0,0) (sda) - 120.0 GB ATA Hitachi HTS54251

3. manual
_____________________________________________________________________________
Can someone tell me which options will allow me to have Windows and Ubuntu installed fully?

---

### Post by upchucky on 2009-04-20
i am suggesting that you do the Try option first, this will prove that your hardware will be ok with an actual install. some hardware will have trouble getting to a graphical display, this potential problem will be exposed when you do the try first option

---

### Post by Therion on 2009-04-20
Keeping it simple, a partition is a piece or section of something.  Slice a pie into eight sections (regardless of size) and you've "partitioned" it.  Hard drives are much the same.  By partitioning you are "slicing up" the drive into distinct sections that your computer can use independently.

What you want to do is called dual-booting and you should be getting an option to do that.  The progress bars can be a little deceiving in my opinion.  If you can post up the verbiage of the options we can tell you which one you want to use.

---

### Post by Lunx on 2009-04-20
> **binglebob said:**
> I need to know which option to choose when I get to that step. I will edit this post in a second with the options.

Not sure which release you are trying to install, 8.10 or 9.04? (the install GUI has changed a little from one to the next, no idea about earlier releases like Hardy Heron as I've never tried them) When you get to that 4th step the options should be full install, guided, or manual. You want the option that lets you choose to install **alongside** your Windows partition. It isn't very clear in the GUI, but the graphical slider you mentioned can simply be moved back or forth to create the size of partition you want to keep for windows, and how much free disk space you want to give over to Ubuntu. I know that doesn't sound very clear but if you try it again and play with the slider I mentioned you'll soon see what I mean


Should go very smoothly, but back up all your Widows files you want to keep just in case something goes pearshaped (hasn't happened to me once and lately I've be changing my partitions more than my underwear as I've been trying out some different distros). If you run into any bother or aren't exactly clear on something it's probably good to ask here for advice before you try, but that said I don't think you should have too many troubles, Ubuntu's installer is the easiest one to follow from the distros I've been trying of late

---

### Post by binglebob on 2009-04-20
i am currently running Ubuntu in the try option....What should I be testing?

---

### Post by Lunx on 2009-04-20
> **Therion said:**
>  The progress bars can be a little deceiving in my opinion.


First time I tried installing Ubuntu (my first ever taste of Linux) it confused hell out of me until I realised it was actually a slider I could move. Why they don't make it more obvious or at least give more info about is something I think the devs should consider rectifying in future releases.

---

### Post by Lunx on 2009-04-20
> **binglebob said:**
> i am currently running Ubuntu in the try option....What should I be testing?


Check out that sound and video work, but be aware that you won't be able to play some files anyhow until you install, as you will need to install a few codecs and plugins. Don't let that put you off, very simple to do and plenty of people here will help you sort out what you need.

what sort of box you installing to, laptop or desktop? May be a good idea to post your computer specs so others can let you know whether you have anything that may cause issues, some hardware don't work well as some manufacturers won't/don't build drivers for Linux. Having said that, my box is a low spec OEM and I've not had one problem getting everything configured and working, couldn't be happier with how stuff works for me now.

---

### Post by binglebob on 2009-04-20
Im using a laptop...

Dell Inspiron 1525
# 15.4-inch WXGA (1280 x 800) CCFL TrueLife (glossy) screen
# 2.0GHz Core 2 Duo T7250 processor
# 2GB DDR2-667 SDRAM (up to 4GB DDR2 SDRAM available)
# 105GB 5400 RPM SATA HDD
# 8x Dual-layer DVD±RW drive
# Video: Intel Integrated Graphics Media Accelerator X3100
# Wireless: Dell Wireless 1390 802.11g Mini Card
# Media Card: 8-in-1 flash memory reader
# Input and Output Ports: 4 USB 2.0, HDMI, VGA, IEEE 1394a, RJ11, RJ45, 2 headphone, 1 microphone, 1 ExpressCard 54mm slot, 3 mini-card slots, consumer IR, S-Video
# Windows XP Home Edition SP2

Should I go on youtube to test sound and video?

---

### Post by upchucky on 2009-04-20
the main thing when booting using the try first option was to be able to get to the graphical desktop. since this worked perfectly it is ok to do an actual install

typically windows needs about 25 to 30 gig of space so it is ok to shrink it to about that after you have run the windows defrag utility a couple of times first. this is because windows likes to place stuff on the drive in random places. the defrag gets the data more compacted and makes resizing the drive easier. after you have done the defrag in windows, boot the pc with the live cd.

Then use the live cd to partition the drive. Ubuntu needs about 25 gig, and the swap partition is good if it is about half the size of the system ram. I have 2 gigs of ram and i set the swap to 1 gig.

you could divide the drive equally between windows and Ubuntu, the drive partitions can be adjusted again later if needed.

if after the install completes and you only see a blank screen, this is because a file called menu.lst needs to be edited to enable booting both windows and Ubuntu, don't panic, it is easy to do. if this happens just reboot with the live cd again, post in here, we will ask for some specific info and be able to tell you how to fix it.

everything will still be there, it is just on some systems that file needs some more info, and on some systems the install just boots right up.

this is due to unpredictable hardware differences in each machine.

---

### Post by binglebob on 2009-04-20
Sound and video work but sound is a little quiet...what now?

---

### Post by Lunx on 2009-04-20
> **binglebob said:**
> Sound and video work but sound is a little quiet...what now?


If you have your Windows stuff backed up, I'd just go with the install :D

The sound is down a little I'm guessing because of the **Front** setting in alsamixer, if you right-click the volume icon in your panel, you will see where you can open the volume control. The setting that says Front will be set to about 3/4 by default, turn that up full and you should be grinning.

---

### Post by theozzlives on 2009-04-20
I have an Inspiron 1525 and it runs Ubuntu fine.

---

### Post by ninjapirate89 on 2009-04-20
If you are going to dual boot with xp then you should make sure that you have defraggmented it before you do an install of ubuntu.

---

### Post by tornadof3 on 2009-04-20
> **binglebob said:**
> 

Options:
1. guided - resize SCS|1 (0,0,0), partition#2 (sda) and use freed space
                    Microsoft Windows XP Home Edition| Ubuntu 8.10
New partition size: 60% (63.9 GBs)                   |40% (42.1 GBS)

2.guided - use entire disk
 * SCS|1 (0,0,0) (sda) - 120.0 GB ATA Hitachi HTS54251

3. manual
_____________________________________________________________________________
Can someone tell me which options will allow me to have Windows and Ubuntu installed fully?

The first option here should do what you want. It will give windows about 63GB hard drive (including used & free space) and will assign about 42GB to your UBuntu installation, which should be fine.

---

### Post by tamas305 on 2009-04-20
> **tornadof3 said:**
> The first option here should do what you want. It will give windows about 63GB hard drive (including used & free space) and will assign about 42GB to your UBuntu installation, which should be fine.

I agree. However, personally, I would give Windows more space because of games and such. Ubuntu can run fine on anything more than 5gb and I would give it about 15.

-tamas

---

