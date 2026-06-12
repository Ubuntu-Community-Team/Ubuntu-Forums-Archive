---
title: "No sound on Chaintech AV-710!"
date: 2005-02-13
forum: Hardware &amp; Laptops
---

### Post by phend-one on 2005-02-13
I finally got the chance to install ubuntu 4.10 (warty) on my computer. I love everything so far, but there's no sound.

My sound card right now is the Chaintech AV-710. It has two DACs, and one gives better quality sound (Wolfson DAC).

I need to find out how to enable it?

The closest solution I got was from [Head-Fi - Chaintech AV-710 Graphical Setup](http://www6.head-fi.org/forums/showthread.php?t=75655) (scroll down for Linux section).

> 
Linux

These instructions on getting the high sample rate mode to work under Linux with ALSA were originally posted by Head-Fi member ADS at [www.vandemar.org](www.vandemar.org)


Quote:
Originally Posted by ADS
In order to get the Chaintech AV-710 to run in high-res mode and use the superior Wolfson DAC, download the asound.state file here(mirror). Copy this to your /etc/ directory as root, and run &#8216;alsactl restore&#8217;. This will enable the high-resolution jack. Notice that this will not mute the volume on your speaker outputs (unlike the windows version), so you can listen to your headphones and speakers at the same time. It&#8217;s a fun effect, but you&#8217;ll probably want to disable it. To do this, open up alsamixer and mute the &#8216;Master&#8217; and &#8216;Master Mono&#8217; controls. If you want your speakers muted by default, then after alsamixer run &#8216;alsactl store&#8217;. If still haven&#8217;t figured out how to get the card into 96000 Hz sampling mode without problems, so if someone could get that to work I&#8217;d appreciate it. I know it has something to do with the &#8216;Multi Track Internal Clock&#8217; setting. To play around with it you can use &#8216;amixer cset numid=43&#8242;.

Let me know if this works, and if anybody has any luck getting it to run at 96000 Hz.
 


I have tried to do what the guide has said, but it is very vague, and I am very new to Linux.


Anyone know what this means?
Any suggestions would be helpful!

Thanks!

---

