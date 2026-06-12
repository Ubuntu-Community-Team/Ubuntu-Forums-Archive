---
title: "Installing and configuring AuzenTech X-Fi Forte on 10.04 LTS x64"
date: 2010-07-21
forum: Hardware
---

### Post by dejanh on 2010-07-21
Hi there,

I have a problem ever since I installed my new AuzenTech X-Fi Forte card.  While 10.04 LTS detects the soundcard (albeit not correctly as AuzenTech X-Fi Forte, rather X-Fi Titanium) I cannot seem to get any audio output at all.  I have tried everything I could think of including upgrading ALSA to 1.0.23 version.  The audio chip is detected correctly as EMU20k2 but there is simply no output coming out of the card.  The card works perfectly in Windows 7.

Please help :(

---

### Post by dejanh on 2010-07-27
Nobody?

---

### Post by h4ck3r on 2010-09-19
I'm having the same problem. Is it possible? Is there any module I need to enable, or something I need to do to get my sound card to work?

---

### Post by dejanh on 2010-09-20
> **h4ck3r said:**
> I'm having the same problem. Is it possible? Is there any module I need to enable, or something I need to do to get my sound card to work?

I have a feeling not.  I am hoping that 10.10 may fix it but I would not hold my breath.  I was hoping for at least one reply to this but nobody, not a single person replied.  You are the first individual that seemingly even looked at this thread.

I don't understand why it does not work at least in the most simplest way with Stereo 2.0/2.1 and basic 5.1.  I'm not after any fancy effects here or anything, just working sound.

:(

---

### Post by h4ck3r on 2010-09-20
Yeah, I'd really use even basic 2.1. I really could care less about anything else. I mean yeah, they're nice. But I want simple sound!!! I'm really not happy about this :(. Whatever. And I can't find anything on the net about getting it to work :(

---

### Post by Loader009 on 2010-10-25
I've tried this soundcard on lucid lynx...
I get only Sound on Rear in the Surround (4.0) configuration. Also if I set to 5.1.

But there's a warning! If you started linux with the creative driver (as I do) the soundcard seems to crash.
If you do a restart to Windows, the Soundcard have the same issues. Only the Rear Jack is working.
Only solution is to reinstall of the soundcard. (After a cold-start. Turn off then on, no restart!)

To avoid this problem you have to coldstart (shut down your PC) after linux.
Then the soundcard works right under windows until you boot linux again.
Greetz

---

### Post by aalega2 on 2010-11-15
> **Loader009 said:**
> I've tried this soundcard on lucid lynx...
I get only Sound on Rear in the Surround (4.0) configuration. Also if I set to 5.1.

But there's a warning! If you started linux with the creative driver (as I do) the soundcard seems to crash.
If you do a restart to Windows, the Soundcard have the same issues. Only the Rear Jack is working.
Only solution is to reinstall of the soundcard. (After a cold-start. Turn off then on, no restart!)

To avoid this problem you have to coldstart (shut down your PC) after linux.
Then the soundcard works right under windows until you boot linux again.
Greetz

horrible compromise to get sound working, after all these months i still havent gotten it to work

anyone have any luck in 10.10?

---

### Post by aalega2 on 2011-04-10
Still can't get this working, i've tried EVERYTHING

the card even shows up in 10.10, i unmute everything from alsamixer and still nothing. i even tried to build the driver from source, but the current alsa one (from what ive read) is way ahead but i still can't get anything to work

---

### Post by dejanh on 2011-05-01
Just installed 11.04 and still no solution to this problem.  X-Fi Forte still does not work and there appears to be no way to make it work.  This is pretty pathetic if you ask me considering how long this issue has been around.  Anybody aware of any fix and/or workaround?

---

### Post by Smiddy12 on 2011-05-29
Can this please be addressed? It's insane how this card has been around for years and 2.1 doesn't even function. It's preventing me from installing and using Ubuntu.

---

### Post by dejanh on 2011-05-30
> **Smiddy12 said:**
> Can this please be addressed? It's insane how this card has been around for years and 2.1 doesn't even function. It's preventing me from installing and using Ubuntu.
I second this!

---

