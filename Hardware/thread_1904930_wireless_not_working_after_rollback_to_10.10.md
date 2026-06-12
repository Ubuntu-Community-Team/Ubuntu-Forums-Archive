---
title: "wireless not working after rollback to 10.10"
date: 2012-01-05
forum: Hardware
---

### Post by hpjanszen on 2012-01-05
I have a Dell V13 with BCM4312 & b43 driver. All network connections cable and wireless worked fine before I updated to 11.10 and then rolled back to 10.10. Now wired network connections are working but wireless sees signals, claims to be connected but isn't - then asks again and again for passphrases and eventually disconnects and disables wireless. Reinstalling the driver doesn't make any difference and none of the other advice I've found here on the forums has worked to solve the problem. Help please.

---

### Post by bluexrider on 2012-01-05
here is the official Ubuntu docs on BCM43** card

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Hopefully this helps

---

### Post by hpjanszen on 2012-01-06
I've already been through the process in the link above a number of times. I activate the STA driver and restart (the b43 driver then shows as not activated) - no wireless connection. Then I activate b43 and restart. Wireless connections now show (and STA is not activated) but after numerous tries to complete the connection Ubuntu gives up and disconnects wireless. Is there some way to activate both? Are they independent? should it work with either one or are both required?:confused:

---

