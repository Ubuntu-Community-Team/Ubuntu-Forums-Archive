---
title: "Gigabyte GeForce GT 610 Ubuntu compatibilty"
date: 2012-08-28
forum: Hardware
---

### Post by PhantomTurtle on 2012-08-28
Hello,
I am thinking about getting a GeForce gt 610 and I was wondering if this graphics card was compatible with Ubuntu. I know that some of the older drivers and the older kernel on Ubuntu 12.04 doesn't work well with some Nvidia cards so I was wondering how well this works in Ubuntu. I want to run Ubuntu 12.04. Also a question unrelated to Ubuntu, my PSU is 400watts(from what I remember, I'll check and confirm soon) and the requirements to use this GPU is 300w. According to 3dguru the Max Power used is 29 W. The most graphics intensive things I do are play League of Legends and watch 1080p video. Is it fine to use this PSU(because I'd rather not have to buy another one). Thanks for you help.

---

### Post by PhantomTurtle on 2012-08-28
I have gotten an answer from Quidsup on Youtube and I will post it here,
> It'll work fine with Ubuntu. 
Im using a GT640 in Ubuntu 12.04 with XBMC and managing to watch 1080P vids and bitstreaming Dolby TrueHD surround sound.

However it won't work with the Nvidia drivers that Ubuntu supply, so you'll need to add the X.Org repository to upgrade them.

Heres a tutorial vid on how to add the X.Org repo: [http://www.youtube.com/watch?v=QtPAJ9BR1W8](http://www.youtube.com/watch?v=QtPAJ9BR1W8)

Might also help to upgrade the kernel:
[http://www.youtube.com/watch?v=traegZveTKo](http://www.youtube.com/watch?v=traegZveTKo)

400W is more than sufficent

So it works for anybody wondering. Thanks to quidsup for helping me out with that (his vids are awesome, check them out) :)

---

### Post by mzeyrek on 2013-02-16
Hi Phantom Turtle,
 
I was about to buy this card due to hardware restrictions in my HP dc5700. I decided to use my desktop as a Media Center running Ubuntu with XBMC. Just a quick question. Was your card pci x1 or pci express ? 
My hardware constraint i'm unable to plug any pcie cards on it as its giving add2/sdvo error. No support for x16 cards while x1 cards only. 
I've found a card named "HP Compaq dc5100 dc5700 SFF Low Profile Half Height 512MB PCI-E x1 HD Video Card" on eBay link : [http://j.mp/XERKRg](http://j.mp/XERKRg) wondering if it works well with Ubuntu 12.04 as well as XBMC hardware rendering.
 
Thanks,
Muco

---

### Post by Minifig666 on 2013-05-24
My 610 is PCIe x16 and that's all I've seen for connections on any of the 600 series GPUs.

---

