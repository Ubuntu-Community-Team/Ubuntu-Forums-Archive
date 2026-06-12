---
title: "Sound"
date: 2005-02-12
forum: Hardware &amp; Laptops
---

### Post by iotc247 on 2005-02-12
Hi i have 2 sound cards... Ones internal in my laptop which uses the atiixp module.. Then i have an external create sound blaster audigy 2 nx.. I hear it uses the emu10k1 module... By default ubuntu comes with that module i think because it always works in modprobe.. The only way i ever get sound to work is through alsaconf... Well guess what.. Alsautils is installed but alsaconf comes up with alsaconf: command not found... Which makes no sense... So how do i go about fixing this.. Also whenever the fix is found for alsaconf is there anything special to get the audigy 2 nx (connects via usb) to work?

---

### Post by iotc247 on 2005-02-13
Ok i got alsaconf to work by compiling alsa-utils... Now how do i go about getting sound to actually be heard.. Already ran alsamixer and unmuted the stuff... Now to go see if i can compile alsadrivers and such to get emu10k1 to work with the audigy 2 nx... I hope thats what it needs.. If anyone knows be nice..

---

### Post by iotc247 on 2005-02-13
Ok well every time i tried to use apt-get it automatically tries to remove gdm because i had removed alsa-utils and alsa-base because i wanted to custom compile those.. So how do i get my custom compilations to stay instead of alsa-base and alsa-utils... Whenever i remove alsa-base and alsa-utils gdm gets removed... How do i fix this.. Still cant figure out how to get alsa to detect my sb audigy 2 nx via usb....

---

### Post by CookieNinja on 2005-03-11
[QUOTE=iotc247]Ok well every time i tried to use apt-get it automatically tries to remove gdm because i had removed alsa-utils and alsa-base because i wanted to custom compile those.. So how do i get my custom compilations to stay instead of alsa-base and alsa-utils... Whenever i remove alsa-base and alsa-utils gdm gets removed... How do i fix this.. Still cant figure out how to get alsa to detect my sb audigy 2 nx via usb....[/QUOTE]
 Simple. Leave them where they are. Compile & install the new version and don't worry about it.

---

### Post by Tiede on 2005-03-14
[QUOTE=iotc247]Ok i got alsaconf to work by compiling alsa-utils... Now how do i go about getting sound to actually be heard.. Already ran alsamixer and unmuted the stuff... Now to go see if i can compile alsadrivers and such to get emu10k1 to work with the audigy 2 nx... I hope thats what it needs.. If anyone knows be nice..[/QUOTE]
 Hi iotc247,
How did you put alsaconf in your system? When I try, I get the command alsaconf, but the database doesn't seem to be updated, as it says it can't find my Soundcard
(I took it from a LiveCD [Slax] that recognizes my soundcard when I run alsaconf on it)
Is there a way to update the database so it recognizes my sound card... Or was I wrong when I just copy-and-pasted alsaconf from the LiveCD to my /alsa directory?

---

