---
title: "New video card... no sound!"
date: 2009-07-01
forum: Hardware
---

### Post by NegativeSpace on 2009-07-01
Hi,

I recently installed a 9600GT video card and, since then, I have no sound.

I understand that I need to connect the supplied S/PDIF connector from the card to my motherboard, which I have done, though I still have no sound.

Note that I'm *not* using a TV, I'm using a monitor with a regular set of speakers hooked up to the motherboard's onboard sound via the usual inputs.

Specification (worth noting):

[LIST]
[*]ASUS EN9600GT video card
[*]ASUS P5Q-EM motherboard
[/LIST]

Without the video card I get sound just fine, with it... nothing...

Can someone advise as to what I'm doing wrong?  I'm pretty sure it's a hardware thing that I'm doing incorrectly, rather than software (though, for your information, I'm running Ubuntu 904).

Many thanks in advance.

---

### Post by PurposeOfReason on 2009-07-01
Post the output of 'aplay -l'. What is happening is the sound is trying to come out of the wrong device, we need to know the correct device to tell alsa to use.

---

### Post by NegativeSpace on 2009-07-01
PurposeOfReason,

Thanks for your swift reply!  Here's the output:
```

card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Does this help/explain anything?

---

### Post by PurposeOfReason on 2009-07-01
I'm no expert, but that all looks just fine. Alsamixer brings up the right channels I'm assuming?

---

### Post by NegativeSpace on 2009-07-01
Yeah, Ubuntu appears to think that everything is working fine on the sound front, hence why I think it's a hardware issue rather than software.

alsamixer shows all the channels as expected.

Does anyone else have any suggestions?

---

### Post by PurposeOfReason on 2009-07-01
> **NegativeSpace said:**
> Yeah, Ubuntu appears to think that everything is working fine on the sound front, hence why I think it's a hardware issue rather than software.

alsamixer shows all the channels as expected.

Does anyone else have any suggestions?
Unhook the spdif connector because you actually shouldn't need it. I doubt it will do anything, but we'll see.

---

### Post by NegativeSpace on 2009-07-01
> **PurposeOfReason said:**
> Unhook the spdif connector because you actually shouldn't need it. I doubt it will do anything, but we'll see.

Yeah I tried that and it's exactly the same -- Ubuntu doesn't complain about anything at all but I still get no sound.

It's extremely frustrating.

---

### Post by NegativeSpace on 2009-07-02
Does anybody else have any possible solutions to this?  I still am not having any luck...

---

### Post by NegativeSpace on 2009-07-03
Bump.

---

### Post by NegativeSpace on 2009-07-05
In case anyone has the same issue, I managed to resolve this by installing the latest ALSA drivers (see [here]("http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/"))

---

