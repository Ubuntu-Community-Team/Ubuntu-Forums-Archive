---
title: "Using 2 identical sound cards?"
date: 2009-01-10
forum: Hardware
---

### Post by redxine on 2009-01-10
I had two Creative SB sound cards I decided to throw in my computer. I can output/input from the cards just fine in Audacity, but the volume control for ALSA thinks that the two cards are the same, and so I cannot independantly control the audio of both of them. For example, if I turn down the volume on the first card primary, then the second one gets turned down also. Here's my lspci:

```
00:0f.0 Multimedia audio controller: Creative Labs SB Audigy LS
00:10.0 Multimedia audio controller: Creative Labs SB Audigy LS
```

Thanks in advance.

---

### Post by damis648 on 2009-01-10
What if you try to use alsamixer? Open a terminal and
```
alsamixer
```

---

### Post by markbuntu on 2009-01-10
You can use aliases for the cards that will allow alsa to distinguish between them.
There is a link to more than one sound card and things you can do with alsa from here

[http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)


There is also a guide here for multiple sound cards that may help.

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

### Post by redxine on 2009-01-11
Thank you. Your help is appreciated.

---

