---
title: "Should I install Ubuntu 14.04 on my 2009 iMac?"
date: 2014-03-23
forum: Hardware
---

### Post by MountainX on 2014-03-23
I have a late 2009 27" iMac i5. Because I really dislike OS X, it gets little use and it still looks like new. I tried to install Ubuntu on it back in 2009 when I bought it and Ubuntu had a lot of problems. Some were serious (display issues) and some were just personally important (lack of full/proper support for the Apple trackpad I purchased).

So I had given up on running Ubuntu on my iMac until today when I read this:

[Phoronix] **Ubuntu 14.04 Now Runs Well On The 2013 MacBook Air**, Beats OS X 10.9 In Graphics  
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1404_mba2013gl&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1404_mba2013gl&num=1)

I would appreciate any informed opinions as to whether 14.04 is worth trying on my older iMac. BTW, my preferred flavor is Kubuntu and I plan to install the current beta - contigent upon feedback here, of course. 

Due to the fact that I have a small-ish SSD, I can't dual boot. If I go with Kubuntu, it is a total commitment. And I would want the following things to work:

1. Apple Trackpad
2. Apple Mouse
3. support for hooking up an external HDTV in various display modes (mirroring or 2nd monitor) 

Why am I asking this question instead of just trying a LiveCD? Last time I tried to install Ubuntu on my iMac the display worked properly with the LiveCD. But when I actually installed Ubuntu, my iMac would only boot up to a blank/black display. I was never able to resolve that and I went back to OS X. Besides, I think it is always better to ask for advice first.

[SIZE=5]My iMac Hardware Info:[/SIZE]

[SIZE=4]Hardware Overview:[/SIZE]

      Model Name:    iMac
      Model Identifier:    iMac11,1
      Processor Name:    Intel Core i5
      Processor Speed:    2.66 GHz
      Number Of Processors:    1
      Total Number Of Cores:    4
      L2 Cache (per core):    256 KB
      L3 Cache:    8 MB
      Memory:    4 GB
      Processor Interconnect Speed:    4.8 GT/s

[SIZE=4]Graphics/Displays:[/SIZE]

    ATI Radeon HD 4850:
    
      Chipset Model:    ATI Radeon HD 4850
      Type:    GPU
      Bus:    PCIe
      PCIe Lane Width:    x16
      VRAM (Total):    512 MB
      Vendor:    ATI (0x1002)
      Device ID:    0x944a
      Revision ID:    0x0000
      ROM Revision:    113-B9110C-425
      EFI Driver Version:    01.00.383
      Displays:
    iMac:
      Resolution:    2560 x 1440
      Pixel Depth:    32-Bit Color (ARGB8888)
      Main Display:    Yes
      Mirror:    Off
      Online:    Yes
      Built-In:    Yes
      Connection Type:    DisplayPort

---

### Post by ajgreeny on 2014-03-23
Assuming you can run a live USB or DVD on a mac why not download that and try it out live first.  Apart from that idea I can't help with anything mac.

I suggest you try the daily image file, however, not the beta as a lot of updates have come along since the beta was released.  I have not tried Kubuntu as I don't like kde now, but I am running Ubuntu, Xubuntu and Lubuntu as virtual machines on my Intel based PC and all three of those are very good; occasional glitches but nothing that is a show-stopper any more.

Get it from [http://cdimage.ubuntu.com/kubuntu/daily-live/pending/](http://cdimage.ubuntu.com/kubuntu/daily-live/pending/)

---

### Post by MountainX on 2014-03-23
> **ajgreeny said:**
> Assuming you can run a live USB or DVD on a mac why not download that and try it out live first.  Apart from that idea I can't help with anything mac.


Quoting from my OP:

Why am I asking this question instead of just trying a LiveCD? Last time  I tried to install Ubuntu on my iMac the display worked properly with  the LiveCD. But when I actually installed Ubuntu, my iMac would only  boot up to a blank/black display. I was never able to resolve that and I  went back to OS X. Besides, I think it is always better to ask for  advice first.

---

### Post by ajgreeny on 2014-03-24
Sorry I missed that comment of yours about live CDs, but it sounds as if you needed a graphic driver or something similar.

When using a mac do you get the option of adding non-free proprietary codecs etc etc and updating as you install, as you do in a PC?  That might solve your black screen problem.

Otherwise, as I said, I really do not know or understand macs, so can't do much other than wish you good luck.

---

### Post by gifford on 2014-03-25
Have you tried the apple users Ubuntu forum? It is under Ubuntu specialized support.

---

### Post by jowan512 on 2014-10-21
Its the graphics card that is going to give you trouble.
The fglrx drivers don't support legacy cards. e.g 4xxx

Look - no support here :
[http://support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx](http://support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx)


However, this may work for you.
[https://launchpad.net/~makson96/+archive/ubuntu/fglrx](https://launchpad.net/~makson96/+archive/ubuntu/fglrx)

---

### Post by MountainX on 2014-10-21
Thank you jowan512. I might also try this:

Upgrade iMac 27" late 2009 video card? | Apple Support Communities
[https://discussions.apple.com/thread/3029120?tstart=0](https://discussions.apple.com/thread/3029120?tstart=0)

---

