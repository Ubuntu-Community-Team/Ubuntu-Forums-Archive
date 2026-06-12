---
title: "bluetooth buttons"
date: 2008-11-16
forum: Hardware
---

### Post by fireoptic on 2008-11-16
I got the sound working pretty easily with puilseaudio how ever the buttons (play/pause, ff, rw ) on my lg bluetooth headset dont work at all. I use rythmbox and the button set on my keyboard works just fine. any ideas on where to start would be great. thanks in advance.

---

### Post by Keyper7 on 2008-11-16
You must register your headset as both an audio device and an input device. Are you on 8.10 or an older version? I'm asking because the steps to do so might differ depending on the version.

PS: It might take an entire day to check your reply to this, but I will.

---

### Post by Guillaume86 on 2008-11-17
> **Keyper7 said:**
> You must register your headset as both an audio device and an input device. Are you on 8.10 or an older version? I'm asking because the steps to do so might differ depending on the version.

PS: It might take an entire day to check your reply to this, but I will.
Hi,
I have the same problem, I'm on 8.10 (on 8.04 it was working).

---

### Post by Keyper7 on 2008-11-17
> **Guillaume86 said:**
> Hi,
I have the same problem, I'm on 8.10 (on 8.04 it was working).

You might need to register the headset twice, one as a audio device and one as an input device. I don't have 8.10 with me now, but the proper options to do so should be on the bluetooth applet.

---

### Post by Keyper7 on 2008-11-18
So, any progress on this? What does the options in the bluetooth applet show?

---

### Post by Guillaume86 on 2009-01-05
> **Keyper7 said:**
> So, any progress on this? What does the options in the bluetooth applet show?

Actually it only shows one device... Any others ideas? (I've already had to recompile the applet to pair the device because of the random pin generation in the new applet...)

EDIT: Problem solved, just add uinput at the end of your /etc/modules file and enjoy AVRCP support...

---

