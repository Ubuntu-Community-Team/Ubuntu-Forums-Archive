---
title: "Realtek HD Audio only comes out of headphones"
date: 2007-08-11
forum: Hardware &amp; Laptops
---

### Post by Guyver1 on 2007-08-11
Hi all

complete newbie to linux so bear with me :)

installed ubuntu on my new Alienware m9750 lappy in a dual boot with XP.

the lappy has the Realtek HD Audio 5.1 chipset with 2 built in speakers in the lappy chassis and also a built in volume wheel.

installed hte latest realtek linux drivers v 4.06a.

all installed ok, but

I only get sound through the headphone socket, as soon as i pull my headphones out, nothing.

the volume wheel works perfectly. alsamixer is all on, no mutes, all turned up full.

i'm a bit stumped :/


any help? cheers

---

### Post by Guyver1 on 2007-08-11
oh some info:

Linux m9750 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

---

### Post by ddrichardson on 2007-08-11
There are literaly dozens of threads on this issue already - here's just a few:

[http://ubuntuforums.org/showthread.php?t=302543]("http://ubuntuforums.org/showthread.php?t=302543")
[http://mailman.alsa-project.org/pipermail/alsa-devel/2007-June/001769.html]("http://http://mailman.alsa-project.org/pipermail/alsa-devel/2007-June/001769.html")
[http://ubuntuforums.org/showthread.php?t=479912&highlight=realtek+hda]("http://ubuntuforums.org/showthread.php?t=479912&highlight=realtek+hda")

It would also help if you identify the chipset and codec suing lspci | grep Audio. There are dozens of Realtek chipset configurations.

---

### Post by Guyver1 on 2007-08-11
guyver1@m9750:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

but alsamixer is showing it as:
Chip: Realtek ALC885

it also shows up in XP as Realtek HD Audio

---

### Post by ddrichardson on 2007-08-11
HDA revision 2 has a lot of problems. There are things you can try, some people have reported success with the latest 1.0.14a ALSA after recompiling and specifying the intel-hda; some have had success with altering [alsa-base]("http://ubuntuforums.org/showthread.php?t=314383"); and some have got somewhere by following the [Howto]("https://help.ubuntu.com/community/HdaIntelSoundHowto").

The driver from Realtek's website doesn't help with this card however so that rules that one out.

I have a revision 2 codec that refuses to work full stop. Try the above solutions first - most people with the headphone jack working have got the speakers up to by patching the alsa source - have a look at the bug tracker in [ALSA]("http://https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948").

---

