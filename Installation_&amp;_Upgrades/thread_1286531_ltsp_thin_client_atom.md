---
title: "ltsp thin client atom"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by shashikant876 on 2009-10-09
I am using ubuntu 8.04 with thin clients the server is P4 machine and all thin clients are old P3 and celeron machine with bootrom.

Now for power saving purpose we are trying these new Atom with D945GCLF motherboard based machines but it seems there is a problem, the machine boots and the login screen comes but once i login there is only mouse cursor and blank screen.

I am unable to solve these problem

Please help me with this problem.

Thanx in advance

Regards
Shashikant

---

### Post by fnjordy on 2009-10-09
Try booting the Atom from a LiveCD first to see if it's all supported and functional with regular Ubuntu.  If that fails repeat using a 9.04 then a 9.10 beta LiveCD to see if you need to update the server.

---

### Post by AlexanderDGreat on 2009-10-11
Hi shashikant876,

Sorry for stepping in your thread, but can I ask a question? I can't find the answer anywhere. I'm a newbie.

If you say you have thin clients in your P3 and Celeron machines, it means they're NOT using their processors and memory, right?

So if you're using an Intel Atom now, does it mean it doesn't also use its processor, board, and RAM?

The reason I asked this is because I just bought an Intel Atom D945GCLF2 dual-core as a thin client. I'm even planning to buy more, but if it doesn't use its hardware, I'm afraid I'm wasting money!

Hoping for your enlightenment.

---

### Post by epsolon77 on 2009-10-12
> **AlexanderDGreat said:**
> Hi shashikant876,

Sorry for stepping in your thread, but can I ask a question? I can't find the answer anywhere. I'm a newbie.

If you say you have thin clients in your P3 and Celeron machines, it means they're NOT using their processors and memory, right?

So if you're using an Intel Atom now, does it mean it doesn't also use its processor, board, and RAM?

The reason I asked this is because I just bought an Intel Atom D945GCLF2 dual-core as a thin client. I'm even planning to buy more, but if it doesn't use its hardware, I'm afraid I'm wasting money!

Hoping for your enlightenment.

Some memory and processing power is used by the thin client, apperently with the option to run apps localally (I do not know how to accomplish this).  The reason to downsize to Atom processors is power savings, however I am pretty sure the Atom does not come as a dual core processor.

shashikant876-
    If you can run the liveCD on your thin client but boot still does not work, you may need to compile a boot rom for that hardware.  You'll need to edit the lts.conf file for the correct xserver settings and run ltsp-uptade-image

---

### Post by solitaire on 2009-10-12
> **epsolon77 said:**
> Some memory and processing power is used by the thin client, apperently with the option to run apps localally (I do not know how to accomplish this).  The reason to downsize to Atom processors is power savings, however I am pretty sure the Atom does not come as a dual core processor.

shashikant876-
    If you can run the liveCD on your thin client but boot still does not work, you may need to compile a boot rom for that hardware.  You'll need to edit the lts.conf file for the correct xserver settings and run ltsp-uptade-image

The Atom 330 is true dual core.
The Atom Z### & N### series are hyperthread (single core simulating 2 cores)
[http://en.wikipedia.org/wiki/Intel_Atom](http://en.wikipedia.org/wiki/Intel_Atom)

Also any LiveCD should work, Try the netbook (UMD?) .ISO

---

### Post by AlexanderDGreat on 2009-10-12
@epsolon7 - Hi, I found this, [www.ltsp.org/~sbalneav/LTSPManual.pdf](www.ltsp.org/~sbalneav/LTSPManual.pdf)

Do all configs in this manual pertain to lts.conf? Haven't read the whole thing yet, but it sure will be handy in the future.

I'm new to localapps but here's the link: [https://help.ubuntu.com/community/UbuntuLTSP/LTSPLocalAppsJaunty](https://help.ubuntu.com/community/UbuntuLTSP/LTSPLocalAppsJaunty)

---

### Post by AlexanderDGreat on 2009-10-12
Also found this if you want to configure your LTS.CONF File: [http://www.ltsp.org/twiki/bin/view/Ltsp/LtsConf](http://www.ltsp.org/twiki/bin/view/Ltsp/LtsConf)

---

### Post by epsolon77 on 2009-10-13
> **AlexanderDGreat said:**
> @epsolon7 - Hi, I found this, [www.ltsp.org/~sbalneav/LTSPManual.pdf](www.ltsp.org/~sbalneav/LTSPManual.pdf)

Do all configs in this manual pertain to lts.conf? Haven't read the whole thing yet, but it sure will be handy in the future.

I'm new to localapps but here's the link: [https://help.ubuntu.com/community/UbuntuLTSP/LTSPLocalAppsJaunty](https://help.ubuntu.com/community/UbuntuLTSP/LTSPLocalAppsJaunty)

That PDF is a great resource.  I found out that by defualt you will not find an lts.conf file anywhere, you must create it yourself.  Creating it in //var/lib/tftpboot/ltsp/i386/ will be added to your thin clients as they boot (no need to recompile the boot image), however creating the file in the /opt/ltsp/i386/etc directory requires an image update, but speeds the thin clients boot a little.  

That url you sent seems really good as well.  I am working on testing the custom boot creation.  Unfortunately this is a semi dead project for me since I have lots of other things required by friday, but I will let it run in the background and will post results.  Thanks for the research.  

Did you try booting the thin client with the liveCD?  I'm very curious!

Oh and another stupid comment, make sure your LTSP server has a gui that you can log in to.

---

### Post by epsolon77 on 2009-10-13
> **solitaire said:**
> The Atom 330 is true dual core.
The Atom Z### & N### series are hyperthread (single core simulating 2 cores)
[http://en.wikipedia.org/wiki/Intel_Atom](http://en.wikipedia.org/wiki/Intel_Atom)

Thank you for the update.  I've been a little out of the hardware market.  I am very glad to be corrected.

---

### Post by AlexanderDGreat on 2009-10-14
Hi epsolon, I will actually boot off a USB stick, because my thin client doesn't have a CD, but if usb doesn't work, I'll try LiveCD, nope I haven't tried it yet, I'll do it tomorrow in the office. Glad to help! Cheers.

---

### Post by epsolon77 on 2009-10-14
> **AlexanderDGreat said:**
> Hi epsolon, I will actually boot off a USB stick, because my thin client doesn't have a CD, but if usb doesn't work, I'll try LiveCD, nope I haven't tried it yet, I'll do it tomorrow in the office. Glad to help! Cheers.

Eh, liveCD or USB stick, shouldn't make a difference.  Just make sure that if the boot on your thin client doesn't work from USB, try the usb on another machine to make sure you boot is good.

---

### Post by AlexanderDGreat on 2009-10-14
Hey I just realized, your advice to boot from a LiveCD - you were talking to shashikant876, yet I'm the one answering. Pardon me coz I was asking a question on another thread, I got mixed up.

---

### Post by Nebutron on 2009-10-14
The 9.04 netbook remix may be a good option as mentioned in a previous post.  The reason being that it is optimized for the Atom processor.

---

### Post by epsolon77 on 2009-10-15
> **Nebutron said:**
> The 9.04 netbook remix may be a good option as mentioned in a previous post.  The reason being that it is optimized for the Atom processor.

Normally I would agree with you that the netbook remix would be a good idea, HOWEVER in this case we are specifically testing if the thin client hardware will boot with the kernel information LTSP will be providing.  The idea is to boot with the same version LTSP server is installed on.  So I have my server running on 9.04 so I want to test my clients with 9.04 live CD.

However if this does not work we want to find a way to send the netbook remix install to the thin clients.  It can be done, I've just never done it before.

---

