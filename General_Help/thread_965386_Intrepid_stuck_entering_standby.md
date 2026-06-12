---
title: "Intrepid stuck entering standby"
date: 2008-10-31
forum: General Help
---

### Post by ug88jdm on 2008-10-31
Having installed Intrepid and installed all patches I've found I'm not able to enter standby. 

The desktop fades to a black screen with a flashing cursor and then nothing more seems to happen.  I've left the machine for several minutes with no response and I eventual have to hard-reset it.

It's a custom build PC with an ASUS m/board which supports ACPI.  It has an NVidia FX5200 graphics card and the problem happens with the restricted drivers both enable and disabled.  Having had a look in syslog, I can't see anything immediately obvious of things going wrong.

I've seen lots of forum posts talking about this sort of issue when resuming from standby but not many talking about it when entering.  This is the first time Ubuntu has been installed on the machine so I don't know if this is specific to Intrepid or not.

Can anyone make any suggestions (or tell me what info to at least provide...)

Thanks.

---

### Post by DLGandalf on 2008-11-26
I've got exactly the same symptoms 
 Have you figured it out?

---

### Post by ug88jdm on 2008-11-27
Sorry, no I wasn't able to figure it out and couldn't find much to try with it.  It was for a media center box so unfortunately I had to resort to using Windows instead which would standby successfully.

Might be worth reverting to Hardy though if it's a big issue?

---

### Post by trapanator on 2009-02-18
Simply put this:

```
    Option "NvAGP"  "0"

```

in the "Screen" section of your Xorg.conf

---

