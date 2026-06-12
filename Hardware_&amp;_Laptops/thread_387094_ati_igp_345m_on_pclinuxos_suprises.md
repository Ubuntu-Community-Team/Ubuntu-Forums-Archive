---
title: "ati igp 345m on pclinuxos suprises"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by edemark on 2007-03-17
Hi all

I had a small surprise when i tried out the new test release of pclinuxos 2007-test3. It happens that first i get awfully great results on glxgears (usually with ubuntu or linux mint i get only 320 fps) approximately 500 fps. Also PCLinuxOS Control Center states that it uses ati radeon (fglrx) graphics driver (that not supposed to work in my card and never actually did in ubuntu). Finally i can enable beryl (that I was unable to set up in my dapper) with just a click and it works really well.

So my questions are the following:
will i get these hi results with the new ubuntu release 7.04 i am waiting for so much?
will i be able to run beryl?
haw it comes the difference?
why pclinuxos is able to use fglrx for my card that i am unable to set up in ubuntu?

any help will be appreciated much

thanks

---

### Post by edemark on 2007-03-18
Hi 

I really would like to have some answers to those questios if there are any. I suppose it is interesting mainly because of the fglrx driver used so please if you have any ideas just let me know.

thanks

---

### Post by edemark on 2007-03-18
ok i have resolved the fps issue (sadly there are no miracles in function of my card) I have checked the xorg setup and it was done with 16 bit color depth. As soon as I have changed to 24 bit i got the usual 320 fps. However the rest of my questions remains open if you have any answers (the more intresting is the use of the fglrx driver).

---

