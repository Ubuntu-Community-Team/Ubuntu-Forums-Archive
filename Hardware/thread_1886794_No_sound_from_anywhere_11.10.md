---
title: "No sound from anywhere? 11.10"
date: 2011-11-25
forum: Hardware
---

### Post by undeadxombie on 2011-11-25
Hello, I am quite new to basically everything, and not as knowledgeable as others (considering i'm 17). So my dad gave me his old Gateway M675prr notebook, running Ubuntu 11.10. The only problem was the Wireless firmware was missing, and no audio worked anywhere. Even the headphone jack doesn't play sound. Last night I researched on the forum and found a command line that i just copied and pasted into Terminal, which then downloaded the necessary drivers for the Wifi to work. Is there anything of that sort I can do with my soundcard to perhaps fix this problem? If it helps, my soundcard is a:
Intel ICH5 with STAC9758 at 59 irq 17... I don't know what this means, but its all i can find out about my soundcard... any help?

---

### Post by S_p_or_t_o on 2011-11-25
i just posted about that in [http://ubuntuforums.org/showthread.php?t=1886818]("http://ubuntuforums.org/showthread.php?t=1886818").

open a terminal window and enter the follow three commands
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

---

