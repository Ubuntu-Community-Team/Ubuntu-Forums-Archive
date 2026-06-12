---
title: "Problem burning Video DVDs"
date: 2009-01-31
forum: Hardware
---

### Post by Crazy K on 2009-01-31
I recently purchased a $20 LG DVD burner from newegg. It's a LG Black 22X DVD+R 8X DVD+RW 16X DVD+R DL 22X DVD-R 6X DVD-RW 12X DVD-RAM 16X DVD-ROM 48X CD-R 32X CD-RW 48X CD-ROM 2MB Cache IDE 22X DVD±R DVD Burner - OEM 

Anyways I tried using DeVeDe to burn a Video DVD, but it's far too slow. 

So is there something I'm doing wrong? The videos I'm putting onto the disc are in avi format, would I have to change the format or something? 

I was able to burn a data DVD with the videos fairly fast, but this takes hours. 

On DeVeDe I tried buring it as an ISO image and also tried creating a disk structure, but that also took ages. 

So any suggestions?

---

### Post by taurus on 2009-01-31
You are using devede to convert an avi to an iso so you can burn it to a DVD with k3b, gnomebaker, brasero, etc. which would play on a stand along DVD player.  How long it takes to convert depends on the quality that you choose in devede.  If you pick the highest quality, than it would take a couple of hours, at least.  So, after adding an .avi to the list, look in the Advance options -> Quality.

---

### Post by Crazy K on 2009-01-31
The video rate always starts at 5001. Anyways I usually change that to the videos original video rate. I'll try the quality menu to see If I can get that to work. 

Anyways I'm trying Tovid GUI right now. If that doesn't work, I'll try DeVeDe again.

---

### Post by Crazy K on 2009-01-31
Ok, so I tried using Tovid, but that also went slow. So here's my question. What do I have to do to the quality to make it work?

Also I have multiple files. I have 14 videos, all of which adds up to over 2GB of space. But it takes forever to do anything.

I also change the quality to match the video quality. So why's it taking more than 2 hours?

---

### Post by taurus on 2009-01-31
It could also depend on your speed of your machine, CPU & RAM.

---

### Post by Crazy K on 2009-02-01
I have 1GB of RAM, and I don't know what CPU I have at the moment.

Found CPU info: Intel(R) Celeron(R) CPU 2.70GHz

---

### Post by taurus on 2009-02-01
What size (MB or GB) output did you pick when you tried to convert from avi to iso?

Sounds like you have probably an average machine, not something like AMD64 X2 6000+ or Intel Dual2Core.

p.s.  Celeron!

---

### Post by Crazy K on 2009-02-01
Do you mean the Disc Usage? If so I had it on 4.7GB. 

But I don't see anything to do with choosing your output on size.

By the way, I use DeVeDe 3.6

Anyways, I just downloaded and installed the new DeVeDe 3.12

---

### Post by taurus on 2009-02-01
In the **Disc usage** (Media size) option, you can pick 8.5GB (blu-ray), 4.7GB, 1.4GB, 700MB, etc.  4.7GB is the default though.  I assume if you lower the size, the conversion would finish sooner.

---

### Post by Crazy K on 2009-02-01
Alright, I'll try the other alternatives. Thanks.

---

### Post by Crazy K on 2009-02-01
So I'm using DeVeDe 3.12, but it's still taking ages. I started the program at around 11AM and it's now 5PM. So far, it's 9/17 done, and has 43% to go on the 9th part.

---

### Post by taurus on 2009-02-01
Maybe you need a faster, much faster, machine than your celeron.

---

### Post by Crazy K on 2009-02-01
Anyways I was able to make the Iso image, it took 9 hours but oh well. Anyways whenever I use Brasero it doesn't seem to let me burn the iso to DVD. It says 0 bytes free.

Anyways I'm trying k3b right now, so hopefully that works.

---

### Post by taurus on 2009-02-01
What is the size of the ISO image?  In k3b, click Tools -> Burn DVD ISO Image and browse to where your ISO file is.

---

### Post by Crazy K on 2009-02-02
It says 3.0 GB

---

### Post by pmooney78 on 2009-02-03
Some (more or less) obvious stuff you can try that might increase how quickly DeVeDe finishes:

* Don't run other programs while DeVeDe is running if you can help it. If you're doing something else, you're using processor cycles that could be used to create your movie. Try to leave your computer creating your movie while you're at work/school/wherever. Especially if you're doing something processor-intensive (gaming, for instance), using other programs at the same time can really slow down the process.
* Make sure that you've got plenty of free space in your /tmp directory. In my experience, this makes a big difference.
* If you've got more than one hard drive, put your source files on the fastest of them, and make sure that your output .iso image is also being written to the fastest hard drive. Drive lag can make a big difference. In my experience, internal hard drives are usually faster than external/USB drives, ext2/3 formatted partitions are faster than partitions formatted with NTFS or vfat, and primary partitions are faster than logical partitions. If you've only got one drive, there's nothing much you can do about this, but if you've got more than one, it can make a big difference.

Hope that helps. You have my sympathy -- I was running DeVeDe for the last year on a computer that's substantially slower than the one you're using, so I feel your pain.

---

### Post by Crazy K on 2009-02-05
Yeah, my computer is shared with my brother and mother, so they just had to check their e-mail and all of that, which in hand did make it slower. But yeah I'll try the other alternatives next time I burn a video DVD. By the way, I saved the file, or temporary files to my desktop, since I expected it to go faster that way. 

I do have a 500GB External HD, but I used my internal HD for the burn location, which of course was my desktop. 

I also could just burn data DVDs, since I usually watch video on my Xbox 360, so usually most video files seem to work on a 360. 

Also, this may be a stupid question, but how much would it cost to update my CPU processor from Intel(R) Celeron(R) CPU 2.70GHz to something more awesome? I have a computer that has some pretty decent specs that I can't use at the moment because it got plauged with viruses and now doesn't even work right. Would I be able to transfer my CPU from that to this one?

---

### Post by duds2008 on 2009-02-06
My pc takes about 2 - 3 hours to convert a 700MB avi to a DVD ISO. And its a P4 dual core 3.2!!

---

