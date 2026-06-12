---
title: "Acer Aspire one model 531"
date: 2009-08-08
forum: Hardware
---

### Post by HenkK on 2009-08-08
Hallo, I hope someone can help me.

I have an Acer Aspire One model 531 (ZG8)
I installed Ubuntu Remix 9.04
Basically things are running well, I got the WLAN to work, and also sound output.

However the internal microphone does not work. (External mic works fine), and the sound disappears after returning from suspend (returning from hibernate is fine)

Under windows xp (dual boot) the internal mic works fine (no HW defect)

I have searched for many days, and tried many things. ALSA has been upgraded to 1.0.19, (dep package install)
The Kernel is 2.6.28-15 generic
The sound module is snd_hda_intel
Codec is Realtek AC272

The live remix version from USB-stick does not give any sound, neither does the live ubuntu cd.
I have read that someone installed the "normal" ubuntu (not remix) and after the updates sound worked fine. (I like to avoid a complete new install)

Who can give me some help in how to analyse the sitautaion and solve the problem?

Thanks

---

### Post by soulston on 2009-09-08
Hi,

I just got one of these the other day so will let you know how I fare. For me the wireless didn't work out of the box even though it was fine on XP. Did you totally overwrite your XP install or dual boot it?

---

### Post by soulston on 2009-09-08
Scrub that last reply. I now have the wireless working after making the following changes in:

/etc/modprobe.d/blacklist.conf

remember to sudo nano blacklist.conf as I went in, made the change and then couldn't save it out!

the line you need to add is

blacklist acer_wmi

restart the netbook and you're good to go

I found this in [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) relating to the AOA 150

---

### Post by HenkK on 2009-09-09
Here an update.
I installed normal Ubuntu 9.04.
I replaced networkmanager with wicd not it works (except for the switch and led).
I compiled and installed the latest ALSA and the microfone also works (sound even works after suspend and hibernate)

So basically 99% is now OK.

---

### Post by DanoClarke on 2009-09-10
Hi, I have also just purchased an Acer Aspire One 531 and have installed ubuntu remix on it, everything is working fine except my wireless, i followed what was written above by soulston but still cannot get the wireless to work, ive been trying now for over a day, dont suppose anyone has any ideas do they? cheers

---

### Post by HenkK on 2009-09-10
As said before. I gave up Ubuntu Remix and installed from scratch Ubuntu 9.04 .
Then Uninstall "Networkmanager" and install "wicd" via Synaptic. That should make the wireless work (an Icon in the top left panel).

I would be interested how you got the internal microphone to wor. I had to compile and install the latest Alsa package (is not in the Ubuntu repositories yet)

---

### Post by HenkK on 2009-09-10
Sorry the icon is in the top right panel

---

### Post by spegru on 2009-09-26
Thanks for these. I got one of these netbooks yesterday.
I like Soulton's solution because wicd does not manage 3G like network-manager does

So it went like this.
1. Installed from scratch: no wifi
2. Installed all updates: no wifi

3. installed wicd (which removes network-manager) using: 
sudo apt-get install wicd

Wifi works but no 3G from my dongle / 3g key


4. reinstalled network manager (which removes wicd) using:
sudo apt-get install network-manager

wifi does not work any more by my 3g dongle / key works fine


5. Used a variant of Soulton's solution except my command used gedit text editor instead of nano (I couldn't see how to save in nano - although I'm sure it's easy really) using:

sudo gedit /etc/modprobe.d/blacklist.conf
(the sudo is very important)

added the lines:  
# for acer 531 as recommended by Soulston on the ubuntu forums  (this is only a comment!)
blacklist acer_wmi

Save

Reboot

Wireless works fine and so does 3G!

---

### Post by HenkK on 2009-09-26
I do not use 3G so I don't know if that works. 
Before I tried all types of blacklist without success. However, I really can't tell which combinations I used.

The Microfone and all sound works when you compile and install the latest Alsa drivers. (be aware you have to repeat that after each kernel upgrade)

---

### Post by spegru on 2009-09-27
However wifi things are not yet perfect.
I had a strange thing wireless: I disabled the wireless (I wanted to force it to change networks) under network manager, but the wireless wouldnt come back on again - even after a full reboot.
I actually thought I'd damaged the wireless nic somehow because I had this happen once before on another laptop.
Luckily I had kept the XP partition so I rebooted into that. For about a minute there was no wireless (I was really worried then) but suddenly it sprang back into life, and works also in linux again.
I havn't dared disable wireless since, but this does not seem right.

(I am now also wondering if the wireless nic I broke before is actually ok)

---

### Post by spegru on 2009-09-27
Also sound things are not yet perfect, because I only got sound in one ear.
I thought it was the headphones or the socket or sound card but I tried different ones and even a USB set (behaves like different sound card) and they are all the same.
XP is fine though

My external mic also does not work, although the one on my USB headset is fine

I expect someone is going to suggest installing another pulse or alsa version so if you do please also explain how to check which version I have and where to get new versions from (I am too reliant on standard distros)

---

### Post by spegru on 2009-09-28
It's a pity this thread is labelled ubutntu netbook remix. I bet it gets less attention

Bump - to all standard interface users!

---

### Post by HenkK on 2009-09-29
I do not have those problems,
I use the standurd Ubuntu distribution.
Instead of Networkmanager I use wicd
I have upgraded to the latest Alsa drivers (self compiling). Since then  microphones, internal and external, work.

Only the Wifi on/off button and indication-led do not work (for bluetooth it works) 
3G I have never tried.
I have only tried one SD slot (there are indications the second slot only works when you start up with a card inserted).

I am pretty satisfied. The disadvantage of using the standard Distribution is all the banners on the windows take vertical space away. Here the remix is better, but I had too many problems in the beginning with the remix. (maybe these probloems are now corrected, I did not try)

---

### Post by spegru on 2009-09-29
Hello HenkK. How did you install the latest Alsa?

spegru

---

### Post by Linux_cat on 2009-09-30
Hi, im also having the same wireless problems, I just bought an 531Z8G and for the life of me cant get the wireless to work.

I have tried:
1. editing the backlist.conf file and appending the acer_wmi link
2. installing wcid
3. installing network-manager

nothing seems to work, works fine in XP.

I know its using the atheros AR9285 card, but again i cant find any driver for this.

Can someone please help??

---

### Post by Linux_cat on 2009-09-30
found a solution check

[http://ubuntuforums.org/showthread.php?t=1179951](http://ubuntuforums.org/showthread.php?t=1179951)

---

