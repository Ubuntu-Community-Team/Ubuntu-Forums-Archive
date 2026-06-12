---
title: "Speakers not showing up"
date: 2013-08-22
forum: Hardware
---

### Post by UncleMonty on 2013-08-22
The speakers on my PC (which runs ubuntu 12.04) are no longer working. They work fine on other computers. I have tried them in both ports and neither work. Can anything be done about this? Is this a sympton of old age creeping up on the machine? (It's nearly seven years old) 

What information about the hardware is relevant?

---

### Post by VMC on 2013-08-22
Not sure what is meant by both ports? Are you referring to the small RCA "pink, blue, green" ports?

---

### Post by Yellow Pasque on 2013-08-22
Try a LiveUSB/CD. If sound works, then it's not the machine itself. This can be helpful too: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by UncleMonty on 2013-08-22
> **VMC said:**
> Not sure what is meant by both ports? Are you referring to the small RCA "pink, blue, green" ports?

Yes sorry I should clarify that - there's a pink, blue and green port on the back and another set on the front. Neither can see the speakers.

---

### Post by VMC on 2013-08-22
Output this command:
```
 lsmod | grep "sound\|snd"
```

Also:
```
lspci
```

---

### Post by BuntuSeriously on 2013-08-22
As Temüjin hinted, I'd rule out the distro install first, then consider the hardware.  Sound issues can be spooky with some installs.

BTW -- The green plug is convention for preamp output to external speakers...

Best wishes --

---

