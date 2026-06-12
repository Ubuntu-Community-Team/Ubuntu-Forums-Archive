---
title: "Can't boot LiveCD on a Gateway laptop"
date: 2006-07-25
forum: Hardware &amp; Laptops
---

### Post by Grayfox777 on 2006-07-25
I can't boot the Ubuntu 6.06 LiveCD on my Gateway Solo 1450. I checked the md5 checksums and it was a good download. I don't think anything went wrong with the burning process, either. No errors popped up and my laptop seems to burn things just fine. Plus I burned a speed setting lower than maximum.

This is the error I get over and over again everytime. The #'s are different numbers each time. 
> 
[#######.######] Buffer I/O error on device hdc, logical block #####

Okay... computer info...
512 MB RAM
1.2 GHZ Pentium III
30 GB internal HD (One partition with Windows XP)
40 GB external HD (One partition. I plan to make another one for Ubuntu, though.)
Any other specs needed?

I already tried noscsi and nodma, but it didn't seem to make any difference. 

What can I do? Anyone have any ideas? :confused:

---

### Post by lH)4~mK0e on 2006-07-25
try acpi=off

---

### Post by Grayfox777 on 2006-07-25
Okay I tried acpi=off, but it didn't seem to work.
I really don't know if this will be of any help, but Knoppix 3.4 seems to boot just fine (with noscsi) by live CD, though in 800x600 resolution and it doesn't detect my network card.

---

### Post by KeesKaas on 2006-07-26
I have exactly the same problem on my Dell Inspiron 8600.

When I boot the LiveCD I have the following symptoms:
The "mounting root filesystem" step takes forerver (almost).
Then it goes to text mode and starts displaying the

[#######.######] Buffer I/O error on device hdc, logical block 1

messages in groups of 10, the block number goes up from 1 to 10. This goes on endlessly. 
The cdrom drive is accessed al the time.

I also tried two images, thinking the 1st one must be faulty.

Breezy Badger Live cd does work. Suse 10.1 live DVD also works.

On this forum I have found several succes stories about Dapper Drake on a Dell Inspiron 8600. SO what is different for me?

---

### Post by Grayfox777 on 2006-07-26
For me, it hangs at "Adding live CD user..." then goes to the error messages after a couple of minutes. Very similar problem though. Hopefully someone has some ideas we can try.

---

### Post by KeesKaas on 2006-07-28
I have found that at least my problem is a very well known problem in DD. It has to do with wrong drive enumeration. Lots and lots of people have this problem in some way or another. 

See : [http://www.ubuntuforums.org/showthread.php?t=208207](http://www.ubuntuforums.org/showthread.php?t=208207)

It was already a known issue even before DD was released....but not considered important.

There are some crappy, maybe fixes.. but I'll switch to another distro.
I was already not happy with the way Eclipse was crippled in BB.

---

### Post by Grayfox777 on 2006-08-02
Hmmm... it seems my problem is different cause on my computer it mounts the root file system just fine. Maybe you are having the same problem I have along with that?

---

### Post by Grayfox777 on 2006-08-10
Does anyone know if these types of problems have been fixed in 6.06.1?

---

### Post by Ralf.Nieuwenhuijsen on 2006-08-15
I can confirm they haven't. I've tried installing Ubuntu 6.06.1 on a friends' system, yet the live cd wont' even boot up. It hangs at 'mounting root file-system'..

Haven't tried out other or older versions though it did boot a kanotix cd. 
What I think is that a large number of bugs that are have the same appearance (hanging at the mounting root file-system) is really a whole stack of different bugs.

And the ubuntu ppls did want to fix the bug, but I think are just not hands dirty enough to fix it so they just post-poned it. 

But it _is_ a shame nevertheless. Their LTS version is most likely the linux distrobution that has the most boot quirks of all linux boot cd's out there. Its beyong my knowledge how this could even be possible. 

I've actually read somewhere they weren't even gonna fix this for Dapper cuz they didn't know how it would affect the other ppls. Honestly, if you can't predict wether a fix will hurt more, its most likely not even a fix. Just a dirty work-around. 

So where's the real bug? And is it really just one? If so, why does turning off USB2 help some? Why does turning off IDE help some others? Why does specifying a root= help some? Why does using a different CD drive help some? I'm not a kernel guru or anything. But this has to be at least 3 to 4 different bugs.

---

### Post by mp3deej on 2006-12-15
I am unable to boot the Live CD on my gateway solo laptop. 

    PIII 1.2 GHZ 
    256 MB Ram
    20 GB HD
    Intel 830 Graphics Chipset 8mb

     X-error even in safe mode..   Server error, no screens found. Make sure you have your system configured properly. 
     Anyone else have this problem? I suspect it's the crappy gfx chipset. Any work arounds? ](*,) 
     
    Suse 10.1 works fine w/wireless support, however only in 8 bit res @ 1024/768 - 800/600. 
    Madrake is a mess. PClinux OS, no better,

---

