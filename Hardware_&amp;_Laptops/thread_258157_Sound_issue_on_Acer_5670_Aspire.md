---
title: "Sound issue on Acer 5670 Aspire"
date: 2006-09-15
forum: Hardware &amp; Laptops
---

### Post by nupton on 2006-09-15
The precise model is Aspire 5672WLMi-ATI X1600, stock except the 1g of ram was replaced with 2g. The sound chipset is the Realtek ALC883. It works under Windows (very recently reinstalled it, so I don't think it's a hardware issue, because there was no way it could have been damaged between then and now), but under opensuse and Ubuntu, I've not been able to get it to work.

The model is listed as having full compatibility except for the webcam and onboard modem on the Ubuntu compatibility list. Yet when I insert a CD and play it with Rhythmbox, or when I try any of my audio files (yes, I've tried .ogg files), sound comes from neither the speakers nor, if they're plugged in, the headphones. The volume control is all the way up and not muted.

Any ideas? I've been struggling with this thing for a while now, and I'd really like to keep using Ubuntu on it if I can get it to work 100% except the webcam and onboard modem, which are unneeded.

---

### Post by nupton on 2006-09-16
Tried a reinstall, still isn't working, although I got the ATI drivers (fglrx, I think) to get me the full 1280x800 res. I think the wireless lan is working, too, which it didn't under SuSE, so that's pretty cool, and I really love the Ubuntu interface, so I'm really hoping to get the sound working.

---

### Post by sheepeatingtaz on 2006-09-18
Hi There,

Try the fix on [this page]("http://ubuntuforums.org/showthread.php?t=202555&page=5&highlight=sound+acer")

It worked on my Acer Aspire 5601 (which hasx the Intel 883 Soundchip) last week :)

---

### Post by nupton on 2006-09-19
Unfortunately, that's not working. It won't let me configure the ALSA driver because it claims I have ALSA built into the kernel. Even though I'm using the newest version of the ALSA driver which certainly isn't in this kernel. I guess ALSA doesn't like it if you try to upgrade?

Is there some install option I can use like, ./configure --upgrade-previous-installation or --with-do-I-care-if-I-have-it-built-into-the-kernel=no?

---

### Post by dyous87 on 2006-09-19
Strange I have the exact same model and have had no problems with sounds what so ever. It all worked fine out of the box. I even reinstalled it multiple times and everytime sound has worked fine. Are you perfectly sure that you didn't have a faulty sound card that burned out?

Also this prob won't work if you don't hear any sound what so ever but you may wan't to try to install all the non free audio codecs using automatix.

I would def check on that sound card though because seeing as i have the exact same computer I'm not sure why else yours would be giving yout trouble.

---

### Post by nupton on 2006-09-19
If it burned out, it would have done it in the past two weeks. Sound card worked under XP Home and then the Vista beta, then I installed OpenSuSE and it didn't work, then I installed XP Pro and the Realtek drivers and it worked, then I installed Ubuntu and it hasn't worked.

---

### Post by jdong on 2006-09-19
With this model laptop, it seems like SOME of them have the no-sound problem while others have sound. It totally depends on randomness :)

Having the new ALSA drivers will solve the problem; Edgy already has this patch integrated, and I'm bugging kernel devs to backport the fix to Dapper, too.

---

### Post by jdong on 2006-09-19
[http://kernel.org/git/?p=linux/kernel/git/bcollins/ubuntu-dapper-updates.git;a=commit;h=dc02624f941c0b279d3f58f263aede1d777323a3](http://kernel.org/git/?p=linux/kernel/git/bcollins/ubuntu-dapper-updates.git;a=commit;h=dc02624f941c0b279d3f58f263aede1d777323a3)

It seems like the sound fix is coming to a Dapper kernel update near you (if not arrived already).

---

### Post by nupton on 2006-10-27
Sorry to bump this thread, but I have new information to add.

Yesterday I downloaded and installed Edgy. You can't imagine how happy I was, after six months of no sound on this laptop, to hear the login sound coming from the speakers.

Likewise, you can't imagine how crushed I was when, after installing the fglrx drivers so I could use my videocard at something approaching its potential, it would not boot. It was the same exact configuration that worked for me with Dapper; I imagine there are just some kinks that need working out with Edgy.

I might have tried the ATI proprietary drivers (it's got an ATI mobility radeon x1600), but since AMD took over ATI, their page has been screwy. Again, I suppose just some kinks that need working out. I'll try to put the fglrx thing as a bug report or the like.

However, since Dapper is also the LTS version, any idea how I can get the update that was mentioned for Dapper? I'm currently back on Dapper, this time with Kubuntu, although I don't imagine that makes too much of a difference. I've kept my system completely up-to-date, and no fixes seem to have come down the line.

---

### Post by nupton on 2006-10-29
Last bump to see if there's any help.

---

