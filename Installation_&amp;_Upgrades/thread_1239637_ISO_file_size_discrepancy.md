---
title: "ISO file size discrepancy"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by Trenchdigger on 2009-08-13
Hello.  I tried searching, but didn't find any info.

I am not able to create an installation CD using the 9.04 ISO image.  When I download the file, the file properties indicate the file size as 696 MB and 730,554,368 bytes.  Obviously, there's a discrepancy there.

I'd really like to create a CD, but the CD capacity I have is 700 MB, and the file will not fit.  What is the CORRECT size of the 9.04 image file?  696 or 730 MB?  Am I doing something wrong?  I tried direct download from Ubuntu, as well as a torrent feed, with the same result.

I download the file to my Vista OS.  Is Vista screwing with the file somehow?  Any help would be appreciated.

Thanks!

-T

---

### Post by raymondh on 2009-08-13
> **Trenchdigger said:**
> Hello.  I tried searching, but didn't find any info.

I am not able to create an installation CD using the 9.04 ISO image.  When I download the file, the file properties indicate the file size as 696 MB and 730,554,368 bytes.  Obviously, there's a discrepancy there.

I'd really like to create a CD, but the CD capacity I have is 700 MB, and the file will not fit.  What is the CORRECT size of the 9.04 image file?  696 or 730 MB?  Am I doing something wrong?  I tried direct download from Ubuntu, as well as a torrent feed, with the same result.

I download the file to my Vista OS.  Is Vista screwing with the file somehow?  Any help would be appreciated.

Thanks!

-T

696 sounds about right.  Still can't burnt the 696?

---

### Post by Trenchdigger on 2009-08-13
No, because windows sees the file size as 730000000 KB, AND 696 MB.  The CD burning software also sees the filesize as 730 MB.

---

### Post by raymondh on 2009-08-13
standby ... let me download and burn a 9.04 liveCD just to verify.  I will use XP and cdburnerxp.

RH

---

### Post by raymondh on 2009-08-13
> **raymondhenson said:**
> standby ... let me download and burn a 9.04 liveCD just to verify.  I will use XP and cdburnerxp.

RH

698 for me.  No problem in burning slow.

---

### Post by jms1989 on 2009-08-13
are you sure you are burning the iso directly and not as a file? the claimed 696mb sounds right.

---

### Post by Trenchdigger on 2009-08-13
I'm saving the file directly to my PC, then burning it.  Does it make a difference if I burn directly on download?

What bugs me is that the file properties indicate (as I've written) the file size as 696 MB and in parentheses 730,554,368 bytes

This is consistent, and repeatable, every time I try to download the file to my Vista OS.  

When you right click on the file in a Windows OS, what do the properties show you for file size, in KB and MB?

---

### Post by Trenchdigger on 2009-08-13
Let's see if I can attach this screen capture:

---

### Post by raymondh on 2009-08-13
I just deleted my download windows after my experiment to verify your sizings .... sorry, force of habit to keep my windows clean.

However, here are screenshots of other distros I have in my linux machine.  Note the sizings in both mb and KB.

Hope this helps.

Raymond

---

### Post by mostafa178 on 2009-08-13
It seems right according to [this]("http://www.google.com/search?client=safari&rls=en-us&q=730,554,268+bytes+to+megabytes&ie=UTF-8&oe=UTF-8")

---

### Post by lensman3 on 2009-08-13
One number uses 1000 for a K, and the other probably uses 1024 for a K.  

The only full-proof way is to use md5sum check-sum program to verify that ever single byte was correctly written.

The following is from a HOWTO I made several years ago for burning a boot CD, but from the Linux side.  It assumes that you have a running Linux distribution.  Step 1 is getting the iso.  Change the devices to reflect the dvd/cd burner on your system.

2.  Check download.  The SHA1SUM file has the check sums to make sure the download was OK.
       If something fails then download it again!

    download the SHA1SUM file, too.
    run:
       sha1sum -c *SHA*

3.  Burn the images to cd's
      cdrecord -v -eject -speed=8 -pad -padsize=63s -tao dev=ATAPI:1,0,0 -data dev=/dev/cdrom <cd_image.iso>

      Slower speeds tend to work better (but experiment).


4. Check burn.
   For the new cd.
      readcd dev=/dev/hdc  sectors=0-`isosize -d 2048 /dev/hdc` retries=0  f=- | md5sum

   For the iso--
      md5sum <cd_image.iso>

   Compare the check-sums.


Hope this helps.

---

### Post by Partyboi2 on 2009-08-14
Hi, check the md5sum of the iso you downloaded to make sure they match, then try using another burn program like [[COLOR=Blue]imgburn[/COLOR]]("http://www.imgburn.com/") and see if you are able to burn the iso to disk.

---

### Post by Trenchdigger on 2009-08-14
Thank you all for your time, and help diagnosing my problem!  I very much appreciate it.  Interesting that MB and KB are measured slightly differently.  I did not know that, obviously.

I was able to burn the disk image; the software I was using choked the first few times, but did finally work.  Turns out the problem was the nut behind the wheel: I was certain that I was "burning" an image, but it is probable I was "copying" instead.  Funny thing is: I went about burning the same way I went about copying, only changed the software settings between tries.  :rolleyes:

Note to self: Find more intuitive software.  Oh wait, that's why I'm switching to Ubuntu!  :)

Anyway, thanks for putting up with the error of my ways.  I look forward to contributing more effectively soon!

-T

---

### Post by raymondh on 2009-08-14
> **Trenchdigger said:**
> Thank you all for your time, and help diagnosing my problem!  I very much appreciate it.  Interesting that MB and KB are measured slightly differently.  I did not know that, obviously.

I was able to burn the disk image; the software I was using choked the first few times, but did finally work.  Turns out the problem was the nut behind the wheel: I was certain that I was "burning" an image, but it is probable I was "copying" instead.  Funny thing is: I went about burning the same way I went about copying, only changed the software settings between tries.  :rolleyes:

Note to self: Find more intuitive software.  Oh wait, that's why I'm switching to Ubuntu!  :)

Anyway, thanks for putting up with the error of my ways.  I look forward to contributing more effectively soon!

-T

k3b or brasero are easy to use.  

Yes, the measurements are/may be slightly different (cylinders).  You ought to see the debates about GB and GiB :)

Congratulations and happy Ubuntu-ing.

---

