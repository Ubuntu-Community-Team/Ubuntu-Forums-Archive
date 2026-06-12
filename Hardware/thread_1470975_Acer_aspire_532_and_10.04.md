---
title: "Acer aspire 532 and 10.04"
date: 2010-05-03
forum: Hardware
---

### Post by BaroqueBloke on 2010-05-03
Despite several threads pertaining to the 532h here on the forums nothing I could find was terribly recent.  So, I thought I would post my progress with this little machine thus far.  

As of now I am running 10.04 UNE with Gnome rather than the UNE desktop (just like it better).  In the release candidate version and in 9.10 I had several hardware issues, some of which are still present: 
  Multi-in-one card reader not recognized
  a couple of the function keys dont register
  multi-touch and scroll bar does not work
  brightness keys dont adjust one level at a time but rather three
  
Whats been fixed?
  wireless seems far more stable
  internal mic actually works**
  screen lock on suspend+wake up no longer freezes with "session time out" (didnt happen all the time)  

**there were some threads where peoples mics seemed to not be picking up anything  or else picked up sound only very faintly.  I thought this was the case still with mine except Gnome Sound Recorder is now able to pick me up from across a large room with reletive ease.  I had to go into sound preference and the input tab and change the input amplification to 2/3s of the way full for this to happen though.  The mic test meter in preferences will not react to any sound though it is definitely working.  Hope this helps some people**

All in all I feel the remaining issues are not that serious.  I still have a remarkably functional and competent little netbook.  Battery life is commendable though not the best in the netbook world and thanks to ubuntu the systems feels worlds smoother and quicker then it did with win7 starter.  

Of the remaining issues left I would most like to see the multi touch (for scrolling) and the card reader fixed.  Ive never been one for page up/down buttons, they just feel clumsy.  And the card reader would be nice to use with a smaller bootable distribution like puppy or DSL for (conceivably) quick boots and access.


If anyone out there has found solutions to these problems please feel free to either post them here or point me in the right direction!

---

### Post by RamahX on 2010-05-03
I have the Gateway version  of the3 AAO 532h - it's the LT2104u: 

-Had spotty wireless issues with upgrade to 10.04, but used SPM to install backport (linux-backports-modules-wireless-lucid-generic) and so far not dropping. Had to reboot though for it to take hold.
-Mic is still not working. Tried the above to no avail.
-F2 does not bring up terminal, but Alt-F2 brings up run window.
-SD multicard reader does not work. Would like that functional so I can use with my digital camera.
-Multitouch does not work
-Brightness keys same - adjust 3 clicks instead of one

---

### Post by lou002 on 2010-05-03
I have the AAO 532H..and when I first installed Ubuntu 10.04 it came up saying it couldn't find or configure the network manager (but i still had internet) and the battery was dead or dying. I went down to 9.10 to see if it might be my system instead of the OS. now im upgrading to 10.04 again and so far *knocks on wood* no problems in the install.

---

### Post by BaroqueBloke on 2010-05-12
Huzzah!  Found a fix for the scroll bar.  Still no multi touch but at least its a start.
The poster linked back to a post somewhere on the forum.  Anyways heres what I found:

"1. Open a terminal and open up the editor by  typing: 

 [I]sudo gedit /etc/modprobe.d/psmouse.conf  [I]

 and add this line to the file:[/I][/I]

*options psmouse proto=imps*
[I]
[/I]2[I]. Then  select  File  -- > Save  (saving the file in gedit)
[/I]
3. Reboot."


Hope this helps.

---

### Post by Rhemat on 2010-06-10
I've been thinking about getting the Acer Aspire One 532H (since we have them where I work now), but considering a lot of the problems I'm reading about it, I'm wondering if I still should.
Are there any other NetBooks/Laptops I should consider instead?  I've been looking for something that has great battery life (at least 4 hours of ACTUAL use, not advertised battery life), two USB ports, and a good keyboard (if a laptop, preferably an optical drive too).
I'm at least hopeful that the WiFi seems to work out of the box, but the other issues keep me away.
Thanks in advance.

---

### Post by BaroqueBloke on 2010-06-10
> **Rhemat said:**
> I've been thinking about getting the Acer Aspire One 532H (since we have them where I work now), but considering a lot of the problems I'm reading about it, I'm wondering if I still should.
Are there any other NetBooks/Laptops I should consider instead?  I've been looking for something that has great battery life (at least 4 hours of ACTUAL use, not advertised battery life), two USB ports, and a good keyboard (if a laptop, preferably an optical drive too).
I'm at least hopeful that the WiFi seems to work out of the box, but the other issues keep me away.
Thanks in advance.

I wouldn't let the issues you've seen above deter you if youre looking for an affordable netbook.  At this point I have only one issue and that is the card reader not working.  Aside from that everything works!  I am running 10.04 UNE (gnome environment, not netbook one).  With 10.04 I had to follow what I posted previously to get the scroll bar working.  9.10 scroll bar function works out-of-box.  The 532h I have came with a 6 cell battery and I routinely get 5-7 hours of battery depending on screen brightness and the amount of youtube and music I play.

All that being said my knowledge of other netbooks is nonexistent.  I have used Ubuntu on a first gen Macbook and had some issues with suspend on lid close and it's battery life was on par (2.5 hours at best).  The new Macbooks are rated at around 10 hours but so are a lot of the newer high end net books, for less than half the price.  

Bottom line:  get what you want and try different things.  I'm more than satisfied with my 532h.  I don't do anything else but email, internet, music, and note taking with it and it performs beautifully for all.  

Good luck and let know you're results!

---

### Post by Rhemat on 2010-06-13
Thanks for the reply BaroqueBloke, but I have one last question; I don't have to compile the kernel myself for WiFi to work, or use NDISWrapper?  I've never compiled any kernel before, though I have wanted to try.  Also, I've tried to use NDISWrapper for WiFi with my laptop (it has a Broadcom wireless NIC in it, which works with BroadCom's restricted drivers), and I was never able to get NDISWrapper working.
Thanks in advance.

---

### Post by BaroqueBloke on 2010-06-14
> **Rhemat said:**
> Thanks for the reply BaroqueBloke, but I have one last question; I don't have to compile the kernel myself for WiFi to work, or use NDISWrapper?  I've never compiled any kernel before, though I have wanted to try.  Also, I've tried to use NDISWrapper for WiFi with my laptop (it has a Broadcom wireless NIC in it, which works with BroadCom's restricted drivers), and I was never able to get NDISWrapper working.
Thanks in advance.

I have used both 9.10 and 10.04 on the acer and wireless has worked 100% every time.  

The only time ive run into trouble is when trying to install from the minimal cd (in attempts at a minimal installation:  just email, internet) Long story  short I never got the minimal cd install to work with wireless from the get go.  

So, if you stick with 9.10 or 10.04 desktop/netbook you will have no issues.  

Enjoy!

---

### Post by elpraga on 2010-08-06
Hello, 
I am thinking about buying this netbook too. But I have a question. What about the graphics chipset? Does it play flash in fullscreen well?? (to be really able to watch it?) 

Has anybody tried to attach external monitor?

Thanks for replies..

Tomas

---

### Post by yahmorah25 on 2010-11-05
i have had 10.04 on my netbook 532h for some time now the only problem now with it is the all in one card reader every thing else works my wifi goes out some times but thats just because i am not neer the wifi spot all together this is a good little computer to get i cant wait till they have a fix for the card reader tho thats the only thing now but its worth getting 8 hours on a computer with out charging it what oh yeah the vga works too i hook up my computer all the time to a bigger ctr monitor or flat tv to watch the new movies with my woman and her family all the time

---

