---
title: "Why is my sound volume so low?"
date: 2009-04-02
forum: Hardware
---

### Post by uhcafigdc on 2009-04-02
Dell Inspirion 1525, latest Ubuntu 8. Ubuntu installed sound for me, and I haven't changed anything yet. 

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

Sound is always at a low volume, even when turned up all the way via alsamixer or another volume control program. It is louder when using Windows.

---

### Post by connorh123 on 2009-04-02
So many sound problems lately.
First, check your alsa. Make sure every thing's fine over their.
If that every thing's good their, then try typing this into terminal.
> sudo apt-get install kmix
After you install it, it should automatically open, if not, type kmix.
Then go into your settings and turn up your volume.

---

### Post by uhcafigdc on 2009-04-02
> **connorh123 said:**
> So many sound problems lately.
First, check your alsa. Make sure every thing's fine over their.
If that every thing's good their, then try typing this into terminal.

After you install it, it should automatically open, if not, type kmix.
Then go into your settings and turn up your volume.

When you say "check your alsa" does that mean making sure that my application is using alsa as the sound output device, and that the knobs in alsamixer are turned up? I have verified that both of these are true. kmix shows the same.

---

### Post by connorh123 on 2009-04-02
When I say that, I mean. Test your settings. Make sure the sound is at a reasonable level for you.

---

### Post by uhcafigdc on 2009-04-02
> **connorh123 said:**
> When I say that, I mean. Test your settings. Make sure the sound is at a reasonable level for you.

Okay. Yes, the sound is turned up all the way.

---

### Post by shutslar on 2009-04-02
Thank you very, very, much!  kmix helped resolve my low volume issue also.

---

### Post by connorh123 on 2009-04-02
> **shutslar said:**
> Thank you very, very, much!  kmix helped resolve my low volume issue also.

Your welcome ;)

---

### Post by uhcafigdc on 2009-04-02
I just want to mention, to avoid confusion, that this didn't solve my problem. Again, the volume is turned up all the way.

---

### Post by connorh123 on 2009-04-02
Darn.
Okay try this
> sudo apt-get install aumix
Scroll down using the arrow keys and turn up the volume.

---

### Post by tyrannor on 2009-04-02
I have the HP zv6130us with Altec Lansing speakers. The volume/wattage is very good, but not so in Ubuntu.
Raising the volume level by two notches is ok in WinXP, but I have to get it halfway for it to be acceptibly audible in Ubuntu. 
I want to try your solution i.e. installing kmix, but it needs 147 MB???
Seriously, WTH?

---

### Post by connorh123 on 2009-04-02
...What?
You're doing > sudo apt-get install kmix right?

---

### Post by tyrannor on 2009-04-03
Yes, its 47 MB archive and the total seems to be 147 MB

---

