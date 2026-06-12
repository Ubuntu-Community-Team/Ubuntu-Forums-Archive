---
title: "hi, i'm completely new to everything, please help!"
date: 2008-11-05
forum: General Help
---

### Post by ds143 on 2008-11-05
hi,

i have this rather sluggish windows xp tower in my guest room, and it's never used because its so slow. as just a fun project today, i decided to install ubuntu to breathe some life into the thing. i've NEVER EVER done anything like this before, and wasn't sure what i was doing.

i went to ubuntu.com, and downloaded the newest version. i made the boot cd and was able to boot from it. once i got to the screen that said like "run ubuntu without installing" and "install ubuntu," every time i clicked on one of those options, the ubuntu orange bar loaded, and then just a blank screen came across. everything i did, this happened. i verified the cd, it was all good.

what's wrong?

thanks!

---

### Post by invalidusername on 2008-11-05
> **ds143 said:**
> hi,

i have this rather sluggish windows xp tower in my guest room, and it's never used because its so slow. as just a fun project today, i decided to install ubuntu to breathe some life into the thing. i've NEVER EVER done anything like this before, and wasn't sure what i was doing.

i went to ubuntu.com, and downloaded the newest version. i made the boot cd and was able to boot from it. once i got to the screen that said like "run ubuntu without installing" and "install ubuntu," every time i clicked on one of those options, the ubuntu orange bar loaded, and then just a blank screen came across. everything i did, this happened. i verified the cd, it was all good.

what's wrong?

thanks!

I had the same problem with the 64bit version even though I have a dual core 3800. So I tried the 32bit version and it loaded up like a charm.

---

### Post by jayson.rowe on 2008-11-05
We are going to need a little more information about the computer you are trying to install it on.
I think the following will get us started:
CPU Type/Speed
Amount of RAM
Type of Video Card.

For example, if that machine has less than 256 MB of RAM, you should use the Alternate Install CD instead of the Desktop CD.

---

### Post by ds143 on 2008-11-06
hi, 

i'm trying to install it on a dell dimension 2350:

[http://reviews.cnet.com/desktops/dell-dimension-2350/4505-3118_7-20717757.html](http://reviews.cnet.com/desktops/dell-dimension-2350/4505-3118_7-20717757.html)

what is this other CD i can boot from that you are talking about?

thanks!

---

### Post by amac777 on 2008-11-06
I had a similar problem when I first installed Ubuntu from the live CD as well. That was a much older version but the problem was related to my LCD monitor not being able to handle the default on the live CD. If I selected something like "safe graphics mode" at the boot menu of the CD then it worked fine. Maybe you could try booting from the same CD and look for that selection.

Edit: Disclaimer: I have not tried running the live CD for the newest versions of Ubuntu so I don't know for sure Safe Graphics Mode is still an option that you can select....

2nd Edit: but yes, as a poster said above, you better confirm you have at least 256MB of RAM or the live cd won't work.

---

### Post by joe180 on 2008-11-06
Hi

Which Ubuntu ISO image did you download and burn to CD ?

---

### Post by alwez_loner on 2008-11-06
What he meant is try another type of the ubuntu [try this site]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") you then go for the desktop i386. It should work better than if you downloaded a 64bit.

---

### Post by ds143 on 2008-11-06
yes, but i DID select the 32 bit version!

---

### Post by Kevbert on 2008-11-06
Welcome. You need to download the alternate (text based) install CD due to your low amount of RAM. It's possible that Ubuntu 32 bit will run quite slowly so it may be better to try something like [[COLOR="Red"]Xubuntu[/COLOR]]("http://www.xubuntu.org/get") instead. I'd go for the Hardy Heron 8.04 version as it's a long term supported OS (Intrepid Ibex 8.10 willo superseded in 6 months time).
You'll need to check your ISO file that you download prior to burning at a slow speed (around x4 best), to minimize any errors. Information on [[COLOR="Red"]burning[/COLOR]]("https://help.ubuntu.com/community/BurningIsoHowto") and [[COLOR="Red"]MD5SUMs[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") are available and the hashes to check your ISO are on the download page.

---

### Post by alwez_loner on 2008-11-06
Well the 8.10 has been having alot of graphics problems try to download the 8.4 since its a stable version and check to see if it has the same problems.

---

### Post by ds143 on 2008-11-06
hi again-

i've downloaded xubuntu, and it has the same problem as the normal ubuntu. it boots from the disc fine, but once i go to "install (x)ubuntu" or "try without any changes on my computer" it just goes blank! i've left it like that for hours, and it hasnt changed.

any other suggestions?

thanks

---

### Post by Kevbert on 2008-11-07
Please run the memory test (memtest in the CD install menu) for a couple of passes.

---

### Post by hyper_ch on 2008-11-07
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by muteXe on 2008-11-07
Do you have another monitor in your house?  How easy would it be to plug in another monitor and test again?

---

