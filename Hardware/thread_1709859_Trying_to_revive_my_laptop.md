---
title: "Trying to revive my laptop"
date: 2011-03-18
forum: Hardware
---

### Post by racie on 2011-03-18
*[COLOR="Red"]*EDIT* Nvm... see my other post...[/COLOR]*

Hi guys.  My Compaq Presario F756NR laptop has slowly declined into its early grave, and I was hoping to make it somewhat usable.

Here's my little background story (**you can skip this paragraph, as it's not necessary** :P)... it started with my DVD-RW drive.  At first, it would disappear and re-appear in Device Manager (Windows) when it felt like it, then one day it disappeared completely and never came back.  My boot speed turned into a snail and I realized that removing the broken DVD-RW drive fixed it.  Then, my hard disk started to fail... or so I thought... Every couple of boots it would take forever to start up, then display the message "Operating System not found."  I ignored it because there was nothing I could think of to do (yes, I tried re-installing Windows and I even tried Ubuntu on that laptop... it didn't help).  Then one day, my laptop decided to freeze and then shut off while I was in the middle of browsing the web.  I could not get it to boot from the hard disk again.  But lo and behold, it works just fine when connected to any other computer.  So I started to only be able to boot things from USB.  I didn't do much of that and instead picked up a cheap desktop.

Okay, so here's where I'm at today... I decided I could finally give my old laptop some use and use Puppy Linux on it from a USB.  Well I go to boot into Puppy and I find out the computer will NOT boot from USB anymore (and it doesn't have a HDD or optical disk drive).  Also, for some reason I cannot get into the BIOS every time.  Kinda sucks.  

However, I FOUND A CLUE!  :o

When I start the computer (and I press ESC to see what the POST is doing), a very odd message appears among the normal-looking messages:

```
No TPM or TPM has problem
```

Now I've looked this up online and found out that it's either the memory, the BIOS is in need of updating, or my motherboard is fried (I'm leaning toward the last one, but the other is fixable).

My computer passed a memory test in the BIOS so that is obviously ruled out.

Now... I'm not sure what to do about the BIOS update.  Nothing will boot, so I'm really not sure if I can go about this.  If any of you have suggestions, I have a Phoenix BIOS that is version F.08, so it is [slightly out of date](http://h10025.www1.hp.com/ewfrf/wc/previousVersions?softwareitem=ob-90167-1&lc=en&dlc=en&cc=us&os=2093&product=3646836&sw_lang=).

ANYWAY

I realize that I probably won't get any responses, but I figured I'd post this anyway just on the off chance one of you knows how to and wishes to help me.  I'll probably post this in some type of hardware forums in the future.  Congratulations if you actually read the whole thing! :)

---

### Post by wweeks on 2011-03-19
Sounds like your power supply is dying.

---

### Post by racie on 2011-03-19
In my laptop?  I highly doubt it.

After further research, the TPM message may be quite normal and was probably always there.

The good news is that now instead of hanging indefinitely it will now restart.  Why is this good?  Because after 3-4 restarts, it boots off of my USB!  I'm running Puppy Linux right now.  :D  Although it unfortunately has to hang for a while then restart a few times every time I want to turn on my laptop.  Meh... at least it's workable.

Now I'm thinking it either needs to be cleaned on the inside, the motherboard is dying, or something else.  Actually, it might still need to have the BIOS updated, but I'm not really sure how I can do it or if I should really go for the risk.  HP only offers an .exe file to update it.

Anyway, I guess my first post is now obsolete.  :/  Thanks for your trouble of replying to me though!

---

### Post by wweeks on 2011-03-19
Alright then. :) Glad to hear that. It just sounded to me like when a my HP's power supply died.

---

