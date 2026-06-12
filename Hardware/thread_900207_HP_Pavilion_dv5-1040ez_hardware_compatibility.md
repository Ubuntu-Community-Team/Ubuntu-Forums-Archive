---
title: "HP Pavilion dv5-1040ez hardware compatibility"
date: 2008-08-25
forum: Hardware
---

### Post by huba! on 2008-08-25
hi@all,

I want to purchase a new notebook and set my eyes on a HP Pavilion dv5-1040ez Entertainment Notebook (FM558EA).

Here's the link to the specs:
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01509158&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01509158&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN")

Does anybody have some experiences with Ubuntu on this machine? It comes with a pre-installed 32bit Vista Home... I am sure you can understand my wish to replace it with a proper OS ASAP :D
I would be interested in any information about hardware compatibility and available drivers for this PC. Thank you very much in advance!

---

### Post by Crafty Kisses on 2008-08-25
Looks pretty solid to me, I'd check the Wireless card though.

Checkout this link > [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by huba! on 2008-08-25
Thanks for your answer.
According to this (IMHO very useful) how-to, the Intel PRO/Wireless 4965AGN which is used in this particular notebook is fully supported in Hardy 8.04 through backport modules:

[http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops#wireless]("http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops#wireless")

Actually I am more concerned about the webcam, Bluetooth and the power saving (laptop-mode).
I'd be grateful for any further information. Best would be if somebody has already tried to install Hardy on this nice notebook and would be willing to share his experience with me.

---

### Post by huba! on 2008-08-27
nobody else? :confused:

---

### Post by Ect. on 2008-08-30
Hello,

I have just bought it 3 days ago, and ended here looking for wifi drivers. The bluetooth worked out of the box, and I managed to connect my phone without any problem. But I didn't went farther on this point. On the Acpi side the cores are running at 800 MHz ondemand, seems ok. The screen dims correctly when unplugged, battery sensors ok, the sensitive buttons for mute and volume are working. Card reader for SD ok.

What's not working out of the box: DVB-T tuner, fingerprint reader, sound master volume slider have no impact on loudness, one have to open the sound controls and use the pcm slider (sensitive buttons commands master volume)...

Edit: the webcam is working perfectly well out of the box.

I haven't tried hdmi yet.

The beast runs warm, the power adapter hot as hell, the fan is quiet provided you don't launch any fancy 3D game.

Hope this helps...
Ect.

---

### Post by Vavi on 2008-09-09
I've just bought a HP dv5-1040el.
After two hours of Vista i couldn't wait anymore and installed Ubuntu 8.04.
After some work everything seems to function properly. Now only the fingerprint sensor and the DVB-T are left.

I've tried fprint-demo which seems to work on old Hp laptop but it can't find my fingerprint device. Do you have better any ideas?
(I have followed [this]("http://aldeby.org/blog/index.php/howto-ita-ubuntu-linux-su-portatili-hp-pavilion-serie-dv2000-dv6000-dv9000") guide)

Furthermore, still no succes in configuring the DVB-T and watching digital television.

---

### Post by leofishman on 2009-03-13
> **Vavi said:**
> I've just bought a HP dv5-1040el.
After two hours of Vista i couldn't wait anymore and installed Ubuntu 8.04.
After some work everything seems to function properly. Now only the fingerprint sensor and the DVB-T are left.

I've tried fprint-demo which seems to work on old Hp laptop but it can't find my fingerprint device. Do you have better any ideas?
(I have followed [this]("http://aldeby.org/blog/index.php/howto-ita-ubuntu-linux-su-portatili-hp-pavilion-serie-dv2000-dv6000-dv9000") guide)

Furthermore, still no succes in configuring the DVB-T and watching digital television.

I have a pavilion dv4 with the same sintoms.
fprint-demo can't find the device.

thanks

---

### Post by StaticIp on 2009-03-19
Same here, DV4 but no finger print reader.. Let me know if the HDMI is worth it, im looking to get a compatible TV

---

