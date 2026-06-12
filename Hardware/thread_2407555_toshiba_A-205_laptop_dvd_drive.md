---
title: "toshiba A-205 laptop dvd drive"
date: 2018-12-05
forum: Hardware
---

### Post by acefromspace on 2018-12-05
It seems my old laptop (toshiba A-205) has finally worn out the optical drive (dvd/cd writer/reader) Need advice on replacement drive, or should I just use external USB optical drive? I have many videos on dvd... must have an optical drive. Having trouble finding one on amazon.
Funny thing is the drive (as old as it is) was very clean and working fine, then I did fresh install of ubuntu 14.04 and tried to burn a music cd with k3b... no optical drive detected (still hear it working mechanically) Now it won't even work on data dvds I have (does not mount) Any advice welcome (except get a new laptop) I will try booting a live ubuntu dvd just to be sure... will post results soon. What do I type in terminal to check if current drive is OK?

---

### Post by acefromspace on 2018-12-05
I got into the BIOS and will not let me boot from optical drive (dvd/cd) I will assume the drive is dead. Need command to verify this in terminal.

---

### Post by crip720 on 2018-12-05
Can't help about finding if dvd is dead, but would go with inexpensive external drive or if you want a replacement try ebay.  Lots on there but watch for shipping charges.

---

### Post by acefromspace on 2018-12-06
Update: it works! Not sure why. I did three things... cleaned lens with a q-tip (it was very clean so don't think that was an issue) changed setting in k3b to don't eject disc (suggestion from another thread) and waited till it was warm (I live up in the mountains... can be very cold in the mornings and have had this issue before) I would mark this as solved, but don't really know why it now works. I was just about to order external dive (very cheap) but no need for now. Sorry if this is not helpful to others, but don't assume your drive is toast.

---

### Post by acefromspace on 2018-12-18
update: got ubuntu live dvd to boot, got a data dvd to work, got another dvd to work, so I opened k3b to burn a dvd (iso) and once again... no optical drive found. This is driving me nuts! I'm trying to determine if this is a hardware issue (dvd drive seems to be going through the ususal routine, but then stops) or a software issue (seems to be related to k3b) A few threads mentioned issues with k3b. My friend has a similar laptop to mine (slightly older, but also toshiba satellite) so I might try swapping his drive for mine (his drive was not used much)

---

### Post by acefromspace on 2019-05-11
Seems to be working fine now. Noticed issues were with cheap dvds, especially memorex. both blanks and burned ones. They are all old dvds.

---

### Post by him610 on 2019-05-11
FWIW, I quit buying internal CD/DVD drives years ago. For quite awhile I have been using an external drive whenever I needed to read/write to a CD/DVD. I have also found that *xfburn* is a very reliable application - longtime user.

---

