---
title: "X server failure"
date: 2005-12-13
forum: Hardware &amp; Laptops
---

### Post by wwbdd on 2005-12-13
I just bought this new laptop primarily to be used with windows (oh how i hate it, but it is necessary for some of the things i do)  but I was thinking about dual booting it.  It is a compaq presario v2000 with an amd turion 64 with 512 ram 14.1 widescreen display and the ati 200 express or something like that (the better of the two video card options).  I am pretty new to linux but I have installed ubuntu on two other desktops in my house.  I thought a good place to start would be to run it with the live cd to see what is recognized and what is not to see if it is even worth taking the time energy and hard disk space to install it.  It got through the whole process and then the x server died before it would log me in.  I dont know if that is a configuration issue or if that is a problem with this laptop or video card.  Is it worth my time and effort to pursue it any further, or will getting it up and running be a big hassle?

---

### Post by Patsoe on 2005-12-15
As a start, change the file /etc/X11/xorg.conf from the command line. Replace the driver 'ati' by 'vesa'. This should get you a working X-server (I have the same integrated video chip).
When that works, we'll take it further from there if needed.

edit: sorry, that may not do the job for the live-cd, I wasn't reading carefully.

---

### Post by wwbdd on 2005-12-15
If i were to resize the existing partition and install it though it would work right?

---

### Post by Patsoe on 2005-12-15
Well, that worked for me anyway.

If you're not in a hurry, I might try the live-cd again when I get home in a few hours, to see if it's possible to get that running. I didn't try very hard the first time and then just ran the install-cd; but I still have the live-cd lying around anyway. Perhaps the right combination of boot-options will get it going.

---

### Post by wwbdd on 2005-12-15
two questions-

Does the brightview screen have anything to do with any problems that may exist?

if/when i have time to install ubuntu how reliable is the resize partition?  Obviously i think it's a good idea to backup important data but i dont want to put the system out of commision for both windows and linux if something goes wrong, especially since i use this laptop for school everyday.  When i installed linux on my desktop it didn't get along with windows and it was out of commision for a week and i can't afford that with this machine.

---

### Post by Patsoe on 2005-12-16
No, I don't think the display has anything to do with it; from what I've read on this forum, many people with different ATi based systems have similar problems.

I resized using a Partition Magic bootable CD, which I have had for some years, and which has proven to do a good job. I didn't try anything new because I'm more comfortable with this known solution; if you have a large enough back-up drive, you may want to make a drive image including boot sectors and all - then you can always restore the full WinXP installation.

I tried the LiveCD, and it allows to edit xorg.conf. However, I can't get the X-server to restart after editing. Error message says it can't find working modes for the screen, although the settings in xorg.conf are correct for sure. Bad luck there.
With the installCD, after installing, I also get these same errors after editing xorg.conf - the difference is, here I can reboot, and then for some obscure reason I do get into X...?!

By the way: if you install, I advise to use this boot-option line:
```
linux noapic nolapic debian-installer/framebuffer=false
```

I have to run now, but I can explain later why - I've tested running with and without each of these options. Bye.

---

### Post by wwbdd on 2005-12-22
I installed ubuntu on the machine and again it get the x server failure thing.  I replaced the "ati" with "vesa" like you said fixed yours, but mine still doesn't work.  Any advice?

---

### Post by wwbdd on 2005-12-22
I figured it out.  I had to add the line

option "noaccel"

and then it worked.  Hope this can be of use to others as well.

---

### Post by towsonu2003 on 2005-12-22
I would report that as a bug to bugzilla.ubuntu.com... if there is no duplicate. Thanks for reporting back :)

---

