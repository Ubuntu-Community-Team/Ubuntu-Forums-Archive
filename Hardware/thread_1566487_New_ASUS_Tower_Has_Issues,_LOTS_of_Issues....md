---
title: "New ASUS Tower Has Issues, LOTS of Issues..."
date: 2010-09-02
forum: Hardware
---

### Post by Lucradia on 2010-09-02
1. If you use ubuntu in VirtualBox, and use bridged adapter, ubuntu can't get network.

2. If you switch from bridged to NAT, Ubuntu will crash VirtualBox, and the system will force a blue screen.

Above are in a windows 7 host.

3. Wubi / ubuntu can boot, but after the initial bootsplash screen, ubuntu fails to send any graphic signals to the monitor by either the ATI 5750 card (DVI nor VGA work) nor the Internal on-board graphics of my motherboard (VGA.)

Motherboard Chipset: AMD 780G (Cannot find motherboard model on ASUS website.)

Desktop Model: CG1330-05

---

### Post by Lucradia on 2010-09-02
The processor is a Phenom II X6 1035T.

---

### Post by Lucradia on 2010-09-03
bump here, there, and everywhere.

---

### Post by Lucradia on 2010-09-04
Bump to the left and to the right.

---

### Post by Lucradia on 2010-09-05
Bumping on a Sunday Night.

---

### Post by em3raldxiii on 2010-09-05
These are very peculiar issues!  First, just to be clear, you are saying that Windows 7 runs perfectly stably?

Second, when you say "tower" are you referring only to the chassis, or to all the guts inside?  The reason I am asking this is to narrow down the problem.  If you are referring to all the hardware contained within the tower, then we may need to isolate specific components to see what is at issue.

Third, if you are only referring to the chassis, then are we referring to a custom system that you or someone else assembled on your behalf?  If so, then consider checking ground-points between the motherboard, power supply, and chassis.

** also, have you attempted to boot the system with the Ubuntu CD?  I am curious to know if it's a VBox/Wubi problem as opposed to an Ubuntu problem.

---

### Post by Lucradia on 2010-09-05
The problem is with the graphics, I know this because ubuntu boots perfectly fine, it's just no signals are sent to the monitor (Via DVI nor VGA.)

it's a tower, pre-built from ASUS, its model is on the Opening Post.

Reason why I say ubuntu "boots" fine is that ubuntu connects to the Internet fine (as shown by my cable modem blinking blue instead of orange.)

---

### Post by cascade9 on 2010-09-06
I'd try removing the 5750, and seeing if the onboard video is working. 

Its possible that you could just move the VGA/DVI connector from the card to the onboard and have it work as well.

---

### Post by Lucradia on 2010-09-06
> **cascade9 said:**
> Its possible that you could just move the VGA/DVI connector from the card to the onboard and have it work as well.

Opening Post says on-board VGA doesn't work. I'm not going to remove the ATI Card, sorry.

---

### Post by mastablasta on 2010-09-06
basically what you are saying is that Ubuntu doens't work in virtual environmnet within win7? and you haven't tried removing the ATI card or actually installing the system to the disk rather than running some virtualized version of it (Wubi, Vbox)?
 
Because propper install is something else. For example i had issues with Gnome crashing in Live CD session due to graphics card i believe, however after installing it on disk it was stable and never crashed so far.

---

### Post by Lucradia on 2010-09-06
> **mastablasta said:**
> basically what you are saying is that Ubuntu doens't work in virtual environmnet within win7? and you haven't tried removing the ATI card or actually installing the system to the disk rather than running some virtualized version of it (Wubi, Vbox)?
 
Because propper install is something else. For example i had issues with Gnome crashing in Live CD session due to graphics card i believe, however after installing it on disk it was stable and never crashed so far.

Live CD didn't work (neither on on-board nor ATI Card). Looks like this machine isn't linux capable yet. :(

I even changed the primary graphiocs device via BIOS, set it to plug and play (which wasn't on before) nothing.

---

### Post by Lucradia on 2010-09-06
Btw, the BIOS Flasher says my motherboard is

M4A78LT-M (CG1330)

---

### Post by cascade9 on 2010-09-07
> **Lucradia said:**
> Opening Post says on-board VGA doesn't work. I'm not going to remove the ATI Card, sorry.

OK. I reckon that removing the ATI 5750 would help things, but not everyone likes playing with hardware.  

> **Lucradia said:**
> Btw, the BIOS Flasher says my motherboard is

M4A78LT-M (CG1330)

Ohh, goodie, now Asus is playing that game it started with building 'cut down' marked asus motherboards in corporate machines......then having no ifo at all about said motherbaord models in the asus website. Tsk, tsk, asus.

---

### Post by Lucradia on 2010-09-07
> **cascade9 said:**
> Ohh, goodie, now Asus is playing that game it started with building 'cut down' marked asus motherboards in corporate machines......then having no ifo at all about said motherbaord models in the asus website. Tsk, tsk, asus.

I also searched around and noticed that this motherboard is actually not supposed to be able to handle the Phenom X6.

---

### Post by cascade9 on 2010-09-07
Much to my suprise, I actually found a page from asus with that board- 

[http://www.asus.com/product.aspx?p_id=exjl00uovtjadqxr](http://www.asus.com/product.aspx?p_id=exjl00uovtjadqxr)

I *think* that last time I just tried searchign the 'global' asus site for that model motherboard, this time I used a search engine...when I tried the 'translate this page' link it was trying to translate from czech, so maybe that motherboard is listed only in europe? I dont know.....

Anyway, it does support the Phenom II X6...but only 95watt TDP models (95watts max for any CPU). Thats why its got a 1035T. There should be 95watt 1055Ts at some point, but I'm yet to see one, so far all the 1055Ts are 125watts AFAIK.

---

### Post by Lucradia on 2010-09-07
> **cascade9 said:**
> Much to my suprise, I actually found a page from asus with that board- 

[http://www.asus.com/product.aspx?p_id=exjl00uovtjadqxr](http://www.asus.com/product.aspx?p_id=exjl00uovtjadqxr)

I *think* that last time I just tried searchign the 'global' asus site for that model motherboard, this time I used a search engine...when I tried the 'translate this page' link it was trying to translate from czech, so maybe that motherboard is listed only in europe? I dont know.....

Anyway, it does support the Phenom II X6...but only 95watt TDP models (95watts max for any CPU). Thats why its got a 1035T. There should be 95watt 1055Ts at some point, but I'm yet to see one, so far all the 1055Ts are 125watts AFAIK.

The link you gave redirects here: [http://www.asus.com/index.aspx?aspxerrorpath=/product.aspx](http://www.asus.com/index.aspx?aspxerrorpath=/product.aspx)

---

### Post by cascade9 on 2010-09-09
> **Lucradia said:**
> The link you gave redirects here: [http://www.asus.com/index.aspx?aspxerrorpath=/product.aspx](http://www.asus.com/index.aspx?aspxerrorpath=/product.aspx)

I hate the way that the asus site has been doing that. :| 

I found it by searching "M4A78LT-M site:www.asus.com" so I'd guess that the same search should bring you to the same page I found.

---

### Post by Lucradia on 2010-09-10
> **cascade9 said:**
> I hate the way that the asus site has been doing that. :| 

I found it by searching "M4A78LT-M site:www.asus.com" so I'd guess that the same search should bring you to the same page I found.

Yeah, I see it, but it doesn't help much with my problem. For exa, my shared video memory exceeds what is listed on the LE version of the motherboard. (over 3 GB Shared, even though the motherboard says it can only handle 1 GB.)

---

### Post by cascade9 on 2010-09-10
WTF? 

3GB shared? 

1st off, why? You wont get any advantage over a far lesser amount of shared RAM. 

2nd- Shared RAM when using a 5770? You're not running in 'hybrid crossfire' are you? That could explain your issue....

---

### Post by Lucradia on 2010-09-10
> **cascade9 said:**
> 2nd- Shared RAM when using a 5770? You're not running in 'hybrid crossfire' are you? That could explain your issue....

Well, the ATI CCC doesn't have any CrossFire setting I believe, nor the BIOS itself, so I wouldn't know.

But when I first booted this computer, the onboard graphics showed as disabled (which I re-enabled somehow when I told the BIOS to put Plug / Play OS to be On.)

Even if it somehow did have a crossfire setting, I wouldn't know how to turn it off.

And btw, I've booted ubuntu before on other computers with Plug / Play On, so that wouldn't be the issue either.

```
  Total available graphics memory 4083 MB 
        Dedicated graphics memory 1024 MB << (ATI 5750)
        Dedicated system memory 0 MB 
        Shared system memory 3059 MB
```

---

### Post by Lucradia on 2010-09-13
Looks like the email I sent to ASUS over 72 hours ago (they said I should get a reply within 72 hours) won't be replied. Guess I can't turn off cross-fire unless I invest in a new nvidia card, which I hope to get in a few months.

---

### Post by cascade9 on 2010-09-15
> **Lucradia said:**
> Looks like the email I sent to ASUS over 72 hours ago (they said I should get a reply within 72 hours) won't be replied. Guess I can't turn off cross-fire unless I invest in a new nvidia card, which I hope to get in a few months.

I'm not sure that you are running in hybrid crossfire. 

Did asus actually answer your email?

---

### Post by Lucradia on 2010-09-16
> **cascade9 said:**
> I'm not sure that you are running in hybrid crossfire. 

Did asus actually answer your email?

Yes, but they said I have to call their third-party motherboard manufacturer, as ASUS no longer does support for them. I don't like phone tagging or calling, so I'll have to leave it at that. if you know another way that Ubuntu can boot properly without removing the cards, I'd like to hear it.

---

### Post by cascade9 on 2010-09-16
> **Lucradia said:**
> Yes, but they said I have to call their third-party motherboard manufacturer, as ASUS no longer does support for them. 

o.O 

OK, thats it, I'm avoiding asus as much as possible from now on......

Sorry, I dont know anything else that could help. Not saying there isnt any other way, but I cant think of anything now :(

---

### Post by Lucradia on 2010-09-16
If anyone else doesn't believe that ASUS Said that to me...

> Hello Sir/Madam

Our desktop units are handled by a third party company now. You will want to contact them, they will make sure you are taken care of. Their number is 1-877-339-2787.

If you need further assistance, please contact
Technical Support at 812-282-ASUS option 2
M-F 8:30 AM - 12:00 AM EST
Sat-Sun 9:00 AM - 6:00 PM

Thank you,
Krisenda
ASUS Tech Support/L2 Support
Phone : 812-282-2787
[http://livesupport.asus.com](http://livesupport.asus.com)

---

### Post by cascade9 on 2010-09-16
Moving the support on "desktop units" to a 'third party'  is not quite the same as a "third-party motherboard manufacturer", but still....

BTW, I believed you, I've dealt with asus before, sometimes they can be....er....not very nice.

---

### Post by Lucradia on 2010-09-16
Hey guess what, Fedora 13 works. However, it can't resize my SATA HDD partitions (should've done it in windows first :( ) so I ended up having Fedora destroy the windows OS partition because it errored when it tried to resize.

Also, the 5750 ATI Radeon HD I have inside is not supported by AMD on Fedora yet... so no 3D Acceleration for a while. (Installing the ATI Catalyst Drivers from AMD causes the entire system to slow down, and windows lag a lot.)

network, Monitor, Resolution, Audio, mouse, USB, CD-RW / DVD-RW, etc. are all supported, just not 3D on my 5750 :(

Also, installing the ATI Catalyst causes major issues (Since both the onboard and HD 5750 are detected, 5750 is disabeld because it is "Unknown Adapter.)

---

### Post by cascade9 on 2010-09-16
Excelent....well, that you got some distro to work, not on borking windows. But these things happen. ;) 

BTW, silly me, I should have said/asked this ages ago....Have you tried turning off the onboard video in the BIOS?

---

### Post by Lucradia on 2010-09-17
> **cascade9 said:**
> BTW, silly me, I should have said/asked this ages ago....Have you tried turning off the onboard video in the BIOS?

it's not possible. The BIOS Settings to deal with graphics does this instead...

PCI/IGFX/BLAH/BLAH

and then has three to four other settings in a drop down that put it in different orders. That's all I can do with the graphics.

I tried installing the 1.8 Catalyst (Which I didn't know didn't support 5750, I guess? On the new kernel?) via rpm fusion, via [this thread...]("http://forums.fedoraforum.org/showthread.php?t=155503")

but it ended up causign Fedora to boot like Ubuntu, where it would constantly turn the monitor off and on and show DVI NO SIGNAL when it turned on, and suddenly turn back off every few minutes. So now I'm back on Windows.

---

