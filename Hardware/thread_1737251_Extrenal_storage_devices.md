---
title: "Extrenal storage devices"
date: 2011-04-23
forum: Hardware
---

### Post by shade_oracle on 2011-04-23
Aside from USB's my laptop cant seem to detect the tera-byte drive and external card reader.  Any thoughts on how to get them to work.  Btw have installed the desktop version on my laptop.

---

### Post by varunendra on 2011-04-23
Please provide some more details. Like these may help:

[LIST]
[*]Brand and model of your laptop
[*]Which desktop version have you installed? If you are not sure, just post output of these commands: ```
lsb_release -a
``` ```
uname -a
```
[*]When you say 'terabyte drive', do you mean the internal drive? (I'm a bit confused because you said "Aside from USB's..")
[*]Is there any other (working) OS on the laptop or is Ubuntu the only one now?
[/LIST]
Besides these, if you can get into BIOS, find and see in which mode USB is being used. I guess 'legacy mode' should help if the option is there. (perhaps something like- support for legacy USB: "Enabled")

I'm assuming your 'terabyte' drive is an external one, and the internal one is detected and working fine. Please correct me if I am wrong.

---

