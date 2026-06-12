---
title: "New Ubuntu install freezes"
date: 2006-01-29
forum: Installation &amp; Upgrades
---

### Post by amherring on 2006-01-29
New Ubuntu 5.10 install freezes at "Starting the Partitioner" 52%. Tried several times, even with different install CD. Keeps freezing in same place. Anyone got any ideas on how to get past this and get it installed?

---

### Post by HJThis on 2006-01-29
Hello,amherring & Welcome

Could you give these Pros more info please

but let me ask did you download the CD from
here [http://www.ubuntu.com/download](http://www.ubuntu.com/download)

& did you do a check sum on the CD

Best of luck

---

### Post by amherring on 2006-01-29
I didn't download the CD, I requested it from canonical. I am running a Dell Optiplex GX110. The Live CD runs fine, just can't get the install one to work. What other info do you need? Thanks for your reply.

---

### Post by r4ik on 2006-01-29
Try "expert" mode and see what it does.
So do not hit enter at boot but type "expert" then hit enter.
It takes a little bit more reading but trying wont hurt.
If you dont succeed i think you are unlucky with you shipment and i would go for the suggested download.
Good luck !

---

### Post by Nutter on 2006-01-29
I had the exact same problem, until I started poking around in the help menus before the installation.  Somewhere in there, it says something about disabling the "buggy APIC interupt router", and tells you to start the installer with some flags that will do this.

I think the flags are "noapic" and "nolapic", so you would type at the first prompt "linux noapic nolapic".  This would install the default linux setup without using this buggy interupt router.

I was poking around on the threads, and it seems like lots of other people have the same problem, so I hope this will solve it for you just like it did for me.

---

