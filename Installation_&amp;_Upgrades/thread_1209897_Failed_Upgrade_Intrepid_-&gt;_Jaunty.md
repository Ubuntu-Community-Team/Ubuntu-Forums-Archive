---
title: "Failed Upgrade: Intrepid -&gt; Jaunty"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by MrDelish on 2009-07-10
I performed the automated upgrade on my Dell minitower to Jaunty via the package manager, replaced the existing config files, and then rebooted. Now, after the Ubuntu loading screen finishes the screen shows a nasty gray bax in the bottom-left corner and I'm unable to do anything except reboot. I've got a live CD loaded in it right now so that I can copy all of my data or work from a terminal, but I'm not sure how I'd go about repairing the problem. I've tried a couple of things already (such as the suggestions here: [http://ubuntuforums.org/archive/index.php/t-482406.html](http://ubuntuforums.org/archive/index.php/t-482406.html)) but have had no luck so far.

Any suggestions will be appreciated.

---

### Post by earthpigg on 2009-07-10
have you tried recovery mode?

when you see the screen that says 'booting in 3....2....1...' hit escape before it finishes the countdown, and choose recovery mode.

that will get us started.

---

### Post by merlinus on 2009-07-10
What video card do you have?  If ATI, then that is probably the cause.

---

### Post by MrDelish on 2009-07-10
Yep, I'm able to reach recovery mode. Not really sure where to start there, though. Attempting to repair broken packages says everything is up-to-date and auto-repairing the graphical problems just moved the garbled box to the top of the screen. The fsck doesn't appear to do anything at all... is there something else I should be doing in the recovery screen?

---

### Post by MrDelish on 2009-07-10
> **merlinus said:**
> What video card do you have?  If ATI, then that is probably the cause.

Sorry, I was writing my last post when yours went up. Yes, it's an ATI. After doing some further searching, I'll go ahead and attempt another fix ([http://ubuntuforums.org/showpost.php?p=7160601&postcount=67](http://ubuntuforums.org/showpost.php?p=7160601&postcount=67)) and post my results.

---

### Post by MrDelish on 2009-07-10
Yep, those instructions did the trick except that I had to run

```
sudo apt-get install xorg-driver-fglrx
```

and then

```
aticonfig --initial -f
```

as suggested. It just booted without a hitch, so I'll keep that handy in case the problem comes up again.

Thanks for the replies. I've been using Ubuntu for a little over a year, but still feel very new to it in some ways and appreciate a push in the right direction.

---

### Post by earthpigg on 2009-07-10
> **MrDelish said:**
> 
Thanks for the replies. I've been using Ubuntu for a little over a year, but still feel very new to it in some ways and appreciate a push in the right direction.

im pretty sure ATI cards give *everyone* a headache that has one, from time to time.

im pretty sure the vast majority of linux users boycott them for that very reason.

---

