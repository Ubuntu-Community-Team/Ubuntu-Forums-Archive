---
title: "Strange DVD/CDROM drive issue"
date: 2006-07-26
forum: Hardware &amp; Laptops
---

### Post by jegler on 2006-07-26
I'm having an issue with both my DVD writer (plextor 716A) and a generic cd burner I've had for a couple years (though the dvd burner is only a couple months old).

Originally, both pieces of hardware worked flawlessly for burning, data reading, and dvd and audio playback under gentoo and windows.  Then at some point I became unable to mount audio cds reliably.  Sometimes it would fail giving me a bad super block or wrong fs error.  But I checked all kernel options pertaining to relevent filesystems and ide-cd stuff and they were all enabled.  Now sometimes I could mount a cd by being root othertimes it would mount as my normal user  and othertimes it wouldn't mount (after doing nothing more than unmounting it).

Seperately I decided to try out ubuntu again, or rather kubuntu.  I finally got the desktop cd image burned and k3b verified it against the checksum (after 2-3 tried and only after I lowered the burn speed).  I rebooted and started the install over my old  gentoo install.  It got to about 99% on the install and hung, tried several more times, all hung in random places, some even before boot.  Checked the media, using the builtin option on the cd.  All OK. Checked it again, 4 files failed, then 7, then all okay again.

Same problem with both drives, regardless of whether both are hooked up or if only one of the two are.  In fact, the cd-burner refuses to boot the media at all.  I've tried all possible jumper combinations.  The bios sees both drives fine and even says dma is working.  

I'm running out of things to try.  I've tried with several types of media, my two drives, different jumper combination, different bios settings, even a new ide cable.

Any ideas?  This is really important as I currently have no working computer.  I could almost careless at this point about the drives not working.  I just want to be able to boot. (Sorry for the length of this post but I wanted to make sure I provided as much info as I could to start)

---

### Post by JoWilly on 2006-07-26
> **jegler said:**
> Checked the media, using the builtin option on the cd.  All OK. Checked it again, 4 files failed, then 7, then all okay again.


Is it working properly in gentoo or any other os ?

Have you tried changing your ide cable ?

---

### Post by ekarni on 2006-07-26
A few ideas:

1) Is Windows still installed on this machine?  If so, do the drives work ok under it?  The symptoms you describe don't sound like a hardware problem to me; functionality under Windows will pretty much confirm that.

2) I've had a number of problems with CD/DVD support under Dapper (DMA incompatibilities, DVD burning).  From what I understand, they switched to a new hardware management scheme, and pushed it out the door a bit prematurely (IMHO).  If you're doing a clean install anyway and have a bit of time, maybe dig up an old Breezy iso and install that to check out the drives, then go ahead with Dapper.  This of course assumes that you have access to a machine with a functioning burner somewhere (school, work, friends, ...)

3) Try installing with DMA disabled.  From the "alternate" CD boot screen, hit F6 and add *ide=nodma* to the boot options.  You can always turn DMA on later:
[https://help.ubuntu.com/community/DMA]("https://help.ubuntu.com/community/DMA")

---

### Post by jegler on 2006-07-27
Thanks for the responses.  I too didn't think it seemed like a hardware problem and i did try changing the ide cable as that was one of my first instincts as to what might cause behavior like this.  

As for windows, I can no longer boot into it because the partially completed install took out grub so now a boot from the hard disk gives me an error 15.  When it was working however, the last cd i tried to burn in it gave me some "readahead" error or sorts and essentially failed immediately so basically a similar problem I believe though I immediately gave up in windows as I hate troubleshooting there.

I tried with a dapper cd one of my friends (also a very linux saavy person burned for me)  but it wouldn't boot from that disk at all.  Its possible that it could be the media, or burn process in this case as I have no idea if he truly burned the disk correctly but I would be inclined to assume he did.

Any other questions I'd be happy to field.  Other than that, no idea what other information I could think to provide.

Oh one more thing, is it possible this could be caused by a bad controller of some sort? All my other drives are either connected through ide1 or a pci controller card.  Could something be wrong with the ide2 controller only? If i get the chance i might try hooking the dvd drive up to ide1 and i guess I still have windows on a seperate drive so theoretically i should be able to switch that to the master on ide1 and boot from it but to me (note personal preference being emphasized only, not a flame) a windows box is nearly as worthless as a box that won't boot, save the fact that I can get frustration out in hl2. :-D

---

### Post by ekarni on 2006-07-27
Hmm, if it hiccuped under Windows, let's not rule out the hardware too quickly.  

1) As you suggested, try switching something over to ide1 and see if it works.  A bad controller is as good a guess as any - maybe it took an ESD hit or something...  For that matter, try booting without one of the offending optical drives and see if that helps any.

2) When you say "wouldn't boot at all" from a Dapper CD, do you mean "never even read it" or "read the CD and got stuck?"  If a), check BIOS again, otherwise try a Knoppix CD or another live CD distribution and see if you get anywhere.

3) If grub is incomplete I'd worry about your Master Boot Record too.  You can try switching the Windows drive to master, but no guarantees that it will boot.

Hope you've got a recent system backup somewhere, it sounds like things are getting pretty ugly...

---

### Post by jegler on 2006-07-27
1) Haven't gotten a chance to switch the dvd drive over to ide1 yet but will most likely be the next thing I try. I have tried with only one of the "offending" drives at a time and made sure to appropriately jumper them.  I use quotes because I am very much leaning toward the conclusion that the problem lies outside the drives.

2) When I say "wouldn't boot at all" I mean acted as if there was no bootable media in the drive and went to hard drive boot before obviously failing that.  I'm still planning on trying other live distros as I can get ahold of them as it still makes no sense to me why I would get different results from different media if the drive was not in some way at fault as well.

3) I am almost positive the mbr is fine as grub gives me error 15 which I believe just means it can't find the grub config files that would normally be installed elsewhere on the drive. Just my understanding.

I do have my data backed up on other drives so I am not that worried about it.  I was planning on the reinstall afterall which is the saving grace of the whole situation.  However, data or not, it'll do me little good without a working system, eh?  Thanks for your concern and aid so far.

---

### Post by gapplewagen on 2006-07-27
I am having a (sort of) similar issue with my Pioneer 106D.  My problem came out of absolutely nowhere though.  I was sitting here happily making backup copies of some of my DVDs when suddenly my whole machine locked up.  I had no response from mouse/keyboard, couldn't get to a console, nothing.  I figured something had just gone haywire so I rebooted and now the 106 won't READ any CDs or DVDs.  Notice that I said it won't READ them... because it had absolutely no problem writing a 4GB ISO I had on my desktop.  About half the time it will lock up my system just like it did originally... the other half of the time the drive light will just stay on forever and then if I hit the eject button on the front about 15 times it will spit out the disc.  

dmesg states that:

[4294830.608000] hdd: lost interrupt
[4294898.633000] ide-cd: cmd 0x25 timed out
[4294898.633000] hdd: lost interrupt
[4294966.648000] ide-cd: cmd 0x25 timed out
[4294966.648000] hdd: lost interrupt
[4294970.910000] cdrom: open failed.
[4294970.988000] cdrom: open failed.

Any ideas?  I have no windows partition left and I FINALLY got my ubuntu install tuned exactly the way I want it (figures!).

---

