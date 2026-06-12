---
title: "Very Abnormal Boot time! please help."
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by Dwiman89 on 2008-12-16
Hi,
(This is rather long winded so ill sum it up to  keep from attention being lost)
Issues;
1) Its taking about 10 minutes for boot.
2) Cant figure out where the root Issue is.
3) Can't get the boot Order in the BIOS right.
4) cant get a working ubuntu install.

IM trying to install Ubuntu on a friends computer. It has turned out to me a major head hurt. Okay first off IT takes like 10 minutes for the computer to even try booting an OS. It sits at a blue HP screen for around 6 to 10 minutes before it says "no operating system found". I have tried unplugging the two CD-rom drives and the HDD to just see if it would speed up the process of booting and tell me that the OS is missing.
Well it still took about 10 minutes to tell me that objective information...

I installed Ubuntu on this computer before, but it wasnt taking the upgrades( it was stuck on ubuntu 7.10 a few days ago) So My friend asked me to simply reinstall the OS with 8.10.

8.10 installed fine a few days ago, but it would randomly get the "no operating system found" error at about 80% of trys to boot, and boot fine other times( after 10 minutes).

As a solution I simply tried reinstalling 8.10 again.... well It didn't make it the full install. I got a message saying something was wrong with ether the HDD, CD-ROM, or disk. Now it wont even load the previous ubuntu...

I have ruled out the OS disk by running the disk test on another computer.
I was trying to use a program called DFT([http://www.hitachigst.com/hdd/technolo/dft/dft.htm](http://www.hitachigst.com/hdd/technolo/dft/dft.htm)) to see if its the HDD but I cant get the program to run. Its supposed to run on boot up like the ubuntu disk does, and it works fine on other computers.

I must not be able to get the boot order right or something... I have went in the BIOS ad set it to check the CD-ROM first  with no avail...

The goal here is to get ubuntu running on this piece of crap without taking 12 minutes to boot... The system is an AMD athalon 1.3Ghz processor with a gig of ram so I know it has the beef to run ubuntu...
I have also tried using just a 256MB stick of RAM, and 512MB of RAM(two 256MB sticks) just to see if that had something to do with it too but it still took forever to boot...

Thank you.

---

### Post by Dwiman89 on 2008-12-16
I was able to check the hard drive on another computer with DFT and it received no errors.

---

### Post by Dwiman89 on 2008-12-16
I feel like im talking o myself... Okay I got ubuntu installed agian but its still getting the "no operating system found" message. Sense I have tested the HDD and it is fine, there must be something wrong with how the motherboard is talking to the HDD. the jumper settings are set to master.

Can someone please help me figure out how to diagnose this problem????

---

### Post by Dwiman89 on 2008-12-16
IM thinking maybe the BIOS needs an update... the computer is an HP xt933. im going to make a new thread for this...

---

### Post by robert shearer on 2008-12-16
On occasion I have had this boot up delay when trying to install on an older system.
It almost always has had to do with the hard-drive type and configuration as you suspect already.

Options and variables to consider are:

What IDE cable type are you using 40 or 80 wire??

1) Assuming an older system that is using IDE cables then look at the board end of the cable for a small 'hole' in one of the wires.This indicates that it is a cable select connector and the drive should be jumpered as cable select to match.
This can be tough for old drives/bios/etc to configure.
Usually easiest to change the cable for a standard ide cable.


2)Check the BIOS settings for the drives. Setting these to 'Autodetect' usually works for most drives. Occasionally older compys with vendor drives can have had their parameters set manually to suit the vendors odd drive and if you change the drive the BIOS can spend a long time hunting for the old one on start-up.

3)Try connecting the Hard-drive as master on the primary ide cable and the cd-rom as slave on the same cable. It is not ideal but often allows the os to be installed and bypasses the secondary IDE controller and helps with troubleshooting.

(Just spent three days trying to install only to find the secondary IDE controller is shot as someone has forced and misaligned the plug at some earlier point and fritzed it!!)

try those and repost if no change.

EDIT... don't update the bios  without checking the battery first.I had assumed you had already but on reflection most of the symptoms described point to a dying bios battery. Especially as they occour without any drives connected at all.

---

### Post by Dwiman89 on 2008-12-16
How do I check the BIOS battery? the thing is these issues wont near as apparent untill I attempted to upgrade... I didnt mess with any Hardware untill this all strted happening...

---

### Post by oilchangeguy on 2008-12-16
> **Dwiman89 said:**
> How do I check the BIOS battery? the thing is these issues wont near as apparent untill I attempted to upgrade... I didnt mess with any Hardware untill this all strted happening...

if the system time and date are correct, there's nothing wrong with the battery.

---

### Post by Dwiman89 on 2008-12-16
The Time and date are correct. I looked for a BOIS update but have been able to find it. I reset the BOIS to default too with no luck. I read somewhere that its a possability that the HDD isnt spinning up and loading fast enough for the BIOS to see it... I have tried setting the HDD jumpers to a 32MB limit and it would have more successful boots(although still hit and miss)

any ideas?

---

### Post by Dwiman89 on 2008-12-16
Also boot time is very fast now and I dont know why, but its still not finding the OS... the HDD is listed in the BIOs main menu though.

---

### Post by oilchangeguy on 2008-12-16
> **Dwiman89 said:**
> The Time and date are correct. I looked for a BOIS update but have been able to find it. I reset the BOIS to default too with no luck. I read somewhere that its a possability that the HDD isnt spinning up and loading fast enough for the BIOS to see it... I have tried setting the HDD jumpers to a 32MB limit and it would have more successful boots(although still hit and miss)

any ideas?

the spin rate has nothing to do with it. if it's plugged in, the bios will see it. and what are you talking about setting the jumpers to a 32mb limit? the hard drive jumper gives you the option of setting it to master, slave, or cable select. sounds like you're playing with the bios manual hard drive settings. set the bios to default, and leave it alone.

---

### Post by Dwiman89 on 2008-12-16
No I ment 32GB limit this particular HDD has 4 possible jumper settings(its labled on the HDD itslef) I can post a picture of it. ON setting is Master, one is slave, one is cable select, and the other is a 32 GB limit(the HDD is an 80GB)

Actually setting the jumpers to that makes it boot every time, BUT ts slow again, and if I am to leave it, thats a lot of wasted space limited it to only 32GB...

---

### Post by Dwiman89 on 2008-12-16
This idea with it not loading the HDD fast enough came from  this post...

> **hikaricore said:**
> I've had this issue with an older PC which I expect is related to a subpar motherboard/bios.

Your grub is likely in the correct place so I doubt that's an issue.
You may want to check your bios setting for an option such as Boot Delay.

On the troubled system I mentioned setting a boot or drive delay of 10 seconds or so made similar issues go away as the drive has time to fully power up and can be recognized by the system before attempting to load the OS.

To sum it all up I'm thinking this is more a hardware issue than a Linux issue in general, but that's just my opinion.  Hope this is somewhat helpful.

I couldnt do this because I dont have a boot delay option n the BIOs....

---

### Post by Dwiman89 on 2008-12-17
OKAY!!!!!!!!!! I got it booting right up ever time, although its VERY weird..... 


im using two hard drives to get it booting. the first master hard drive has nothing on it. its jut a blank 10gm unformated HDD....

The second slave HDD has Ubuntu on it.... it boots every time quickly...

so the questiion here is WHY does this stupid way work?????? I need to know so I can figure out where the REAL issue is...

---

### Post by sandy8925 on 2008-12-17
That's funny. It should actually be slower but I guess since master hard disk is unformatted it's not being accessed. I have a similar setup only with win xp + hardy on master and intrepid on the slave disk.I've never experienced the problems you have though.

I asked someone whether it would be slowed down if I had that kind of setup and he said yes.It's funny that yours actually boots up faster.

Could be soemthing to do with the HP system. The BIOS upgrade is not worth doing unless you have a serious problem and since it's working fine leave it.

Also check if you really set the jumper to master and not slave when you were trying it before.If you actually set it to slave earlier then that might explain why it wasn't working properly earlier and why it's workign now.

---

