---
title: "SoundMax on ubuntu 10.10 X64"
date: 2011-04-25
forum: Hardware
---

### Post by djgepard on 2011-04-25
hello :)

I have problem with install drivers to my sound card, It`s Sound Max (at the ASUS P5B Deluxe Motherboard) i have Ubuntu X64 i must have the 64 bits drivers?, Sound card play sound on alsa driver, when i try connect my subwoofer (don`t have low pass filter) on windows play great, on linux play at normal speakers who i can make?

sorry for my en language i learning him :)

---

### Post by lidex on 2011-04-27
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

