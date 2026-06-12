---
title: "Intel and Nvidia drivers not playing nice"
date: 2010-10-25
forum: Hardware
---

### Post by tomeofknowledge on 2010-10-25
I have a Gateway ID49C running Ubuntu 10.10 with a Intel card for power saving and a Nvidia card for performance. I installed the Nvidia drivers and rebooted to find a CLI, I checked /etc/X11 and found a **xorg.conf** which I found strange since I thought it had been depreciated. I then renamed it and rebooted to find my self back in a GUI. I immediately ran  **Nvidia X Server Settings** which informed me that I was not using the nvidia driver. I tried *nvidia-xconfig* and* dkpg-reconfigure xserver-xorg* with the same effect.

How can I make it use the Nvidia card preferably with the ability to switch back to the Intel card in battery conservation situations.

---

### Post by tomo0607 on 2011-02-07
I use the same model and have had exactly the same problems for almost half a year.

I know that Optimus technology does not support Linux. (I'm really sad.)
But I am just wondering whether or not there is a way to enable the GPU instead of the IGP without Optimus technology.

I would appreciate any information on it.

---

### Post by Yellow Pasque on 2011-02-07
It depends on whether your BIOS allows you to switch off the IGP. You're at the mercy of Gateway BIOS designers (and you have my deepest sympathies).

---

### Post by tomo0607 on 2011-02-08
>Temüjin

Thank you for your reply and sympathies.

Unfortunately, it seems that the BIOS of ID49C does NOT allow users to switch GPUs even though I keep it the latest one.

May Gateway engineers be benevolent to Linux users!

---

