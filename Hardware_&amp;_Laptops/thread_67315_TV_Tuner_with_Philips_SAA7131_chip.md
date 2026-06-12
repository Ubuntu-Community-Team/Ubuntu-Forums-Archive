---
title: "TV Tuner with Philips SAA7131 chip"
date: 2005-09-19
forum: Hardware &amp; Laptops
---

### Post by puterfixer on 2005-09-19
Hello,

I have a [KWorld V-Stream Studio TV Terminator](http://www.kworldcomputer.com/product/Studio-TV-Terminator/Studio-TV-Terminator.html) tuner, model VS-LTV7131RF, featuring a Philips SAA7131 chip. I've read forums and tutorials trying to get it to work in Hoary, but haven't had much luck. **lspci** finds it as *0000:00:0c.0 Multimedia controller: Philips Semiconductors SAA7133 Audio+video broadcast decoder (rev d0)*, and the saa7134 module gets loaded automatically. However, tvtime can't use it.

After a bit of digging, I understood that the module needs to be told which card model is it, since the card lacks the EEPROM and is seen as UNKNOWN/GENERIC. I have found two lists of cards ([1](http://www.physorg.com/news4314.html) and [2](http://xawdecode.sourceforge.net/aideUS/htmlpage/TVCardall.htm)), but my KWorld model is not on any of them. I've tried several of the other cards without success. I used the **tuner=5** option, for Philips PAL B/G, varying the **card=** parameter, unloading the module and reloading it each time. **tvtime** reported "no signal" for each, and **tvtime-scanner** couldn't tune in.

The Windows driver lists the EB001000-EB0017FF address range under card's resources, if that helps.

Am I doing something wrong here? Has anyone else managed to get this card to work? Could someone instruct me which card should I use from the list, or how to proceed to get the card to work?

Thanks in advance,

puterfixer

---

### Post by chk9 on 2006-04-12
I have the same TV card!
Has anybody been able to get this to work?

---

### Post by hackataca on 2006-06-12
Hi,

I've Kworld 220dvbt in dapper; it works with:

rmmod saa7134_alsa
rmmod saa7134
modprobe saa3134 card=81

Tuner model is tda8290+75a

:idea:

---

### Post by nice hat on 2006-06-15
i have the same card and this is my first time using linux...so i have no idea on were to start inorder to get it to work...i have a few diferent tv apps but none of the recignise the card??it whould rely help if some one could give me a few pointers on what to do

---

### Post by puterfixer on 2006-06-18
Hoary doesn't support this model of card. I found out that the card IS supported in more recent builds of video4linux, but I would need to download the sources from cvs and build them locally. Far too complicated for me. Hopefully a new build that includes support for this card has been compiled and included in Dapper.

Video4Linux discussion list: [http://www.redhat.com/mailman/listinfo/video4linux-list](http://www.redhat.com/mailman/listinfo/video4linux-list)

---

### Post by bbya2064 on 2006-09-03
I got myne to work!
Downside: This has to be done everytime the computer is started.:frown: 

When computer starts up go into terminal:

Sudo rmmod saa7134_alsa

Sudo rmmod saa7134

Sudo modprobe saa7134 saa7134 card=65 tuner=54

and open TvTime, etc. and it works!

=D> :biggrin:

---

### Post by marco007 on 2006-09-22
# nano /etc/modprobe.d/options
  options saa7134 card=65 tuner=54
and thats it :)
anyone get lirc to work?
sorry my bad english :D

---

### Post by Alien.col on 2008-03-10
I've got the Kworld TV Tuner analog PCI card Model No.:VS-PVR 7131SE that also uses the saa7131 chip. Has anybody got this to work at all in Gutsy????? I've been trying for a while now but can't get any info on how to get this to work.

Thanks

PS this is the product's URL [http://www.kworld.com.tw/product_overview.aspx?P_ID=11](http://www.kworld.com.tw/product_overview.aspx?P_ID=11)

---

