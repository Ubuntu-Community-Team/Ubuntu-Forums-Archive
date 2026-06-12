---
title: "Installing Ubuntu 9.10 Alongside Mac OS X"
date: 2009-12-09
forum: Hardware
---

### Post by mwmsje on 2009-12-09
I currently have an Intel MacBook from Apple's 2008 range, which runs Mac OS X. Around about a week ago I used the 'BootCamp Assistant for Windows' software on my Mac in order to install Ubuntu. I got quite far in the process, then it informed me that it was unable to complete and that I have to reformat the disc.

Therefore I had my chance last night. I reformatted the disc and installed a fresh copy of OS X onto it. However it's only just occured to my that I was using 'bootcamp for WINDOWS' to install it, is this correct?

Question: If you're got experienced with installing Ubuntu on a Mac, could you please link me to any documentation you found useful or any particular methodology you used, as I'm not too sure where to start.

---

### Post by killa.fr0gg on 2009-12-09
First you need to use Disk Utility to partition your disk to the format of your choosing. Just use the nice gui to create a new partition. Basically, you'll be deciding on how big your Ubuntu install will be. Next, you'll want to install something like rEFIt to give you a disk option on boot. This way, when you've installed Ubuntu you'll be asked which OS you want to start into.

Download Ubuntu (standard standard vanilla standard) and use Disk Utility again to burn the .iso file to a CD. Insert the completed CD into your disc drive and start the computer whilst holding the C key to start from the CD drive and install Ubuntu on your new partition. MAKE SURE you select the right partition on install, as if you select the wrong one, ALL OF YOUR DATA WILL BE LOST.

On boot, if you installed rEFIt or something similar, you will be given the option to boot into OS X or Ubuntu. Most things work flawlessly after fresh install. Most anything else that doesn't will after you update. Anything further and that's why this forum is here!

---

### Post by mwmsje on 2009-12-09
Thanks a lot for the reply. 

You say to install the *"standard standard vanilla standard".*

Will I not be able to install the latest release i.e. 9.10?

---

### Post by killa.fr0gg on 2009-12-09
> **mwmsje said:**
> Thanks a lot for the reply. 

You say to install the *"standard standard vanilla standard".*

Will I not be able to install the latest release i.e. 9.10?


Sorry for the confusion. What I meant was don't go searching for the "right install disc." Just get the same disc everyone else uses (main link).

I say "sorry for the confusion" because my attempt to avoid it seems to have had the opposite effect!#-o

---

### Post by mwmsje on 2009-12-09
> **killa.fr0gg said:**
> Sorry for the confusion. What I meant was don't go searching for the "right install disc." Just get the same disc everyone else uses (main link).

I say "sorry for the confusion" because my attempt to avoid it seems to have had the opposite effect!#-o

I see, so I will be installing the latest Ubuntu ISO (9.10).

I just partitioned the disk however I was only allowed to format it with "*Mac OS Extended(Journalled)"*. Will this be okay to install Ubuntu on?

---

### Post by mwmsje on 2009-12-09
I'm following this[1] tutorial at the minute and I'm a little stuck. I've followed it through to the end however I'm up to the 'When you get the "Ready to install" dialog do *not* click on Install button because we still need to tell the installer to install the boot loader to a non standard place. Click on **Advanced** instead."

However, when I click advanced, all I get is:
-----------------------------------------------------
Boot Loader

[tick box(ticked)] Install Boot Loader

Device for boot load installation:
    (hd0)

//some survey crap.
-------------------------------------------------------

It says nothing about 'GRUB'.

 [1] [https://help.ubuntu.com/community/MacBook/TripleBoot](https://help.ubuntu.com/community/MacBook/TripleBoot)

---

### Post by killa.fr0gg on 2009-12-10
Are you trying to double-boot or triple-boot your system? I am unclear as to exactly what you are doing that is giving you problems. Please follow my instructions from before or post the process that you are undergoing so I can help you. I very happily boot my system into Ubuntu often.

---

### Post by mwmsje on 2009-12-10
Well I'll be using Ubuntu whenever I'm in work and Mac OS X for home / other things. Therefore I'll currently be 'double booting', however I wouldn't be surprised if I were to install Windows in the future.

I'm just slightly confused as to where I install the boot loader as I'm not familiar with Macs. Surely if I install it for the 'whole disk', then it's just going to continuously boot Ubuntu and ignore Mac OSX? Or does reFit counteract this process??

---

### Post by killa.fr0gg on 2009-12-10
when you start from the install disc after partitioning your hard drive, boot into the live GUI, open a terminal and type sudo gparted. This will bring up a partitions manager. Select the partition you plan on installing Ubuntu on (and for the love of god, PLEASE select the right one) and click "erase disk." Afterwards run the installer and perform a normal install onto that partition. Before you give the final install command, just go to the settings and install GRUB on dev/sda3 (or leave it be if that is already the setting). After install, boot to the rEFIt splash and click the disk icon and sync your Master Boot Record. Then you can start into Ubuntu.

---

