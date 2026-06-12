---
title: "HDD problems, What went wrong???"
date: 2009-04-13
forum: Hardware
---

### Post by gundam1965 on 2009-04-13
OK, so everything was working well. I was playing games on Saturday night and decided to go to bed. My mobo has an annoying blue led that shines when I sleep, so I flipped the switch on my power supply to shut it off. The next day I tried t turn back on my computer. It got stuck on Detecting IDE Drives... (which my HDD is a SATA 3.0) and the next screen said something like, unable to find boot files. I went into BIOS and it wasn't showing the HDD at all. This morning I turned it on and now it says "PXE-E61 Media Test Failure, check cable". I also tried plugging it into an external HDD, but it won't show on another system. It sounds just fine, I can hear the platters spinning, and the head clicks a few times and then stops. I've (attempted to) attatch a sound recording of my HDD while it boots, however you will probably need headphones to hear anything. My mobo also has a LED diagnostic. When it tries to boot it gets stuck on code 75 "Detect HDD IDE device detection" . I'm hoping someone can give me some advice other than "your screwed". If the attachment doesn't going through, please let me know. Thanks

---

### Post by doas777 on 2009-04-13
did you gracefully shut down the machine before you cut the power?
if not, your hdd has most likely suffered a critical physical malfunction. it may have been destroyed.

I had somthing like this happen a few months ago when a game crashed at a very bad time. Occurrence is pretty rare, but a possibility if the hard disk is performing exactly the wrong operation at exactly the wrong time. 

if you did shut down, I would recommend unplugging the pc from the wall for an hour or so, and disconnect/reconnect the hard disks. then cross your fingers and fire it up.

in future, consider putting a peice of electrical tape over the led.

replacing a hard disk is pretty easy, but you will have to reinstall everything from scratch.

good luck,
franklin

---

### Post by AceRimmer234 on 2009-04-15
I am new here with using Ubuntu. But plenty of experience playing in windows. This sounds like you have fried the hard drives MBR. which is the boot record the computer is looking for when it hangs. Except I have never had it happen from doing what you described. If thats the problem then there are programs you can use to fix it. I dont know any windows based ones that are free, and being new in linux, I am learning myself.. lol
 AceRimmer234](*,)

---

### Post by doas777 on 2009-04-15
you can install ms-sys to the liveCD and rewrite your mbr with it. 
[http://freshmeat.net/projects/ms-sys/](http://freshmeat.net/projects/ms-sys/)

I don't think it's the MBR though, because a bad MBR would not stop it from showing up in the bios. you don;t need any data structure on a drive to get it to show in the bios, just functional hardware/firmware. 

If you can't see it in the BIOS, you most likely can't see it in ubuntu or from a liveCD anyway, so unless that changes, you will not be able to rewrite the MBR or recover any data. you can find out from the LiveCD. just open gparted, and if it shows a HDD, you may be in luck.

---

### Post by Scubdup on 2009-04-15
I'm a newbie too. I'm sure others will be able to advise more helpfully.

I'd create a LiveCD and boot your machine from that. That should let you explore the (possibly) fried HDD and see if there's anything that is salvageable.

---

