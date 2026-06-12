---
title: "BarPanel configuration?"
date: 2008-08-08
forum: General Help
---

### Post by Giant Speck on 2008-08-08
Hello, 

I recently installed barpanel because I wanted to check it out and I have to say it is pretty awesome.

My only problem is that I don't know how to configure it.

Is anyone here able to point me to a website that shows how to configure barpanel?

Thanks!

---

### Post by pokxm on 2008-09-29
Basically the configuration takes place in one file, ~/.barpanel/config.xml. All configurable aspects can be modified there. Starting from version 0.5.0 of Barpanel, this file will automatically be created for you upon first running Barpanel (in older versions, you will need to copy the /usr/lib/python2.5/site-packages/barpanel/config.xml.in file manually to that location first, then edit). After making changes, Barpanel should then be restarted.

The file may hopefully be self-explanatory enough to help get started with the tweaking. More detailed documentation/information will hopefully be available soon.

---

