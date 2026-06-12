---
title: "audio dificulties with HP Pavilion"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by catty0320 on 2007-12-30
my hp pavillion works seamlessly with ubuntu but the audio is not working
i checked the volume and have tried changing the apps volume but i get nothing
the only thing i can think of is drivers, but i dont know how to fix that. thanks

---

### Post by ItsManaged on 2007-12-30
Have you checked that the volume is not muted? Right click on volume control.

Check this link first: [https://help.ubuntu.com/community/DebuggingSoundProblems]("https://help.ubuntu.com/community/DebuggingSoundProblems")
This link may prove useful too:  Check your sound card first (The following URL applies to Intel based sound) 
(in a terminal) type lspci
Look for a line like this:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 

[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

Happy new year!

Cheers,
ItsManaged

---

### Post by catty0320 on 2007-12-30
i tried the alsa thing fro hp. i will tell you how it works once i reboot but i am currently updating so i am gonna wait to reboot

---

