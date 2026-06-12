---
title: "CRT incompatible?"
date: 2010-07-20
forum: Hardware
---

### Post by jroa on 2010-07-20
I am new to Linux and Ubuntu.  I have a dual boot loaded on my HP Pavilion a6400f desktop and I have been having a lot of fun learning and experimenting with Ubuntu.

I recently swapped the Gateway LCD Monitor that I was using for an older CRT monitor.  I can boot into Vista with no problem and I can see Grub and startup details for Ubuntu.  However, right around the time when the login screen on Ubuntu should appear, the screen goes blank on the CRT.  I don't know why it is doing this because I can see the rest of the startup screens up to that point.  If I plug the LCD monitor back in, it boots up fine.

Is there something I can do to be able to use this CRT with Ubuntu?  The odd part is that I tried Fedora and DSL versions of Linux and they would not display either.  They do about the same thing, boot to a certain point and then the screen goes blank.  The only Linux that I could get to display on the monitor was GParted live, but I can't do much with that disk other than manage partitions.

In case anyone wants the monitor information, the CRT is emachines brand, model eview 17s and the LCD is Gateway, model FPD1975W.

Any ideas you may have will be greatly appreciated.

---

### Post by dtr1001 on 2010-07-20
You will need to find which resolution and refresh rate your crt can deal with as it sounds like it cannot sync to the signal. - Have you tried using it as second screen on a laptop to see what outputs work with it? (might be best to test ones known to work else you might fry it) Does it work if you boot with live cd as this is low res to begin with...?

---

### Post by jroa on 2010-07-20
I have not tried using it as a second monitor on a laptop, but I can give that a go.

If I boot Ubuntu live, it does the same thing; it boots to what seems should be the login screen but goes blank instead.  Same with Fedora and DSL.  Live disks work fine with the LCD monitor.

I will try the laptop and let you know how it goes.  The only one I have available at the moment is my daughter's and it runs Fedora, so I will have to figure out how to change the resolution in it.

---

### Post by jroa on 2010-07-20
Alright, I got the CRT to work, but not in the way that I thought I would.  I booted the computer with the LCD screen, changed the resolution, shutdown and rebooted with the CRT.  I tried it several times and with the CRT, the screen would always go blank at the login screen.

Out of curiosity, I booted up with the LCD and while the computer was running, I switched cables and voila, the CRT worked and I was able to use any resolution.  I rebooted with the same monitor and it went blank again.

So, I made my account login automatically with no password and now I am able to boot up with the CRT.

I guess the CRT does not like the login screen.  Is there anyway I can change the resolution on the login screen or any other adjustments I should try?  The CRT seems to work with all of the resolutions that I have tried so far, including the one for the 19' LCD monitor, so maybe the resolution of the login screen is not the problem.

---

