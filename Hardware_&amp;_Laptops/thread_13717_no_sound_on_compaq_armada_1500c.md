---
title: "no sound on compaq armada 1500c"
date: 2005-02-02
forum: Hardware &amp; Laptops
---

### Post by josh on 2005-02-02
hi guys!

i was amazed that ubuntu full install ran on my old compaq armada 1500c! nice work! the problem though is that i have no sound and i could not also play vcds with totem movie player it sez that it needs a plugin. i do not have a modem or a network card for that laptop. that is why i could not download plugins. questions:

1. how do i enable sound? 

2. how do i watch vcds? 

thanks guys!

regards,

josh

---

### Post by oasill on 2006-02-19
Hi Josh,

To activate sound on Compaq Armada just add the single line:

snd-es1688

to the end of /etc/modules. Reboot or make a insmod and you should have
sound if the rest is set up ok. Check that you have correct accessrights
to /dev/dsp and /dev/audio and that you are a member of group audio.
Finally install e.g. the program "saytime" to verify that things work.

                     Regards oasill

---

### Post by tonyhawz on 2007-12-07
thank you very much for this post , it worked perfect in a compaq armada 1500c with feisty on it.
to do it in copy/paste mode :
```
sudo su -
modprobe snd-es1688
echo snd-es1688 >> /etc/modules
exit
```

---

