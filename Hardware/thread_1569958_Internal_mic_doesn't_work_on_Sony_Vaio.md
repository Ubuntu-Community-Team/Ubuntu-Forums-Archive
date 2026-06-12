---
title: "Internal mic doesn't work on Sony Vaio"
date: 2010-09-07
forum: Hardware
---

### Post by pseudosmart on 2010-09-07
I have a sony vaio VPCF115FM, and I'm running Lucid. Everything works except for the internal microphone. I have checked the sound preferences to make sure it's set to capture from the internal mic, and I have checked the alsamixer too, and have both the captures turned up to 100, but it doesn't capture any sound. I found a link to a patch that can be used to make it work, [http://code.google.com/p/vaio-f11-linux/wiki/EnableMicrophone](http://code.google.com/p/vaio-f11-linux/wiki/EnableMicrophone), but I think you have to recompile the kernel to apply the patch, and that's way out of my league as I am brand new to linux. Does anyone have any other ideas on how to make the microphone work? Thanks in advance.

---

### Post by zecapistolas on 2010-09-09
You can go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc3-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc3-maverick/) and:

[LIST=1]
[*]Install linux-headers-2.6.36-020636rc3_2.6.36-020636rc3.201008300905_all.deb
[*]Install linux-headers-2.6.36-020636rc3-generic_2.6.36-020636rc3.201008300905_(i386 or amd64).deb
[*]Install linux-image-2.6.36-020636rc3-generic_2.6.36-020636rc3.201008300905_(i386 or amd64).deb
[/LIST]

With this you update your kernel. In version 2.6.36 of kernel the problem with ALC275 and internal mic is corrected....

---

### Post by dark.l0rd on 2011-01-08
Hi.. I installed these versions using the software installer..  It doesn't seem to make the mic work.. What do I do ? Thanks in Advance

---

### Post by pseudosmart on 2011-03-14
Thanks so much for those instructions! It worked perfectly for me. I did get a warning message asking if I was sure I wanted to change the kernel or something, but after installing the packages and restarting, my mic picks up everything. Thanks so much!

---

### Post by pseudosmart on 2011-03-14
I should mention that after I installed the packages and restarted, I did install the GNOME Alsa Mixer, and played with the Mic capture a bit before it worked. But it is working perfectly now with Skype and Audacity. Thanks again.

---

