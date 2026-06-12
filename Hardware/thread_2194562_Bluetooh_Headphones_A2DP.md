---
title: "Bluetooh Headphones A2DP"
date: 2013-12-19
forum: Hardware
---

### Post by brufus on 2013-12-19
Since I upgraded ubuntu to 13.10 I've been having problems connecting with my Bluetooth headphones which worked perfectly in previous version.

Initially, I couldn't even connect them. In order to solve that I had to change  /etc/bluetooth/audio.conf file by adding:
```

[General]
Enable=Socket

```

After that, I was able to connect my headphones but when I connected them sound was still outgoing through the speakers. Before I upgraded, when the Bluetooth were connected the system automatically select the Bluetooth headphones as output, similarly to connect the wire headphones. Moreover, the Bluetooth headphone does not even appear in the still in the "Sound Properties" Output tab.

I solve that by, every time after connecting the Bluetooth headphone, executing:
```
pactl load-module module-alsa-sink device=bluetooth
```

Still it doesn't select automatically the Bluetooth headphone, but make the available in the Sound Properties (it appears as a sound card, without any name or property). Look screenshot: [image]("http://imgur.com/DRHK5rg").
 
Even if I get it to work it is still has some inconvenient:
[LIST]
[*] To execute "pactl load-module" each time I connect them.
[*] Not switching automatically between speakers and head when I connect and viceversa
[*] When I disconnect the headphones the applications that have sound either crash or freezes, eg. browser, totem, spotify, etc..
[/LIST]

Could someone give me some clues to solve those still remaining problems? 

Thank you very much

---

