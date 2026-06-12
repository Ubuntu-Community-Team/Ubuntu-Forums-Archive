---
title: "Tascam Us-144"
date: 2009-11-05
forum: Hardware
---

### Post by Greentree on 2009-11-05
Basically the only reason I don't have Ubuntu installed(i used to though) is because it does not detect my  USB audio interface, the tascam US-144. I've seen a bit of dead ends on google while searching for answers for this problem and nothing brightening whatsoever. 
Will it ever be compatible?

---

### Post by ram130 on 2009-11-21
same here ..anyone??

---

### Post by gnomeza on 2010-01-23
From linux-2.6.31/sound/usb/usx2y/us122l.c:
```

static struct usb_device_id snd_us122l_usb_id_table[] = {
    {    
        .match_flags =  USB_DEVICE_ID_MATCH_DEVICE,
        .idVendor = 0x0644,
        .idProduct =    USB_ID_US122L
    },   
/*      { */        /* US-144 maybe works when @USB1.1. Untested. */
/*      .match_flags =  USB_DEVICE_ID_MATCH_DEVICE, */
/*      .idVendor = 0x0644, */
/*      .idProduct =    USB_ID_US144 */
/*  }, */
    { /* terminator */ }
};

```

That is, support for US-144 is commented out.

Looks like user EliasKesh had a go at uncommenting it here: [http://ubuntuforums.org/showpost.php?p=7639341&postcount=7](http://ubuntuforums.org/showpost.php?p=7639341&postcount=7)

Edited to add: [MigBc]("http://ubuntuforums.org/member.php?u=437320") posted a [howto]("http://wiki.ubuntuusers.de/Benutzer/BigMc/Tascam_US-144").

After [configuring ALSA]("http://wiki.briata.org/doku.php#step_3_-_set_alsa") confirmed working under Karmic i686 with 2.6.31-17-generic.

---

### Post by ram130 on 2010-01-23
> **gnomeza said:**
> From linux-2.6.31/sound/usb/usx2y/us122l.c:
```

static struct usb_device_id snd_us122l_usb_id_table[] = {
    {    
        .match_flags =  USB_DEVICE_ID_MATCH_DEVICE,
        .idVendor = 0x0644,
        .idProduct =    USB_ID_US122L
    },   
/*      { */        /* US-144 maybe works when @USB1.1. Untested. */
/*      .match_flags =  USB_DEVICE_ID_MATCH_DEVICE, */
/*      .idVendor = 0x0644, */
/*      .idProduct =    USB_ID_US144 */
/*  }, */
    { /* terminator */ }
};

```

That is, support for US-144 is commented out.

Looks like user EliasKesh had a go at uncommenting it here: [http://ubuntuforums.org/showpost.php?p=7639341&postcount=7](http://ubuntuforums.org/showpost.php?p=7639341&postcount=7)

Edited to add: [MigBc]("http://ubuntuforums.org/member.php?u=437320") posted a [howto]("http://wiki.ubuntuusers.de/Benutzer/BigMc/Tascam_US-144").

After [configuring ALSA]("http://wiki.briata.org/doku.php#step_3_-_set_alsa") confirmed working under Karmic i686 with 2.6.31-17-generic.

What did you do to get it working?

---

### Post by gnomeza on 2010-01-24
Follow the [Ubuntu Tascam US-144 howto]("http://wiki.ubuntuusers.de/Benutzer/BigMc/Tascam_US-144").

At the end it directs you to [this page for configuring ALSA]("http://wiki.briata.org/doku.php#step_3_-_set_alsa").

---

### Post by ram130 on 2010-01-24
> **gnomeza said:**
> Follow the [Ubuntu Tascam US-144 howto]("http://wiki.ubuntuusers.de/Benutzer/BigMc/Tascam_US-144").

At the end it directs you to [this page for configuring ALSA]("http://wiki.briata.org/doku.php#step_3_-_set_alsa").

damn so much trouble jus to get it working. I also have a mbox 2 mini, so I guess this is my best option for Ubuntu. I hate when manufactures think its only Mac and Windows out there.

anyways thanks!

---

### Post by gnomeza on 2010-01-26
Took all of 20 mins. It was surprisingly painless.

It'll be supported out of the box as soon as someone sorts out the damn uhci/ohci/ehci mess and someone else gives the US144 enough testing to enable it in kernel mainline.

Having to disable USB2.0 is rather annoying.

---

### Post by ram130 on 2010-01-26
Yep. Hopefully they will in 10.04, but I doubt anyone remembers about it. Nice to know if I need to do any recording in Ubuntu I can use the 144.

---

### Post by Jonatello on 2011-04-26
> **gnomeza said:**
> Follow the [Ubuntu Tascam US-144 howto]("http://wiki.ubuntuusers.de/Benutzer/BigMc/Tascam_US-144").

At the end it directs you to [this page for configuring ALSA]("http://wiki.briata.org/doku.php#step_3_-_set_alsa").

this article seems to be missing (and beyond that, i can't read german lol)

any advice getting the tascam us-144 to work?

---

### Post by MigBc on 2011-10-29
It was moved here: [http://wiki.ubuntuusers.de/Benutzer/BigMc](http://wiki.ubuntuusers.de/Benutzer/BigMc)
And it is in English.

---

