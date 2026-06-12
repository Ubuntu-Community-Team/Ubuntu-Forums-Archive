---
title: "No sound"
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by Mission 10 on 2005-12-14
Ok, I really like Ubuntu and the install and setup was relativly easy even for a linux n00b like myself. But I'm having a problem with the sound.. well.. lack thereof. Is there any known problems with sound and Dells? I have a Dimension 3000 btw. Any help would be appreciated. 

**Edited for content error**

---

### Post by Gandalf on 2005-12-14
[QUOTE=Mission 10]Ok, I really like Ubuntu and the install and setup was relativly easy even for a linux n00b like myself. But I'm having a problem with the sound.. well.. lack thereof. Is there any known problems with sound and Dells? I have a Dimension 3000 btw. Any help would be appreciated.[/QUOTE]
can we have more informations? do you have any errors when you do 
```

dmesg | more

``` at the command line?

what happens if you type at the command line
```

killall esd && esd &

```

---

### Post by Mission 10 on 2005-12-14
I really could find any device errors or anything regarding sound in the "dmesg | more" 

And "killall esd && esd &" didn't do anything.

---

### Post by Mission 10 on 2005-12-14
Should I be looking for anything specific in the "dmesg" log?

---

### Post by Gandalf on 2005-12-14
well if there is anything about loading alsa it must be in dmesg now if you can't hear any sound by killing and launching esd i'm afraid that there's some problem with the configurations of ur card

---

### Post by Mission 10 on 2005-12-14
Hmm.. it's weird. It's not a 3rd party card, its onboard sound. If I had a usb midi sound input attached, could it be confusing the kernal on which one is actually supposed to be used for playback?

---

### Post by Gandalf on 2005-12-14
well try to boot without it and see if sound works

---

### Post by Mission 10 on 2005-12-14
Nope. Still no audio. So how does one reconfig the audio. Any guides or tutorials I can check out?

---

