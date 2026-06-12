---
title: "Screen Resolution on a Gateway Solo 2500"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by mwdowns on 2007-02-14
Hello folks.  

I just installed Xubuntu Edgy on a Gateway Solo 2500 (400mhz Celeron, 288 MB RAM), and I can not get the screen resolution to 1024x768.  Under Settings->Display Settings the highest listing is for 800x600.  In my xorg.conf file, the default resolution is 1024x768.  I'm not sure what I need to do.

Also, the right-hand and bottom edges of the screen are black.  I assume that if I get the correct resolution, then the screen take up all the available space.  Is that a correct assumption?

Thanks for your help.

---

### Post by encompass on 2007-02-15
try just deleteing all resolutions in your conf except for the one you want.  It is a dirty hack but should do it.  Otherwise... what is your graphics card.  If we know that we could probably fix things a lot better.
To find your graphics card try this....
lspci
and look for a name like intel graphics, nvidia or ATI

or simply post the whole whopper here.

---

### Post by mwdowns on 2007-02-15
> **encompass said:**
> try just deleteing all resolutions in your conf except for the one you want.  It is a dirty hack but should do it.  Otherwise... what is your graphics card.  If we know that we could probably fix things a lot better.
To find your graphics card try this....
lspci
and look for a name like intel graphics, nvidia or ATI

or simply post the whole whopper here.

Thanks for the quick reply.  The thing is in the xorg.conf file, the only resolutions are 1024x768.  There are no listings of 800x600.

The graphics card is a Neomagic Corporation NM2160 [MagicGraph 128XD].

---

### Post by veloce on 2007-02-15
And a search for your graphics card on this forum results in:

[http://ubuntuforums.org/showthread.php?t=257696](http://ubuntuforums.org/showthread.php?t=257696)

---

### Post by mwdowns on 2007-02-15
> **veloce said:**
> And a search for your graphics card on this forum results in:

[http://ubuntuforums.org/showthread.php?t=257696](http://ubuntuforums.org/showthread.php?t=257696)

Thanks for that link.  I tried out the solution there, but it didn't work.

My xorg.conf only lists 1024x768 as the option for my screen, but I can't choose that anywhere (neither in Display Settings or using the "xrandr" command).

---

### Post by veloce on 2007-02-15
I read that link as saying that you need to lower the bit depth to 16 to get 1024x768.

---

### Post by mwdowns on 2007-02-15
> **veloce said:**
> I read that link as saying that you need to lower the bit depth to 16 to get 1024x768.

Well, color me stupid!  In my haste, I seemed to have forgotten to delete the other depths from the file.  Now that I did it, the problem is fixed.  Sorry to clog up the forum! :oops:  Thanks again for your help.

---

