---
title: "&lt;0&gt;Kernel panic - not syncing: Attempted to kill init!"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by since1989 on 2006-01-09
I really need help with this:
When I try to boot/install/use my Ubuntu live CD I get this error:
<0> Kernel Panic - Not Syncing: Attempted to kill init!
and then it hangs.

I've googled the problem but despite getting a ton of results I've been unable to find a solution. I've tried different HDs but I haven't had any success. I need to fix this by tomorrow afternoon or I'm screwed (I need to finish my semester final for Wednesday and I lost my power supply on my other computer).

I'm also having similar problems with every OS I try to install. Mandrake hangs on a black screen right after I chose to install. Linspire does the same thing. Windows 2000 hangs during the installation process when it says "Starting Windows 2000". Again I've tried several HDs and disc drives and get the same problem.


Here's what's directly before the kernel panic:
```
Code 01 00 00 00 eb 17 31 d2 8d 04 5a 83 bc 81 04 01 00 00 00 75 ea 42 83 fa 01 76 ed 31 c0 56b c3 57 31 c0 b9 45 00 00 00 8b 7c 24 08 <f3> ab 5f c3 90 90 90 8b 3c 24 04 8b 51 08 8b 42 0c 85 c0 89 41
```
```
<0>Kernel panic - not syncing: Attempted to kill init!
```

The hard drive was last formatted this summer, probably in August. I haven't used partition magic since the last format, so there is currently only one partition. I've googled this problem and I've found several forums but no one answers the question. It's a bunch of replies by people having the same problem.

I've installed and used linux in the past but by no means am I an expert.  Please any help would be greatly appreciated.

---

### Post by jonathanm on 2006-01-09
i had this problem ages ago but my solution might not work for you.

I had put the hard drive with everything on it onto the secondary ide port on the motherboard, this also gave a kernel panic.  You could try swapping the hd onto the other port and seeing what happens.

Sorry if your hard drive is scsi but i have had no experience with them

---

### Post by since1989 on 2006-01-09
[QUOTE=jonathanm]i had this problem ages ago but my solution might not work for you.

I had put the hard drive with everything on it onto the secondary ide port on the motherboard, this also gave a kernel panic.  You could try swapping the hd onto the other port and seeing what happens.

Sorry if your hard drive is scsi but i have had no experience with them[/QUOTE]

Alright, I tried that and it still gave me the same error.  Any other suggestions?

---

### Post by Maupertus on 2006-01-10
I just got the exact same error. Only I already have Ubuntu installed.
Now when I boot I get the exact error mentioned above. Even when I try the LiveCD. 

Only thing that has changed since yesterday is that I've put in a new powersupply. Hardly life changing.

---

### Post by grid-itc on 2006-01-13
I've just been confronted by this little S-o-B.  What did I do to cause this unhappy state of affairs?

I removed the DVD-RW drive (I wanted it for an external USB cradle).

Configuration is nothing spectacular - Athlon 2000+ (Palomino), 160GB ATA HD as master, DVD-RW as slave (it's a shuttle box and I didn't want to pack it with ATA cables so they share a single channel).

Simply refused to boot after I'd removed the DVD-RW drive.  I have 3 flavours of kernel installed - the one which ships with Breezy, 2.6.10-12-386 and 2.6.10-12-k7 (which is the default).  None of these would boot and none of the recovery options would boot either.  Played around with GRUB to no avail.

I did manage to cure it though.  I put a different DVD-RW drive back into the system and it boots again without complaining.  I've not tried any further diagnosis (at this stage I just want a working system), but it seems pretty odd to me that the boot process appears to be relying a piece of hardware which is not necessary for booting.

---

### Post by since1989 on 2006-01-16
I ended up solving this little problem by using another Ubuntu CD.  I ordered a few off of the site and I decided to try another one.  Luckly it worked and I'm using Ubuntu fine, for now.  My suggestion is to just find another CD, or download another copy.  Good luck!

---

### Post by dutch_boi1 on 2006-01-27
hi,

i have been having the same problem, i have recently installled windows as my ubuntu linux could not connect to the net, i tried everything and still no luck:( ... i wanted to try and run linux in windows to try and troubleshoot the problem, so i searched around the net on which linux works with Microsoft Virtual PC 2004 and , Ubuntu worked, they even had images.

So i installed Virtual PC 2004 and set it up right, with a virtual hdd etc... i put the ubuntu 5.04 i386 cd into my cd drive and rebooted the virtual system, the boot screen came up fine, then i pressed enter for a normal installation, some fast text went past then this error came up : <0>Kernel panic - not syncing: Attempted to kill init! .i tried using the boot cd, in both 4.10 and 5.04 and it still did noting, the same error :mad: so if anyone knows the problem to why this is happening , please let us know.

thankx

---

### Post by mohapi on 2006-01-28
I ran into this today for the first time, trying to reinstall Ubuntu. I had reformatted the drive and got the kernel panic error before most of the initial setup was even over.

I can only suspect it was somehow related to the reformat. I ran Active@'s Killdisk on the drive, start to finish, and when last I looked (I had to go to work before it finished), it was installing normally.

Of course, that being said, I'll probably go home and see the kernel in a panic again. Sheesh. :( Kernels are flighty that way.

Edit: I'm using Breezy.

---

### Post by ubuntes on 2006-01-30
[QUOTE=mohapi]I ran into this today for the first time, trying to reinstall Ubuntu. I had reformatted the drive and got the kernel panic error before most of the initial setup was even over.

I can only suspect it was somehow related to the reformat. I ran Active@'s Killdisk on the drive, start to finish, and when last I looked (I had to go to work before it finished), it was installing normally.

Of course, that being said, I'll probably go home and see the kernel in a panic again. Sheesh. :( Kernels are flighty that way.

Edit: I'm using Breezy.[/QUOTE]

I am pretty new to ubuntu.  I recently installed ubuntu on one of my systems without any problems.  So far i'm in love.

I just tried installing on a second system, and I have run into this problem.  I will try the suggestions and keep posted on what I find.  Wish me luck.

---

### Post by ubuntes on 2006-01-31
Okay I was fortunate enough to fix my problem.  First, I tried swapping out the cd-rom drive since it was an old drive.  This did not work.  Next I tried moved my memory stick to the second slot and WHAM!!  Everything worked fine.  

My Specs:
ECS Nforce3-a mobo
Kingston pc3200 valueram
sempron 2800+ cpu
350 watt psu
Maxtor 160 hd

Good luck to all

---

