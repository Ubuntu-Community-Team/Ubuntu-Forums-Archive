---
title: "Help with Toshiba L30 audio"
date: 2008-06-03
forum: Hardware
---

### Post by hemajith on 2008-06-03
I have recently installed Ubuntu 8 and LOVING IT. I use a Toshiba L30 Laptop with 1.2GB RAM. I have a problem with Linux version and this laptop. Audio only works from the audio out! When I want to hear audio, either I have to plug in a headset or external speakers! built in speakers doesn't work. Earlier I used Fedora 8 and it had the same problem. Can anyone help?

---

### Post by Travaux Publics on 2008-06-12
Hello from France,
you must change your "alsa-base" config.
To do it you have to edit /etc/modprobe.d/alsa-base and place at the end of the text doc but before this ligne 
# Ubuntu #62691, enable MPU for snd-cmipci
this elements :
options snd-hda-intel model=6stack-digout
options snd-hda-intel model=dallas

You get something like that :
# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
options snd-hda-intel model=6stack-digout
options snd-hda-intel model=dallas
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

You must restart your laptop and you go to <system/preferences/volume control> (or something like that). Please chek "surround".

Then you will have sound on speakers and earphone.

If you have no sound try again with "3stack" and not "dallas".

If nothing is change, you can see the "french doc" with the surch on "Toshiba L30".
[http://forum.ubuntu-fr.org/](http://forum.ubuntu-fr.org/)


Good by (sorry for my english !)

---

### Post by hemajith on 2008-06-12
Thank you for your help. When I modified the file as you suggested, the speakers started working. But when I plugged in the head phones nothing happened, the laptop sounds kept on coming. So I changed 'dallas' with '3stack'. Now when I plug in the head phone, the laptop speakers get cutoff but still can't hear anything on head phones! The microphone of the headphone works.
Is there a reason why the sounds automatically doesn't switch to the headphone when I plug it in?

---

### Post by Travaux Publics on 2008-06-13
Hello,
I don't know why it doesn't work. I've got Hardy with the config I send to help you. It doesn't work at the first time, but after 3 restarts.

You can find some others ideas here :
[http://doc.ubuntu-fr.org/materiel/liste_portables/toshiba](http://doc.ubuntu-fr.org/materiel/liste_portables/toshiba)
(For the L30 it's at the end of the page)

I join some "capture d'écran", perhaps they help you.

You can have more info here, in french :-)
[http://wiki.ubuntu-fr.org:81//audio_intel_hda](http://wiki.ubuntu-fr.org:81//audio_intel_hda)

Good Bye

---

### Post by hemajith on 2008-06-14
> **Travaux Publics said:**
> Hello,
I don't know why it doesn't work. I've got Hardy with the config I send to help you. It doesn't work at the first time, but after 3 restarts.

You can find some others ideas here :
[http://doc.ubuntu-fr.org/materiel/liste_portables/toshiba](http://doc.ubuntu-fr.org/materiel/liste_portables/toshiba)
(For the L30 it's at the end of the page)

I join some "capture d'écran", perhaps they help you.

You can have more info here, in french :-)
[http://wiki.ubuntu-fr.org:81//audio_intel_hda](http://wiki.ubuntu-fr.org:81//audio_intel_hda)

Good Bye

OK I got it to work! Thank you very much for your help.

---

