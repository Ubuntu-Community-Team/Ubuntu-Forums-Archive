---
title: "Remove Update Icon from panel"
date: 2008-11-17
forum: General Help
---

### Post by lightstream on 2008-11-17
Does anyone know if there is a way to prevent the 'Update' icon from appearing in the notification area?

I no longer use automatic updates, and have set the update manager to never check for updates, but I cannot find out how to stop the icon appearing to 'warn' me that the update information is outdated (of course it is, I disabled it!)

BTW just in case anyone is wondering why I have updates disabled, it's because my computer works great so therefore I do not intend to fix it. I wasted a whole morning last week when an update for X and the kernel images rendered my machine unusable. Once I'd fixed the mess, I turned off updates and would prefer never to see or hear about them again! 

Thanks for any help with this irritation!!

---

### Post by rampageoberon on 2008-11-17
No idea how to remove the icon, i'd just ignore it personally if i didn't want to update.

But updating is quite important, especially with security fixes and critical updates to your system and applications. It as always good practice to keep the system updated.

---

### Post by jesuisbenjamin on 2008-11-17
You may want to remove the notification applet altogether. It will not show your connection however, but who needs that?
Right click on applet, remove. Voila.

---

### Post by philinux on 2008-11-17
> **lightstream said:**
> Does anyone know if there is a way to prevent the 'Update' icon from appearing in the notification area?

I no longer use automatic updates, and have set the update manager to never check for updates, but I cannot find out how to stop the icon appearing to 'warn' me that the update information is outdated (of course it is, I disabled it!)

BTW just in case anyone is wondering why I have updates disabled, it's because my computer works great so therefore I do not intend to fix it. I wasted a whole morning last week when an update for X and the kernel images rendered my machine unusable. Once I'd fixed the mess, I turned off updates and would prefer never to see or hear about them again! 

Thanks for any help with this irritation!!

This is a bad idea. However if you want to do the minimum updating with zero risk then I would suggest this. In software sources click the Updates tab. Then ensure that only Important Security Updates is ticked. And install these with no notification. Problem solved.

---

### Post by lightstream on 2008-11-17
> **jesuisbenjamin said:**
> You may want to remove the notification applet altogether. It will not show your connection however, but who needs that?
Right click on applet, remove. Voila.

Hmm, this should be possible shouldn't it. However I don't see a 'Remove from Panel' or similar option when I right-click the icon.

I've now gone into System > Administration > Software Sources, and turned off all the options on the update tab (i.e. so it will not check for any updates, not even 'critical' ones).

Hopefully that will be the end of that.

Pretty annoying that there is no way to configure what should display in the notification area really.

I understand the concept - in general, users should be forced to update their machines because they're probably stupid as monkeys and need to be constantly nannied. Imagine a load of sheep sat in front of their PCs, happily tapping away at the keyboard with their little hooves, yes sure auto-update them.

Some of us remember the 'red alert' virus outbreak, which thanks to the legions of unupdated Windows machines spread round the globe faster than a picture of Paris Hilton's minge. 

I realise events like that make people a bit over-cautious, and the guys at Canonical probably realise that anything even remotely approaching the scale of Red Alert would blow Linux's reputation to pieces.

So sure idiot-proof the OS if you must, but I think it's a mistake to prevent knowledgeable users operating their machines in ways that are most appropriate to them.

At the time of Red Alert, I was running Win XP, and I had no anti-virus, and no anti-spyware, and was not affected. In fact I've never used either of these on Windows, and have never had an infection. I do have a firewall of course, that is essential.

So if I can operate Windows for many years without problems despite lack of AV and anti-spyware, I'm pretty confident that I'll not suffer any issues on Linux either.

And yes I do know that my Win XP is uninfected. I'd be more than happy to bet money on that.

Rant over, thanks for people's help!

---

### Post by CatKiller on 2008-11-17
> **lightstream said:**
> Hmm, this should be possible shouldn't it. However I don't see a 'Remove from Panel' or similar option when I right-click the icon.

Following this suggestion, you aren't trying to remove the icon. You're trying to remove the Notificaton Area. It's a small group of dots to the left of the icon.

By default, it doesn't auto-update. If it did, you wouldn't need the icon to show that updates are available. I would also recommend leaving the security updates enabled. You can set the update checks to be less frequent if they bother you. Once a month might be less irritating to you.

---

### Post by lightstream on 2008-11-17
> **CatKiller said:**
> Following this suggestion, you aren't trying to remove the icon. You're trying to remove the Notificaton Area. It's a small group of dots to the left of the icon.

By default, it doesn't auto-update. If it did, you wouldn't need the icon to show that updates are available. I would also recommend leaving the security updates enabled. You can set the update checks to be less frequent if they bother you. Once a month might be less irritating to you.

One icon appears when updates are available, but there's another that shows when connection to the update servers failed. What does annoy me about this is that the icon will not go away until you get the update manager to check for updates.

It does this even if it is not due to check the update servers. I think the icon is overkill, and it annoys me because it belongs more with the Windows "all-users-are-muppets" mentality than with Linux. I mean it's Linux ffs - so what if I can't connect to the update servers right this very second? A Linux machine isn't going to just instantly get hacked.

These sorts of things have started to bug me lately - a growing proliferation of completely unnecessary pop-up bubbles is another classic example.

---

### Post by mindwarp on 2009-02-13
You can remove just the update icon by going to System -> Preferences -> Sessions and unchecking update-notifier from the programs to run at startup.

---

