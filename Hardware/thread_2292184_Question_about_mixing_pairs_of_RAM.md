---
title: "Question about mixing pairs of RAM"
date: 2015-08-25
forum: Hardware
---

### Post by Old_Printer on 2015-08-25
I have a question about configuring RAM. I have two matching sticks of DDR2 2G PC2-6400 and two matching sticks of DDR2-800 2G (2X2G) PC6400. There are four slots on my ASUS, color coded, of course: DIMM_A1 (yellow) and DIMM_A2 (black); DIMM_B1 (yellow) and DIMM_B2 (black).

Can these two pair be used together? Am I to assume that, if they can, one of each pair should go in the same color slot?

I thought they would give me 6G total, if I was understanding them correctly; however, in Win7 they displayed barely over 3G. They did, however, make VirtualBox in Zorin stop hanging when I installed them. I was getting some stop and go while using the scanner, and each time I maximized my XP in VB, it sometimes took 10 to 15 seconds before I could move the cursor.

Zorin performance really increased, while a Win7 drive barely crawled when I went to move a couple of files and to use my WinISO to burn a disk.

Old_Printer

---

### Post by Bradley_J_Doern on 2015-08-26
[COLOR=#000000]DDR2 DIMM channels need to be matched pairs (from your description, you've got channel "A" and channel "B" on your mobo, though they arent color coordinated, which is odd)
Also, I'm having a hard time understanding what exactly you have for memory...

[/COLOR][COLOR=#000000]two matching sticks of DDR2 2G PC2-6400[/COLOR][COLOR=#000000]
and
[/COLOR][COLOR=#000000]two matching sticks of DDR2-800 2G (2X2G) PC6400

Speed is the same, and even if they werent, you would just set the speed, timings and voltage to the LOWEST of the mixed chips for them to function correctly.

My question is...  are these all 2gb chips?  "2x2g" usually refers to the memory set itself, from what youve got posted the 2x2g kit should be 4gb total, and the other two chips are 2gig each...  you should have 8gb total ram...

That aside, always check BIOS for RAM settings and capacity.  It will tell you definitively how much is AVALIABLE, regardless of if the OS is actually using it.  I know some versions of Win7, especially non-64bit systems, wont do the 4gb thing.

Also, in a VM you specify how much of the RAM that the VM gets, and if you specify too much, itll cause massive issues with system latency, which you described.
[/COLOR]

---

### Post by Old_Printer on 2015-08-26
Thanks for the reply, Bradly_J_Doern. I'll take a look in the BIOS. The labels on the two sticks with the parenthesis 2G (2X2G) are a bit unusual for me. That's why I had to ask. I can post back when I get them to register properly.

Old_Printer

---

### Post by Bucky Ball on 2015-08-26
If they're not, try using them with one set in slots 1 & 3 and the other in 2 & 4. I don't know about other boards, but that is the way my older one works.

You will be limited by the slowest and they will not work as four match sticks would because, well, they're two different pairs. :)

---

### Post by Old_Printer on 2015-08-26
Okay, I have all 4 sticks installed, and I went by Bucky Ball's configuration: 1 & 3; 2 & 4. Ubuntu shows, in the "About" window, that I have 5.8 GiB. The BIOS shows 6071MB. I think I should have 8 GiB, though. I'm going to do some more swapping and check the readings again.

Old_Printer

---

### Post by QIII on 2015-08-26
Don't go looking too hard.

It looks to me like you should have 6GB by your count.

Ubuntu is saying you have 5.8GiB.

Notice that **GB** != **GiB**.  The units of measure are different.

GB = 10^9 bytes  <-- this is how manufacturing engineers think: decimal.  1000 (10^3 = 1000) bytes is a kilobyte.  This is how the OEM sells it.  This is how Windows reports it.

GiB = 2^30 bytes <-- this is how computer scientists think: binary.  1024 (2^10 = 1024) bytes is a kilobyte.  This is how I use it.  This is how Linux reports it.

That works out to 1,000,000,000 bytes per GB and 1,073,741,824 bytes per GiB.  So one GB = 0.931GiB.

Notice that a GiB is slightly LARGER than a GB.  That means that the total number of GiB is going to be SMALLER than the number of GB.  In fact, I would expect 6GB to be about 5.59GiB, or roughly what you are seeing.

I reckon that Ubuntu telling you it has 5.8GiB is about right, if just slightly generous.

---

### Post by Old_Printer on 2015-08-26
Thanks, QIII. I appreciate the reply -- and the info.

My two sticks that are 2G PC-6400 should give me 4GiB total. I can understand these and they're brand new from last weekend. Those other two sticks are from 2009, labeled 2X(2X2G). They just don't make much sense to me. I would think they should produce a total of 4GiB -- not only 2GiB. That's why I was thinking all four sticks should read as 8GiB, not 6GiB.

Old_Printer

---

### Post by Bradley_J_Doern on 2015-08-26
Shared memory from onboard graphics will eat up physical memory before Windows or even BIOS has a chance to count it.  Even if you have an AGP/PCIe video card, somethign onboard may still be eating up your memory; def something to look in to. :)

---

### Post by Bucky Ball on 2015-08-26
In that case, my next suggestion would be to check each stick one by one or using one pair only. If you're saying all sticks are 2Gb, yes, you should have 8Gb or close (as QIII says, 5.8 is about right for the 6Gb and I would read that as 6Gb). Seeing as you have only 6Gb showing that would indicate one of the older sticks (probably) is dead. 

Pull them all and stick in one of the older sticks. Boot. Error? If not, take that old stick out and stick in the other. Boot. Error? If still none, move on to the newer sticks.

Bit of stuffing about but exactly where I would be heading. 2Gb missing heightens the probability of one 2Gb stick being dead.

---

### Post by Old_Printer on 2015-08-26
Thank you for the replies. Bucky Ball, I think I may indeed have a spent stick of RAM. This morning the machine couldn't / wouldn't finish loading the desktop all the way. I had to force a shutdown. I removed the oldest pair and we're singing right along without a hint of problem. I have some typesetting and printing to do this morning, and after that I'll be doing as you suggested -- testing those pieces of RAM.

Thanks again,
Old_Printer

---

### Post by Bucky Ball on 2015-08-26
Yep, sounds like it's one of the old ones. Try them one at a time and you'll soon find the culprit. :)

---

### Post by Yellow Pasque on 2015-08-26
Possibly helpful command since you can't figure out the size of your RAM sticks:
```
sudo dmidecode -t memory
```

> I don't know about other boards, but that is the way my older one works.
Unfortunately, mobo manufacturers didn't standardize on the meaning of the color codes or channel names. So if you've got two sticks of RAM and want dual-channel operation, you might have to put them in the same color slot on one mobo and different color slots on another mobo. You either have to read the manual or do a guess and test (assuming you disable the BIOS splash screen and it informs you if dual channel is active when you turn on the computer).

> Shared memory from onboard graphics will eat up physical memory
I highly doubt onboard graphics (and/or other hardware) is reserving 2GB of memory for addressing. It seems far more likely that OP has a bad stick or is confused about the size of the stick(s).

> Notice that GB != GiB
Are RAM manufacturers pulling that false advertising crap too? I thought it was just disk makers.

---

### Post by QIII on 2015-08-26
Could be the difference is reserved memory and I'm just full of it.  :)

---

### Post by QIII on 2015-08-26
I'm full of it.  RAM is designed and manufactured in GiB, GB being a misnomer.

So never mind all that.  The difference is the system reserving memory.

---

### Post by Old_Printer on 2015-08-26
My ASUS froze and re-froze today. I tried all different configurations with the RAM -- and three different hard drives with existing installs of Ubuntu and Zorin. When each drive was inserted, they lasted about three minutes until their desktops froze. Once they did, there was no booting from them again. I then inserted my XP drive, which I had been using all of the time for the past 6 years. It wouldn't even get passed the splash.

I have the tower on the floor right now. I had to move along with my day. In fact, I had to dig out an old laptop that doesn't even have a hard drive in it just so I could go online. I'm free-wheeling it right now with Zorin.

I had to commandeer my Internet machine and made it my typesetter for the day. I put Ubuntu on it with VirtualBox and imported my XP appliance so that I could resume my first week ever of typesetting with Linux as the undercarriage of all my software. At one point this afternoon, that machine froze and I had to reboot the system to initiate a VB launch of XP.

There must be some sort of interference in the air today. This has never happened.

I'll admit that my problems could come down to a PS2 plug for the keyboard possibly not being completely tight in the back of the ASUS machine. I thought about that after I had disconnected it. I'm going to give it another shot on my test bench tomorrow.

Thanks for the replies, I appreciate the help. I'll post back when I learn more. This typing on a laptop is not my cup of tea.

Old_Printer

---

### Post by Yellow Pasque on 2015-08-26
Make sure it's not overheating...

---

### Post by Old_Printer on 2015-08-26
[[COLOR=#000000]@Temüjin[/COLOR]]("http://ubuntuforums.org/member.php?u=327594"), I'll look into it possibly overheating. Last night I loaded x64 Ubuntu 15.04 on that machine. It's a x32 machine when you're running Windows. Could this have caused some long-term problems for me? Last night was the second time I loaded that disk and ran the platform. Now that I think of it, I was having problems with my XP hard drive taking forever to boot up last week after I installed x64 and played around with it for a bit. The machine pretty much snapped out of it as the week went on, but that's why I bought new RAM.

Could running a x64 OS mess up a x32 system?

Old_Printer

---

### Post by Yellow Pasque on 2015-08-26
> Could running a x64 OS mess up a x32 system?

No, either your system is capable of running a 64-bit OS or it's not. If it's not, then the LiveUSB/CD wouldn't start/boot, much less allow you to install to a disk.

---

### Post by Bucky Ball on 2015-08-27
You want to be using the 64bit OS if you are intending to run with 8Gb of RAM (or 6). :)

---

