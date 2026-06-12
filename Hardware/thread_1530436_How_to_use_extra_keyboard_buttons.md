---
title: "How to use extra keyboard buttons"
date: 2010-07-13
forum: Hardware
---

### Post by Crazedpsyc on 2010-07-13
Hello, I have a AT translated set 2 keyboard (at least that's what many commands tell me) and it has audio control buttons as well as application launching buttons. Most of the buttons work, but I would like to assign commands to the mail button and the Bluetooth button (Which is an odd thing to have considering there is no Bluetooth support ). I tried to use xev to get the keycodes, but for the mail button I got:
```

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  

```
as well as a window saying 
> 
Couldn't execute command: thunderbird 
Verify that this is a valid command."

and for the bluetooth button I didn't get anything at all from xev.
My keyboard is not listed in keytouch, so I don't know what to do.
any ideas?

---

### Post by Tech2077 on 2010-07-13
Have you tried xbindkey-config to set the email button and bluetooth buttons commands?

---

### Post by Crazedpsyc on 2010-07-27
Yeah, I looked at that but it doesn't seem t work.

---

