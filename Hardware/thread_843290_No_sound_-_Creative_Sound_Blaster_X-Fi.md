---
title: "No sound - Creative Sound Blaster X-Fi"
date: 2008-06-28
forum: Hardware
---

### Post by neil9999 on 2008-06-28
Hi,

I've just installed ubuntu hardy heron on an external hard drive.It all works fine, except I can't get any sound. I'm using the Creative Sound Blaster X-Fi Fatality edition. lspci -v gives me 'Creative Labs SB X-Fi'. Is there a way to get the sound to work?

Thanks,

Neil

---

### Post by PeterBBB on 2008-06-28
Try the ALSA Mixer and make sure all the volume settings are turned up. The default simple volume control is not enough.

PB

---

### Post by neil9999 on 2008-06-28
Ok thanks, is this the alsamixer in terminal? I've done that now, but for some reason I can't get the headphone volume or volume for IEC958 (whatever that is...) above 0 (even when I unmute them). Still, I get no sound, neither through the headphones or the speakers. The sound works fine in windows vista.

Any more suggestions?

Many thanks for your help so far,

Neil

---

### Post by AmpersUK on 2008-06-28
> **neil9999 said:**
> Hi,

I've just installed ubuntu hardy heron on an external hard drive.It all works fine, except I can't get any sound. I'm using the Creative Sound Blaster X-Fi Fatality edition. lspci -v gives me 'Creative Labs SB X-Fi'. Is there a way to get the sound to work?

Thanks,

Neil

Hi,

I haven't a solution, but you may find the following reassuring in as much as others have had it working, albeit with problems.

I have an X-FI card.

Playing CDs and music files with Rhythmbox is usually OK 98% of the time, and when it fails, a quick reboot usually fixes the problem.

However, with Videos (YouTube, Google and others) I have problems around 40% of the time, and a quick reboot only fixes this about 75% of those times.

You may find [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) a very useful site when this happens.

Ampers

---

### Post by neil9999 on 2008-06-28
> **AmpersUK said:**
> 
I haven't a solution, but you may find the following reassuring in as much as others have had it working, albeit with problems.

I have an X-FI card.
That sounds reassuring!

> **AmpersUK said:**
> 
Playing CDs and music files with Rhythmbox is usually OK 98% of the time, and when it fails, a quick reboot usually fixes the problem.

I've just tried playing a CD and some of the example ogg files with rhythmbox, but unfortunately no sound still.
> **AmpersUK said:**
> 
You may find [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) a very useful site when this happens.


I've tried that, and it told me to check at [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main) for a driver, but unfortunately the X-Fi is listed as 'unsupported', so the troubleshooter "cannot help" me at the moment:(

Is there anything in particular you did to get your X-Fi working, or did it work 'out of the box'?

Thanks,

Neil

---

### Post by AmpersUK on 2008-06-28
> **neil9999 said:**
> That sounds reassuring! Is there anything in particular you did to get your X-Fi working, or did it work 'out of the box'? Neil

It never worked with 7.10 and I had decided to order another £100 card which I knew that worked. I ordered it and paid for it, but the same time I downloaded 8.04 and, magically it just started working. I managed to cancel my order and saved £100, but now I wonder if that was such a good idea. But I can live with it until they manage to solve the problems, I think!

Ampers

---

### Post by neil9999 on 2008-06-28
Another thing I should mention is I installed Ubuntu onto the external hard disk from a different computer than the one I'm running it on now as I've never managed to boot from USB on that computer (it's 6 years old). Is there any driver that should have been installed had I done it from this computer?

Thanks,

Neil

---

### Post by neil9999 on 2008-07-05
I have managed to boot it on my old computer now, and the sound on that works (it has a Creative Sound Blaster Audigy 2). I still can't get it to work on my Sound Blaster X-Fi Fatality Edition though:( Any more ideas?

Neil

---

### Post by neil9999 on 2008-07-12
Anyone?

---

### Post by AmpersUK on 2008-07-12
> **neil9999 said:**
> Anyone?

I am giving up all hope of getting an answer myself and will now source a card that will definitely work with Ubuntu.

I can hear my music but can only hear sound on YouTube and Google Video about once every two weeks. It changes with updates so someone is messing about with ALSA somewhere on a regular basis.

Although I have received a lot of help here on other matters, I guess **unless** one of the more experienced users also has such a card, we will never get help. And we must remember, the cards aren't cheap and therefore there will be much fewer Linux users.

Ampers.

---

### Post by neil9999 on 2008-07-12
Yeah I wish Creative would just release a working driver for linux! Good news - I've got sound working through a headphones socket that we were told had been disabled when we got the computer! I think this is going through a realtek soundcard. However, the sound quality is awful! There is lots of interference (although there is on vista too). I'll think I'll get a usb soundcard once I've check it's compatiable with Ubuntu!

Neil

---

### Post by AmpersUK on 2008-07-12
*> **neil9999 said:**
> I'll think I'll get a usb soundcard once I've check it's compatiable with Ubuntu! Neil*
[B]
Now that is a very good idea. [/B]Buy a cheap USB sound card so at least it will work in the meantime.

They are still working on the X-FI - I believe they have reverse engineered it. This may take up to a year, so an USB sound card could well be an interim answer.

[SIZE=3]**Is there anyone who is reading this who has had a USB sound card working well with 8.04 and, if so, what make and model is it?**[/SIZE]

Ampers

---

