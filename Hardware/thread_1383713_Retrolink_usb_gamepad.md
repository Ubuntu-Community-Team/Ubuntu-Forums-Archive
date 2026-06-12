---
title: "Retrolink usb gamepad"
date: 2010-01-17
forum: Hardware
---

### Post by Dado_x on 2010-01-17
Hello to everybody, i have bought this gamepad:

 [http://www.amazon.com/gp/product/B00281PFQI?ie=UTF8&tag=liliputing09-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=B00281PFQI](http://www.amazon.com/gp/product/B00281PFQI?ie=UTF8&tag=liliputing09-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=B00281PFQI)

The system recognize it:
Bus 002 Device 002: ID 0079:0011 DragonRise Inc.

Zsnes recognize it and the pad works correctly but fceux no!
On fceux i can setting up the keys with --inputcfg gamepad1 with success but when i try to play some games the pad seems don't working correctly. On a bad mario rom only the start button works at title screen, after that nothing is work...
No games are working with this pad and fceux.

What can i do? maybe some patch? o.o

Dave

---

### Post by Groucho Marxist on 2010-03-08
I'm having the same problem. However, in NesterJ, I am able to map the Select, Start, B and A buttons. Both axes are currently inoperable; any help will be greatly appreciated!

---

### Post by Dado_x on 2010-03-10
I have make it work with all of my apps, in fceux seems there was a bug, it set the joypad device path to the rom name i have provided on command line in it conf file.
The pad is completly supported by linux kernel.

---

### Post by Dado_x on 2011-06-21
> **Groucho Marxist said:**
> I'm having the same problem. However, in NesterJ, I am able to map the Select, Start, B and A buttons. Both axes are currently inoperable; any help will be greatly appreciated!

I have reinstalled my linux and i have the same problem too, fceux recognize all buttons but no axes.
Are you fixed that at this time? My pad on tuxnes works great o.o

---

### Post by patrick295767 on 2012-05-27
> **Dado_x said:**
> Hello to everybody, i have bought this gamepad:

 [http://www.amazon.com/gp/product/B00281PFQI?ie=UTF8&tag=liliputing09-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=B00281PFQI](http://www.amazon.com/gp/product/B00281PFQI?ie=UTF8&tag=liliputing09-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=B00281PFQI)

The system recognize it:
Bus 002 Device 002: ID 0079:0011 DragonRise Inc.

Zsnes recognize it and the pad works correctly but fceux no!
On fceux i can setting up the keys with --inputcfg gamepad1 with success but when i try to play some games the pad seems don't working correctly. On a bad mario rom only the start button works at title screen, after that nothing is work...
No games are working with this pad and fceux.

What can i do? maybe some patch? o.o

Dave


try fceu and configure your inputs

for hatari you can use this improved compiled /usr/bin/ adapted to retrolink

---

