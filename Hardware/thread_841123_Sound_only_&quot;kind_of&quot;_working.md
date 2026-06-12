---
title: "Sound only &quot;kind of&quot; working"
date: 2008-06-26
forum: Hardware
---

### Post by nirkolous on 2008-06-26
Hi

I have a lenovo T61 laptop running lastest Ubuntu. Sound was working fine until I updated some packages. Now the sound works when I start up the computer (African drums -- yay!), but for any applications I run (ahem StarCraft) or when I click the 'volume +' button on my keyboard (I expect a pleasant chirp) I don't get any sound.

However, When I go to System -> Preferences -> Sound and test the sound configuration there, I hear everything great. 

Any idea what to do? Per the sticky in the Multimedia section, I uninstalled the sound packages and reinstalled them, to no avail (though sticky was from 2006 -- maybe outdated?). I have also fiddled with the sound icon and all its various preferences on the top right, to no avail.

Pls help!

---

### Post by blueturtl on 2008-06-26
The latest Ubuntu comes with the new PulseAudio sound server system which bring many new features and enhancements.

Unfortunately the state of PulseAudio support and integration is totally half-assed in 8.04 (Hardy Heron).

You need to fine tune and fix multiple problems by hand, for that the greatest resource for me has been this thread:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

After you have completed the necessary steps in this thread, you can mostly just select PulseAudio as the output method in most applications and it will work wonderfully. In applications that don't properly support PulseAudio you select OSS or ALSA depending on the case.

In my case, Skype and StarCraft (in Cedega) work with OSS output selected.

---

### Post by Odrodzona-Sarmacja on 2008-06-26
Just set everywhere you can do it ALSA as your main sound driver. Then just install alsamixergui package to fix all your problem with sound. Enjoy!

---

### Post by nirkolous on 2008-06-27
> **Odrodzona-Sarmacja said:**
> Just set everywhere you can do it ALSA as your main sound driver. Then just install alsamixergui package to fix all your problem with sound. Enjoy!

tried this. i could manipulate most sound outputs except headphones and speaker (so obv something is very wrong here). why wont it recognize these outputs? no change in my sound situation

---

### Post by nirkolous on 2008-06-27
> **blueturtl said:**
> The latest Ubuntu comes with the new PulseAudio sound server system which bring many new features and enhancements.

Unfortunately the state of PulseAudio support and integration is totally half-assed in 8.04 (Hardy Heron).

You need to fine tune and fix multiple problems by hand, for that the greatest resource for me has been this thread:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

After you have completed the necessary steps in this thread, you can mostly just select PulseAudio as the output method in most applications and it will work wonderfully. In applications that don't properly support PulseAudio you select OSS or ALSA depending on the case.

In my case, Skype and StarCraft (in Cedega) work with OSS output selected.


tried this also, tho no change in my sound situation even when i selected OSS for sound output (you are talking about going into System -> Preferences -> Sound and selecting the appropriate source?)

---

### Post by blueturtl on 2008-06-30
> tried this also, tho no change in my sound situation even when i selected OSS for sound output (you are talking about going into System -> Preferences -> Sound and selecting the appropriate source?)

In here you're supposed to set everything to PulseAudio (after following the guide I previously posted a link to).

Skype it appears has to be spesifically installed an OSS version. You can do that by entering this command into the terminal.

```
sudo apt-get install skype-static-oss
```

---

