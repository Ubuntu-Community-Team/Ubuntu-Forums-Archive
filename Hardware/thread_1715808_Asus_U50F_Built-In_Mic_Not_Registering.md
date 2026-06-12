---
title: "Asus U50F Built-In Mic Not Registering"
date: 2011-03-27
forum: Hardware
---

### Post by coastaltuba on 2011-03-27
I installed Ubuntu in Windows 7 and when I tried to use Skype, there was no sound from my mic.  So I checked the sound, and it doesn't even show my mic.  Is there anyway for me to fix this, because that is the only reason I am keeping Win 7 right now, because my fiancee is 6 hours away atm.  If someone could help, I would be very appreciative.  Thanks.

---

### Post by lidex on 2011-04-03
Do you mean wubi install?
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

