---
title: "No sound with ALSA &amp; snd-intel8x0"
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by wantilles on 2005-07-03
Having been using Gentoo Linux for over a year now and having learned quite a lot about Linux from it, it was time for me to setup and try Ubuntu, mainly for learning its intricancies for installing it to my parents' PC (getting rid of XP).

However, no matter what I do, I cannot get sound output from ALSA.

The same setup works flawlessly in Gentoo with the following setup files:

**/etc/modules.d/alsa**

```
alias snd-card-0 snd-intel8x0
options snd cards_limit=1
```

But there is no **/etc/modules.d** directory in Ubuntu to find the equivalent file and edit it.

My custom compiled Gentoo kernel has the support built-in with only the specific support of the last branch built as a module

```
Linux Kernel v2.6.11-gentoo-r11 Configuration
Device Drivers  --->
  Sound  --->
    <*> Sound card support
    Advanced Linux Sound Architecture  --->
      <*> Advanced Linux Sound Architecture
      <*> Sequencer support
      <M> RTC Timer support
      PCI devices  --->
        <M> Intel/SiS/nVidia/AMD/ALi AC97 Controller
```

I have been using Gnome 2.10 & beep-media-player (with mp3 plug-in) in both Gentoo and Ubuntu, trying to play some mp3 files.

In Gentoo, beep-media-player plays flawlessly via the ALSA output plugin.

However, in Ubuntu, I can only hear sound only via the esound plugin, not via the ALSA plugin.

And yes - before you ask - all master & PCM volumes are unmuted and set to 50%. I have double-checked this with both Gnome Volume Control & console alsamixer:

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer 
&#9474; Card: NVidia CK804           
&#9474; Chip: Realtek ALC850 rev 0   
&#9474; View: Playback               
&#9474; Item: Master                 
&#9474;                              
&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;   
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;   
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;   
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;   
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;   
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;   
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;   
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;   
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;   
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;   
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;   
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;   
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;   
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;   
&#9474;    &#9474;OO&#9474;     &#9474;MM&#9474;      &#9474;OO&#9474;   
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;   
&#9474;   52<>52      0      71<>71  
&#9474; < Master >Master M    PCM    
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
```

The system is an amd64 (running amd64 Gentoo & Ubuntu) with nForce4 SLI chipset.

I am also having the exact same problems (same snd-intel8x0 card) on a x86 system (nForce2 Ultra-400 MCP-T SoundStorm).

---

### Post by felipe on 2005-07-03
you're looking for /etc/modprobe.d/ or /etc/modutils/ those are the mainstream names for 2.6 kernels. ideally all distro's should adopt something similar

...intricacies? huh? o0

EDIT: i have the same sound card (nforce2) and no problem

---

### Post by wantilles on 2005-07-03
[QUOTE=felipe]you're looking for /etc/modprobe.d/ or /etc/modutils/...[/QUOTE]

Both directories exist and in both of them there is a text file named **alsa-base**.

Which file should I edit and what should I add to it?

---

### Post by varunus on 2005-07-03
You can hear sound with ESD but not with ALSA?  I think I know your problem...I also have the same sound card, and there are howtos on these forums on how to get everything playing sound.  Go here:
[http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753) 

Ubuntu has ESD set to use OSS instead of alsa for some reason.  If you set up the dmix and dsnoop ALSA plugins as per that howto, and download libesd-alsa0, you should be good to go.  (I know it works, I wrote the howto that one's based off of...and I have sound working great on my computer.  :) )

If that howto doesn't work for you, try copying /etc/asound.conf to ~/.asoundrc (notice the '.' in front of the file name.

Good luck.

---

