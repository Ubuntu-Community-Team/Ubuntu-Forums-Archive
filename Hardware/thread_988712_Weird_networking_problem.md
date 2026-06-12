---
title: "Weird networking problem?"
date: 2008-11-20
forum: Hardware
---

### Post by Mewshi on 2008-11-20
I seem to be having this weird as hell glitch right now.

What happens is, whenever I use any app that does use HTTP (IRC, Pidgin (except when MSN is set to use HTTP), Thunderbird, etc) it makes my wireless disconnect.  Also, it keeps *very* randomly dropping out on its own.  This is really frustrating for me, and it wasn't always like this.  Please help :(

Chipset - ath9k
Running Ibex

---

### Post by bulan880 on 2008-11-20
I think i share exactly the same problem as you. Can you connect right back after the disconnect?

---

### Post by Mewshi on 2008-11-20
Indeed I can.  But it's so annoying!  :(

Do you know how to fix it?

Any help?  :(  Please?

I love Ubuntu, and think it's wonderful, but this is just... disgusting me to no end :(

Wired works without a hitch, and... yeah...

---

### Post by Mewshi on 2008-11-20
Does anyone know how to fix this?  It's really disappointing :'(

---

### Post by srilyk on 2008-11-20
try opening a terminal window and type "tail -f /var/log/messages" and then repeating whatever it is you do to disconnect. Hit "ctrl+c" to stop logging. If something interesting pops up it may be of use to someone who knows more than me! (or give you a clue to google for)

---

### Post by Mewshi on 2008-11-20
Nothing came up :(

So, anyone else have any ideas?  I'll try anything up to and including ... favors... >.>

Should I get a chicken and light the candles now?

---

### Post by Mewshi on 2008-11-20
Does anyone have *any* clue how to fix this?  Because this sucks.

---

### Post by srilyk on 2008-11-20
What's in the wlan section of ifconfig? Do you know if there are "proprietary" drivers? Are you using ndiswrapper? (ndiswrapper -l)

I know with some cards the ndiswrapper will either use the wrong driver, or ndiswrapper is just not needed.

Of course it's also possible that it's something entirely different... I don't have tons of experience with various hardware, but I'll do my best to help!

---

### Post by dmglouis on 2008-11-22
I have the exact same problem. When I installed Ibex, the default driver for my wireless card was the ath9k one. However, when I am browsing lightly it is fine. When I try to watch on youtube or hulu or there is some update available, the connection drops. And it doesn't show that its dropped on the taskbar. I have to click on my wifi network to connect again each time this happens. I'm pretty sure ath9k is not proprietary, its been developed specifically for the newer atheros n wifi cards.

---

### Post by tohomas on 2009-03-26
I have a similar issue, but not with a wireless card.  Anytime I would launch pidgin, skype, or vuze I would lose my Internet connection.  This has plagued me for weeks.  I just happen to find a temporary solution.  

Launch pidgin 
From Command line
  ```
sudo ifconfig eth0 down
```
  ```
sudo ifconfig eth0 up
```

Then pidgin seems to work fine.  I still need to try it with skype and other programs.

If anyone finds a better solution please let me know.

---

