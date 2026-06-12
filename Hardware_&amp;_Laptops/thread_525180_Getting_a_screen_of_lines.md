---
title: "Getting a screen of lines"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by TMinus10 on 2007-08-14
I decided to try Ubuntu. But I seem to be having a big problem with it.  It shows the loading bar, but after its done loading. I just get a screen of lines like so:
[img]http://i17.tinypic.com/6fjx81s.jpg[/img]

I'd really like to fix this. Is it because I'm dual booting it with XP?

I currently have an ASUS motherboard(I can find out all the information on it if needed) and a Nvidia GeForce 6600.

---

### Post by K.Mandla on 2007-08-14
Hmm. :-k That's not quite right. Did you install a different driver for your card, or is this the first thing you get after installing the entire system? Does a live CD work? What happens if you press CTRL+ALT+F1? Do you get any text there? What does it say?

(It shouldn't have anything to do with dual-booting, by the way. That's either good news or bad, depending on your perspective. ;) )

---

### Post by TMinus10 on 2007-08-14
> **K.Mandla said:**
> Hmm. :-k That's not quite right. Did you install a different driver for your card, or is this the first thing you get after installing the entire system? Does a live CD work? What happens if you press CTRL+ALT+F1? Do you get any text there? What does it say?

(It shouldn't have anything to do with dual-booting, by the way. That's either good news or bad, depending on your perspective. ;) )

Well, I do have have the driver for it on windows. But like you said, that shouldn't be a problem..

Also, live CD doesn't work. I got the same results. So I tried a text based install, and I still get the same problem. I also believe I still get lines with I pretty CTRL+ALT+F1. I do notice a change in the color of the lines though, so I know its still working.

---

### Post by K.Mandla on 2007-08-14
There's something odd going on there. Try rebooting, and selecting the rescue option from the Grub menu. If there's some sort of inconsistency between your monitor and the driver, we might be able to back away from the default Linux driver and get some sort of video output to show up. The problem is, without some sort of terminal screen, that will be slightly impossible. 

If it works, when you reboot to rescue mode, you should get a text-mode screen with a root access prompt.

---

### Post by TMinus10 on 2007-08-14
> **K.Mandla said:**
> There's something odd going on there. Try rebooting, and selecting the rescue option from the Grub menu. If there's some sort of inconsistency between your monitor and the driver, we might be able to back away from the default Linux driver and get some sort of video output to show up. The problem is, without some sort of terminal screen, that will be slightly impossible. 

If it works, when you reboot to rescue mode, you should get a text-mode screen with a root access prompt.

It works when I use rescue mode just fine.

---

### Post by K.Mandla on 2007-08-14
Okay, that's good. When you're in rescue mode, edit your /etc/X11/xorg.conf file and change the Driver section to the "vesa" driver.

```
nano -w /etc/X11/xorg.conf
```

Find the driver section. Where it says driver, change it from "nv" or whatever it is to "vesa" then press CTRL+O (that's an "oh", not a zero), then CTRL+X then 

```
reboot
```

And let it start up normally. Then cross your fingers. On both hands. :)

I have to run out now but I'll check back on this thread when I return.

---

### Post by TMinus10 on 2007-08-14
> **K.Mandla said:**
> Okay, that's good. When you're in rescue mode, edit your /etc/X11/xorg.conf file and change the Driver section to the "vesa" driver.

```
nano -w /etc/X11/xorg.conf
```

Find the driver section. Where it says driver, change it from "nv" or whatever it is to "vesa" then press CTRL+O (that's an "oh", not a zero), then CTRL+X then 

```
reboot
```

And let it start up normally. Then cross your fingers. On both hands. :)

I have to run out now but I'll check back on this thread when I return.

Now, how would I got about finding the driver section and changing it vesa. Sorry, this is my first time using ubuntu.

---

### Post by TMinus10 on 2007-08-14
Sorry to bump my own thread, but I'd really like to know how to do this.

---

### Post by K.Mandla on 2007-08-14
No problem. When you follow the first command above, use the page down key to sift through the text. About three-fourths of the way down you'll see a section called "Driver" and in that subsection, a line like this

```
Driver  "nv"
```

It might say something other than "nv"; no matter what it says, change the nv part to vesa, so it looks like this.

```
Driver  "vesa"
```

Press CTRL+O to write out the file, then press CTRL+X to exit nano. Then type "reboot" and let Ubuntu boot normally. Hopefully that will give you rudimentary (but visible) video output.

Sorry this is so complicated. Ordinarily you shouldn't have to jump through hoops like this just to get some video. If this works, it should be a step forward, in any case.

---

