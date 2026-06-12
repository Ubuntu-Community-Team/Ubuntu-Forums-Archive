---
title: "Sound works, but only part-time"
date: 2005-07-04
forum: Hardware &amp; Laptops
---

### Post by djpenguin on 2005-07-04
I'm working on setting up ubuntu on an ASUS Z71A (Dothan 2GHz) laptop for a friend.

The installation went fine, but I've still got a couple problems.

The strangest one is the sound.  ALSA seems to be properly configured, and when the machine boots, it does play a little drumbeat sound at the login splash.  I can use alsamixer, and everything seems fine, but xmms will not play sounds.

This is, to say the least, incredibly confusing.


Any help would be greatly appreciated

---

### Post by PMO6022 on 2005-07-04
[QUOTE=djpenguin]I'm working on setting up ubuntu on an ASUS Z71A (Dothan 2GHz) laptop for a friend.

The installation went fine, but I've still got a couple problems.

The strangest one is the sound. ALSA seems to be properly configured, and when the machine boots, it does play a little drumbeat sound at the login splash. I can use alsamixer, and everything seems fine, but xmms will not play sounds.

This is, to say the least, incredibly confusing.


Any help would be greatly appreciated[/QUOTE]

Try checking the output plugin selected in xmms, under "options" -> "preferences".

You can also click configure for the CD Audio Player input plugin on that same preferences screen. The play mode should be "digital audio extraction"

Good luck

---

### Post by djpenguin on 2005-07-04
Yeah, it's set right.

I tried noodling around with the Multimedia Systems preference tab, and I'm not sure what it's telling me.  When I set the top entry (input sink) to ESD, and hit the test button, it makes a tone.  Nothing makes a tone when selected from the output drop-down menu

Where are the text files that control these functions?  I tried looking in the places I'm used to looking from working with gentoo, but found nothing.

---

### Post by raghav_p on 2005-07-04
Isn't this the problem with ALSA not accepting more that 1 source at a time?

I had this problem when I started with Ubuntu too. I found the solution by googling around for "sound problems ubuntu 5.04 ALSA multiple source" or some other variant. Hope this helps. :)

---

### Post by raghav_p on 2005-07-04
Here:

[LINK](http://ubuntuforums.org/showthread.php?t=32063)

---

### Post by PMO6022 on 2005-07-04
I'm using the eSound Output Plugin 1.2.10 [libesdout.so] as the output plugin in xmms, not alsa.

---

### Post by raghav_p on 2005-07-04
I believe the afforementioned guide is applicable for ESS as well as ALSA.

---

### Post by djpenguin on 2005-07-04
That guide worked just fine.

Thanks for the prompt help.

Now if I could only [get ssh working](http://ubuntuforums.org/showthread.php?t=46425)

---

