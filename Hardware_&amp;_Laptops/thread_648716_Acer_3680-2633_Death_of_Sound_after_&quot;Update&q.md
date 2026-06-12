---
title: "Acer 3680-2633 Death of Sound after &quot;Update&quot;"
date: 2007-12-23
forum: Hardware &amp; Laptops
---

### Post by ebbygonzo on 2007-12-23
I've been running Gusty without a hitch since it's debut and granted I shouldn't leave "automatic update" turned on, but I'm lazy like that.  About a week ago, I woke up my notebook (Acer 3680-2633) and There was an icon indicating:

"Reboot necessary for update to be completed" (or something like that)

So I thought, "Sweet, maybe they fixed something" and did what it told me to do. After reboot, however, the sound just stopped working.  The speaker icon indicates that it is muted, but I get an error stating:

No volume control Gstreamer plugins and/or devices found

Also, If I try to finagle setting under "sound" in  System -> Preferences I get another error when I "test" the ALSA as well as  ESD and OSS:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not establish connection to sound server

I don't know what the heck that update did, but I definitely don't have the skills to fix it.  Any help would be greatly appreciated.

---

### Post by rivera151 on 2007-12-24
I ran into the same problem after the most recent kernel upgrade.  I'm gonna recompile ALSA to see if that fixes it, but this shouldn't be an issue.

---

### Post by rivera151 on 2007-12-24
I came back home and decided to tackle this, and it worked.  Just recompile ALSA; drivers, libraries, and utilities.  The link provided should have all the info you need.  Mind that if you do not have the hda-intel card, you have to change the "--with-cards=X" parameter so that X is your card.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Good luck.

---

### Post by ebbygonzo on 2007-12-24
I took your advice before you responded.  It also worked for me, but now the gnome volume control doesn't work.  I can only adjust volume with the alsa mixer.  Any advise on this?

---

### Post by rivera151 on 2007-12-24
Hmm.  Did you recompile all three?  libs, driver, and utils?  Aside from that, I can't say much more.  Follow the guide, it helps.

---

### Post by ebbygonzo on 2007-12-24
pfff, I'm just a moron.  I got it to work; thanks for the help!:)

---

