---
title: "Sound not working in Ubuntu 11.04 (C-Media Electronics Inc CMI8788)"
date: 2011-04-15
forum: Hardware
---

### Post by glh5 on 2011-04-15
Hello,

I have Ubuntu beta 11.04 (latest version) running on a machine with a sound card with the C-Media Electronics Inc CMI8788 chipset. According to the alsa page, this chipset is **[supported](http://www.alsa-project.org/main/index.php/Matrix:Module-oxygen)**. However, **[here](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus)** it says I should use PulsedAudio (?). Anyway, when I'm trying to follow the first guide I get on a complete dead end. Maybe this is because the guide was written in 2008 and no edits have been made ever since. 

Anyway, it tells me to use /proc/asound/cards at some point but there is no such thing in the most recent version of Ubuntu.

I have to edit /etc/modules.conf or /etc/modutils but neither of them exist.

I have to use alsamixer. The mixer is installed and it's the most recent version, but this is the error message I get. 

```
cannot open mixer: File or directory doesn't exist

```

Can somebody point me in the right direction to get this working or should I just buy a sound card that has better support?

---

### Post by oscar1977 on 2011-09-23
I just bought Asus Xonar DS PCI 7.1 (CMI8788) on my desktop, and still couldn't make it work.

I will write back if I find something.

---

### Post by nazaroo2 on 2012-01-31
Did you get your xonar card working?
I have a xonar DG  and haven't figured out how to get system to see it.

---

