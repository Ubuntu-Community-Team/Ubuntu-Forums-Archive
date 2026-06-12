---
title: "flash players have no sound after upgrading to U8"
date: 2008-10-17
forum: General Help
---

### Post by rwarwarwa on 2008-10-17
Hi there,

I just upgraded to ubuntu 8 and now there is no sound from youtube, google video etc.

Thanks'

Wayne

---

### Post by beno1990 on 2008-10-17
Try this:

```

sudo apt-get install libflashsupport

```

That's a library to tell Flash to send its sound stream through Pulseaudio.

---

