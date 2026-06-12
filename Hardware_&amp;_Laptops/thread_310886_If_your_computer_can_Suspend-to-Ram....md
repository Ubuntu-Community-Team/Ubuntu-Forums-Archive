---
title: "If your computer can Suspend-to-Ram..."
date: 2006-12-02
forum: Hardware &amp; Laptops
---

### Post by grndslm on 2006-12-02
If your computer can resume from Suspend-to-Ram...list it in this thread so I can figure out which computer to buy.  This is a very big issue for me as Edgy & suspend-to-ram worked flawlessly on my previous laptop (even with beryl, too).  And specifically for me...are there any Thinkpad T-Series or ASUS laptops that have good or bad memories on this subject matter that they'd like to share?

Thanks,
  grndslm


**Working S3 Laptops**
ASUS Z63A
HP Pavilion dv8230
Lenovo/IBM Thinkpad T41p
Lenovo/IBM Thinkpad T42p
Lenovo/IBM Thinkpad Z61m
Sony TR1A

---

### Post by hikaricore on 2006-12-02
LOL I linked my suspend script to /dev/null

Saves me the trouble of kicking myself in the arse when I bump the sleep button on my keyboard, now it simply launches the screensaver.  :P

---

### Post by tamasrepus on 2006-12-02
My Thinkpad T42p suspends to RAM pretty flawlessly.

Every once in a while I encounter weird difficult-to-reproduce problems with either my wireless (won't associate, _have_ to cold reboot), or on resume my mouse cursor is gone (KDE problem? I switch to a console tty and reboot). These occur once every 1-2 weeks, going through 10+ suspend-resume cycles a week.

---

### Post by archiesteel on 2006-12-02
> **tamasrepus said:**
> Every once in a while I encounter weird difficult-to-reproduce problems with either my wireless (won't associate, _have_ to cold reboot), or on resume my mouse cursor is gone (KDE problem? I switch to a console tty and reboot). These occur once every 1-2 weeks, going through 10+ suspend-resume cycles a week.

I also have the issue with the disappearing mouse cursor. This can be quite annoying...

---

### Post by dmizer on 2006-12-02
to restore your mouse ... unload and reload the mouse module.  if you're using a laptop, it's most likely psmouse, but if you're not sure, you can look at the list of loaded mouse modules like so:
```
modprobe -l | grep mouse
```
and remove/add all modules listed until you find the one that fixes your mouse.
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```

---

### Post by grndslm on 2006-12-02
Anybody use an ASUS laptop with functional suspend-to-ram?  That'd be sweet, 'cause I'm not a huge fan of Thinkpad matte screens.

Still leaning toward ASUS or IBM Thinkpad....

Any objections?  or suggestions?

Thanks

---

### Post by Chatbox on 2006-12-03
T41p (2373-GGU)

---

### Post by grndslm on 2006-12-04
This is the latest round of contenders to become my next laptop.  Have any of y'all used one of these?  And could you tell me if Suspend-to-Ram is supported by any of these or not:

**I'm prolly gonna buy one of these...**
Toshiba Satellite U205
IBM Thinkpad X60
PortableOne SX (aka: ASUS Z35F)

**Runners up**
IBM Thinkpad T60
HP nc2400

---

### Post by apalacheno on 2006-12-06
Consider adding the IBM/Lenovo ThinkPad Z61m to your list.
I got mine a few weeks ago (had a Dell Inspiron 81o0 before) and I'm deeply impressed by the quality of this little machine.
Edgy works well and I encountered no unsolved issues except for the already mentioned problem with WLAN not connecting after suspend once in a while.

I'll try to post every needed workaround and keep the list updated: [LaptopTesting]("https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadZ61m").

Cheers,
apalacheno

---

### Post by armware on 2006-12-06
HP Pavilion dv8230

i had to mess with the suspend configuration a bit, but i did have it working at one point, so at least i know it's possible.

---

### Post by tamasrepus on 2006-12-06
If you're looking at the Thinkpad T60, you may be interested in that Lenovo is having a "sale" of sorts: [Thread at Anandtech Hotdeals forums]("//http://forums.anandtech.com/messageview.aspx?catid=40&threadid=1960262&frmKeyword=&STARTPAGE=1&FTVAR_FORUMVIEWTMP=Linear")

---

### Post by grndslm on 2006-12-07
> **tamasrepus said:**
> If you're looking at the Thinkpad T60, you may be interested in that Lenovo is having a "sale" of sorts: [Thread at Anandtech Hotdeals forums]("//http://forums.anandtech.com/messageview.aspx?catid=40&threadid=1960262&frmKeyword=&STARTPAGE=1&FTVAR_FORUMVIEWTMP=Linear")Yea, I couldn't miss the sale.  That's the ONLY reason that Lenovo's still on my list...because of the friggin' sale.  Otherwise I would have tossed their matte & standard aspect screens outta here.

Deep down inside I want a Thinkpad.  But even deeper down, something or someone's telling me to Think Different.  Maybe my inner conflict wouldn't be so bad if the widescreen Thinkpad were already here.

Honestly, that Toshiba U205 is starting to sound pretty dern tempting.  The ASUS Z35F is my second fav.

---

### Post by tamasrepus on 2006-12-07
> **grndslm said:**
> Yea, I couldn't miss the sale.  That's the ONLY reason that Lenovo's still on my list...because of the friggin' sale.  Otherwise I would have tossed their matte & standard aspect screens outta here.

I personally like matte screens--the glare on glossy screens is extremely annoying, especially in environments with all-around flourescent lighting.

> Deep down inside I want a Thinkpad.  But even deeper down, something or someone's telling me to Think Different.  Maybe my inner conflict wouldn't be so bad if the widescreen Thinkpad were already here.

Any other reason? I'd personally take working Suspend-to-RAM/Hibernate over a widescreen.

---

### Post by penvzila on 2007-01-11
I had it working on my Toshiba u205-s5002, using Trevino's repository, but a subsequent update broke it.

---

### Post by thesoothsayer on 2007-03-16
Asus A8Fm can do it quite well. Only problem is that if the wireless is off when you suspend, you can never wake it up again except with a reboot. I did a workaround by waking up the wireless device everytime before I put the laptop to sleep.

---

### Post by vivii on 2007-04-23
> **Chatbox said:**
> T41p (2373-GGU)

Hi,
my T41p won't suspend-to-ram - or, to be exact, it does suspend, but won't wake up.
So, Chatbox, could you tell me how you got it to work? (I did use google, but so far it didn't turn up anything helpful). I'm running Feisty, btw.

Thx, Vivi

---

