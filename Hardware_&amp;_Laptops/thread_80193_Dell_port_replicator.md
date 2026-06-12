---
title: "Dell port replicator"
date: 2005-10-21
forum: Hardware &amp; Laptops
---

### Post by Ventajou on 2005-10-21
Hi,

I have a Latitude D505 and just got a port replicator. It works just great except for one detail: when I plug my speakers into the replicator's headphones jack, I do not get any sound. If I plug them directly to the laptop or don't plug them at all then I do have sound.

I have tried changing all the volume settings in the sound mixer but it didn't help.

Anbody has a clue?

Thanks

---

### Post by jmacdonagh on 2006-11-15
Sorry to resurrect this post, but I'm having the same problem with my Inspiron 8600 and my port replicator. Any solutions?

---

### Post by K.Mandla on 2006-11-15
I had this same problem with an old Dell Latitude CPi-A and a C-Port (was that what it was called?) port replicator. To be honest I wrote it off as a hardware fault in the replicator. I see I probably should've troubleshot it a little more. 

Are there any BIOS settings on the 8600 that might push sound through the replicator? I know there weren't for my Latitude.

---

### Post by superami on 2006-12-21
I have a Dell Latitude D620 and have the same problem.  No sound through the port replicator, but sound works fine through the headsets and laptop speakers, bot no through the speakers attached to the port replicator, although they work through windows.

---

### Post by mjthfx on 2007-01-03
> **superami said:**
> I have a Dell Latitude D620 and have the same problem.  No sound through the port replicator, but sound works fine through the headsets and laptop speakers, bot no through the speakers attached to the port replicator, although they work through windows.

Ditto, same gear, same problem.Anyone know of a fix?

---

### Post by caldevil on 2007-01-31
It seems like a problem with alsa.
See this:
[http://article.gmane.org/gmane.linux.alsa.devel/44168](http://article.gmane.org/gmane.linux.alsa.devel/44168)

Let me know if anyone gets it working. I am also using port replicator on Inspiron 600m.

---

### Post by jmacdonagh on 2007-02-25
I'm using an Inspiron 8600, but this patch may work. Can anyone help me get the latest code from the developer repository?

---

### Post by jmacdonagh on 2007-02-25
I got the latest developer build code, applied the patch, installed it, but the issue persists on my 8600. I have submitted the issue to ALSA:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2917](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2917)

---

### Post by Meson on 2007-02-26
Hey guys, here's the fix for this annoying problem:

    [http://ubuntuforums.org/showthread.php?p=2218245#post2218245](http://ubuntuforums.org/showthread.php?p=2218245#post2218245)

---

### Post by caldevil on 2007-03-05
Guys, the new alsa-base 1.0.14rc3 has added support to the following models:

Dell D820, D620, M90, 630m, 120L, 9400/E1705, M1710, M90.

I have added support request for 600m/D600 and 8600.

If you any other model and want to see d/port replicator working can you please post the output of:
/proc/asound/card0/codec*/ac* file.

---

### Post by jtekUSA on 2007-10-05
> **mjthfx said:**
> Ditto, same gear, same problem.Anyone know of a fix?
Likewise, same equipment and same issues.  I have been searching this out and finally got the latest drivers but am not sure how to install them.  The instructions I found pertain to speakers on the laptop not working so I am leery of using them.  I am providing the links to what I found since they were not easy to find - at least for me.

[INDENT][ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2")
[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14rc3.tar.bz2]("ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14rc3.tar.bz2")
[ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14rc2.tar.bz2]("ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14rc2.tar.bz2")[/INDENT]

What you do next is not known to me.  Although I am not new to Linux/Unix, it has been many years since I used either so I consider myself a dangerous newbie. :D

---

### Post by atlas95 on 2007-10-05
Hello, I search a port replicator for my xps 1330, could you help me please, i want to let it at work for example with ac,screen,keyboard etc

---

### Post by nutz on 2007-10-27
> **superami said:**
> I have a Dell Latitude D620 and have the same problem.  No sound through the port replicator, but sound works fine through the headsets and laptop speakers, bot no through the speakers attached to the port replicator, although they work through windows.

+1 same issue and same hardware, D620 with the advanced port replicator. I have enabled the IEC958 within the volume control but still no sound from the SPDIF or line out jack on the dock. Both work under XP...

This is with a clean install of Gutsy BTW...

---

### Post by fuzzmo on 2008-02-25
Same here except I am using a m1710 with a d/port.  Works flawlessly in Windows but just can't get it to display properly to an external Samsung 226BW.  After much fiddling with Screens and Resolutions I can get it to display to the Samsung with no output to the internal LCD (although the backlight is still on) - but after that when I reboot and then try and log into Ubuntu (7.10) it reverts back to the internal LCD and does not output anything externally.

The graphics card is an nvidia 7900gtx.

---

