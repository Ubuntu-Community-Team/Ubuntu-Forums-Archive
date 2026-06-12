---
title: "MSN Messenger on Ubuntu 8.10"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by totallyclueless on 2009-04-04
I really don't know much about computers 
but after doing a bit of research 
apparently, it is possible to get msn 2008 or 2009:
[http://www.wine-reviews.net/wine-reviews/microsoft/msn-messenger-2008-and-2009-on-linux-with-wine.html](http://www.wine-reviews.net/wine-reviews/microsoft/msn-messenger-2008-and-2009-on-linux-with-wine.html)


First I found installed Wine 1.0.1:

[http://ubuntuexperiment.wordpress.com/2008/11/09/installing-wine-on-ubuntu-810/](http://ubuntuexperiment.wordpress.com/2008/11/09/installing-wine-on-ubuntu-810/)

After that, I installed cabextract through my Synaptic Package Manager
and then I got winetricks by:

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)
(then i just typed sh winetricks corefonts flash gecko gdiplus msls31 msxml3 riched20 riched30 tahoma)

Then I got downloaded the "Install_{508CE775-4BA4-4748-82DF-FE28DA9F03B0}.msi" from:

[http://cid-261d8fb2a992b4e1.skydrive.live.com/self.aspx/Geek|4s%20Anatomy/Windows%20Live%20Installers/Install_%7B508CE775-4BA4-4748-82DF-FE28DA9F03B0%7D.msi?sa=274924275](http://cid-261d8fb2a992b4e1.skydrive.live.com/self.aspx/Geek|4s%20Anatomy/Windows%20Live%20Installers/Install_%7B508CE775-4BA4-4748-82DF-FE28DA9F03B0%7D.msi?sa=274924275)

Finally, I went to my terminal and did the rest but it wouldn't work!
All I got was:

~$ msiexec /i Install_{508CE775-4BA4-4748-82DF-FE28DA9F03B0}.msi
err:msi:copy_package_to_temp failed to copy package L"Install_{508CE775-4BA4-4748-82DF-FE28DA9F03B0}.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"Install_{508CE775-4BA4-4748-82DF-FE28DA9F03B0}.msi"
~$ 


I dont know anything that's going on right now 
What do i do to fix this? It's worked for other ppl..

---

### Post by leandromartinez98 on 2009-04-04
You actually really want to install MSN Messenger? With Pidgin (installed by default and available at applications -> internet) you can use your msn account.

---

### Post by SunnyRabbiera on 2009-04-04
If it gets too much of a pain, amsn is worth a try.

---

### Post by Ben Crisford on 2009-04-04
If you want MSN so much there is a free linux version called aMsn which is *incredibly* similar.

If you want to download it goto:
***Applications> Add/Remove Programs> Search for aMsn***

---

### Post by totallyclueless on 2009-04-04
I don't want to be stubborn, but I just can't do without MSN :(
I never knew ubuntu couldn't install it.
I still want to stick with the system since it's a lot better then Windows
but, its not the same without msn 
helppp

---

### Post by berdux on 2009-05-16
i would also realy like to install windows live messenger 2009 in ubuntu. it has sooo many more features that every msn client for ubuntu do not have... i'm stuck with amsn for now, it isn't even close though to msn live 2009

---

### Post by NTpspE on 2009-05-16
Personally the new MSN live 09 annoyed me when they changed all the buddy list and layout e.c.t.

If you have multiple accounts, for example, maybe one or two msn's, a gmail, Irc, and aim, or possibly facebook too, you can have all these up in pidgin at once, and it supports different dp's for each, and works brilliantly. 
i reccomend that :D

---

### Post by sardamil on 2009-05-16
I've tried kopete, pidgin and now I'm using aMSN. If you really need MSN, I think this is the tool to use. It's got the look&feel of MSN, but without the nasty ads. I suggest you try this, before going through loads of trouble to try to make msn work.

---

### Post by imon9 on 2009-05-16
or you can give "emesene" a go, it is a good alternative client to WLM

---

### Post by noice742 on 2009-05-16
> **imon9 said:**
> or you can give "emesene" a go, it is a good alternative client to WLM

this is the one i am using. i am very satisfied with it.

---

### Post by howefield on 2009-05-16
> **totallyclueless said:**
> First I found installed Wine 1.0.1

The howto referenced is talking about a newer version of wine than 1.0.1, you need Wine 1.1.14

---

### Post by berdux on 2009-05-16
with emesene you cannot start a webcam session, and whatever i do i cannot send or recieve files. with amsn webcam works, and i can send and recieve files bur at VERY low speeds (lower than dial up connection).. it looks like old msn, but does not have the new features of msn 2009...
with pidgin and copete you cannot have even the custom emoticons feature..

amsn is the closest to msn but does not look nice at all.. also something happens (that does not happen with emesene and other messengers), when i type on a contact something and an other contact comes online it suddently stops typing in the window, though it is stil focused, and i have to click somewhere else (e.g. desktop or an other window) and then back on it so i can continue to type. i even disabled the notifications but still when someone comes online i have to go through all this..

(i've been using emesene for 3 months and amsn for about 2 weeks..)

i reeeaaaly want to go throuhg any trouble to find a way to install windows live messenger 2009 on ubuntu :)

---

### Post by Sef on 2009-05-17
[MSN]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=127") does not seem to work well on GNU/Linux with WINE.

---

### Post by thesoul1987 on 2009-05-17
thanxxxxxxx dude

---

