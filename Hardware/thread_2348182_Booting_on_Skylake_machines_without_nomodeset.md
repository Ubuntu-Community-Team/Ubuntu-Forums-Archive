---
title: "Booting on Skylake machines without nomodeset"
date: 2017-01-01
forum: Hardware
---

### Post by pipo2004 on 2017-01-01
Somehow, the kubuntu 16.10 installer runs fine on my new machine (without using the nomodeset boot option) (Medion X6601, skylake + nvidia GTX90M) and all seems to be working ok. When I type ls: /sys/class/backlight, I get and entry: intel_backlight.

But after installing, all is wrong. The system won't boot unless I add the dreaded nomodeset to the boot options, and that means that the system runs with degraded graphics capabilities. Also /sys/class/backlight is empty after installing, which means that the screen brightness cannot be adjusted.

I have been pulling out my hairs for several days now and searched all forums about how to fix this, but to no avail. Many suggest other boot options, but none work on my system.

Does anyone know how to boot 16.10 on a skylake machine without having to use nomodeset?

---

### Post by Bashing-om on 2017-01-01
pipo2004; Hello; Welcome to the forum .

A thought, have you tried installing a nVidia proprietary driver for the  nvidia GTX90M card ?
Try from the Additional Drivers utility .
Having this driver installed will make a world of difference.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by pipo2004 on 2017-01-01
I cannot find an additional drivers utility in Kubuntu. Also, this is a laptop with a combined intel/nvidia chipset. I am not sure that these systems can run fully on nvidia.

---

### Post by Bashing-om on 2017-01-01
pipo2004; Hey ;

I have not seen (k)ubuntu in ages . I can not explicitly tell you where the "Additional Driver" tool is located.
We can however use the terminal.
At the login screen key combo ctl+alt+F1 to gain a console interface.
Here login with username and password.
Now run;
```

sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```
which in addition to installing the nVidia driver will also install ' nvidia-prime and nvidia-settings' to control the graphic's sets .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by pipo2004 on 2017-01-02
Thank you. I got it to work. I re-installed ubuntu and then noticed that there was a check mark: "Install third party drivers".

That fixed it. I now boot without any extra boot options. I haven't tried the nvidia setup yet, but that is less interesting for me, as I don't use the machine for gaming. All is working fine on the laptop now, including the brightness control.

I have to use the brightness slider in KDE because the brightness hot-keys are not recognized, but that is no problem for me.

The laptop is a Medion Erazer X6601.

---

### Post by Bashing-om on 2017-01-02
pipo2004; Great !

As this matter is now concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

I look forward to our next adventure in 'buntu'n .

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

### Post by pipo2004 on 2017-01-09
Ok, I guess I celebrated too soon. Since doing a sudo apt-get update, sudo apt-get upgrade, and sudo apt-get dist-upgrade, the system again only boots when selecting adding in grub2.

If I select the previous kernel in grub2, the system starts fine.

---

