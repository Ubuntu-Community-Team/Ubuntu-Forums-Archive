---
title: "Wine game screen size?!"
date: 2008-10-18
forum: General Help
---

### Post by blootek on 2008-10-18
I have got wine to run steam and I can get it to run Doom3, but the game screen is so small. I dont know how to make it full screen. I tried changing the in-game res nothing happening I unchecked "Emulate a virtual desktop" and it make the screen a little bit larger...im a nub with wine..first time ubuntu and wine user.

---

### Post by jerome1232 on 2008-10-18
Guess What, Doom 3 can run in Linux Natively. :) No need for wine.

There's probably a better guide than this but [http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/)

---

### Post by blootek on 2008-10-18
Hahah awesome lol, only I have to open it through steam because I bought it online with steam while i still used windows...:(

---

### Post by blootek on 2008-10-18
awesome thanks a lot!

---

### Post by jerome1232 on 2008-10-18
[http://ubuntuforums.org/showthread.php?t=746276&page=2](http://ubuntuforums.org/showthread.php?t=746276&page=2)

Post number 11 gives a way to grab your files out of the steam install hope that helps you out.

---

### Post by blootek on 2008-10-18
Righteous thanks a ton! ALSO zombie panic! wont run, I get an error message saying something about a source engine is required to run mods...any thoughts?

---

### Post by jerome1232 on 2008-10-18
Just making sure you downloaded [this file]("ftp://ftp.idsoftware.com/idstuff/doom3/linux/doom3-linux-1.3.1.1304.x86.run") (doom3-linux-1.3.1.1304.x86.run) ran it as root. Then copied your .pk4 files over to /usr/local/games/doom3/base.  They should be located under ~/.wine/drive_c/steam/something-or-the-other.

What video card do you have? What driver are you using? Can you post the exact error?

---

### Post by noerrorsfound on 2008-10-18
> **blootek said:**
> Righteous thanks a ton! ALSO zombie panic! wont run, I get an error message saying something about a source engine is required to run mods...any thoughts?
Well, the obvious question: Do you already have another game installed that uses the Source engine? You need one.

---

### Post by jerome1232 on 2008-10-18
Well the demo works fine out-of-installer for me.... sorta it starts in a refresh rate and/or resolution that my monitor doesn't support. I wonder if there's a way to pass those as a command-line argument (that's so annoying etqw does that too)

---

### Post by jerome1232 on 2008-10-18
Well I figured out the resolution thing, you can create a file at /usr/local/games/doom3/base/autoexec.cfg and add custom settings to it. It works. 

mine were
seta r_displayRefresh "50"
seta r_mode "5"

I got the info from here [http://www.nvnews.net/tweaks/doom3/index.shtml](http://www.nvnews.net/tweaks/doom3/index.shtml)

---

