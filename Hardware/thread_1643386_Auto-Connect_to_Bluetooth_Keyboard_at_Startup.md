---
title: "Auto-Connect to Bluetooth Keyboard at Startup"
date: 2010-12-11
forum: Hardware
---

### Post by gtsorbo on 2010-12-11
I have a bluetooth keyboard for my HTPC. I pair it with my computer via bluetooth, and it works fine. However, when I turn off the keyboard or my computer, it has to connect again  (which requires me entering a passcode on the computer and keyboard) when I turn them back on. I've looked through many forums and through that I have found that I'm missing some seemingly vital bluetooth files:

/etc/default/bluetooth
/etc/init.d/bluetooth
/etc/bluetooth/hcid.conf

In the instructions that I've found online so far, I must change certain lines in any of these files. I am unable to, since they do not exist.

Am I missing a dependency or something? I've also tried installing Blueman but that didn't help at all.

I'm running Ubuntu 10.10 (Maverick).

---

### Post by marcemi on 2010-12-31
I have the same problem!

---

### Post by gtsorbo on 2011-01-01
Have you had any luck with a possible fix?

---

### Post by mattewong on 2011-01-29
I also have the same problem. I have tried using hcitool putkey and changing the /etc/bluetooth/*.conf files, and still have not figured out a way to make this work. the most annoying thing is, this used to work in my earlier version of ubuntu, but I updated it to support my new multi-touch pad, and after updating, I can't get anything to connect automatically. would love to find a solution somewhere. not very impressed with ubuntu's pre-release qc process...

---

### Post by Quish on 2011-03-01
Would be nice if someone give us solution. .)

---

### Post by dbrb2 on 2011-03-01
I seem to be in the same boat. I can explicitly reconnect easily enough from the gnome applet, but can't persuade Ubuntu to connect at startup :-(

---

### Post by kristiaan_d on 2011-03-20
figured i would hijack your thread as well to say i also have the same problem as you, bluetooth dongle works perfectly and it sees both my keyboard and mouse but neither of them re-connect at startup...

the other problem i have is that ubuntu does not seem to recognize any mouse button clicks from my mouse.

its an Apple keyboard and Apple Mighty Mouse.

cheers everyone.

---

