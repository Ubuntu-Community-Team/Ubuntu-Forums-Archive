---
title: "no sound on asus laptop"
date: 2011-04-04
forum: Hardware
---

### Post by kelvin27 on 2011-04-04
Hi all forum users!
I've ubuntu 10.10 over asus series x52 laptop...the sound doesn't work and alsamixer recognizes the card as a Conexant CX20585.
I tryed all, like this [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules) but no result.
The strange is that when I start the system I can heard the ubuntu login sound but since when I'm logged then I can't heard nothing.
Can you give me an help, please?
Thank you very much, bye.

---

### Post by lidex on 2011-04-05
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by kelvin27 on 2011-04-05
hi lidex, this is the link to the alsa information:
[http://www.alsa-project.org/db/?f=eeeba5fbcba026d6396c973e84f1cdf870129ada]("http://www.alsa-project.org/db/?f=eeeba5fbcba026d6396c973e84f1cdf870129ada")

As you can see, I've the 1.0.24 alsa release, because I tried to install it following the instruction taken here:
[http://duopetalflower.blogspot.com/2011/02/alsa-1024-in-ubuntu-1010.html]("http://duopetalflower.blogspot.com/2011/02/alsa-1024-in-ubuntu-1010.html")

But the sound doesn't work (and doesn't work before of this).

Thank you very much for your help, bye

---

### Post by lidex on 2011-04-05
Yeah that upgrade was botched. Re-install alsa then run the script again:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by kelvin27 on 2011-04-06
Hi lidex, I have done what you advice me, this is the new link:
[http://www.alsa-project.org/db/?f=d2a2f16da0fa13095bb747fc653b5a460c1297dd]("http://www.alsa-project.org/db/?f=d2a2f16da0fa13095bb747fc653b5a460c1297dd")

No card are recognized by the system...but we can see, by the link,  that there are already the newest release of the alsa driver...

Thank you again! Bye

---

### Post by lidex on 2011-04-07
It didn't work. You'll need to re-install again, but the kernel may need to be re-configured. Reboot into a different kernel then open synaptic. Search that kernel number (2.6.35-28-generic). The two packages that show up as installed (headers and image) mark for complete removal then apply. Now reboot and this in a terminal:
```
sudo apt-get update
sudo apt-get upgrade
```
If it doesn't offer to install that kernel, go into synaptic and manually select for install, apply, reboot. Now run the alsa info script again.

---

### Post by kelvin27 on 2011-04-07
Hi lidex, I did all you adviced me, but the result is the same...this is the new link:
[http://www.alsa-project.org/db/?f=851ecc5e7650332593d922481635716d5886a496]("http://www.alsa-project.org/db/?f=851ecc5e7650332593d922481635716d5886a496")

thanks a lot!

---

### Post by lidex on 2011-04-08
Try post #4 again.

---

### Post by kelvin27 on 2011-04-09
I did it, but the result is the same, again:
[http://www.alsa-project.org/db/?f=21f88d02f6e7a1216d740ce545f108f79c13938c]("http://www.alsa-project.org/db/?f=21f88d02f6e7a1216d740ce545f108f79c13938c")

Nevermind, with the kernel 2.6.35-27 it works...

Thanks anyway!

---

### Post by lidex on 2011-04-10
> **kelvin27 said:**
> I did it, but the result is the same, again:
[http://www.alsa-project.org/db/?f=21f88d02f6e7a1216d740ce545f108f79c13938c]("http://www.alsa-project.org/db/?f=21f88d02f6e7a1216d740ce545f108f79c13938c")

Nevermind, with the kernel 2.6.35-27 it works...

Thanks anyway!

As long as it works;)

---

