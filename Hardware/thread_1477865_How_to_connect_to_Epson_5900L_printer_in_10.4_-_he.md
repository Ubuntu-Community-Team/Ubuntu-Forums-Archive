---
title: "How to connect to Epson 5900L printer in 10.4 - help?"
date: 2010-05-09
forum: Hardware
---

### Post by neilblue on 2010-05-09
Hello,

I have an Epson 5900L and Ubuntu 10.4. I have found this thread which covers installing printer on 8.04 or the 6900l on 9.10, but sadly this doesn't seem to work on 10.4.

Can anyone tell me if they have had success with this on 10.4?

Thanks
Neil

---

### Post by neilblue on 2010-05-09
OK , I have got a little further with this. I have compiled epsoneplijs-0.4.1 from source and with the ps2epl tool I can convert a .ps to an .epl file. This file when sent to /dev/usblp2 manages to print the page, but when run through cups there is no progress :(

I guess if I can get cups to call these commands then it will work?

Any suggestions please :)

Neil

---

