---
title: "Vaio VPC-EH1L1R - troubles with sound"
date: 2011-08-29
forum: Hardware
---

### Post by Riateche on 2011-08-29
Hello. I have Ubuntu 11.04 installed on Sony Vaio VPC-EH1L1R. 
```
$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant CX20590
```
In sound settings I disabled HDA NVidia sound device and set other device as default, analog stereo duplex. Input and output are enabled and volume is set properly. Main speakers work fine, but:

1. Build-in microphone doesn't work. 
2. External microphone doesn't work.
3. Headphones doesn't work, speakers continue to sound off.

I found many manuals how to fix it, but they all are helpless.

What should I do?

---

### Post by ferezvi on 2011-09-04
hi, yo can try this 

sudo gedit /etc/modprobe.d/alsa-base.conf

and add the this at the end

options snd-hda-intel model=thinkpad

---

### Post by Riateche on 2011-09-05
Thank you, it works.

---

### Post by flavin on 2011-09-17
Thanks ferezvi

that works for me in a vaio VPC EH1S1E

---

### Post by rafaellg on 2011-09-28
Also worked for me.
Sony Vaio VPC EH10EB

---

### Post by j4java on 2012-04-09
> **ferezvi said:**
> hi, yo can try this 

sudo gedit /etc/modprobe.d/alsa-base.conf

and add the this at the end

options snd-hda-intel model=thinkpad

This has worked for my VPCEH15EN Vaio which uses the same chipset.

---

