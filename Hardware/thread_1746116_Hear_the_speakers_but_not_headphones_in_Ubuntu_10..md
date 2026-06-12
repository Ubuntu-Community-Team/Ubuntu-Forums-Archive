---
title: "Hear the speakers but not headphones in Ubuntu 10.10 and 11.04"
date: 2011-05-01
forum: Hardware
---

### Post by sidaphextwin on 2011-05-01
Hello,
I have a headset jack that I can not run on ubuntu. The point is that yes I have sound but always through the speakers on my laptop.

I edited the file **/etc/modprobe.d/alsa-base.conf** adding the following lines:

**options snd-hda-intel model = acer position_fix = 1 index = 0 enable = 1 enable_msi = 1**

does not work, then ...

**options snd-hda-intel model = auto position_fix = 1 index = 0 enable = 1 enable_msi = 1**

did not work, then ...

**options snd-hda-intel model = laptop position_fix = 1 index = 0 enable = 1 enable_msi = 1**

but neither.

Following the instructions I have to launch this command, see codec used and the list of models displayed in the address below to configure **/etc/modprobe.d/alsa-base.conf** getting the model as above.

Launching this **cat /proc/asound/card0/codec # * | grep Codec** I get:

Codec: ATI HDMI R6xx

[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt]("http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt")

The fact is that the list of models no R6xx ati hdmi or hdmi or ati, nothing ... And I can not solve the issue that the headphones.
Running alsamixer for **R6xx ATI HDMI** codecs I have only one S / PDIF to 00. If you press F6, I get a second card HDA ATI SB with **Conexant CX20584** codec and I get this only controls MASTER, PCM and BEEP.

Anybody can help me?

---

### Post by PikachuX on 2011-07-19
Exactly the same issue on the *EasyNote TK11*-*BZ*-[I]056NC which appears to have the same soundchip so I guess we'll just have to sit tight in the boat and wait until the drivers get updated.
[/I]

---

### Post by PikachuX on 2011-07-20
[IMG]http://img34.imageshack.us/img34/8490/31624a.jpg[/IMG]

I went ahead and bought a usb sound card "Device 011: ID 1130:f211 Tenx Technology, Inc. TP6911 Audio Headset". I bought mine from Kjell och company in sweden(check usb ljudkort swedes) but [http://www.dealextreme.com/p/usb-3d-sound-adapter-color-assorted-5831](http://www.dealextreme.com/p/usb-3d-sound-adapter-color-assorted-5831) seems to be same model but i can't verify if it has the same chips inside.

It's a ultra cheap solution for us with the **Conexant CX20584 **who wants some headphone action.

---

