---
title: "atheros wifi card button keeps blinking"
date: 2010-10-01
forum: Hardware
---

### Post by rajeshjsl on 2010-10-01
i have theros ar5b93 card , ubuntu 10.04  64 bit automatically installed athk9 drivers for it .

but i have one problem , the wifi led on my laptop keeps blinking , which is annoying , it doesn't blinks in windows as i have atheros drivers in windows , but what about ubuntu ?

also i want to know that the led keeps blinking , does it working correctly or if its switching on and off continuously ? what does that mean ?

---

### Post by coffeecat on 2010-10-01
> **rajeshjsl said:**
> but i have one problem , the wifi led on my laptop keeps blinking , which is annoying , it doesn't blinks in windows as i have atheros drivers in windows , but what about ubuntu ?

It sounds to me as though there is something wrong with your Windows. The light is meant to blink - at least on the laptops I've used. Light on steadily means that the wireless device is active. Blinking means that there is traffic passing one way or the other.

On my Acer laptop with a different Atheros chipset but using the ath9k driver in Ubuntu, the wireless light blinks only when I am downloading or uploading something, or surfing the internet. Or when the update manager is checking for updates in the background. In Windows 7 it blinks much more when I am not surfing, which tells me that Windows or the virus checker (or something) is phoning home. I am more reassured by the behaviour in Ubuntu.

What laptop do you have? What version of Windows?

---

### Post by rajeshjsl on 2010-10-01
^^
actually in windows also it blinks but when you install the propreitory atheros drives the blinking stops ..how to stop it in ubuntu ?

i have acer 5740g

---

### Post by coffeecat on 2010-10-01
Googling 'Acer 5740g' tells me that it comes with Windows 7 Home Premium which is what I've got on my (different) Acer too.

> **rajeshjsl said:**
> actually in windows also it blinks but when you install the propreitory atheros drives the blinking stops

I think what you mean is that with the version of the Atheros driver in Windows 7 that came with your machine the light blinked, but that when you installed another version of the driver, the blinking stopped. Am I right? If that is so, then I would guess there is something wrong with the version of the driver that doesn't make the light blink. In which case, my thanks for warning me. I'll avoid updating the Atheros driver in Windows. :wink:

> **rajeshjsl said:**
>  ..how to stop it in ubuntu ?

I have no idea. I don't even know if it's possible. Sorry I can't help. To me, the blinking is an important functionality that I would not like to lose. If it really worries you, the only thing I can suggest is to stick some opaque electrician's tape (or similar) over the LED.

**Edit:** just to add, I've booted into Windows 7 to check which Atheros driver I have there. By the way....

> **rajeshjsl said:**
> i have theros ar5b93 card

That's what Windows 7 calls it - in fact 'Atheros AR5B93'. That's the same card as mine. If you do a 'lspci' in Ubuntu, you'll see that it is the AR928X chipset. When posting on an Ubuntu forum, it's best if you use the terminology used by Linux. I don't know why the Atheros identifiers are different in the two OSs. Anyway, Windows Device Manager is telling me that I have the Atheros driver version 8.0.0.238. And that does cause the light to blink in my laptop.

When you say 'proprietary driver' in Windows, where did you get that? Which version?

---

