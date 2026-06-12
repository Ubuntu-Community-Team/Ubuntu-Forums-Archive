---
title: "Problem while re-partitioning an existing WinXP"
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by simone.brunozzi on 2005-12-13
Hi guys,
my laptop came back after an hard disk crash, and obviously I have it with only winXP installed (they weren't able to save data).
I tried twice to install Ubuntu, but when I get at the point of "partitioning", after selecting "re-partition /part", the computer hangs up with nothing left to do but manually reboot.

Do you have any hints about it??

Is there a smooth way to FIRST re-partition everything (don't tell me partition magic, I WANT TO USE LINUX SOFTWARE!) and THEN boot with ubuntu CD and install it?

Thanks for any help!

Cheers,

---

### Post by tomski on 2005-12-13
yes you can use linux software to re edit the partition table for this you need

a live cd based distrobution (ubuntu has one)

insert disk when you're logged into windows, then reboot the pc, you may need to enable the cd to boot first in the bios (to enter this try hitting delete or esc or F2)
follow the setup procedure that follows (this look similar the install)
when you get to desktop search the menus for parted or qtparted if you cannot find that then you can use the linux version of fdisk , to start this open a terminal and type :

$ sudo fdisk --help (this will give breif details of how to use it)

or if you dont like that then try another live cd (knoppix or mepis) and have a look in the menus that come with those.
You may also want to try looking for something called 'hirens boot cd' which contains lots of very,very useful tools that can help you in a lot of different problems 

I can see that you do not want to use windows appp's but may i tell you that when you use the floppy based version of partion magic you are in a high mem dos enviroment & not windows, if you could name this it would be 'Caldera Dr Dos' which i have as a 7 floppy install & has lots of uses.


Lets face it when it comes to fixing a certain problem who cares if you use windows or mac,*nix, plan9, etc.. because from the sounds of it as soon as you have fixed the problem you will go and put linux on it, so if it fixes the problem use it !! dont make the job harder by restricting your tool collection.

I have even created Barts PE cd which is a windows install but live on cd for the simple reason that the same app on different OS's will give different results.
I like to be sure i have fixed the problem because windows will fall over at the slightest of problems but linux will hold on and try to work around the problem or even try to resolve it and only kernel panic as last resort or to protect hardware
 so to say that a problem is fixed just because linux works does not mean it is definately fixed.

what was the cause of the harddrive 'crash' and what was done to rectify that problem (did they replace the drive?)

---

### Post by simone.brunozzi on 2005-12-13
Hi Tomski,
thanks a lot for your answer.
Your suggestions are precious, I will follow them.

The hard drive simply crashed, and they changed it without additional cost (it was still under warranty). Obviously, they weren't able to save data inside the disk (but I luckily backup one a week, and it happened on tuesday yup!!!)

Thanks again, cheers,

Simone

---

### Post by tomski on 2005-12-13
i would recommend having a look for 'Hiren's Boot CD i could post a link but the content of that cd is a bit questionable (licenses,etc..)!!!!!!
one hint though try 9down in google

---

### Post by StefanoCole on 2005-12-14
Simone, go to [http://www.sysresccd.org/]("http://www.sysresccd.org/") and download the iso file: SystemRescueCd-x86-0.2.15 (110 MB).
Burn it to a CD. The SystemRescue CD contains an application called QtParted which is a Partition Magic clone for Linux.
Boot to the rescue disc, at the first prompt type "menu" and hit enter. At next prompt choose rescue disc. Wait for your prompt and type run_qtparted, hit enter. Choose your mouse - ps/2 - just type -3.
Wait for it, then you are in qtparted. Click hda on the left-top of your screen, now look right ... Select the win XP partition and resize it. Close the qtparted program and reboot your computer.

Hope this helps, ciao Stefano

---

