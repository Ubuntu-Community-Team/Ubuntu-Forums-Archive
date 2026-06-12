---
title: "nO SOUND"
date: 2008-07-15
forum: General Help
---

### Post by Professore on 2008-07-15
&#921; &#919;&#913;ve A Problem With Sound On My Computer. I Use Ubuntu 8.04 And Have No Sound. I Cant Install Any Drivers. What Do I Have To Do???

---

### Post by jonian_g on 2008-07-15
Do you have two soundcards on your computer? One onboard and one pci/external?

If not, give us some more info. The soundcard model?

---

### Post by Professore on 2008-07-15
onboard. msi

---

### Post by jonian_g on 2008-07-15
The exact model of the sound card or the motherboard please.

---

### Post by Professore on 2008-07-15
where can i see that?

---

### Post by Professore on 2008-07-15
Ck804. That Is The Code That The Hardware Testing Gives Me When I Check The Sound

---

### Post by PGScooter on 2008-07-15
I don't know too much, but I think you could find sound information using the code:
```
sudo lshw
```
It's going to be a long output, but I think you should be able to recognize what your sound card is.
You might also find useful information with
```
sudo lspci
```

However, the first thing I would try if I were you is:
```
alsamixer
```
what comes up? Is the first column muted?

---

### Post by jonian_g on 2008-07-15
In the stuff (books) you got with your computer or open you case and look at the corners of the motherboard.

---

### Post by Professore on 2008-07-15
Msi Ms-7125

And

Ck804 Ac'97 Audio Controller

---

### Post by jonian_g on 2008-07-15
So it is an Nvida Ck804 On Board Sound Card...

---

### Post by Professore on 2008-07-15
> **jonian_g said:**
> so It Is An Nvida Ck804 On Board Sound Card...

Yes

---

### Post by Squid Tamer on 2008-07-15
This may sound REALLY, REALLY stupid, but make sure your speakers are plugged in and/or in the right port. That got me when I put Ubuntu on my computer.

---

### Post by Professore on 2008-07-15
> **Squid Tamer said:**
> This may sound REALLY, REALLY stupid, but make sure your speakers are plugged in and/or in the right port. That got me when I put Ubuntu on my computer.

....YES...THATS IT....
#-o#-o#-o

THANK YOU MAN YOU ARE A GENIUS!!!

---

### Post by jonian_g on 2008-07-15
It seems that there is a problem with this soundcard:

> [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg883738.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg883738.html)

Public bug reported:

I am using kubuntu 8.04 with all updates installed. I have an Asus A8N-
sli premium motherboard. Sound was working when I was using kernel
version 2.6.24-16-generic. When I upgrade to a later version, I have
tried 2.6.24-17-generic and 2.6.24-18-generic, sound card does not work.
I have reverted back to kernel version 2.6.24-16-generic as sound is
working with it.

When I run "lspci | grep audio" I get:

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97
Audio Controller (rev a2)

When I run "aplay -l" to list audio devices I get:

aplay: device_list:205: no soundcards found...

I have tried to see if a module is loaded using "lsmod | grep snd",
nothing is returned.

** Affects: ubuntu
     Importance: Undecided
         Status: New

-- 
CK804 AC'97 Audio does not work with kernels after 2.6.24-16-generic
[https://bugs.launchpad.net/bugs/240094](https://bugs.launchpad.net/bugs/240094)
You received this bug notification because you are a member of Ubuntu
Bugs, which is subscribed to Ubuntu.

So my advice is to use kernel 2.6.24-16

---

