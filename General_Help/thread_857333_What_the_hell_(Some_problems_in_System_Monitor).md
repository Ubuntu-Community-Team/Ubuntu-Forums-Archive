---
title: "What the hell? (Some problems in System Monitor)"
date: 2008-07-12
forum: General Help
---

### Post by Redrazor39 on 2008-07-12
The screenshot is attached. It shows that in normal use my CPUs are being used about 50-60%, which is not normal. In windows it's like 3% and normally in ubuntu it's like 2%. Checking the processes shows it should add up to about 10% at most.

Also, I have 2GB of RAM but it only shows 1.4GB of swap. I thought it's supposed to be the same as RAM. Maybe that's why I can't hibernate/suspend? Also, none of the swap is ever used for some reason. I don't even understand what swap is for, so if someone would explain that it would be great.

How do I fix this CPU usage and make my swap 2GB like it should be?

---

### Post by avtolle on 2008-07-12
On your second question: to resize the swap partition, you will need to boot from the Live CD and select the swap partition to resize. This will be successful iff there is sufficient room immediately adjacent to the existing swap partition to add to it (at the end, not the beginning). 

You are not using any swap generally because of the 2 GB RAM in your system; as I understand it, swap is used so the system can write to disk when the RAM is full, and more room in RAM is needed to continue the operations then occurring; with 2 gig, there should be very few times this will happen.

On the CPU usage, you checked the processess as I understand it, and didn't find anything; it appears that both your processors are being utilized correctly. I have no response (unless running System Manager was increasing CPU usage).

---

### Post by Redrazor39 on 2008-07-12
Thanks!

also, do I need to resize my swap to be 2GB or is 1.4GB fine?

---

### Post by sdennie on 2008-07-12
> **Redrazor39 said:**
> Thanks!

also, do I need to resize my swap to be 2GB or is 1.4GB fine?

1.4GB is fine unless you need to use hibernate.

As for the CPU usage, it's probably coming from the CPU monitor itself.  I would use top or htop in a terminal to get more accurate information.

---

### Post by Redrazor39 on 2008-07-12
I'd much rather use suspend, but sadly that doesn't work :( (stupid black screen of death)

---

### Post by sdennie on 2008-07-12
> **Redrazor39 said:**
> I'd much rather use suspend, but sadly that doesn't work :( (stupid black screen of death)

Sometimes if the machine doesn't resume correctly it's possible to hit Ctl-Alt-F1 and then Ctl-Alt-F7 and it starts working properly.  It's worth a try at least.

---

