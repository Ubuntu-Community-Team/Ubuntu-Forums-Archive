---
title: "do you have a recommendation for a socket AM-2 motherboard?"
date: 2007-04-13
forum: Hardware &amp; Laptops
---

### Post by jcpeart on 2007-04-13
With the recent price drop of the AMD processors, I was thinking about building a new cheap computer.  Does anyone have a recommendation for a socket AM2 motherboard, preferrably with onboard audio and video that will work well with ubuntu?

Thanks.

Jim

---

### Post by thelinuxguy on 2007-04-14
> **jcpeart said:**
> With the recent price drop of the AMD processors, I was thinking about building a new cheap computer.  Does anyone have a recommendation for a socket AM2 motherboard, preferrably with onboard audio and video that will work well with ubuntu?

Thanks.

Jim

I have **ASUS M2NPV-MX** with nVidia 6150 onboard graphics and onboard sound, LAN etc. Combined with an AMD 3600+ Socket AM-2 and 1 GB Transcend DDR2 533, I have had no problems whatsoever with my system being compatible with Ubuntu. Dapper worked fine and Edgy is doing great. The main concern, graphic card drivers, installed without a hitch from the Edgy repositories. On Dapper, I  had to install it from the motherboard CD. Took some time but worked fine. Haven't tried out Feisty yet. I use the 32 bit version of the OSes since 64 bit support needs some more work.

However, on every system boot, an error message pops up saying something like "Warning: CPU has been changed. Press F1 to continue". This is a known problem with this mobo and even after trying out the jumper settings and other things mentioned on many forums, I didn't have much success. But this is not related to any OS and as far as Ubuntu is concerned, my system is doing great.

Ignoring the CPU related error message, I definitely recommend this mobo for Ubuntu compatibility.

---

### Post by jcpeart on 2007-04-18
After a lot of research and getting advice, I have opted for the following:

 GIGABYTE GA-M61PM-S2 Socket AM2 NVIDIA GeForce 6100 Micro ATX AMD Motherboard

Once it is built, I will post how it worked.

---

### Post by rickggreen on 2007-04-18
I'm also using a ASUS M2NPV-VM, 4200 X2 with Kingmax 800 DDR2 (2 x 512). I through in an old ASUS video/fm card (7133/7135 can't remember model, but Feisty found it), 2 DVD burners  LG GSA-H10N and GCC-4520-, LS-120 for a floppy/120 meg ZIP. Seagate ST 3160023A ( hda), Seagate ST 380013AS (sda), Flash Reader 02, Logitech wireless keyboard and mouse, Wingman Force Feedback  3D joystick.
 Running both  CRT and TV.II have  not had any problems at all, not even the one mentioned in the earlier post. Took some time to get the video to work the way I wanted (clone to TV), I would recommend to anybody to read the nVidia readme with the 9755 drivers before installing, it would save a lot of video problem posts.
I had built the machine to install VISTA, decided to try LINUX while waiting, installed for about 4-5 hrs, then went back to Ubuntu, been a very happy camper since.. I switched 5 people away from M$ after they saw my machine running with Beryl.and  vMware .:popcorn: :popcorn:

---

### Post by Hercules on 2007-04-18
rickggreen, any problems with the LAN controller, or is it working ok?

---

### Post by rickggreen on 2007-04-18
no problems at all, only problems I have had were all of my own doing. (ie not reading first), there is too much information out there (net and forums)  The nVidia issue is the biggest one to me. I spent 21/2 hrs last night reading the whole  nVidia readme from their site, fixed what I wanted to do with my multi monitors.in a couple of minutes.

---

### Post by Hercules on 2007-04-21
thanks rickgreen

so you've definitely connected up the computer via a LAN?

the reason i ask is that i'm about to buy a new motherboard, and like the sound of the ASUS M2NPV-VM, but have read posts in various forums from people saying they have not been able to get the LAN controller working

apologies for asking the question again, but i'm keen to get moving with my new PC, and have been getting a bit frustrated trying to identify a motherboard that will definitely work!

---

### Post by rickggreen on 2007-04-23
I have had no problems with this board, it is a great low cost board. I am running a 4200 X2 with DDR2 800 ram, it is fast, and the built im video is quite amizing. I was building the machine for VISTA, because it could use the areo interface, but then I installed Ubuntu.. Just make sure tou have the latest bios and all should be fine

---

### Post by Healey on 2007-08-02
> **jcpeart said:**
> After a lot of research and getting advice, I have opted for the following:

 GIGABYTE GA-M61PM-S2 Socket AM2 NVIDIA GeForce 6100 Micro ATX AMD Motherboard

Once it is built, I will post how it worked.



Hi

Reference your reply  - GIGABYTE GA-M61PM-S2 Socket AM2 NVIDIA GeForce 6100 Micro ATX AMD Motherboard

I just wondered if you built this system and if if worked well with Ubuntu Linux

I am thinking about buying it myself 

Regards

Healey

---

### Post by Wiglet on 2007-10-25
I am also thinking of purchasing a Gigabyte GA-M61PM-S2 to build a system on and run Ubuntu. Did you have any problems with it?

---

### Post by Healey on 2007-10-25
Hi

I ended up not getting that motherboard

The one I bought was Gigabyte GA-M61SME-S2 which has the Nvidia 6100/n force 405 on board.

I am not a hardware expert but I think it is very similar to the one discussed before.

Anyway it worked very well under Feisty (needed to edit xorg.conf to get my widescreen working) Apart from that it all worked very well.

I have just tried gutsy Gibbon but I will be going back to fiesty as it is far more stable

Hope it helps

Healey

---

