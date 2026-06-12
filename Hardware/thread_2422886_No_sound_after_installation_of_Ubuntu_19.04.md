---
title: "No sound after installation of Ubuntu 19.04"
date: 2019-07-14
forum: Hardware
---

### Post by UBUminJ on 2019-07-14
My PC of everyday is an old Dell Inspiron 530s (Intel Core 2 Duo E8500, Intel G33, manufactured in 2008) which still works well.

My LTS 14.04 run out of security updates and I installed 19.04. As usual after re-installation of a new Ubuntu, the sound was missing. 
I remember how many things I tried last time until the problem went away. This time I was lucky, I found the following helpful page immediately:

[https://www.linuxuprising.com/2018/06/fix-no-sound-dummy-output-issue-in.html](https://www.linuxuprising.com/2018/06/fix-no-sound-dummy-output-issue-in.html)
Fix No Sound (Dummy Output) Issue In Ubuntu With SND HDA Intel

After
"1. If you do get snd_hda_intel in the output of the above commands, and you get no sound (and only a Dummy Output) in Ubuntu, here's what you can try to fix it. You need to add options snd-hda-intel model=generic at the end of the /etc/modprobe.d/alsa-base.conf file. Do not modify anything else in this file!"
(see that page for details)

and a restart, the problem was solved.

Thank you.

---

