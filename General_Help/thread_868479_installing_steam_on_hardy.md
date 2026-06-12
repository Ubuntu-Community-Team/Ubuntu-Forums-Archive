---
title: "installing steam on hardy"
date: 2008-07-23
forum: General Help
---

### Post by ali999 on 2008-07-23
Hi

I was wondering if there is anyway of intalling steam on ubuntu so that I can play counter strike and other steam games. I have googled this enough to make me think that this may be possible but have unable to get any intsructions. Currently whenever I want to play counter strike or something I have to restart my computer and boot into windows...I'd rather not do this if I don't have to. Thanks in advance.

---

### Post by evets25 on 2008-07-23
Steam has a platinum rating with wine, which means it should work almost perfectly, see [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554") for more info on it.

---

### Post by ali999 on 2008-07-23
> **evets25 said:**
> Steam has a platinum rating with wine, which means it should work almost perfectly, see [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554") for more info on it.

thanks...i'll try that

---

### Post by ali999 on 2008-07-25
hey...i installed steam through wine and everything seems to work perfectly until I actually load up counter strike. Once I connect to a server, the gameplay turns extremely choppy. I'm guessing there is some issue with wine's 3d capabilities but I have no idea what to do. any suggestions?

---

### Post by mojorising on 2008-07-25
ali, do you have the 3d drivers installed for your video card?

BTW: A really good FPS for native Linux is Urban Terror ([www.urbanterror.net](www.urbanterror.net)). You might like that game as well. 


Mike

---

### Post by ali999 on 2008-07-25
> **mojorising said:**
> ali, do you have the 3d drivers installed for your video card?

BTW: A really good FPS for native Linux is Urban Terror ([www.urbanterror.net](www.urbanterror.net)). You might like that game as well. 


Mike

I'm pretty sure I got the right drivers installed. My video card is an nvidia 9600gt and I have the driver that I found off the nvidia website installed (173.14.09). I'm gonna assume this is working as everything else for me works fine, including compiz 3d effects so I know 3d is enabled as well.

Thanks for telling me about urban terror...haven't heard of it before but will definately check it out

---

### Post by ali999 on 2008-07-26
waaaa......somebody help me

---

### Post by Gopher88 on 2008-07-30
Sorry for the bump, But I was installing steam via this guide and I got it running, but I can't see any of the text. I attached a screen shot of what it looks like

---

### Post by danwood76 on 2008-07-30
Disable compiz when running 3d in WINE.
It doesnt work well with compiz at all so you will need to turn it off.

You can turn it off by setting the desktop effects to none in the appearance control pannel.

---

### Post by Gopher88 on 2008-07-30
Hmmm I tried that and it didn't seem to work, same result as before

---

### Post by Flynn555 on 2008-09-15
ever since i installed gusty about a year ago i have been unable to get steam/counterstrike to run correctly. i have even gone to the extent of running it under different desktop environments (fluxbox, xfce) still cant get it to work right.

my problem is that : the game runs fine for about 2-3 min then my computer locks up and i am forced to restart.  i have surfed countless threads about this issue and i have pretty much given up.  i just use my windows machine for all my gaming (until someone figures it out)

---

### Post by d3vaguru on 2008-10-19
*bump*

---

### Post by brianfreytag on 2008-10-19
> **Flynn555 said:**
> ever since i installed gusty about a year ago i have been unable to get steam/counterstrike to run correctly. i have even gone to the extent of running it under different desktop environments (fluxbox, xfce) still cant get it to work right.

my problem is that : the game runs fine for about 2-3 min then my computer locks up and i am forced to restart.  i have surfed countless threads about this issue and i have pretty much given up.  i just use my windows machine for all my gaming (until someone figures it out)

The reason it runs like crap is because the way Steam works, is that the way it runs the games is through virtualization.  The way that wine works is through virtualization.... So essentially, you are virtualizing through a virtualizer.

Steam in particular has a lot of issues running through Wine.  I'm running Soldier of Fortune II through wine and have no issues (if I have Compiz turned off), but when I try to play Team Fortress 2 through steam, I have super issues.  90% it freezes up on me when I try to connect to a server.

If you want to use Steam, I would suggest going into Windows for that... at least until winehq.com gets their act together and makes it work better.

If you've also noticed, Steam Friends doesn't work right.  You can't see what you type, and you can't see what they type.  To "fix" this, you have to randomly resize the Steam Friends window and the chat box will refresh.  This has been an issue for a long time, and wine hasn't gotten around to fixing it.

---

### Post by almahtar on 2008-11-29
> **Gopher88 said:**
> Sorry for the bump, But I was installing steam via this guide and I got it running, but I can't see any of the text. I attached a screen shot of what it looks like

You need to install the Tahoma font.  Get it here: [http://www.dsource.org/projects/bindings/browser/trunk/freetype/examples/Tahoma.ttf?format=raw](http://www.dsource.org/projects/bindings/browser/trunk/freetype/examples/Tahoma.ttf?format=raw)

Copy it to ~/.wine/drive_c/windows/Fonts/Tahoma.ttf


> **brianfreytag said:**
> The reason it runs like crap is because the way Steam works, is that the way it runs the games is through virtualization.  The way that wine works is through virtualization.... So essentially, you are virtualizing through a virtualizer.


Wine doesn't virtualize, actually.  It's pretty much a reverse-engineered re-write of the windows DLLs, but everything runs native.

---

