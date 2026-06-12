---
title: "Thunderbird graphics problem on AcerAspire AO751h"
date: 2010-09-26
forum: Hardware
---

### Post by pirx82 on 2010-09-26
Hello everyone,

I have Ubuntu Netbook 10.04 LTS installed on my laptop (Acer Aspire AO751h) which uses a Intel GMA500 graphics card. This requires me to have the Poulsbo[ (https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo")) driver update installed.

Every piece of software seems to work fine, except for the Thunderbird (v 3.08). Whenever I start the program, the graphics seems to have some kind of trouble. Some of the text can be seen, some not and when I move a window, a trail is left behind (there is a screen-shot available in the attachment).

Does anyone here have a similar problem or does anyone know how this could be solved? 

Any kind of help is much appreciated!

Thanks and best regards.

---

### Post by lucazade on 2010-09-26
> **pirx82 said:**
> Hello everyone,

I have Ubuntu Netbook 10.04 LTS installed on my laptop (Acer Aspire AO751h) which uses a Intel GMA500 graphics card. This requires me to have the Poulsbo[ (https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo")) driver update installed.

Every piece of software seems to work fine, except for the Thunderbird (v 3.08). Whenever I start the program, the graphics seems to have some kind of trouble. Some of the text can be seen, some not and when I move a window, a trail is left behind (there is a screen-shot available in the attachment).

Does anyone here have a similar problem or does anyone know how this could be solved? 

Any kind of help is much appreciated!

Thanks and best regards.

Use thunderbird from tar.gz packages, not from repository.
Don't ask me why but it works.

---

### Post by pirx82 on 2010-09-26
> **lucazade said:**
> Use thunderbird from tar.gz packages, not from repository.
Don't ask me why but it works.

Hi, thanks for your quick reply.

So, should I uninstall the Thunderbird which I got from repository and install the 3.1.4 version from their website? I never installed a tar.bz2 package before... But I'll try.

Thanks again!

---

### Post by MartyBuntu on 2010-09-26
I had this **exact** same problem yesterday.

Try enabling Compiz if you haven't already. If you have Compiz, try disabling it. There seems to be a sticking point with desktop effects, I'm not sure, but for me, installing Compiz from the software center made the problem go away.

---

### Post by pirx82 on 2010-09-26
> **MartyBuntu said:**
> I had this **exact** same problem yesterday.

Try enabling Compiz if you haven't already. If you have Compiz, try disabling it. There seems to be a sticking point with desktop effects, I'm not sure, but for me, installing Compiz from the software center made the problem go away.

Hi! Well, this just killed my Ubuntu. I installed Compiz and the screen just keeps looping between a blank screen and between showing some startup info. I will try to get in in safe mode and uninstall Compiz.

---

### Post by pirx82 on 2010-09-26
OK, this seems now like a bit of a problem. I went to the command line and tried to uninstall "compiz" by typing:

sudo apt-get remove compiz

I was notified that compiz is not installed... However, it WAS installed without a doubt.

I tried to start up the graphic mode by typing "startx" and I get a following message:

xinit: No such file or directory (errno 2): unable to connect tp X server
xinit: No such process (errno 3): Server error

There is also a line which says:

PSB: Failed to load module "Xpsb" (module does not exist, 0)

Anyone knows how could I fix this? I hope it's not too serious. Thanks.

---

### Post by pirx82 on 2010-09-26
Phew, I've solved the issue by reinstalling the Poulsbo drivers.

OK, so I'm off to try the installation from Mozilla's webpage.

---

