---
title: "Laptop Sound Issues"
date: 2008-08-21
forum: Hardware
---

### Post by midnight0000 on 2008-08-21
I recently inherited an older laptop from my sister that was running XP, but i took that off and put Ubuntu on and now i dont have any sound at all. sound was working just fine before the install, ive tried checking to make sure nothing was muted, ive also tried reinstalling - no change in the problem

its an older gateway laptop, nothing special about it. 

i dont have this issue on my other 2 machines that are running ubuntu, just this laptop.  any help? im hoping it's just a driver thing that someone might be able to point me to

---

### Post by Psychoscorpic on 2008-08-22
Hi Midnight

It's a common glitch.

Do this:
```
sudo gedit /etc/modprobe.d/alsa-base
```

Add the line:
```
options snd-hda-intel model=lenovo
```

(my notebook is a Sahara, but "lenovo" does the trick! If it doesn't do ti for you, use "auto" instead (without quotes))

---

### Post by midnight0000 on 2008-08-23
> **Psychoscorpic said:**
> Hi Midnight

It's a common glitch.

Do this:
```
sudo gedit /etc/modprobe.d/alsa-base
```

Add the line:
```
options snd-hda-intel model=lenovo
```

(my notebook is a Sahara, but "lenovo" does the trick! If it doesn't do ti for you, use "auto" instead (without quotes))
hey, for some reason,  neither "auto" or "lenovo" worked. any other leads on how to fix this?  why it doesnt get fixed in a reinstall just confuses me

---

### Post by Nepherte on 2008-08-23
First you must find which model of sound card you use, so run this command: ```
cat /proc/asound/card0/codec#* | grep Codec
```

It will return the model of your sound card, for example: "Codec: Realtek ALC260". Search for your model [here]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt"), and take a look at its types. Read all of them listed under your model and try to find the one which is more similar to your sound card. Now open up alsa-base:
```
sudo gedit /etc/modprobe.d/alsa-base
```
Then edit the line at the end of the file to resemble to:
```
options snd-hda-intel model=MODEL
```
Save the file and reboot.

---

### Post by midnight0000 on 2008-08-23
ok, this might be a total noob mistake, but when i type in:

cat /proc/asound/card0/codec#* | grep Codec  

i get "no such file or directory". i did look at that list and look for different models of snd-hda-intel  and tried a few, but so far no success

---

### Post by midnight0000 on 2008-08-26
bumping - really need sound on this. i know it probably has to do with changing the file and adding the option for the soundcard, but the code to show the soundcard isnt working for me
anything?

---

### Post by eggdeng on 2008-08-26
Post the output of
```
aplay -l
```
The laptop is a Gateway - which model?

---

### Post by cmoran on 2008-08-26
hey I'm having the exact same problem(s)... again on an older gateway 3520GZ

eggdeng, I get:

chad@chad-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Any help is greatly appreciated!

---

### Post by midnight0000 on 2008-08-26
my hateway *ahem* gateway, is model w322

when i type the code you provided, it worked and gave me this:
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by eggdeng on 2008-08-26
You can check whether your drivers are working by opening a music file in Totem-xine or Audacity. If you can see the waveform, sound is working but not getting routed to the speakers, the usual Intel HDA problem.
Very few people seem to have got sound working on Gateways. The only fix I have seen to work in one or two cases is, as above
```
sudo gedit /etc/modprobe.d/alsa-base
```
but adding
```
options snd-hda-intel probe_mask=1
```
You must reboot for changes to take effect. You may get lucky. If not, maybe a set of usb speakers?

---

### Post by Erewhonman on 2008-08-30
Nepherte, after finding out the precise model of my sound card on my Acer Aspire laptop, I input that as you suggested but that did not work.  Then I simply put in 'Acer' and that worked.  Perhaps the sound card model works on some but on others it is the manufacturer name.

---

### Post by Psychoscorpic on 2008-09-02
Right - did this, and found my chipset, but not my manufacturer (Sahara). Then tried all the options (3stack, lenovo, etc) and finally "hp" was the one that did it for me! 
:guitar: Now have sound both through speakers and headphones, with headphone jack switching automatically when the plug is inserted!

> **Nepherte said:**
> First you must find which model of sound card you use, so run this command: ```
cat /proc/asound/card0/codec#* | grep Codec
```

It will return the model of your sound card, for example: "Codec: Realtek ALC260". Search for your model [here]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt"), and take a look at its types. Read all of them listed under your model and try to find the one which is more similar to your sound card. Now open up alsa-base:
```
sudo gedit /etc/modprobe.d/alsa-base
```
Then edit the line at the end of the file to resemble to:
```
options snd-hda-intel model=MODEL
```
Save the file and reboot.

---

### Post by Morgoroth on 2008-09-28
> **Nepherte said:**
> First you must find which model of sound card you use, so run this command: ```
cat /proc/asound/card0/codec#* | grep Codec
```

It will return the model of your sound card, for example: "Codec: Realtek ALC260". Search for your model [here]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt"), and take a look at its types. Read all of them listed under your model and try to find the one which is more similar to your sound card. Now open up alsa-base:
```
sudo gedit /etc/modprobe.d/alsa-base
```
Then edit the line at the end of the file to resemble to:
```
options snd-hda-intel model=MODEL
```
Save the file and reboot.

i have an acer 5920 and non of this is working- im still not getting any sound from the laptop speakers:(

---

