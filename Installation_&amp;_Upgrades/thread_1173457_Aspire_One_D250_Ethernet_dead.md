---
title: "Aspire One D250 Ethernet dead"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by Oreo on 2009-05-29
I've installed 9.04 UNRemix on the Aspire One D250 (10 inch) and could not get either Ethernet to work.
Now I've installed the regular Desktop edition of Ubuntu on the machine and also cannot get Ethernet to work.

I don't find this problem mentioned at the [Aspireone Community page]("https://help.ubuntu.com/community/AspireOne").

Has anyone else experienced this?
Is there a fix out there?

Thanks,
Phil

---

### Post by tracker2k on 2009-05-30
Answer is here: [http://forum.mandriva.com/viewtopic.php?p=684093&sid=3d30f5430001cd9ea338a7a13dee076e#684093](http://forum.mandriva.com/viewtopic.php?p=684093&sid=3d30f5430001cd9ea338a7a13dee076e#684093)

Works good for me ;)

---

### Post by Oreo on 2009-05-30
Thanks so much Tracker2k!

Your information did it.

And now I find that there is a similar thread that gives a little bit simpler information:
[http://ubuntuforums.org/showthread.php?t=1141529&highlight=acer+d250]("http://ubuntuforums.org/showthread.php?t=1141529&highlight=acer+d250")

Thanks! I am one happy camper. I was afraid the Ethernet was defective.

---

### Post by Oreo on 2009-06-22
What happens when I upgrade to a new kernal?

Upgrading to /2.6.28-13-generic caused me to lose my Ethernet again.

When I tried to follow the instructions for compiling the driver using sudo in the thread above, I now get:

....stuff/AR813X Ethernet Driver/src$ sudo make install

make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/oreo/stuff/AR813X Ethernet Driver/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
make[1]: *** No rule to make target `Ethernet'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [default] Error 2

---

### Post by Oreo on 2009-06-23
I have asked the above question at
[http://ubuntuforums.org/showthread.php?p=7504636#post7504636]("http://ubuntuforums.org/showthread.php?p=7504636#post7504636")

---

### Post by suomaf on 2009-07-04
Hey Oreo,

Have you fixed your ethernet yet? I am able to compile and get the eth0 working with the recent kernel updates.

Suo

---

### Post by Oreo on 2009-07-22
Sorry for my late reply. 
I haven't gotten my Ethernet with the .13 kernal.
.11 still works. That's how I have booted now.

My wireless using .13 is not connecting!

Help anyone?

---

