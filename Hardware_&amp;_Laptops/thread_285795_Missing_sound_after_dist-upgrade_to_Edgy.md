---
title: "Missing sound after dist-upgrade to Edgy"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by diego_dambra on 2006-10-27
After dist-upgrade to Edgy I'm unable to get sound working.

Volume Control looks good and Playback isn't muted - same with AlsaMixer.

#cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.12rc1 (Thu Jun 22 13:55:50 2006 UTC).

Sound device is: Intel 82801DB-ICH4

Trying the "Test" option in "Sound Preferences" doesn't produce any sound.

Note: Sound did work before the dist-upgrade.

I'm unsure how to debug this, so any help appreciated.

---

### Post by chaosgeisterchen on 2006-10-27
Which packages were updated with the last **dist-upgrade** you made?

---

### Post by sannong on 2006-10-27
Hey ya,

I've got the same problem with the same sound card. Sound worked before the upgrade but now nothing. Checked out everything like the first post but same result. As far as I can tell it should be working...

---

### Post by forger on 2006-10-27
Um were you playing any songs while the upgrade was in progress? Because I was, and now I have no sound as well.. I'll try to reinstall and see what happens

---

### Post by forger on 2006-10-27
okay, the no sound problem was solved here, it looks like listening to music while upgrading is not a good idea :P

---

### Post by diego_dambra on 2006-10-29
> **chaosgeisterchen said:**
> Which packages were updated with the last **dist-upgrade** you made?

I was running Dapper before and updated my system in one go, so basically every package updated by the dist-upgrade process (IIRC over 600MB was downloaded).

I just used the command:
gksu "update-manager -c"
and clicked on the update button.

Are you thinking about specific packages?

---

### Post by diego_dambra on 2006-10-29
> **forger said:**
> okay, the no sound problem was solved here, it looks like listening to music while upgrading is not a good idea :P

I wasn't using any "sound related" program (or at least not to my knowledge) during the upgrade.

How did you "reinstall"?

---

### Post by diego_dambra on 2006-10-29
> **diego_dambra said:**
> After dist-upgrade to Edgy I'm unable to get sound working.

Volume Control looks good and Playback isn't muted - same with AlsaMixer.


Finaly I got sound to work - I followed this thread [http://www.ubuntuforums.org/showthread.php?t=276167&highlight=sound+edgy](http://www.ubuntuforums.org/showthread.php?t=276167&highlight=sound+edgy)

I simply muted and then un-muted everything in AlsaMixer and turned down/up volume.

My guess is that the problem was item <PCM>, so others that might read this - try starting with that.

---

