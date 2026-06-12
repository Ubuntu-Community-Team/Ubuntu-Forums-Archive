---
title: "how to find the keycodes from remote control input."
date: 2010-09-26
forum: Hardware
---

### Post by ost2life on 2010-09-26
Hi, I have an emprex 3009URF remote control which shows up on lsusb as ```
Bus 004 Device 004: ID 046e:5577 Behavior Tech. Computer Corp. 
```

Is there any way that I can work out exactly what the remote is sending in terms of input, so that I can work out how to edit the keyboard xml file for xbmc, so far as I can tell the keys 0-9 are mapped to 0-9, "Clear" is mapped to escape, "Enter", * and # are mapped to Enter * and £ (UK layout)
and a few other buttons seem linked to key presses but others appear to be dead in that they have no discernible effect or input but something must be sent

---

### Post by kyle911 on 2010-09-27
I think the command "xev" is what you are looking for.
also, some of the stuff from this link might help:
[https://help.ubuntu.com/community/MultimediaKeys](https://help.ubuntu.com/community/MultimediaKeys)

---

### Post by ost2life on 2010-09-29
thanks for your help, xev only gave me limited help though, as some of the keys didn't register an input through it, even though they appeared to send something. any advice?

---

