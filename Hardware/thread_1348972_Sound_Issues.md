---
title: "Sound Issues"
date: 2009-12-07
forum: Hardware
---

### Post by Joomla12 on 2009-12-07
I'm having issues with my sound and with the last thread I started, I didn't get much help. I keep getting popping noises from speakers for some reason and no other soutput setting works besides Analogue. I know that it's more than likely a driver issue but I'm not really sure what I should do.

Sound Card Info:

HDA NVidia
Conexant CX20549 (Venice)

Edit: I went ahead and went back to 9.04. I'll stay here until a few more bugs are worked out in 9.10... ;)

---

### Post by quixote on 2009-12-08
Is sound working okay in 9.04?  Hope so.  Then all's well that ends well.  (I'm still on 9.04 too, waiting for the dust to settle.)

---

### Post by lbharti on 2009-12-09
I am facing the same popping sounds in 9.10. Hope an update comes out.

---

### Post by nedwed on 2009-12-09
sudo gedit /etc/modprobe.d/alsa-base.conf
Comment out this line:
options snd-hda-intel power_save=10 power_save_controller=N

Restart. Stoped the cracking speaker sounds on my laptop.

---

### Post by Krovas on 2009-12-20
> **nedwed said:**
> sudo gedit /etc/modprobe.d/alsa-base.conf
Comment out this line:
options snd-hda-intel power_save=10 power_save_controller=N

Restart. Stoped the cracking speaker sounds on my laptop.


Worked for me too. Thanks.

---

### Post by Joomla12 on 2009-12-23
I'll try that after a few updates are released for 9.10. I'm still waiting for a good Grub 2 editor and a way to not theme the GDM manually.

Thanks for the posts guys. :)

@quixote: It works fine for me.

---

