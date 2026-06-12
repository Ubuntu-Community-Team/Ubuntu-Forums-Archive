---
title: "Laptop has locked me out"
date: 2009-09-05
forum: Hardware
---

### Post by pablo180 on 2009-09-05
I was having problems with my USB mouse on my Dell 1525 on Intrepid, it was randomly stopping working and the only way to get it to work again was to reboot. 

Stupidly I tried to find a quick way of getting it to work again by stopping and starting services. I stopped dbus (yes, I know, I ignored the warning) and started it again. Apart from the screen changing briefly everything seemed OK, but I logged out my touchpad/trackpad stopped working, so I couldn't log back in again!

I've restarted but although it boots up fine, plays sound fine, the touchpad doesn't work, so I cannot log in. The USB mouse doesn't work either so my laptop is now useless!

What the hell have I done? And how can I put it right? I have backups so I can copy files over, but I haven't got a clue what I need to replace. I have been searching Google for answers but nothing, at least nothing that I understand, or that won't make things worse. 

Other than this touchpad problem everything else seems to be working fine. 

Hope someone can help.

---

### Post by jerrrys on 2009-09-05
have you tried **gconf-editor**

navigate to here and enable touch pad

[ATTACH]127578[/ATTACH]

---

### Post by RabbitWho on 2009-09-05
How does he get there without the touch pad? 

On windows you could do everything without the mouse.. but as the super key does next to nothing now I'm just wondering how you get around without a mouse/touchpad?

---

### Post by jerrrys on 2009-09-05
> **RabbitWho said:**
> How does he get there without the touch pad? 

On windows you could do everything without the mouse.. but as the super key does next to nothing now I'm just wondering how you get around without a mouse/touchpad?

Alt + F2 enter/run **gconf-editor**

---

### Post by pablo180 on 2009-09-05
> **jerrrys said:**
> Alt + F2 enter/run **gconf-editor**

Thanks for the help. Alt + F2 didn't work, nothing happened. I can't seem to type anything on the login screen, I am not sure if it is because I have to select the users picture. 

I thought that the keyboard may be messed up too but I pressed Super and an arrow key (just to see if there was a way of moving the mouse pointer) and it went to a console style login screen. I logged in there, so the keyboard is working, but when I typed in gconf-editor it said 'Unable to open display'.

---

### Post by jerrrys on 2009-09-05
if you can get your keyboard to navigate to terminal enter 
**sudo modprobe psmouse**

also this

[ATTACH]127586[/ATTACH]

---

### Post by pablo180 on 2009-09-05
> **jerrrys said:**
> if you can get your keyboard to navigate to terminal enter 
**sudo modprobe psmouse**

also this

[ATTACH]127586[/ATTACH]

Thanks again. I tried fix-x in recovery mode, it didn't make any difference when I tried to log back in. I also tried sudo modprobe psmouse, but neither the touchpad nor the USB mouse worked when I switched back to the login screen.  

I did notice however when flicking through the screens that there was a red asterisk with:

Cannot start hardware abstraction layer - please ensure dbus is running

Is that the problem?

---

### Post by jerrrys on 2009-09-05
sudo update-rc.d -f dbus defaults

---

### Post by pablo180 on 2009-09-05
> **jerrrys said:**
> sudo update-rc.d -f dbus defaults

That did it! Thanks! As soon as I went back to the login screen the mouse was working and I could log in as normal. As far as I can tell everything seems to be working fine. 

Thanks a lot for all of your help.

---

### Post by jerrrys on 2009-09-05
glad to hear that

---

### Post by pablo180 on 2009-09-07
Looks like I spoke too soon. Unfortunately that only worked until the next time I booted up, whereupon I had the problem again. I tried that command again:

```
sudo update-rc.d -f dbus defaults
```

But I got a 'File already exists' message. Dbus was definitely running as I could see it in the booting up screen ('dbus started' or something like that), but the only way I could log in this time was to restart it:

```
sudo /etc/init.d/dbus restart
```

That works and I can login, but now I have to do that everytime I boot up my laptop! It is not a massive problem but just a bit annoying.

I tried restoring /etc/init.d/dbus from a backup from a couple of months ago, but that didn't make any difference. 

Are there any other dbus files or configuration files that I could restore to put things right?

Thanks for the help.

---

### Post by pablo180 on 2009-09-07
Fixed it! I just restored every backup that I had of the /etc/ folder, one after another. Not sure what it did, but everything is working perfectly again now and my touchpad is working at log in. 

Important lesson learned, don't mess with the Services tick boxes, it's just not worth it!

---

