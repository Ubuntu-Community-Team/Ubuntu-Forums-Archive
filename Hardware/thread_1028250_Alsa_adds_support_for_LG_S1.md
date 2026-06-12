---
title: "Alsa adds support for LG S1"
date: 2009-01-02
forum: Hardware
---

### Post by thefish123 on 2009-01-02
Hi everyone,

I have never been able to get sound working properly on my laptop under **any** Linux distro. I have the LG S1 (model QB01A9).

The sound works fine on the headphone jack but not on the internal speakers. I have read tonnes of suggestions with similar problems but none of the suggestions has worked for me.

After much digging I think I am finally on to something. I found on the alsa-project.org site that support for the LG S1 laptop was added between versions 1.0.11 and 1.0.12. You can see the change log here:

[http://www.alsa-project.org/main/index.php/Changes_v1.0.11_v1.0.12](http://www.alsa-project.org/main/index.php/Changes_v1.0.11_v1.0.12)

Ubuntu 8.10 has Alsa 1.0.17 so presumably this problem has been resolved. The change log (only says &#8220;*Add support for LG S1 laptop*&#8221; and then later &#8220;A*dded the model entry for LG S1 laptop*&#8221;. This fills me with hope but no where (that I can see) does it say what that model entry is. I know that this has to go into my alsa-base file but what is the model entry to use?

Perhaps I am not reading the change log correctly? Can someone help me out here? Perhaps I can email one of the developers?

So close and yet so far.... :)

Best regards,
The Fish

---

### Post by thefish123 on 2009-01-03
Does no one know how I can go about finding out what the correct model entry is?  I have checked the ALSA-configuration.txt file and there is nothing in there about the LG S1.  I have tried the obvious lg-s1 and lgs1 and simply lg but none of those has worked.

If I am overlooking something obvious that I should be doing before posting please let me know.

It is depressing that my Google queries on the subject return my own posts :-(

The Fish

---

### Post by thefish123 on 2009-01-05
Bump

---

### Post by thefish123 on 2009-01-09
bump...

---

### Post by thefish123 on 2009-02-14
Bump...

---

