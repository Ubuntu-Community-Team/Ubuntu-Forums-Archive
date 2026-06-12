---
title: "Amarok libnjb dependency problem"
date: 2006-10-25
forum: Hardware &amp; Laptops
---

### Post by Abaddon on 2006-10-25
Running the Gnome Edgy RC.

I have a Creative Zen Vision M that I've successfully gotten to work with Gnomad (courtesy of [this]("http://www.ubuntuforums.org/showthread.php?t=199250&highlight=creative+zen+vision+m") thread).

I'd heard that Amarok had support for MTP players, and that it was an excellent media program - even for people that use Gnome.

I installed Amarok, only to discover that one of its dependencies - libnjb5 is incompatible with one of the gnomad dependencies - libnjb.  Both of these libraries have the same version number, so I wonder if they are actually the same library just renamed.

In any event, with the Gnomad files not installed, but with amarok and the libnjb5 installed, Amarok still doesn't recognise my media player, so it looks like I'll be sticking with Gnomad and Rhythmbox for now.

If anyone has any ideas, I'd be pleased to hear them.

---

### Post by senzapadroni on 2006-10-27
Unfortunately, you have to compile Amarok from sources enabling MTP support in this way:
```
./configure --with-libmtp
make
sudo make install
```

---

### Post by Abaddon on 2006-10-31
Error message from ./configure:

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

What is the --prefix= setting I have to use to fix this?

---

### Post by senzapadroni on 2006-10-31
Hi Abbadon,
I solved the problem by upgrading Amarok to 1.4.4 that includes native support for MTP devices. Check it at [http://amarok.kde.org]("http://amarok.kde.org")

---

### Post by Abaddon on 2006-10-31
Unfortunately, 1.4.4 doesn't seem to want to detect my Vision:M.

Do you select NJB Media device, or should there be another option for MTP?  I thought it would just work without needing recompiling.

---

### Post by senzapadroni on 2006-11-01
> **Abaddon said:**
> Do you select NJB Media device, or should there be another option for MTP?  I thought it would just work without needing recompiling.

I simply selected Creative Nomad Jukebox from Devices list, gave it a name (ie 'Zen') and then connected.

---

