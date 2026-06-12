---
title: "Sound stopped working"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by bubbawv on 2006-11-04
When I installed Unbuntu about 5 months ago the sound work flawlessly.  After an update in the recent past the sound stopped working.  I have not noticed any error during boot.  I have tried restarting alsa but all I get is a small  "pop" from the speakers.  Does any one have any suggestions?  I'm using 6.06 and my sounds card is a C-Media PCI CMI8738.

---

### Post by andradelipe on 2006-11-04
have you tryed:

$> sudo alsaconf

??

---

### Post by bubbawv on 2006-11-04
Yes, but the command can not found.  I did a seach and it is not installed.  I also tried removing the ALSA packages then reinstalling them but that did not work either.

---

### Post by mcg on 2006-11-04
Hmm, I'm running 6.10 and an update today broke my sound as well.

---

### Post by chriscando on 2006-11-04
Perhaps try running alsamixer and just make sure its not being muted or too low

---

### Post by bubbawv on 2006-11-05
I checked alsamixer and the only thing turned off is the mic boost.  I have found that muting/unmuting master will give me a small pop form the speakers.  Other than that, still no sound.

---

### Post by Othersider on 2006-11-05
Same problem here.  Sudo alsaconf results in "command not found."

---

### Post by mcg on 2006-11-05
I don't think alsaconf is in Edgy.  It's in the alsa-utils package in Debian, but is missing from that package in Edgy.  I have a well supported SB-Live card that has worked flawlessly from Warty -> Edgy, until a very recent update.  This isn't good.

---

