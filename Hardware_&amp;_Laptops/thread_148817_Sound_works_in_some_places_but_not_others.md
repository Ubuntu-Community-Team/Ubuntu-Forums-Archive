---
title: "Sound works in some places but not others"
date: 2006-03-22
forum: Hardware &amp; Laptops
---

### Post by msolano23 on 2006-03-22
I installed a sound card (Sound Blaster Audigy SE) and have been able to get the sound to work with some apps but not others. My event sounds work fine and the system plays CD's without a hitch but I can't get sound from Firefox or Xine. Also, when I use the volume key on my keyboard, it doesn't change the volume I see in volume control anymore.

Is there a preference somewhere that I havent' got set up right? I think some things might still be set up to use the onboard sound.

I altered /etc/asound.conf and set up the correct card as the default. I went to System-> Preferences -> Sound and changed the default card. I changed the options in Volume control to use the new card. What am I forgetting?

Thanks in advance :)

---

### Post by dragomirov on 2006-03-22
I don't consider you a stupid, but... have you unmute all the volumes? And have you restarted ALSA?

h&k

---

### Post by msolano23 on 2006-03-22
I manually restarted ALSA and I've also restarted my system several times...

Whats really weird is that my event sounds work perfectly and so do CD's. Its just certain apps like Firefox.

---

### Post by msolano23 on 2006-03-22
And I also checked to make sure my volume wasn't muted :)

---

### Post by msolano23 on 2006-03-23
When I went into my bios and disabled my onboard sound, the event sounds stopped working but I could hear sound out of Firefox. The sound was greatly distorted though.

Also, when I plug in the speakers to my onboard sound (when it is active but not the default for ALSA) I still don't hear anything from Firefox. So, I don't know whats going on.

---

