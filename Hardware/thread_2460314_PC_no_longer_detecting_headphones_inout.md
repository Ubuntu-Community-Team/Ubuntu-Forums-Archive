---
title: "PC no longer detecting headphones in/out?"
date: 2021-04-07
forum: Hardware
---

### Post by adrian-h on 2021-04-07
This could be a hardware fault by now on this old PC, but thought I may have corrupted some software when trying to amateur radio programs as one caused the system to crash and that was dealing with audio connections.

Anyway I upgraded from Ubuntu 18.04 to 20 in the hope it could reinstall some corrupted package, but still no joy.

I have installed pavucontrol just so I can see if it detects headphones on plug in and it does not.  can someone tell me what software does the detection of the headphones and other audio jacks on a system.

Things like plugging in a memory card or USB device all work so if it is the same software then there is a chance it is hardware failure.

Cheers

Adrian

---

### Post by CatKiller on 2021-04-07
> **adrian-h said:**
> can someone tell me what software does the detection of the headphones and other audio jacks on a system.

When you plug something in, it pushes in a pin, which triggers a signal from the hardware. When correctly configured, ALSA (the part of the sound stack that deals with the hardware) can use this signal (called "pin detect" by ALSA) to send its own signals to PulseAudio to decide what to do about it. 

All hardware (particularly small hardware put under repeated mechanical strain) will wear out. Maybe your spring is no longer as springy as it once was, or your pin no longer retracts enough to trigger a signal. 

Assigning signals to functions without documentation - which is generally necessary for ALSA, since hardware manufacturers are generally not helpful - is done mostly by guesswork. Sometimes the results of that guesswork are incorrect. However, that usually manifests as hardware not working properly and then gaining functionality over time rather than the other way round. It could have happened, though. Where hardware exists that is known to have more than one behaviour, or specific non-standard behaviour, how signals should be interpreted is governed by "quirks" for that hardware. Which signal is in and which is out is a relatively common quirk that needs to be applied for some hardware. If the signals interpreted by ALSA *have* changed between it working for you and not, you may be able to configure it by applying a quirk.

---

### Post by adrian-h on 2021-04-07
OK thanks, I was thinking something acpci or dbus that may have failed, but it could well be a hardware issue, sound still comes out of the internal speaker but will not switch to the front headphone socket but plugging into the rear speaker socket works, so perhaps a strip down of the hardware is in order.

Cheers

Adrian

---

### Post by adrian-h on 2021-04-07
OK I am going to mark this as solved as a fresh install of 20.04 still has the same issue, other packages were not working as expected hence doing a fresh install after backup of data.

Adrian

---

