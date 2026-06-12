---
title: "Computer Speaker"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by makaveli789 on 2009-09-04
Hi Guys,

I installed Ubuntu on my office PC a few weeks back and everything went smoothly. However, I noticed that my sound was working. I managed to fix this by traversing through these forums. But the issue I am having now is that if I plug in my earphones I can hear sound, but if I unlpug then I don't hear anything.

My office pc has some kind of built-in speaker and when I was running Windows on it, I could hear notification sounds from the pc itself. But in Ubuntu I don't hear anything. In Ubuntu all I hear are beeps every time a Ubuntu sound event occurs :(

Any clues would be appreciated.

---

### Post by makaveli789 on 2009-09-04
Bump.... boing!

---

### Post by makaveli789 on 2009-09-07
Bump2!!

---

### Post by makaveli789 on 2009-09-09
:confused:

---

### Post by akudewan on 2009-09-09
Guess No. 1): In the volume control, you  may have a "Switches" tab. There is a *Headphone* option over here. Try ticking/unticking it.

Guess No. 2): Linux may have loaded the wrong drivers for your sound card, or your sound card may be unsupported. Try to google your soundcard model and see if you can find relevant info. (Use the 'lspci' command to check the model if you don't know)

---

### Post by dE_logics on 2009-09-09
> But the issue I am having now is that if I plug in my earphones I can hear sound, but if I unlpug then I don't hear anything.

aaaa...I think that should happen...

What's your sound card?

BTW I think you should be working in the office...:rolleyes:

---

### Post by daisyashe on 2009-09-09
I am having the same problem friend but thaks for the solution I will definately try this out.
Is same setting is useful for linux opensuse.
Or something different.

---

### Post by akudewan on 2009-09-09
> **daisyashe said:**
> I am having the same problem friend but thaks for the solution I will definately try this out.
Is same setting is useful for linux opensuse.
Or something different.

It may be slightly different, depending on the desktop environment you're using. (For KDE, you'll have to check under "kmix"). For Gnome, it should be the same.
(It wasn't a *solution*, just a guess)

---

### Post by makaveli789 on 2009-09-16
> **akudewan said:**
> Guess No. 1): In the volume control, you  may have a "Switches" tab. There is a *Headphone* option over here. Try ticking/unticking it.

Guess No. 2): Linux may have loaded the wrong drivers for your sound card, or your sound card may be unsupported. Try to google your soundcard model and see if you can find relevant info. (Use the 'lspci' command to check the model if you don't know)

I had a look in the volume control window, Switches tab and couldn't see a Headphone option. Only two tick boxes: 1) IEC958 2) IEC958 Default PCM. Both are unticked, I tried checking them but didn't make any difference.


This is what lspci says about my sound card: Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller. Is there any way I can check which driver Ubuntu is currently using?

---

### Post by makaveli789 on 2009-09-16
> **dE_logics said:**
> BTW I think you should be working in the office...:rolleyes:
hahaha, I am trying but would like to hear sound notifications for Ubuntu, and preferably get rid of the beep sound from the terminal!

---

### Post by lvlint67 on 2009-09-16
> **makaveli789 said:**
> hahaha, I am trying but would like to hear sound notifications for Ubuntu, and preferably get rid of the beep sound from the terminal!

i want to say the beep in the terminal is somewhere in a menu when you open it.

When you say you heard alerts from windows.... was it just a beep or was it the musical melodies they have?

---

### Post by makaveli789 on 2009-09-16
> **lvlint67 said:**
> i want to say the beep in the terminal is somewhere in a menu when you open it.

When you say you heard alerts from windows.... was it just a beep or was it the musical melodies they have?
 
They were actually musical alerts, like a mail notification message alert or im message alert sound.

---

### Post by makaveli789 on 2009-10-07
Any ideas, anyone? It's getting a little annoying to hear a beep everytime I get new mail in Evolution...

---

