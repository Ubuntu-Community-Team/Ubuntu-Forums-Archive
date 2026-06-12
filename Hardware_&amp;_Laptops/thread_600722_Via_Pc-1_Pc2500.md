---
title: "Via Pc-1 Pc2500"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by RMorris78 on 2007-11-02
i was wondering if anyone has any experience with this motherboard/chipset running ubuntu. it seems to be all via components so i think itll work pretty well since most via chipsets i have worked with have done alright.

[http://www.clubit.com/product_detail.cfm?itemno=CA4842001](http://www.clubit.com/product_detail.cfm?itemno=CA4842001)

thanks, and wow its a good price

---

### Post by patobrocks on 2007-12-12
Hey RMorris78,

Have you had any luck with the Via set-up?

I am debating about buying the $200 Everex, or going the Clubit way and building a low budget box.  I have never built a computer or used any Linux distro, but after buying a laptop with Vista, last month, I am desperate.

I don't have a clue what I am doing, but hey...

After XMAS, I plan to do something, if the Vista doesn't put me on suicide watch.

Pat

---

### Post by RMorris78 on 2008-01-02
after some research, ive concluded that it should work just fine.  since gOS is based on ubuntu, i dont forsee there being many problems running it.  you can pick up a gig of PC5300 for about 30, and i have a sata hdd and dvd burner laying around that i can use.  i am looking into getting this case for it

[http://www.svc.com/ycc-s27.html](http://www.svc.com/ycc-s27.html)

im about to order it tonight, ill let you know how it goes

---

### Post by dbellva on 2008-01-02
I have installed Ubuntu 7.10 on the VIA pc2500 board and it worked fine with only one small problem in that the video install ended with a default VESA driver.  When researching the problem, I found suggestions to manually install the "OpenChrome" driver to support the video on this motherboard.  I have re-installed gOS at this time, but plan to return to straight Ubuntu later.

---

### Post by patobrocks on 2008-01-03
> **RMorris78 said:**
> after some research, ive concluded that it should work just fine.  since gOS is based on ubuntu, i dont forsee there being many problems running it.  you can pick up a gig of PC5300 for about 30, and i have a sata hdd and dvd burner laying around that i can use.  i am looking into getting this case for it

[http://www.svc.com/ycc-s27.html](http://www.svc.com/ycc-s27.html)

im about to order it tonight, ill let you know how it goes

Good and good luck.

Please keep us posted on your progress.  I bet a lot of people are interested, even if it is just to criticize.

I am also looking at the Zonbu laptop as an alternative.

The good news is that we have more choices these days, and our choices are cheaper.  Yes, cheaper, but more and more the computer is essential.  I am a full time online student.  My computer is vital and my data is irreplaceable, or at the very least, a major hassle to do the assignment aver again.

the Zonbu uses the same mother board and cpu.  Gee, it is built by Everex.

If Everex had a Linux laptop, well...

---

### Post by sauyeeluo on 2008-01-13
I recently purchased this board from clubit with 2 gigs of ram.

[B]
Install comments.[/B]
Painless. Everything works out of the box (for the most part).

For video, I used the openchrome driver from the ubuntu repos. After the install I was getting around 200fps give or take 10 percent.  Then ran the following command 'sudo dpkg-reconfigure -phigh xserver-xorg'

selected 'via' as the driver and then the screen resolutions. now, i get about 1000fps running glxgears. i also reduced my bit depth to '16' and i can get approximately 1500fps.  light 3d apps work fine like screensavers. anything graphically intensive will make the board angry. but then again, if your using this board i'd assume your not using it for cad work or gaming.

personally its a great value board.

---

### Post by Syke on 2008-01-14
> **patobrocks said:**
> If Everex had a Linux laptop, well...

Take a peek at what's coming very soon:

[http://www.everex.com/press/](http://www.everex.com/press/)

---

### Post by sboutwell on 2008-02-17
Could someone post the details on how they got the openchrome drivers working with this machine.  Love it but it keeps putting the VESA drivers in.  Tried just grabbing all of the openchrome from the Program manager but still seems to missing a setp.

Thanks in advance for the help.

---

