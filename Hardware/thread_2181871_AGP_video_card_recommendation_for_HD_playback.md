---
title: "AGP video card recommendation for HD playback"
date: 2013-10-19
forum: Hardware
---

### Post by victorcl2 on 2013-10-19
Hi. I'm new to the forum and wanted advice for an AGP video card upgrade. I have an old system that I want to bring back to life and put Linux on.
The current specs for this system is, Pentium 4 2.4ghz, 1.5gb of ram, with an old ATI 64mb AGP card. 
I am looking for an inexpensive video card that will play 720p HD videos smoothly. This is for video playback only, so I don't need anything that is overkill. Also, I want a video card that is compatible or can be easily configured for Linux. I was looking at a Radeon 2400 Pro and 2600 Pro, but ATI/AMD website doesn't have Linux drivers for those models. I read that there are a lot of compatibility problems with the old Radeon video cards, so I looked into some of the nVidia Geforces. I was looking at the Geforce 6200 but I'm not sure if it can play 720p videos; also, the Radeon 2400 and 2600 had better specs.
Any recommendations will be appreciated. Thanks!

Oh, the motherboard has an AGP 4x slot; I'm guessing an AGP 8x card will work too but at 4x speed.

---

### Post by mörgæs on 2013-10-19
Hi, welcome to the fora.

There will not be closed-source (=fast) drivers available for ATI's AGP cards. Nvidia have generally better support for old cards, but I don't know the 6200.

Which system are you planning on installing?


Edit: The 2400 and 2600 cards will still be much faster than your present 64 MB card, also when using open-source drivers.

---

### Post by SeijiSensei on 2013-10-19
I don't know about ATI's offerings, but you are pretty much out of luck when it comes to NVIDIA cards that use AGP.  You need a card in the 8xxx or later series, but [I don't believe such a beast exists]("http://www.gossamer-threads.com/lists/mythtv/users/360090#360090").  Cards before that do not include hardware video decoding so they won't work the the VDPAU interface that NVIDIA uses to off-load video processing to the card.  The 6200 you mentioned defintely will not help.

---

### Post by victorcl2 on 2013-10-19
I'm thinking about installing something lightweight like the latest Lubuntu or Xubuntu. The computer is pretty old so it'll probably be slow with Ubuntu. I'm okay experimenting with any distro as long as it's smooth with multimedia playback.
I just tested my friend's old Radeon 9600 Pro 256mb AGP on my system with Linux Mint 13 Xfce, and it was able to play 720p videos fairly smoothly; however, it struggles with streaming videos. I could barely play 360p videos on Youtube. Maybe it's a flash problem? Not sure.

---

### Post by victorcl2 on 2013-10-19
Thanks for the advice. I will not waste my money on the 6200.

---

### Post by Yellow Pasque on 2013-10-19
AGP's dead. Look for a PCI card like a GT520.

> it struggles with streaming videos. I could barely play 360p videos on Youtube. Maybe it's a flash problem?
Yes, it's a Flash problem, in that Linux Flash doesn't offload to most GPU's and takes a relatively fast CPU just to play 720p. The last time I checked, Flash could get some acceleration through VDPAU on nvidia cards.

---

### Post by victorcl2 on 2013-10-19
I'm guessing you're referring to PCI-Express? Unfortunately my motherboard only has the standard PCI 2.2 slots which I believe is slower than AGP.

---

### Post by Yellow Pasque on 2013-10-20
No. If you had PCI-Express, then you wouldn't have made this thread. PCI may have less bandwidth than AGP, but for light gaming and video playback, it will be better than an ancient AGP nvidia card or a poorly supported ATI AGP card.
Example:  [http://www.newegg.com/Product/Product.aspx?Item=N82E16814500262](http://www.newegg.com/Product/Product.aspx?Item=N82E16814500262)

---

### Post by victorcl2 on 2013-10-22
temujin, thanks! i'll look into a pci card and hope it has better support.

---

