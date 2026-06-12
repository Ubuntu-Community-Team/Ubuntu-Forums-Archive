---
title: "No sound on HP Pavilion a1600n-HELP"
date: 2017-01-30
forum: Hardware
---

### Post by mitch.gray on 2017-01-30
I am new to Ubuntu and am currently running 16.10. I cannot get my sound to work no matter what I attempt.

I am running ubuntu from an older computer and the specs can be viewed from [http://support.hp.com/us-en/document/c00749157](http://support.hp.com/us-en/document/c00749157)

when i run command in terminal: alsamixer, it says the sound card is HDA ATI HDMI, but doesnt allow me to mute or unmute or adjust any sound settings.

I apologize if this isnt much to go by, i may be able to answer more questions just not sure what info i need to provide.

Thank in Advance

---

### Post by Yellow Pasque on 2017-01-30
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by mitch.gray on 2017-01-30
[http://www.alsa-project.org/db/?f=d1391485386098cccf4feaf11f40a0e2a0c97076](http://www.alsa-project.org/db/?f=d1391485386098cccf4feaf11f40a0e2a0c97076)

---

### Post by mitch.gray on 2017-01-30
I obtained a neat little device to use temporarily, its a usb sound card thing, never seen one before but it has my sound working, just would like to get the sound working without using the device, as i will need to return it fairly soon

---

### Post by RobGoss on 2017-01-31
Have you tried adjusting the Alsamixer sound volume this might be of help   [https://wiki.ubuntu.com/Audio/Alsamixer](https://wiki.ubuntu.com/Audio/Alsamixer)

I would also try to see if your sound device is listed and checked for usage is the sound settings

---

### Post by Yellow Pasque on 2017-01-31
The onboard audio (Realtek ALC888 chip according to specs) isn't even showing up in lspci. If you're lucky, it got disabled in the BIOS and all you have to do is enable it there.
If you look in the BIOS and find it's enabled, then I would try disabling it, booting, rebooting back into BIOS, and enabling it again.
If you're really unlucky, the onboard audio has some sort of hardware fault and it's time to look for a replacement.

---

### Post by mitch.gray on 2017-02-07
> **Temüjin said:**
> The onboard audio (Realtek ALC888 chip according to specs) isn't even showing up in lspci. If you're lucky, it got disabled in the BIOS and all you have to do is enable it there.
If you look in the BIOS and find it's enabled, then I would try disabling it, booting, rebooting back into BIOS, and enabling it again.
If you're really unlucky, the onboard audio has some sort of hardware fault and it's time to look for a replacement.
it was set on auto, and enabling it solved my issue! thank you!

---

