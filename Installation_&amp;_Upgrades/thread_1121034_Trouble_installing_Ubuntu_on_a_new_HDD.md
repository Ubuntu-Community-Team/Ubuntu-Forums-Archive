---
title: "Trouble installing Ubuntu on a new HDD"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by denphi03 on 2009-04-09
[QUOTE="lindsay7"]
Also, if it is a sata hard drive some motherboards need to have the bios set to have the sata controller set in bios.[/QUOTE]

Hello, I am new to Ubuntu and this forum, but I have a similar issue to the original poster, so I figured this is a good place to ask...

My wife dropped her gateway mx6930 laptop and broke the (SATA) hard drive permanently. I bought a new SATA hard drive and of course it happens to be a different manufacturer and model, but I'm trying to get Ubuntu on it.

The computer boots to bios and i can configure it, but once i press "install" ubuntu tells me that it cannot detect my hard drive.

i think setting my sata controller in bios might fix this issue, but i need a little guidance on how this is accomplished please?

---

### Post by manishtech on 2009-04-09
Are you able to boot as a Live environment?
Is the Hard Disk connected properly?

---

### Post by denphi03 on 2009-04-09
The hard drive disk is definately *physically* connected properly. as far as anything else, probably not.

Ubuntu runs from cd and gets to the install screen (keyboard only). Then i hit 'install' and the disc spins for a while and then i get an error message saying that it cant find my hard drive.

i dont have any driver disks for the new hard drive (western digital 250 gb sata). and i dont have any driver disks for the mobo either

im assuming this is a bios issue. but i dont know what to do about it

---

### Post by Yvan300 on 2009-04-09
Most likely it's the bios unable to recognize the hard drive, because ubuntu comes with great driver support. Can't remember at the moment but there is supported to be a setting menu in the bios that shows connected peripherals. Is the new hard drive listed?

---

### Post by denphi03 on 2009-04-09
> **Yvan300 said:**
> Most likely it's the bios unable to recognize the hard drive, because ubuntu comes with great driver support. Can't remember at the moment but there is supported to be a setting menu in the bios that shows connected peripherals. Is the new hard drive listed?

great point.

i dont think so, but i'll check it in a few minutes and get back.

on a side note - I know that everyone on this forum is probably a ubuntu fan, but i simply can not express the excitement i have about ubuntu. i tried a dual boot setup on my laptop a few weeks ago and the system has impressed me ever since.

i have been professing its greatness to all of my friends and i'm even helping a buddy of mine install on his ps3. so cool :)

i'm already impressed by the user community as well. so in advance- thanks everyone!

---

### Post by lindsay7 on 2009-04-09
On sata hard drives for desktops there is a jumper at the back of the drive to set it for 150 speed or 300 speed. If the motherboard is set up to only run at the 150 speed and the drive is set for 300 the motherboard will not recognize it. I am not familiar with laptop drives I have only used an IDE drive on one and they do not have that feature.

Check you documentation for the drive and see if your laptop drive has this jumper setting arrangemnet and if i does make sure that it is set to the 150 speed.  If this solves the problem then leave it that way. If it does not then you can change it back and continue to trouble shoot.

---

### Post by manishtech on 2009-04-09
> **denphi03 said:**
> 
I know that everyone on this forum is probably a ubuntu fan, but i simply can not express the excitement i have about ubuntu.

Fan is a correct word :p

I am not a blind supporter of Ubuntu though. We even need critics to find out the mistakes which can even help in better quality. I do criticize Ubuntu if its fails to deliver in some area. All those criticism is constructive.

---

### Post by coffeecat on 2009-04-09
**denphi03**, if none of the other suggestions work, the problem may be because a brand new drive is completely blank and has no partition table or disklabel. Boot up from the live CD and go to System -> Administration -> Partition Editor. It should show you the size of the hard disk, but completely unallocated. Now the procedure varies according to which version of Gparted (the Partition Editor) you have on whichever version of the live Ubuntu CD you are using.

In Jaunty (which is what I am posting from) you go to Device -> Create Partition Table. In earlier versions (from memory) you go to Gparted -> Create disklabel (or something like that). Have a hunt around and see which fits. But whatever you find, make sure you choose 'msdos partition table' or 'msdos disklabel'. Yes, that's right - msdos. Sorry. :(

You don't have to create any partitions now. If you want the installer to do this, at the partitioning stage just choose whichever guided option you want.

---

### Post by denphi03 on 2009-04-09
> **coffeecat said:**
> **denphi03**, if none of the other suggestions work, the problem may be because a brand new drive is completely blank and has no partition table or disklabel. Boot up from the live CD and go to System -> Administration -> Partition Editor. It should show you the size of the hard disk, but completely unallocated. Now the procedure varies according to which version of Gparted (the Partition Editor) you have on whichever version of the live Ubuntu CD you are using.

In Jaunty (which is what I am posting from) you go to Device -> Create Partition Table. In earlier versions (from memory) you go to Gparted -> Create disklabel (or something like that). Have a hunt around and see which fits. But whatever you find, make sure you choose 'msdos partition table' or 'msdos disklabel'. Yes, that's right - msdos. Sorry. :(

You don't have to create any partitions now. If you want the installer to do this, at the partitioning stage just choose whichever guided option you want.

two issues:
1) not really new- its a used hard drive to replace the old one
2) i have no disks. no firmware. no bios. nothing. if i need them i will have to find another way to acquire them

---

### Post by denphi03 on 2009-04-09
> **lindsay7 said:**
> On sata hard drives for desktops there is a jumper at the back of the drive to set it for 150 speed or 300 speed. If the motherboard is set up to only run at the 150 speed and the drive is set for 300 the motherboard will not recognize it. I am not familiar with laptop drives I have only used an IDE drive on one and they do not have that feature.

Check you documentation for the drive and see if your laptop drive has this jumper setting arrangemnet and if i does make sure that it is set to the 150 speed.  If this solves the problem then leave it that way. If it does not then you can change it back and continue to trouble shoot.

yes, these laptop hard drives also have jumper setting capabilities, but by default the master is always set to "no" jumper. in other words, they usually dont even come with a jumper on a new laptop

---

### Post by denphi03 on 2009-04-09
now my bios is seeing the hard drive (kind of). it says

Main SATA: 0MB SATA1

why would it do that?

oh, and fyi- i just found out the oem hard drive was also western digital

---

### Post by lindsay7 on 2009-04-09
Sata 1 is the 1.5 gbps or the 150 speed I talked about before. Does the bios have a way to set the motherboard to that setting?

---

### Post by denphi03 on 2009-04-09
> **lindsay7 said:**
> Sata 1 is the 1.5 gbps or the 150 speed I talked about before. Does the bios have a way to set the motherboard to that setting?

i have just gone into the bios and there is absolutely no option to do anything with my hard drive options in my bios.

after downloading the iso image for the drivers and trying to install this hard drive

i am starting to suspect that the used hard drive i got was actually DOA.

thanks for the help, but I am going to try and return this through ebay ;)

---

### Post by pbotros1234 on 2009-04-09
I had a similar problem with a fully functional hard drive, a Western Digital hard drive, as well.

I have had Ubuntu Hardy on it for awhile, and I have installed numerous other linux's on the hard drive, and everything worked fine.

However, when I tried to fresh install intrepid via a live cd, it didn't see my hard drive either.

I have no idea what the reason is, as fdisk could see it, but the intrepid installer apparently couldn't.

To fix this, download the Hardy Live CD ISO, and install that. It should work fine.

Then, follow the directions to upgrade Hardy to Intrepid, and smooth sailing from there, hopefully :)

---

