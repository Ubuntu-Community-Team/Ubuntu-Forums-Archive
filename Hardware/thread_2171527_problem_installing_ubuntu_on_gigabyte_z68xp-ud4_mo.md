---
title: "problem installing ubuntu on gigabyte z68xp-ud4 motherboard"
date: 2013-08-31
forum: Hardware
---

### Post by Dylan_White on 2013-08-31
Hi everyone,
I hope you guys can help me out on this - I am new to building computers and have recently put together a new system based on a gigabyte z68xp-ud4 motherboard. However, I have set everything up - got thru' BIOS etc - but when I try to set up a new operating system (my personal choice is Ubuntu or Debian) it doesn't work (ie: the screen goes pixellated and I can't install). I am worried that my board doesn't support Linux as I am not the biggest Windows fan in the world and don't want to be forced into using an operating system I really don't want. Do I have to set up my BIOS in a way that will allow the install of a Linux system? Is there some way around this problem? Guys...I'd really appreciate any help re. this matter.
Thanks.
Dylan.

---

### Post by oldfred on 2013-08-31
Not sure about that model Gigabyte. They released updated UEFI/BIOS for many early UEFI system where old version was very minimal. I might check on that.

Are you installing in BIOS mode or UEFI mode?

But screen issues are related to video. Are you using Intel built in video or a video card and which one? Often nomodeset will get you into system to install proprietary drivers if nVidia or AMD. Intel is supposed to just work but sometimes needs other boot parameters.

 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

