---
title: "Problems with AMD proprietary driver &amp; HD7770"
date: 2013-07-19
forum: Hardware
---

### Post by Mazate on 2013-07-19
I just switched back to linux  from windows.  That could be a whole post in and of itself but this  isn't the forum for it.  In any case, I bought an HD7770 that worked  brilliantly in windows.  Now that I'm in Linux I'm having a ton of  troubles with it.  

First off, when I first load the mint  installer, the fan on the video card goes 100% and stays there until the  OS is installed.  Then, it continues that way until I install the  proprietary driver.  Another issue I'm having which I have attributed to  the video card based on comments of others with the same problem is  that some of the icons in the tray in the bottom right corner don't  update at all.  To check if there are any updates to mint that I have to  download, I have to move my mouse over the icon in order to see if  there is anything available. There are other icons as well that should  notify me of certain things but don't.

Yet another issue is in  games.  I've installed steam and I installed the game I thought would be  the least taxing on the video card which is team fortress classic.   While it is playable, there are a lot of errors in the video and lots of  hesitation, etc.  Counter-strike source is unplayable.  I tried loading  Kubuntu just to try it there and it wouldn't even let me play any of  the simple games such as supertuxcart and other simple such games.  The  games would load but the screen was black.

There are other things  but these are the highlights.  This card plays some fairly advanced  games in windows but clearly the drivers aren't up to par in linux.   I've never been a fan of MS before but lately with all that has been in  the news, it was the straw that broke the camel's back and I'm back with  linux to stay.

Anyway, the OS works fine for the most  part, its just the games that are mainly causing the problems.  The fan  on the card even makes some weird noises at times.  However, the OS is  usable and I can live with that until a future time when, hopefully,  there are some good updates to the drivers.  If anyone else has had any  problems like this or knows how to improve on the situation, your advice  is most welcome.

---

### Post by Claus7 on 2013-07-19
Hello,

I own an ati myself, yet another model. My question is: how have you installed the proprietary driver? I would suggest you to use amd's website, and according to your architecture, install it from there.
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Since you have also a new card (newer than mine at least), newer versions of ubuntu will work better with your card.

Regards!

---

### Post by Mazate on 2013-07-19
Actually I'm using 13.04. I'm always afraid of installing the drivers from the ati site because I've read about too many people that have broken their Ubuntu install doing it that way. I'm sure it's because they didn't know what they were doing but neither do I. :)

---

### Post by Yellow Pasque on 2013-07-19
@Claus7: if you're going to advise people to manually install drivers from AMD, please have them follow a procedure that installs the dependencies and builds packages: [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

---

### Post by Mazate on 2013-07-19
Before I try this, is there any real advantage to doing this manually over installing the proprietary drivers using the Ubuntu repos?

---

### Post by Yellow Pasque on 2013-07-19
It's a newer version (fglrx-updates in Raring repo is Catalyst 13-1), latest stable is Cat 13-4.

You may even want to try Catalyst 13-6 beta, since that has official support for Ubuntu 13.04 (for whatever that's worth): [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL)

---

### Post by Mazate on 2013-07-19
Well, that made all the difference in the world.  I followed the instructions and installed 13-4.  All of my issues have disappeared and everything works perfectly.  Thanks for the assistance.

---

### Post by Claus7 on 2013-07-20
Hello,

> **Temüjin said:**
> @Claus7: if you're going to advise people to manually install drivers from AMD, please have them follow a procedure that installs the dependencies and builds packages: [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

mea culpa. I thought that the OP had already installed some driver manually, yet a proprietary one can be installed from software center as well which is entirely different than installing a driver from amd's site.  

> **Mazate said:**
> Well, that made all the difference in the world.  I followed the instructions and installed 13-4.  All of my issues have disappeared and everything works perfectly.  Thanks for the assistance.

Glad you have found out a solution!

Regards!

---

