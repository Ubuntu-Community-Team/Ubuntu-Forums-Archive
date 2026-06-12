---
title: "experances with HP dv1000 series?"
date: 2005-08-06
forum: Hardware &amp; Laptops
---

### Post by vtec on 2005-08-06
I'm thinking about ordering a HP dv1000 series laptop. Has anyone tired this and if so how does it work?? My main concerns are power managment and wireless. Bluetooth would be a big pluse too.

---

### Post by mustekala on 2005-08-06
I'm using a dv1000 laptop right now (HP Pavilion dv1155ea) which I bought last month. 
I also had reservations about whether most hardware would work "out of the box" or not.  So to spare me endless frustrations I decided to dual boot it with Windows XP (it comes bundled with) --just in case. But now, weeks later, I haven't found any reason yet why I should boot to XP because everything works fine in Ubuntu (Hoary).

Ethernet works, Wi-Fi works (it's amazing how it just worked like that, without much fanfare), the 1280x760 resolution works out-of-the-box, the media control buttons work, the touchpad works, the "fn" buttons work. 

Power management works splendidly, like the suspend-to-RAM (sleep), suspend-to-disk (hibernate), CPU Frequency-Scaling (speedstep), and the AC/Battery monitor. Like I said, it works splendid. However, there is one minor thing that is a little bit annoying (I haven't found a good solution yet), it's the screen brightness buttons. When I press it up or down, it doesn't respond. Only when I type on the terminal "acpi -t" that the screen go bright or dim. It's only a minor annoyance anyway.

I have yet to test the firewire port and the card readers though. But like the others,   I don't have a dv camera or media cards. My laptop doesn't have Bluetooth, so I don't know if that would work splendidly or not.

---

### Post by vtec on 2005-08-06
Wow that sounds really good. I think i'm going to order it real soon. What wireless card did you have, the intel 2200? Thanks for the response.

---

### Post by burningbed on 2005-09-14
The screen brightness buttons worked for me out of the box with the breezy preview.

---

### Post by mlmurray on 2005-09-14
I'm running Hoary on a Compaq X1000 (which had an HP twin whose designation I can't remember).  It is 100% functional.  The ipw2200 wireless network card was recognized and works great.

Power management works as expected.  I had to do some tweaking with my .xmodmaprc file and KDE's (I'm running Kubuntu) hotkeys to get the volume and mute buttons working but that was about it.

Ubuntu should have no trouble with your dv1000.  Here's a [forum](http://www.dv1000forums.com/index.php) I found useful.  There are lots of tips for Linux in general that apply specifically to your machine.

---

### Post by mtupper on 2005-12-08
My dv1000 has done well with Ubuntu, however I opted for the KDE desktop and then the media controls (play, ffw, volume, mute, etc.) stopped working and I am having a hard time getting them up with the khotkeys app.

---

### Post by mustekala on 2005-12-15
Just for fun, I tried Kubuntu too but it just didn't feel right. So I'm back to Ubuntu (upgraded to Breezy). I do have lots of KDE apps in GNOME though. 

P.S.
My dv1000's wi-fi is ipw2200

---

### Post by WanStiller on 2005-12-29
I have a dv1000 (1335) dual boot with XP working perfectly fine, the fn buttons, media controls, everything. The original Quickplay funtions are unaffected. However I did have problems with wireless the first time I installed, the connection worked for a while and the stoppoed working until I entered all the nework settings again (SSID, WEP key). I fiddled around with some solutions from the forum and found that the option hwcrypto=0 did solve it for a while, but not upon restarting the machine.

I finally opted to reinstall Breezy completely, get all the updates first through the wired ethernet connection, and then as a final step configure wireless. Now everything works just fine :D

---

### Post by vladuz976 on 2006-03-03
I wanna order the dv1000, too. 
i am really glad to hear such positive responses on here. 
one question, did you guys use the hp laptop customized version of ubuntu?
[http://www.ubuntu.com/download/derivatives/hp?highlight=%28hp%29](http://www.ubuntu.com/download/derivatives/hp?highlight=%28hp%29)

---

