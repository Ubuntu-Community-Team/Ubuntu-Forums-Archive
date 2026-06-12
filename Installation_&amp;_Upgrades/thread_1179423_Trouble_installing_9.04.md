---
title: "Trouble installing 9.04"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by Faceless79 on 2009-06-05
I have an older laptop, compaq armada e500, 192mb ram, 20gb hard drive, ati rage mobility 8mb. And ive been trying to install xubuntu 9.04. My 1st attempt went ok, it installed and when it said to remove cd and press enter it froze forcing me to remove the battery. When i powered it on again it went to the splash but again froze. My 2nd attempt went similar except i tried using 'noatip' at boot (after seeing a similar thread) and it booted....once. After trying to boot it up again it froze even with the boot command. 3rd attempt went just like the second except now im getting a grub error 18. I know what the error is but are no options in my bios to remedy it. Im pretty new to linux but i never want to go back to windoze please help, thank you for your time.

---

### Post by presence1960 on 2009-06-05
Try the altenate text based installer.  [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

System Requirements

The minimum memory requirement for Ubuntu 9.04 is 256 MB of memory. Note that some of your system's memory may be unavailable due to being used by the graphics card. If your computer has only the minimum amount of memory, the installation process will take longer than normal, but will complete successfully, and the system will perform adequately once installed.

Systems with less memory may be able to select "Install Ubuntu" from the boot menu to run just the installer, rather than the whole desktop, or may be able to use the alternate install CD.

---

### Post by Faceless79 on 2009-06-05
> **presence1960 said:**
> Try the altenate text based installer.  [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

System Requirements

The minimum memory requirement for Ubuntu 9.04 is 256 MB of memory. Note that some of your system's memory may be unavailable due to being used by the graphics card. If your computer has only the minimum amount of memory, the installation process will take longer than normal, but will complete successfully, and the system will perform adequately once installed.

Systems with less memory may be able to select "Install Ubuntu" from the boot menu to run just the installer, rather than the whole desktop, or may be able to use the alternate install CD.

I already installed it and it ran that one time, im just getting errors. This is my only way to get the distro so unless i can download the alternative and burn it while in live mode im kinda screwed it would seem

---

### Post by Faceless79 on 2009-06-05
Its not ubuntu im installing, its xubuntu and i meet its requirements. As a matter of fact live mode even runs faster than the previous windows xp install

---

### Post by presence1960 on 2009-06-05
> **Faceless79 said:**
> Its not ubuntu im installing, its xubuntu and i meet its requirements. As a matter of fact live mode even runs faster than the previous windows xp install

you are right on the bubble with RAM of 192 MB. If any is allotted to your on board graphics you fall short. you meet the requirements to run the CD but may be just shy to install from the Live CD. 

Note : System Requirements

Xubuntu is available for PC, 64-Bit PC.

CDs require 128MB RAM to run, or 192MB RAM to install. Desktop install requires at least 1.5GB of free space on your hard disk. 

see this for more info : [http://www.ubuntu.com/products/whatisubuntu/xubuntu](http://www.ubuntu.com/products/whatisubuntu/xubuntu)

I would find a way to burn the alternate text based install, even if I had to walk to use someone else's machine to download the iso and burn the image to disk.

---

### Post by Faceless79 on 2009-06-05
Something is getting lost in the translation i think. Ive installed it and had it running. I fixed the grub errow now it hangs when it tries to load the touchpad

---

### Post by presence1960 on 2009-06-05
sorry if I misunderstood.

---

### Post by Faceless79 on 2009-06-06
No problem. By the way i got it up and running by playing with the boot string for a bit. Except i cant for the life of me remember what i did. But its running like a champ except i am considering lxde or openbox to make it a bit faster

Ok i figured it out on line 2 of the boot code after the 'uuid=' line there was 'ro' after deleting that it boots fine. No idea what it is tho

---

### Post by Faceless79 on 2009-06-06
Ok it was booting but not anymore. Can anyone please help?

---

### Post by presence1960 on 2009-06-06
I hate to say it again, but why don't you try the alternate text based installer. It can't hurt. You have tried sticking to the Live CD but it obviously is not working. What have you got to lose?

---

### Post by Faceless79 on 2009-06-07
I cant do that, i have zero other way of getting on the net (im posting this using a cell phone) i did some research and apparently i put the boot flag in the wrong place. Where the vmlinuz and initrd files should be there were only shortcuts to the files. Im going to reinstall and make sure im carefull where i put the flag. Oh and thanks for atleast trying, i appreciate that and on a side note i had it up and running like a champ all night last night so i dont think the installation medium was the issue, it was my procedure

---

