---
title: "[SOLVED] Alsa default soundcard and hardware ID changes after each reboot"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by Encryptor on 2007-11-20
Hello!

I have been experiencing a problem with the 2 soundcards on my system. I have an integrated HDA Intel soundcard and a PCI Creative Audigy2 sound card.
After each reboot, the sound cards' hardware ID changes every time, so thus the default sound card (0) changes too. After one reboot it is Audigy, after another reboot it is HDA Intel. This is annoying since everytime I boot into the system I have to change the soundcard IDs in the applications themselves.

I have checked the ALSA instructions on how to change the default soundcard, but it wasn't helpful since soundcards are referenced by their ID (i.e. 0, 1, etc) and not by their name or some unique string. And since after every reboot the hardware ID changes, setting the default soundcard to 1 does not help.

I've also searched on the forums and nobody seems to have an answer to this problem. I'm hoping somebody will be able to answer my question this time since I've been having this issue for about a year and I was hoping somebody solved it already.

Information about my system:

```
root@vjp030381:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"

```

```

root@vjp030381:~# uname -a
Linux vjp030381 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

```

```

root@vjp030381:~# cat /proc/asound/cards
 0 [Audigy2        ]: Audigy2 - Audigy 2 ZS [SB0350]
                      Audigy 2 ZS [SB0350] (rev.4, serial:0x20021102) at 0xc880, irq 22
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebf8000 irq 22

```

```

root@vjp030381:~# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).

```

```

root@vjp030381:~# ls /proc/asound
Audigy2  card0  card1  cards  devices  hwdep  Intel  modules  oss  pcm  seq  timers  version

```

It just occured to me.. is it because they are both using the same IRQ number?
Also, I see there is a symlink named Audigy2 in /proc/asound. Can I use the symlink in the ALSA config files to indicate that I want my Audigy2 to be the default soundcard?

Thank you in advance!

---

### Post by Encryptor on 2007-11-23
As usual, the person who asked the question is the one replying ... 

Anyways, for the sake of helping others, here is the solution:

find out the name of the sound card you want to set as the default:

```

[user@localhost] **asoundconf list**
Names of available sound cards:
Audigy2
Intel

```

In my case, I want "Audigy2" to be the default sound card:
```

[user@localhost] **asoundconf set-default-card Audigy2**

```

You don't have to be root to run the above command. Probably it's because the configurations are user specific. If you try to run it as root, the command will execute without errors, but a warning message will be printed out: "Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.".

I have yet to restart and test my changes, but this was what I was looking for; set the default sound card by name, not by hardware ID.

Good luck to you all who have the same problem!

P.S.: I found the "asoundconf" command by accident, I was looking at the results of the "locate asound" command, I was trying to find asound.conf, because apparently /etc/asound.conf doesn't exist on my system. Talk about pure luck :D

---

### Post by p$y on 2007-11-23
thanks, I hope this works for my myhtbuntu machine, too ;-)

---

### Post by harelguy on 2008-02-12
Thanks alot!
This does the trick for Gutsy with a Sound Blaster Live 5.1 as well.

---

### Post by rare HERO on 2008-02-27
Thanks. Just what I was looking for.

---

