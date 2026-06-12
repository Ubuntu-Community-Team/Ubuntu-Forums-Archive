---
title: "acx111"
date: 2004-11-06
forum: Hardware &amp; Laptops
---

### Post by elempoimen on 2004-11-06
I'm trying to get at TI acx111 chipset PCMCIA card working on my Thinkpad T23.  (USR5410).  Upon initial bootup, Ubuntu doesn't acknowledge the card as an interface, although it does detect it.  If I remove and reinsert the card, it is recognized as wlan0, but when I ifup it, I end up with a series of errors.  (Sorry, can't post them right now...in XP /me ducks).  Any ideas on this?  Basically, the light is on but it doesn't connect with the AP, even after I enter the ESSID.  

I had a similar problem on MEPIS, but it had a KDE config app in which I could enter the frequency of the card.  I entered 2.4 GHz, and it worked perfectly.  I suspect it may be a similar problem here.  I am using the updated firmware--the latest--from USR.  The initial firmware didn't work, so no biggie there.

Is there a way I can stipulate that frequency?  Or are there any other ideas?

---

### Post by daniels on 2004-11-07
I need to do 'iwconfig wlan0 key off' on my ACX111 to get it working, and sometimes a nickname as well.  So, try 'iwconfig wlan0 nick computername key off'.

---

### Post by Nerque on 2004-11-19
Hello,

I am new in the Linux systems and I have problems with the USR5410 pcmcia card.

I have chosen the Ubunto OS. It looks good, but I don't know how to install the drivers for the USR5410.

I have tried to use the ndiswrapper, but I don't know if I have done right. I have followed the directions showed at the forum, but I don't get any message from the system when I write the commands.

I don't know if I have the correct drivers from the USR. I have used the USR11G.inf file from the windows/inf directory.

Can you show me how you do it?

Thanks

---

### Post by crovax123 on 2004-12-17
i got it working under linux suse whit driverloader 
it also contains a debian package so i gues you can use the drivers to 
i have some problems getting the connection at 100% where i always have 100% under windows xp but it works whit little to no slowdowns for internet ( for games i use my ethernet port so i dont have any problems whit it )

the drivers can be found on the [http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/) website
it uses the windows drivers:-(

---

