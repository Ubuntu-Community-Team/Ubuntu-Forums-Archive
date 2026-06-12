---
title: "Pulseaudio Skype Mic question ..."
date: 2009-11-05
forum: Hardware
---

### Post by abominable on 2009-11-05
After a lot of time (and negative votes) I decided to install pulseaudio, since sound in my 9.10 system was not working properly. And I must admit that solved almost all of my sound problems. All is left is a small one. My mic works perfectly. I tested it under audacity. But when it comes to skype I can't get it working. In skype preferences, all my sound devices options is "PulseAudio Server (local)". I have no other option, but mic still doesn't work.The thing now is that I don't know what could I search for solving this.

Thanx in advance for any help.

---

### Post by Lee2eel on 2009-11-05
The problem is with skype 2.1.  I had the same issue, I basically uninstalled skype 2.1 completely.  Then I downloaded skype 2.0 and when you go into the sound settings it now allows you to choose other options in the dropdown menu.

---

### Post by Jiawen on 2009-11-12
I'm having the same problem with Skype 2.10, and since Skype 2.0 randomly hangs, it looks like I have a choice between Skype that hangs or Skype that doesn't actually access my sound devices. :(

---

### Post by abominable on 2009-12-11
Finally solved !!!

```
padevchooser
```

And then pick padevchooser > volume control > Recording > show :: All streams

Then Skype > Options > Sound devices > make a test call and play around with the options given in the volume control panel from the padevchooser.

---

### Post by nossifer on 2009-12-14
> **abominable said:**
> Finally solved !!!

```
padevchooser
```

And then pick padevchooser > volume control > Recording > show :: All streams

Then Skype > Options > Sound devices > make a test call and play around with the options given in the volume control panel from the padevchooser.

Thank you so much.  Worked.
For those who need a touch more explanation (it isnt too intuitive)
Launch padevchooser, and keep the Volume Control window open.  Then, do a test call.  Only then will you be able to see it in the Control.  Make your changes there, and you will be AOK to make your real call just after that.  At least, that is how I am doing it for now.

---

### Post by yelvington on 2009-12-15
I had a similar problem; fixed it by unchecking Skype's option to automatically control the sound level.

---

