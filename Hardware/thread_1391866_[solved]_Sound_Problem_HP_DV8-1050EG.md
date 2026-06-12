---
title: "[solved] Sound Problem HP DV8-1050EG"
date: 2010-01-27
forum: Hardware
---

### Post by LinuxUser1988 on 2010-01-27
Hi all

i installed kubuntu 9.10 and got a problem with the sound.

kubuntu played all the sounds over the "subwoofer" which is integrated into the notebook.

i fixed that issue with upgrading alsa to the newest release (1.0.22.1)

a update script can be found here:
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

even that modified the file /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=laptop

i don't know if the last step is really nessesary (the config thing).


Just wanted to let you all know how to fix that issue.

---

### Post by codylambrecht on 2010-01-29
Thank you very much for this info, I have the same exact laptop.

Is there any other problems that you have ran into with this laptop? I use to have LinuxMint on my previous laptop due to a wireless card issue (it was a broadcom) and wanted to know how well Ubuntu would work or if I would run into tons of problems. You're the only one that I have found that has put linux on this laptop, so any kind of information or insight would be appreciated. 
Thanks for your time,
Cody.

---

