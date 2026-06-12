---
title: "Please fix ATI Drivers, or at least give us one that works !"
date: 2009-05-11
forum: Hardware
---

### Post by atarianer on 2009-05-11
Why is it so hard to give us at least one working driver for ATI Cards ?

Right now we have xorg.radeon, xorg.fglrx and the proprietary catalyst driver from ATI.
But none of this is really working 100%.
One does not support older cards, one comes without 3D acceleration and on some hardware combinations no driver works out of the box, instead it makes systems unusable.
This sux and is totally userunfriendly !
So, instead of trying to maintain unstable and buggy drivers, why not spend manpower just on one driver that works on all common ATI Hardware ?

Besides, this sure isn't an ubuntu problem only since i've had similar issues with opensuse 11.x

---

### Post by dE_logics on 2009-05-11
You can have a look at my efforts here - 

[https://answers.launchpad.net/ubuntu/+source/xorg/+question/70366](https://answers.launchpad.net/ubuntu/+source/xorg/+question/70366)

[https://answers.launchpad.net/ubuntu/+source/xorg/+question/70522](https://answers.launchpad.net/ubuntu/+source/xorg/+question/70522)

[http://ubuntuforums.org/showthread.php?p=7230666#post7230666](http://ubuntuforums.org/showthread.php?p=7230666#post7230666)

[https://answers.launchpad.net/ubuntu/+question/69581](https://answers.launchpad.net/ubuntu/+question/69581)

[https://launchpad.net/~tormodvolden/+archive/ppa](https://launchpad.net/~tormodvolden/+archive/ppa)

This is a really good one - 

[http://www.phoronix.com/forums/showthread.php?t=9951](http://www.phoronix.com/forums/showthread.php?t=9951)

---

### Post by ssri on 2009-05-11
someone compiled xserver 1.5.2 for Jaunty, the version that works with 9.3.  Now, I have not tried it myself since I've been busy lately.  I would strongly advise someone to use a test system or partition before replacing their Jaunty xserver.  I would exercise extreme caution.

[http://www.kdedevelopers.org/node/3942](http://www.kdedevelopers.org/node/3942)

---

### Post by atarianer on 2009-05-11
@dE_logics

This shows exactly what the probem is, numerous fixes and workarounds exist but none of them is really usable if you just want to use your ati card "out of the box".
And what makes this situation even worse, the moment a new kernel/module comes via synaptic/updatemanager you have to fix the driver again and again and ...
Too much effort to just get graphics running !

---

### Post by Filippo on 2009-05-11
hi, 
here there are some useful tips :
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

Fil

---

### Post by NoVista on 2009-05-13
[http://ppa.launchpad.net/tormodvolden/ubuntu/pool/main/x/xserver-xorg-video-ati/](http://ppa.launchpad.net/tormodvolden/ubuntu/pool/main/x/xserver-xorg-video-ati/)
[URL="https://launchpad.net/%7Etormodvolden/+archive/ppa"]
[/URL]

---

