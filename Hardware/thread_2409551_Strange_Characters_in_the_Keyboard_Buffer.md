---
title: "Strange Characters in the Keyboard Buffer"
date: 2019-01-03
forum: Hardware
---

### Post by CharlesT423 on 2019-01-03
I'm using Ubuntu 18.04 with the Lubuntu desktop for a media centre and I'm having some strange issues with my keyboard both in X11 and on the system console.  Basically every once in a while when I switch my TV receiver back over to the Ubuntu box from the cable TV box I get a lot of junk characters in the keyboard buffer.  X11 seems to filter them out and I just get typing lag, but if I switch over to the console it just keeps repeating the same thing over and over.  It's usually ^[[D but sometimes it's ^@ or another control string.  Pressing enter will cause a linebreak so it's acting like a key is being held down or something. The only thing that seems to make it stop is rebooting.

I thought it was an issue with my wireless keyboard but I swapped that out for a standard USB keyboard and it does the same thing.  I'm wondering if it might be my remote control but unplugging the IR receiver doesn't seem to fix the issue.  In fact unplugging both the keyboard and the IR receiver doesn't stop the key issues.  The IR receiver is an MCE USB unit that seems to work fine with lircd and the keyboard is a Logitech K400.  The system was originally a Ubuntu 16.04 install which didn't have this problem, but I installed a new AMD Radeon 6450 and did a release upgrade to 18.04 over the holidays and it started almost immediately.

---

