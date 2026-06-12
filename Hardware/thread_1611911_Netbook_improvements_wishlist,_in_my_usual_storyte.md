---
title: "Netbook improvements wishlist, in my usual storytelling way"
date: 2010-11-02
forum: Hardware
---

### Post by Th3_uN1Qu3 on 2010-11-02
Long story short, i've been given an Aspire One ZG5 to play with. It had a failed BIOS, (possibly) blown LAN controller, missing SSD ribbon and damaged SSD connectors. My job? Fix it.

I first removed the Realtek NIC chip from the motherboard. Still no change, blank screen. I then found out about the BIOS problem, reflashed using the recovery procedure, and surprise surprise. She's up and running. I still have to tackle the main problem and that is a new SSD ribbon and connectors, but since uni is quite boring sometimes, i decided to take 'er to class with me. Sure beats carrying that 17" DV9000. I stuck a 4GB flash drive with Ubuntu Netbook Remix in. She booted up fine, albeit it took quite long. Hooray for suspend mode.

**First day.**

Flash Player, check. Wifi, check. So far so good.
Music, umm... downloading Audacious... WHAT IN THE WORLD IS UP WITH THIS SILLY REDUCED LAME SKIN?????? Oh well, it plays music. But no shuffle no repeat no equalizer... wow, they really screwed it up. But okay, this isn't Ubuntu's fault. Moving on.
Opera installs fine. Flash Player works in Opera too. Good.
OpenOffice takes less than a thousand years to load. That ain't good, that's awesome! :)

**Like:** I like the new menu bars, they look professional. They're a tad slow though, and the buttons take several clicks till they do anything. But i can live with that.
**Dislike:** Nowhere to set the time to 24 hours or show the date. WHAT???

I had barely finished screwing around with it and the battery was hitting the red mark already. It'd been just 3 hours, and more than half of the time i was taking notes and the Aspire was on suspend. Indeed, not too long after and she shuts down. I thought the battery would last longer.

Oh well. We plan a WLAN party for European History classes on Thursday since they're super boring. We settle upon NFS Most Wanted as the game of choice. Guess i'll have to lug the DV9000 after all. Then i go home and start working on my technical drawing for tomorrow.

I charge up the Aspire and start looking for some improvements. I try installing some CPU utilities that worked in the past - none of them will work with the Aspire. Something about permissions. I read [this thread](http://ubuntuforums.org/showthread.php?t=1195253) and [this thread](http://ubuntuforums.org/showthread.php?p=10062228) and decide there has to be a better way. 

**Dislike:** A file manager. I need a file manager. Where is it??? [http://ubuntuforums.org/showthread.php?t=1609589](http://ubuntuforums.org/showthread.php?t=1609589) IN THE TRASH??? That's like that company that told us to shut down our computers by clicking the Start button. Bad ubuntu.

I find the file manager, pin it to the menu bar and after about half an hour of digging find the file responsible of CPU power settings. I fix what was supposed to be working out of the box. See my post [here](http://ubuntuforums.org/showthread.php?p=10062228).

**Dislike:** I decide to also add a hardware monitor applet to the panel to keep an eye on the CPU and make sure it sticks to my configs. Okay but it won't show up. I right-click the panel and nothing... oh, you LOCKED DOWN THE PANEL. Great. Awesome. In your vision, all netbook users are idiots, or what?

**So-so:** You could've thought about a more straightforward way of adding items to the panel. Maybe you can also highlight the ones that are actually running?

That's it for today, gotta study a bit now. Let's hope day 2 with the Aspire will be better, especially in terms of battery life. I'll only get to keep this one for so long you know, but if i get the SSD to work on it the owner may give me another one that i can keep. This one is white, so it makes a better impression. I'll probably get a blue one.

---

### Post by Th3_uN1Qu3 on 2010-11-03
At the end of day one, after i did the CPU frequency configs, i let it play music at maximum volume, with the display on at all times. It clocked in at 1:44. Not bad.

Day two. I didn't use it a lot since we had important classes today and also an exam at maths. It saw just over an hour of use over the whole day, the most it did was when i helped a friend copy some stuff from another classmate's PSP onto his. The battery meter started at 2:22 and was down to 40 minutes when i got home.

One other observation. The brightness goes "below minimum level" when it is left unattended. I would like the option to turn it this low available in the Fn keys range. Also, above minimum brightness the change is very smooth over the first 4 keypresses, then it goes to 5 coarse steps until full brightness. I'd gladly fix it myself - only tell me where the brightness configs are located, since i've tried every spot i found on the 'net and it didn't work.

Oh, and i've soldered the ethernet controller back in place and it turns out it works just fine.

---

