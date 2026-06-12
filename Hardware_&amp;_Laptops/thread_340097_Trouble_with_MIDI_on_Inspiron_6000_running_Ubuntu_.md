---
title: "Trouble with MIDI on Inspiron 6000 running Ubuntu 6.10"
date: 2007-01-16
forum: Hardware &amp; Laptops
---

### Post by Neil Goodman on 2007-01-16
Hello,

I just recently switched over to Ubuntu from WinXP a few months ago. I am very new to Linux, so bare with me please =).

I am trying to run The Elder Scrolls Arena under dosbox. It runs fine, except there is no sound. Looking at the terminal widow that launched dosbox I found the following error message:

```

CONFIG: Using default settings. Create a configfile to change them
ALSA:Can't subscribe to MIDI port (65:0)
MIDI:Opened device:oss
```

I looked up the ALSA error and found a solution that told me to use a command called aplaymidi -l to try and find my midi device. I did this, but no device was listed for me. This is what I get:

```
 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
```

I am on an Inspiron 6000 laptop running Ubuntu 6.10. I don't know how to go about solving this problem. Does my laptop not have midi support? Or do I need some sort of driver?

If anyone could help, it would be greatly appreciated.

---

