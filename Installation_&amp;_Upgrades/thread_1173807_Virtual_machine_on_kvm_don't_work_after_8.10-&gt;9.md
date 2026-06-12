---
title: "Virtual machine on kvm don't work after 8.10-&gt;9.04 upgrade"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by ED_209 on 2009-05-30
Although I have tried Ubuntu every now and then since 6.10 or so I'm still pretty much of a beginner when things go wrong. 
I'm very happy with 8.10 and 9.04 and rarely use windows anymore but still need it for some software that runs very poorly under wine. But now the problem:
While using 8.10 I configured a virtual machine running WinXP and since it worked almost instantly (after following a guide) I guess I missed lot's of the theory behind VM:s.
After upgrading to 9.04 I get the following message:
[FONT="Impact"]kvm-run -m 768 -k sv -hda /VirtualOS/WinXP.img
/etc/kvm-ifup: could not launch network script
Could not initialize device 'tap'[/FONT]

I guess something has changed with the catalogue structure in the upgrade since I don't have any /etc/kvm-ifup

I have searched the web all morning today but drown in information. Since I don't want to damage my WinXP.img I don't dare to try all the different suggestions I have stumbled upon without furter research. Is there anyone here who have a good idea of what has happened and can suggest a good solution?
Kind regards,

Ed

---

### Post by ED_209 on 2009-05-31
I'll answer my own question here, atleast the solved parts of it.
After plowing through tens of guides and countless numbers of help files I finally found the simple solution to the basic problem.
/etc/qemu-ifup had to be moved to /etc/kvm-ifup

*slaps myself for needing nearly 10 hours to find this solution*

Now the vm starts and functions as usual, the network bridge however seems to need some more work since I can't get online from my virtual environment.

---

