---
title: "Compaq Pres. 2000 - PXE Boot Issue (aka my biggest adventure)"
date: 2009-10-10
forum: Hardware
---

### Post by Chi The Designer on 2009-10-10
[B]If you don't like reading, skip down - I put a summary down there.


So my story begins.. [/B]
I have a 2003 Compaq Presario M2000 *(Compaq is now HP)* laptop which I used mainly for e-mail, internet and that sort of stuff. I am an Media student *(read: geek)*, so I like to play with all different sorts of new technologies. One day I decided: "Middle finger to windows, let's get Ubuntu on this laptop!" I blatantly installed Ubuntu next to XP and used it, not being able to jump back into Windows XP. This was back in 2007 using Gutsy Gibbon.

After a few weeks I desperately needed Windows *(prob. for Photoshop)* and I reinstalled Windows XP, which killed the entire MBR. ****. So at that point my laptop didn't want to do anything at all, not even read a CD. I cried, because now I didn't have shitty windows, but def. no Ubuntu. I sent the laptop over to five different computer repair shops *(and yes, paid hourly costs five times as well - good times)* and got it sent back to me five times not repaired, either stating "I should just buy a new one - not worth the effort of fixing" or "I don't know how to fix this."

So at this moment, I had no laptop. And I only had it for about a year or two. I put the laptop back in the special sleeve I had bought for it, put the sleeve in the bag, disconnected the power cords, put those in the bag. Put the bag in my closet, and closed the door. Bam. Fast forward two years later, 2009.


**2009**
Now, in 2009.. I have a macbook. I'm def. more design-oriented but always have had a weak spot for open source. What I really liked about the mac was that it was able to run both ubuntu/xp and OSX at the same time.* Double the fun, yay.* I used to have a PC at home, but my friend killed it while playing Crisis on a stormy night with the windows* (no xp, real ones)* open. Sad again, because I only had a laptop at this point and the PC served as my home server. *Well, you get over things anyway.*

So I decided to redecorate my bedroom, and while pounding my old closet into wood mash, I found an old dusty bag containing an old, not-so-dusty laptop. Pulled it out the closet before destroying the closet, and decided to see how it held up in 2009. **Two Bleeps**, that is all I got from him. No screen or visual signal. Only a power button and two bleeps.

I went online to locate the problem, discovering I had to open my entire laptop to reset a battery. ****. I didn't want to open it because I had a fear of killing the damn thing altogether, but then again I had nothing to lose. Besides, the geek inside of me wanted to know what the inside of a laptop looks and works like. *(all geeks will concur)*

So I totally ripped the sucker open, did some checks *(I'm way better at fixing computer than I used to be)* and reset the battery. Poof! Screen showed startup signs, computer responded to my keypresses, I was happy. But then a blinking sentence crushed my day:

**CANNOT FIND OS TO BOOT.**

****. So I was back where I once was, only to find my CD/DVD Drive broken and not working half of the time. No floppy drive, I had no USB boot. I did not know to what to do. I called up my friends to bring their laptops to my house, stole all the DVD drives I could find out their laptops, tried every last one of them in my laptop, but the damn thing would not recognize and read.

[B]Boot from LAN (PXE Style)
[/B]I went back into the BIOS, only to find "Boot from LAN". Did some research on it, got the programs needed to send stuff *(the tpftp32 or something)*, got the **ubuntu 9.10 netboot** and tried to connect from a friend's pc to my laptop via router. I put the laptop in "Boot from LAN" mode, and started the program.

After much ip conflicts the two heavyweights finally found each other, and the PC wanted to send the *"pxelinux.0"* file. It opens five transfer requests, but **all five do not send!** The program is stuck at* "0 bytes of 0 bytes" *and after a while my laptop *(On the recieving end)* goes: *"Well, **** that"* and restarts.





**<READ FROM HERE IF YOU WANT TO BE QUICK ABOUT IT>**


[B]- LET'S REVIEW 

[/B]- Conpaq Presario M2000 Laptop problem
- HDD is IDE (It's old)
- Had XP on it, then went to Ubuntu, then went to XP again
- MBR fail, had to clear the CMOS
- Laptop starts now, but can't find OS to boot (damaged prob.)
- CD/DVD Drive is broken
- Tried DVD Drives from other laptops; wouldn't work
- No USB boot or floppy drive
- "Boot from LAN" (PXE) seems like last option
- Got a friend's PC, downloaded the tpftp32 program along with the karmic koala netboot
- Put both on a router and tried to connect
- Connection finally found after some IP conflicts
- Laptop requests boot file five times
- Friend PC tries to send **pxelinux.0** to my laptop, but fails five times
- The send stays stuck on *"0 bytes of 0 bytes"*

[IMG]http://img164.imageshack.us/img164/434/tpftp.jpg[/IMG]

So now I desperately need you guys to help me, if you can. I feel like I'm so close after all these years of screwing around that it's crazy. The error I get is:

PXE-E32: TFTP Open Timeout
PXE-E32: TFTP Open Timeout
Exiting PXE Rom

And then it just restarts.
I tried tinkering around in my router settings, maybe not enough - you'll have to note me on that.. 

**Does anybody have any idea what I have to do to install ubuntu on my precious laptop? I feel that I am close on the whole laptop thing, it's just weird it does not send. Help is wanted!**

---

### Post by viper250 on 2009-10-10
your cmos battery has probably failed and default bios setting may not recognize your optical drive
If you can get the system into bios set your drives to auto with the cd rom as first boot device hdd as second and usb boot as third, network boot as fourth.

reboot the system and wipe the drive with d-ban
 anytime you partition a drive with microsoft it creates a log file on the drive sometimes it causes problems for example running rebuild with vista more than 3 times will cause an extended setup time frame
(almost 9 hours) I have seen this on 3 different computers (all less than 1 year old)  

d-ban will wipe any log files off the drive and test for bad sectors
you can find and download d-ban at [www.linuxlinks.com]("http://www.linuxlinks.com")
pc tech for 30 years!

---

