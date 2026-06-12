---
title: "hda_intel stopps working in Ubuntu 7.10 - worked excellent in 7.04"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by skyttan on 2007-12-30
Hello everyone!

I fresh-installed Ubuntu 7.10 today, previously using 7.04 (uppgraded to 7.10 without any sound-prblem) and now I don't get any sound!? I have a Lenovo 3000 V100 with some Realtek High-Defination sound card. I'll post lists if you give me commands.

Hope you can help me,
skyttan

---

### Post by santoxyz on 2007-12-31
hda_intel is a trouble.... in my xubuntu on fujitsu v3515, i resolved patching alsa 14 (i wrote another post about this... you can search in the forum for 'v3515') and passing 

options snd-hda-intel model=laptop
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel

in /etc/modprobe.conf

------

in my LFS otherwise i installed (from sources) alsa 15:
./configure  --with-cards=hda-intel,via82xx  --with-card-options=hda-codec-via #you should need hda-codec-realtek (do a ./configure --help for all options)
make 
sudo make install
alsaconf



and i have no problems 

P.S: in every case you need to recompile the kernel *DISABLING* the build-in ALSA driver !!!

i hope this can help.

---

### Post by skyttan on 2008-01-01
Dude, I ain't that good.. But really thanks for trying helping me, really appreciate it. But I go for installing 7.04 and upgrade it, that works for me.

---

### Post by skyttan on 2008-01-02
Well, It didn't. Installed 7.04 - great, uppdated - fokked up. Hope it won't keep going on like this in further releases of Ubuntu. Would rather skip compiling stuff to kernel so I stick to 7.04 with this wonderful dekstop-cube :D

---

### Post by CyberRaven on 2008-01-17
@skyttan;

have you disabled the modem in your BIOS? In that case, try enabling it again. Seems the modem is somehow linked to how the sound chip works.

On my girlfriends V100 I had the same problem as you with Kubuntu 7.10 - no sound - but after enabling the modem (and perhaps fiddling a bit with the settings in alsamixer, can't remember), the sound works flawless!

Got the hint from this page, btw; [http://thinkwiki.org/wiki/Problem_with_no_sound_on_ThinkPad_R60e](http://thinkwiki.org/wiki/Problem_with_no_sound_on_ThinkPad_R60e) - great page for Thinkpad/Lenovo owners!

Well, that's my 10 cents worth! Good luck:-)

/cyberraven

---

### Post by theophile on 2008-01-17
Reinstall Gutsy and recompile ALSA modules according to this:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Worked for me on Dell Inspiron 1501.

---

### Post by Yellow Pasque on 2008-01-17
I would try adding "options snd-hda-intel model=3stack" into the /etc/modprobe.d/alsa-base file. Try different variations on 3stack, (e.g model=lenovo101e or model=lenovo) as listed below. The first word in each line is the model type.

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

ALC883/888
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack digital with SPDIF I/O
3stack-6ch 3-jack 6-channel
3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
6stack-dig-demo 6-jack digital for Intel demo board
acer Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
acer-aspire Acer Aspire 9810
medion Medion Laptops
medion-md2 Medion MD2
targa-dig Targa/MSI
targa-2ch-dig Targs/MSI with 2-channel
laptop-eapd 3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
lenovo-101e Lenovo 101E
lenovo-nb0763 Lenovo NB0763
lenovo-ms7195-dig Lenovo MS7195
haier-w66 Haier W66
6stack-hp HP machines with 6stack (Nettle boards)
3stack-hp HP machines with 3stack (Lucknow, Samba boards)
auto auto-config reading BIOS (default)

---

