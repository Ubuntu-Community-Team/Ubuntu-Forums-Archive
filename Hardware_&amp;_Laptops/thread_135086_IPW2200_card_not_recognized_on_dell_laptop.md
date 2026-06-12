---
title: "IPW2200 card not recognized on dell laptop"
date: 2006-02-23
forum: Hardware &amp; Laptops
---

### Post by napoleon on 2006-02-23
Hey... I've got a Dell 600m with the pro wireless 2200 card, and Breezy Kubuntu won't recognize it anymore.  With the stock installation, it at least listed it as an interface, but it would never work, so I installed the ieee802.11 subsystem to the newest release, as well as the ipw2200 driver and firmware. Now my wireless card won't even show up in kcontrol's network settings. I've tried running iwconfig in console to no avail; it just returns an error that the interface doesn't exist.  I also tried loading the ipw2200 modules in the console--unsuccessfully. Here's the error report:

sudo modprobe ipw2200
WARNING: Error inserting ieee80211_crypt (/lib/modules/2.6.12-9-386/net/ieee80211/ieee80211_crypt.ko): Invalid module format
WARNING: Error inserting ieee80211 (/lib/modules/2.6.12-9-386/net/ieee80211/ieee80211.ko): Invalid module format
FATAL: Error inserting ipw2200 (/lib/modules/2.6.12-9-386/kernel/drivers/net/wireless/ipw2200.ko): Invalid module format

Anyway... kind of annoyed... reminds me of all the reasons I hated Fedora 4 on my laptop. I can't understand the difference, but Breezy Ubuntu configured my wireless right the first time in the install, but kubuntu hasn't... *sigh*... anyway. Any help would be much appreciated. Thanks.

Jon

---

### Post by K.Mandla on 2006-02-23
I'm using the same card in an M170 and tried Kubuntu; sorry to say it, but everything worked perfectly for me. 

Is rebuilding the system with a server install an option? From there, assuming the card was recognized and configured right, you could *sudo apt-get install kubuntu-desktop*, which might get you where you want to be.

And if not, it would at least pin the problem down to something within Kubuntu.

---

### Post by napoleon on 2006-02-23
No... like I said... I know it works with Ubuntu, I've just put so much work into customizing my current setup that I'm really not interested in starting it all over again until I get tired of it, lol.  Anyway... yeah... I'm actually thinking about dropping the trusty 600m for an xps, but not right now--there's some more time left in our romance (at least that's what I tell it while I wait for my wallet to grow... *shrug*).  Thanks, though, for the comment.

---

