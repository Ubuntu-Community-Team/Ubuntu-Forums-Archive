---
title: "Speakers still play with headphones plugged in (Asus U50)"
date: 2010-07-02
forum: Hardware
---

### Post by Mugendai42 on 2010-07-02
I recently bought the Asus U50 laptop, and installed 64-bit Ubuntu 10.04 onto it. When I plug my headphones in, the sound comes out of both the speakers and the headphones, and I would rather it only plays through the headphones when I plug them in.

I don't know if the same also happens on Windows; I uninstalled it as soon as I got the laptop, after testing a few things first.

ALSA seems to recognize the sound hardware as being Intel HDA. I tried out a few solutions I found on Google, but none of them worked and seemed to only apply to older versions of Ubuntu.

If anyone could help me with my issue, I would appreciate it.

---

### Post by Moozillaaa on 2010-07-02
Sounds like the headphone port is configured NOT as a headphone port, but as a speaker output in a Surround Sound configuration 5.1, 7.1, etc. Or maybe even as a center-channel speaker setting...

Right click on the speaker volume applet, open volume control, 'switches' tab, check to see if headphones is checked.

Volume controller might not control advanced sound cards' configuration...

---

### Post by Mugendai42 on 2010-07-02
The switches tab isn't even there, unless I'm right-clicking on the wrong volume control applet.

---

### Post by phsopher on 2010-07-02
I had/have the same problem. I went to System>Preferences>Sound>Output and changed Connector from "Analog Speakers" to "Analog Output". However this is only a partial solution since I have to switch manually back and forth when plugging and unplugging headphones. This isn't really a big problem for me since I almost always use headphones, but it would be great if it could just sense when headphones are plugged in like Windows does.

---

### Post by Mugendai42 on 2010-07-02
"Connectors" doesn't seem to be there either, although it's probably a hardware-specific setting.

---

### Post by Mugendai42 on 2010-07-04
Anyone? I really would like this issue fixed.

---

