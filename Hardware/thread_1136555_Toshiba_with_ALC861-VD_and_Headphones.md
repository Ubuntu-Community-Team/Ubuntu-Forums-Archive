---
title: "Toshiba with ALC861-VD and Headphones"
date: 2009-04-25
forum: Hardware
---

### Post by Choobie on 2009-04-25
Hi guys!

I have a Toshiba A134-S2457 (or something close to that model number). The one thing that doesn't work is is my headphone jacks, and possibly my microphone jack but I don't have a mic so that isn't something I can test...

My codec is the ALC861-VD

I have tried every single sound how to and headphone fix I could find, including the little trick where you modify /etc/modeprob.d/alsa-base and put "options snd-had-intel model=xxx" where xxx corresponds to a model in this:  /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
 (and I tried nearly every different model name.

This is on every version of Ubuntu (including 9.04) since 7.04.

Relevant output from lspci: 

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)

```

Any ideas on what I can do to finally get my headphone jack working? Anyone else have any experience with this model laptop? Or something else in the A135 series?

Also I have been considering installing OSS to see if that would fix the issue. What are your thoughts on that? Should I send a bug report in (to ALSA right?).

Thanks for your help!

Editing: Sound from the speakers is very loud and clear, by the way.

---

### Post by lisati on 2009-04-25
A quick note to let you know that your query has been noticed and people are thinking about it.....

My A100 laptop has a different chipset for the sound, so no clues likely there. My Toshiba M200 laptop has a *similar* chipset, and the headphone socket works, only it's the 82801H instead of the 82801G. Do you have anything else that you know to work and can plug into the headphone socket?

I might have to let someone else jump in if they have suggestions to make.

---

### Post by Choobie on 2009-04-25
Thanks for your response!

I'm afraid I don't quite know what you mean by this:

> Do you have anything else that you know to work and can plug into the headphone socket?

I have used the headphone jack to output sound from my computer to my speakers under Windows (dual booted right now), as well as tried regular headphones that I use with my mp3 player, if that is what you mean.

---

### Post by lisati on 2009-04-25
If it works in Windows...... well.....

There could be some subtle difference between the 82801G in your machine and the 82801H in mine (which seems to be happy to work with Ubuntu) that could be confounding things.

I'm going to have to pass the reins on to someone else...... anyone?

---

### Post by Choobie on 2009-04-25
Yeah, it seems soundcards are weird, and wireless cards too. I have read about other people who also have the 828001G with the ALC861 VD card and have no problems with it, so it could simply be the manufacturer. Would you agree that this is an ALSA problem? I could file a bug report with them if so.

Do you think there is a possibility that installing and using OSSv4 would solve the problem? I could give that a try as well if I don't get a solution within a couple days.

---

