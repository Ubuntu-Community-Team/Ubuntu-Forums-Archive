---
title: "Sound problems on LG S1-QB01A9"
date: 2008-12-28
forum: Hardware
---

### Post by thefish123 on 2008-12-28
Hi everyone,

I have been running Ubuntu 8.10 now since it came out.  Prior to that I have also run openSUSE 10.3.

I really like the new Ubuntu but I have never been able to get sound working properly under any Linux distro.  I have the LG S1 (model QB01A9).  Here is the URL to the exact model of laptop I have:

[http://ca.lge.com/en/products/model/detail/s1expressdualseries_s1qb01a9.jhtml](http://ca.lge.com/en/products/model/detail/s1expressdualseries_s1qb01a9.jhtml)

The sound works fine on the headphone jack but not on the internal speakers.  I have read tonnes of suggestions with similar problems with other LG laptops but none of the suggestions has worked for me.  This has been the one thing I cannot get work under Ubuntu.

When I let the install CD boot into a "live" environment I sometimes (very occasionaly) hear the login sound and get all excited thinking that for some reason sound just started working but this hasn't happend in a while and I have no idea why it did happen when it did.

I know Ubuntu supports my sound card (because the headphone jack works) but I would love to have normal sound working on this machine.

Any suggestions on how to troubleshoot this would be most welcome.

Best regards

The Fish

---

### Post by linux_tech on 2008-12-28
what is output of ```
aplay -l
```

---

### Post by linux_tech on 2008-12-28
there is a couple useful guides here:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by thefish123 on 2008-12-28
> **linux_tech said:**
> what is output of ```
aplay -l
```

Wow!  I just posted this question here before going to church and when I come back and I have two replies already!  Thanks guys.  Here is the output you asked for.

The Fish

---

### Post by markbuntu on 2008-12-28
There is probably (or should be) a headphone switch in the sound mixer that you need to play with to get the sound to your speakers instead of the headphones. It is difficult to give you a more exact answer since the OEMs have messed about the firmware on these chips so much, even within models. Here are a few links that delve deeply into getting hda sound chips figured out:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

You should look here (look through the entire thread if the OP does not fix your problem , people have posted solutions for many specific machines):

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

If you are having problems with headphone/speaker control with your HDA sound device you can try this thread:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

---

### Post by thefish123 on 2008-12-31
> **markbuntu said:**
> If you are having problems with headphone/speaker control with your HDA sound device you can try this thread:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)OK, so I have a new &#8220;development&#8221; in my quest to get this working.  I have been reading the links provided (thanks guys) and particularly this link:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

Now I currently have the last line of my alsa-base file set to:

```
options snd-hda-intel model=acer
```

And when I booted up my computer this morning I got sound on my speakers.  I was all excited but by the time my desktop had loaded to the "usable" stage it had stopped working again (still working through the headphones).  I have no idea why.

There are so many &#8220;success&#8221; stories of people getting it to work on their specific laptop and I want to be one of them :-)  I can't be the only one running Linux on this particular notebook.  I had this issue under openSUSE as well so it can't be an Ubuntu specific problem.

Best regards,
The Fish

---

### Post by thefish123 on 2009-01-01
Hi everyone,

I think I am on to something.  I found on the alsa-project.org site that support for the LG S1 laptop was added between versions 1.0.11 and 1.0.12.  You can see the change log here:

[http://www.alsa-project.org/main/index.php/Changes_v1.0.11_v1.0.12](http://www.alsa-project.org/main/index.php/Changes_v1.0.11_v1.0.12)

Ubuntu 8.10 has 1.0.17 so presumably this problem has been resolved.  The change log (only says “hda-codec - Add support for LG S1 laptop” and then later “Added the model entry for LG S1 laptop”.  But no where (that I can see) does it say WHAT that model entry is.

Perhaps I am not reading the change log correctly?  Can someone help me out here?  Perhaps I can email one of the developers?

Best regards,
The Fish

---

