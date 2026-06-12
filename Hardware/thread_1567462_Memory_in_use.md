---
title: "Memory in use"
date: 2010-09-03
forum: Hardware
---

### Post by Doulos1 on 2010-09-03
Why is my system using so much memory?  I currently have gnome and bind 9 running, but no internet activity occurring.

Ubuntu 10.04 LTS Dell Inspiron 4600 2.8Gz 1.25Gb RAM (1-512mb + 3-256mb mem sticks).
 
**Memory Usage**

                  Type: Physical Memory
Usage: 52% 
         Free: 611.98 MiB
               Used: 642.16 MiB
Size: 1.22 GiB

Is that normal for an idling system?

---

### Post by squaregoldfish on 2010-09-04
Yes, that's normal - Linux will use as much RAM as it can as a disk cache, and file buffers, so it's not unusual to see large amounts of RAM in use when only a few programs are running.

The top program will give you a more detailed breakdown of how your RAM is being used, as well as allowing you to see how much RAM individual programs are using.

Steve.

---

### Post by Xeronage on 2010-09-04
> **Doulos1 said:**
> Why is my system using so much memory?  I currently have gnome and bind 9 running, but no internet activity occurring.

Ubuntu 10.04 LTS Dell Inspiron 4600 2.8Gz 1.25Gb RAM (1-512mb + 3-256mb mem sticks).
 
**Memory Usage**

                  Type: Physical Memory
Usage: 52% 
         Free: 611.98 MiB
               Used: 642.16 MiB
Size: 1.22 GiB

Is that normal for an idling system?

Look at it this way: Why waste all the excess memory? It's much better to use it for buffering, caching, preempting, etc. Don't worry, if you run out of RAM (Which I doubt will happen) the kernel will free up space :). Because of this, don't compare it to Windows memory usage and be like "Oh my, Ubuntu is using way more!"

---

### Post by Doulos1 on 2010-09-04
Thanks, I don't use this server for anything but a few web pages, data backup, and stats so I wasn't worried, just curious.

---

