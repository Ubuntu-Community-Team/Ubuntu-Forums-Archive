---
title: "Lenovo t400 slow application startup"
date: 2009-06-01
forum: Hardware
---

### Post by D.horse on 2009-06-01
Hello,

I got a new computer, it is a Lenovo t400

Intel Core 2 Duo T9600 @ 2.80GHz
4 Gigs DDR3
160 GB 7200 RPM
Dual boot Vista Business 64bit / Ubuntu 9.04 64bit

Now I am having performance issues where it is not preforming as well as i feel it should.  It works, but starting an application is not as fast as it is on my girlfriends computer, and it is considerably lower quality hardware then mine.

Where i really notice the problem is in mozilla.  When i minimize a window and try to reopen it it takes about 2 seconds.  On my girlfriends it is instantaneous.  I would just like it if someone can point me in the right direction to figure out what the issue it.

Both systems are freshly installed today, using normal special effects.

....i was thinking it may have something to do with video drivers but i am unsure....

---

### Post by Steelmourne on 2009-06-01
What video card do you have? New drivers should speed it up. It takes less than a sec on my Geforce Go 7400 with 180.51 drivers running compiz.

---

### Post by D.horse on 2009-06-02
ATI Mobility Radeon 3470 with 256MB

Driver: FGLRX graphics driver

---

### Post by simplysimple on 2009-06-04
> **D.horse said:**
> ATI Mobility Radeon 3470 with 256MB

Driver: FGLRX graphics driver

I have a T400 as well dual booting Vista and Ubuntu 9.04 64 bit. I have half the RAM and not quite the processor (a little jealous :) ) but when I minimize and open a mozilla window it happens in an instant. 

The difference? 

I'm running the integrated graphics (Intel) not the discrete (ATI). I've played around with ATI card using open source drivers and FGLRX but found a better system experience with the Intel. If I play any games I just switch to discrete in the bios then boot into Vista. 

So, my suggestion would be to use the integrated graphics. If you decide to do so make sure you uninstall FGLRX either using jockey-gtk or if you installed by downloading from ATI, there is an uninstall script located in /usr/ATI

Probably not the answer you wanted, but perhaps it will help. :)

---

### Post by D.horse on 2009-06-04
ANyone have any ideas?  Is the application loading slow, would that possibly be the harddrive?  it is only a 160gb and has windows and ubuntu on it.

---

### Post by D.horse on 2009-06-04
Missed that last post.  Okay i will try that, but everytime i try to boot with the intel no UI comes up.  It just boots to command line.  If i disable that driver willit boot normal?

---

### Post by simplysimple on 2009-06-04
> **D.horse said:**
> Missed that last post.  Okay i will try that, but everytime i try to boot with the intel no UI comes up.  It just boots to command line.  If i disable that driver willit boot normal?

Yeah you need to disable/uninstall the ati driver if not X will fail to start like you experienced. The other option would be to have 2  xorg.conf files, one for ati and one for intel.

---

### Post by D.horse on 2009-06-04
Okay, that sounds good.

I like to think of myself as Ubuntu "savvy",  but i do not know how to create two of those files, and how to switch between which one is used.  Could you please point me to a guide or give me a rough explanation?

thank you

---

### Post by simplysimple on 2009-06-04
I wrote a guide explaining my theory of how to run 2 xorg.conf files for switching between ati and intel. I just tried my theory and it doesn't work so scratch that.

The only way my theory would work is if you were running the open source ati drivers. My way didn't work with fglrx.

---

### Post by D.horse on 2009-06-04
I tried the guide, but i was too impatient to double check i did everything....  So i forgot to uninstall the ATI driver and when i tried to restart and boot up with Intel it froze, trying ati and it froze,  so it was crippled.  Tried booting in recovery mode and the automatic graphics repair and tried both cards and it did not work. 

So I just reinstalled but reinstalled it with Intel as the card and it is working great!  I guess I will just wait for a while until the card has a bit better support.

I am still very interested in a less drastic way to switch between the graphics mode then a reinstall (OS selection maybe?), but my computer is working much snappier now.

---

### Post by simplysimple on 2009-06-04
> **D.horse said:**
> I tried the guide, but i was too impatient to double check i did everything....  So i forgot to uninstall the ATI driver and when i tried to restart and boot up with Intel it froze, trying ati and it froze,  so it was crippled.  Tried booting in recovery mode and the automatic graphics repair and tried both cards and it did not work. 

So I just reinstalled but reinstalled it with Intel as the card and it is working great!  I guess I will just wait for a while until the card has a bit better support.

I am still very interested in a less drastic way to switch between the graphics mode then a reinstall (OS selection maybe?), but my computer is working much snappier now.

Sorry you were forced to do a reinstall. But I'm glad you are having a better experience using the integrated graphics. One positive is that you will get longer battery life using the integrated. 

I sure hope ATI support for linux improves. I know it's come a long way from where it used to be but it's nothing compared to NVIDIA's support for linux.

Well, if you have any other issues related to your T400 let me know. 

Take care,
Clark

---

