---
title: "Nvidia current : Can't manage to it install correctly"
date: 2013-06-18
forum: Hardware
---

### Post by rXp on 2013-06-18
Hello,

For several days (5 days), I tried everything I saw on the internet to install those drivers. I reinstalled ubuntu or kubuntu at least 20 times both.
I tried installing nvidia-current with "additional drivers" or with the repository x-swat or manually by downloading them on nvidia.com or with aptitude.
Every time I end up with a unity broken or on kubuntu a resolution of 640*480 with no opengl or anything working.

I have hit rock-bottom, please help me !

I have a laptop Dell-XPS702X (17"), my graphic card is a Nvidia 555m and I use a x64 ubuntu OR kubuntu (either way I'm good).
I'm installing ubuntu once again, so I can try whatever you think could work.

I have tried everything with a clean install in here [http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html).
I also tried to reinstall lightdm after installing the driver...

Please help me I don't want to go back to Windows ](*,)

Best regards,

rXp>!<

---

### Post by oldfred on 2013-06-18
Is this a dual video system?

       nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)


 Some discussion of limits of new nVidia driver with some Optimus support
[http://ubuntuforums.org/showthread.php?t=2142215](http://ubuntuforums.org/showthread.php?t=2142215)
Installing new nVidia driver 319.12 beta
[http://www.barunisystems.com/index.php/site/page?view=blog](http://www.barunisystems.com/index.php/site/page?view=blog)
The problem was caused by another technology by Intel called the Integrated Network Interface Controller (NIC) that was conflicting with my USB controller that prevented my LiveUSB from working

Often the drivers are the same across Dell models. Not sure if this applies or not.

 Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)

---

### Post by rXp on 2013-06-19
Thank you :)

I see that it is not really optimus supported like I wanted it.
Actually what I need is a way to run opengl application with my 555m.
Bumblebee should work (used it before) but it doesn't really work with steam.

---

