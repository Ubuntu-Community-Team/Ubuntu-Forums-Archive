---
title: "Hasee: headphones do not mute speakers"
date: 2008-08-20
forum: Hardware
---

### Post by Marzian on 2008-08-20
Hello,
I'm using a Hacee WQ280 laptop with Kubuntu 8.04 and as audio device Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03).

When I plug-in the headphones they work, but the problem is that audio still comes out from the speakers.

It only happens in Kubuntu, but not in Windows.

Thank you for your help,

-- Marzian (Italy)

---

### Post by sergiom99 on 2008-08-20
I fixed mine following this howto, but I have a different soundcard.

[http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750)
scroll to "**Fixing the Sound Card**" section.
Maybe it helps.

Or: check this thread [http://ubuntuforums.org/showthread.php?t=707231&highlight=Intel+Corporation+82801H+headphone](http://ubuntuforums.org/showthread.php?t=707231&highlight=Intel+Corporation+82801H+headphone)
Or: search the forums for your soundcard model.

---

### Post by Marzian on 2008-08-20
Updated Alsa to 1.0.17 (using this script: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)).

Now, i'm not sure about how to modify /etc/modprobe.d/alsa-base

I've added "options snd-hda-intel model=auto" at the end of the file but I still have double audio.

I have Realtek ALC883, so my options are:

ALC883/888
858		  3stack-dig	3-jack with SPDIF I/O
859		  6stack-dig	6-jack digital with SPDIF I/O
860		  3stack-6ch    3-jack 6-channel
861		  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
862		  6stack-dig-demo  6-jack digital for Intel demo board
863		  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
864		  acer-aspire	Acer Aspire 9810
865		  medion	Medion Laptops
866		  medion-md2	Medion MD2
867		  targa-dig	Targa/MSI
868		  targa-2ch-dig	Targs/MSI with 2-channel
869		  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
870		  lenovo-101e	Lenovo 101E
871		  lenovo-nb0763	Lenovo NB0763
872		  lenovo-ms7195-dig Lenovo MS7195
873		  haier-w66	Haier W66
874		  6stack-hp	HP machines with 6stack (Nettle boards)
875		  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
876		  6stack-dell	Dell machines with 6stack (Inspiron 530)
877		  mitac		Mitac 8252D
878		  auto		auto-config reading BIOS (default)

Any help? I would prefer not to try them all :-)

---

### Post by Marzian on 2008-08-21
Any other solutions, please? Thanks

---

