---
title: "Firefox window borders disappeared, regular borders still fine"
date: 2008-07-26
forum: General Help
---

### Post by alwiap on 2008-07-26
My Firefox window borders completely disappeared, I have no idea why (I'm running Compiz with Emerald as my window decorator).  Every other border i.e. for Nautilus or anything else is perfectly fine, it's just Firefox. It is incredibly annoying as I can't minimize, Firefox takes up the entire screen, and I can't access my Gnome panels on that screen at all.  I don't know what could have caused this.

I have tried:

- enabling and disabling the 'Place Windows' plugin in ccsm
- emerald --replace

Any ideas?

---

### Post by jombeewoof on 2008-07-27
> **alwiap said:**
> My Firefox window borders completely disappeared, I have no idea why (I'm running Compiz with Emerald as my window decorator).  Every other border i.e. for Nautilus or anything else is perfectly fine, it's just Firefox. It is incredibly annoying as I can't minimize, Firefox takes up the entire screen, and I can't access my Gnome panels on that screen at all.  I don't know what could have caused this.

I have tried:

- enabling and disabling the 'Place Windows' plugin in ccsm
- emerald --replace

Any ideas?

Hit  F11 key

---

### Post by kirk ammon on 2008-08-12
I have the same problem. 

Hitting F11 first makes the toolbars disappear too. Hitting it again brings back the toolbars AND the window border like firefox is supposed to look. However hitting F11 twice everytime I open up firefox is annoying. Are there any permanent fixes?

---

### Post by mess110 on 2008-11-16
I had the same problem. this is what I did and now it works properly. the problem I think is some sort of overwriting of a location variable or sth like that.(might sound bad so I am sorry if it is wrong) -  but hey I have a solution

press F11 twice and it should look normal. after that resize the window so it does not take all your screen. close the window, log out, log in again and open firefox. it should open to the small window. now you can maximaze it agian. it worked for me. if it doesn't work reply here

try typing firefox in a terminal and check the output

---

### Post by binbash on 2008-11-16
It is bug at workspace plugin @ compiz

open compiz go to workarounds plugin and disable legacy fullscreen support.

---

### Post by stoogiebuncho on 2008-11-21
Thanks for the fix, binbash.  Does disabling that affect anything else?

---

### Post by DennisD on 2008-11-21
It does not appear (again, APPEAR :P) to mess up anything else. I had this problem arise today, a quick google search brought me here and within minutes after reading about the "fix", my laptop was as usual. Disabling fullscreen legacy support seem to "restore" thing to "normal". Odd bug, I'm sure we'll hear more about this soon and compiz will release an update. Until then, this seems at present the most viable fix.

Edit: For the Nix noobs, have no fear.. Look below for step-by-step (Happy linux learning!)

mouse up to applications, select system tools, select configuration editor, selects APPS, Select COMPIZ, Select Plugins, select Workarounds, Select Allscreens, select Options ---- A window to the right will fill with options, scroll down to Legacy_Fullscreen and UNCHECK the box with a mouse click and close. Close firefox an restart to find firefox (and other apps) functioning as prior to the hiccup. Quite a friendly process.

---

### Post by rrobe on 2008-11-24
> **DennisD said:**
> It does not appear (again, APPEAR :P) to mess up anything else. I had this problem arise today, a quick google search brought me here and within minutes after reading about the "fix", my laptop was as usual. Disabling fullscreen legacy support seem to "restore" thing to "normal". Odd bug, I'm sure we'll hear more about this soon and compiz will release an update. Until then, this seems at present the most viable fix.

Edit: For the Nix noobs, have no fear.. Look below for step-by-step (Happy linux learning!)

mouse up to applications, select system tools, select configuration editor, selects APPS, Select COMPIZ, Select Plugins, select Workarounds, Select Allscreens, select Options ---- A window to the right will fill with options, scroll down to Legacy_Fullscreen and UNCHECK the box with a mouse click and close. Close firefox an restart to find firefox (and other apps) functioning as prior to the hiccup. Quite a friendly process.


This solved the problem for me (ubuntu intrepid, ubuntu suggested drivers for Nvidia 8400M GS, , firefox 3.0.4, thanks DennisD.
:popcorn:

I'm curious: what does legacy fullscreen do? I thought I'd allow windows to go "completely" fullscreen, but now that I've disabled it I still can set to "FullScreen Mode" VirtualBox Virtual Machines (which is great! O:) )

---

### Post by whos2know on 2009-01-19
Thanks for the info!!  Helped a lot!! :)

-=Bobby=-

---

### Post by PT.Linn.A on 2009-01-19
> **DennisD said:**
> 
Edit: For the Nix noobs, have no fear.. Look below for step-by-step (Happy linux learning!)

mouse up to applications, select system tools, select configuration editor, selects APPS, Select COMPIZ, Select Plugins, select Workarounds, Select Allscreens, select Options ---- A window to the right will fill with options, scroll down to Legacy_Fullscreen and UNCHECK the box with a mouse click and close. Close firefox an restart to find firefox (and other apps) functioning as prior to the hiccup. Quite a friendly process.

Dennis, great walk-through! Fixed my trouble, and with ease.

A step-by-step as you did here is always appreciated.

Thanks Dennis

---

### Post by al688 on 2009-01-22
Just installed ubuntu and was struck by this problem.  However now sorted after following this run through and no longer have to "Ctrl+Q" to close firefox. Cheers.

---

### Post by karrank% on 2009-01-23
Hah! Just discovered I had this prob too, and searched the forum and bingo! fixed! Thx ppl.

---

### Post by karrank% on 2009-01-23
Gah! Spoke too soon! That didn't do it for me, But, from compiz fusion icon, switching from gtk to emerald for window decorator DID reinstate the missing window borders! Pls don't ask me why it worked or I'll start to whimper....

---

### Post by rottie on 2009-07-13
> **DennisD said:**
> 
Disabling fullscreen legacy support seem to "restore" thing to "normal". Odd bug, I'm sure we'll hear more about this soon and compiz will release an update. Until then, this seems at present the most viable fix.

Edit: For the Nix noobs, have no fear.. Look below for step-by-step (Happy linux learning!)

mouse up to applications, select system tools, select configuration editor, selects APPS, Select COMPIZ, Select Plugins, select Workarounds, Select Allscreens, select Options ---- A window to the right will fill with options, scroll down to Legacy_Fullscreen and UNCHECK the box with a mouse click and close. Close firefox an restart to find firefox (and other apps) functioning as prior to the hiccup. Quite a friendly process.

Hi, had the same problem. This solution resolved my issue. 
However, the compiz configurator was located in a different location. 
Menu System > Preferences > CompizConfig Settings Manager 
Start the tool and search for "workaround". Deselect the box, press back and close.

---

