---
title: "webcam not recognized... canyon cnr-wcam43"
date: 2007-12-23
forum: Hardware &amp; Laptops
---

### Post by crash0 on 2007-12-23
hi,
i got a [webcam]("http://www.canyon-tech.com/products/companions/webcams/CNR-WCAM43") for my birthday and gutsy can't recognize it. nothing happened when i plugged it in and i can't get skype/kopete/canorama/xawtv/etc to do anything with it. canorama says "can't connect to video device (/dev/video), check your connection."

it isn't listed on [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
i tried everything and i got nowhere. :(

the camera is obviously a piece of crap since googling it gets something like 10,000 pages and googling "cnr-wcam43 linux" or "cnr-wcam43 ubuntu" results in 25 web pages.

if anyone has an idea, i'd really appreciate it. maybe there's a driver for a similiar cam that would work (the cn-wcam series are more popular than the cnr-wcam...) or some sort of generic driver like spca5xx. :-k

thanks :-|

---

### Post by linuxwizard on 2007-12-23
in terminal > lsusb -v  > post results >this will give Product & Vendor ID#

---

### Post by dnvikram on 2007-12-24
Did you try with ,"cheese" too?If not,try installing that package from the reps and check if cheese application detects your webcam.

Give it a shot,nothing to lose I guess.If that also aint working,then it surely is drivers problem..

---

### Post by crash0 on 2007-12-24
cheese doesen't work :(

lsusb -v gives nothing specific and lsusb (without the -v) gives this:
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  
Bus 007 Device 003: ID 0c45:6128 Microdia 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000

---

### Post by linuxwizard on 2007-12-24
No webcam listed. You did have webcam plugged in when running commmand > lsusb > ?

---

### Post by crash0 on 2007-12-24
i did - the webcam is the "microdia" thing. ok, what to do now?

---

### Post by vivalant on 2007-12-27
Hello crash0, there are drivers at [http://www.linux-projects.org](http://www.linux-projects.org) for a lot of microdia webcams.

---

### Post by crash0 on 2007-12-27
thanks for the link... :)

....but:

my cam isn't a microdia, it's a canyon. (ok, maybe i'm dumb, but i assume microdia is a company?)

and btw. which driver should i use? it doesen't say microdia what, it just says microdia.

---

### Post by intel on 2008-01-07
For all those with microdia (0c45:xxxy) webcams, please visit this website

https://groups.google.com/group/microdia

and provide/add details about your specific webcam, join the group,
this will help in getting decent drivers.

0c45:608f, 0c45:60ec, 0c45:60fe, 0c45:6242, 0c45:6260, 0c45:6270, 0c45:60c0, 0c45:613b, 0c45:613c, 0c45:624f, 0c45:627b, 0c45:62c0, 0c45:8105

---

