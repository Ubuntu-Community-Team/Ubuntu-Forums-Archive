---
title: "How do I get sound to work on Asus Transformer T100 with Ubuntu 16.04?"
date: 2017-10-15
forum: Hardware
---

### Post by peridian on 2017-10-15
Hi,

I've been following the instructions for installing Ubuntu 16.04 LTS (kernel: 4.10.0-37) onto my old Transformer T100 (model: T100TA-DK002H) found here: [http://www.jfwhome.com/2016/01/04/latest-steps-to-install-ubuntu-on-the-asus-t100ta/](http://www.jfwhome.com/2016/01/04/latest-steps-to-install-ubuntu-on-the-asus-t100ta/)

The system boots, and a full apt-get upgrade has run fine.  Everything (that I care about) works, except for the sound.  In the main UI for Sound settings, it lists "Output -> Play sound through" with "Dummy Output".

Following the instructions, when I run the below command, I get the following output:

```

> sudo alsactl -f /var/lib/alsa/asound.state restore

No state is present for card bytcrrt5640
Found hardware: "bytcr-rt5640" "" "" "" ""
Hardware is initialized using a generic method
No state is present for card bytcrrt5640

```

The original post ([http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/](http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/)) talks about pulling down Intel firmware files from ChromiumOS and putting them in the system directories.  However in 16.04 it appears these files are already present, so I don't want to go overwriting them unnecessarily.

There are various posts around the web about how to get this to work, but they all vary in model and Ubuntu version, so I don't know which instructions to follow.

Does anybody know which files are needed to get Ubuntu 16.04 to work on the specific model of sound device on this tablet?

Regards,
Rob.

---

### Post by peridian on 2017-10-16
Okay, got this working.  After a bit of fiddling around, I discovered that the alsa ucm folders for this particular device were missing from the Ubuntu install.  Firmware drivers were already correct.

Thanks to a post here: [https://plus.google.com/117678584843504718765/posts/Z47kmVKe13K](https://plus.google.com/117678584843504718765/posts/Z47kmVKe13K)

All I needed to do was:


[LIST]
[*]download the UCM files,
[*] copy the two folders for the sound device (as indicated by the linuxium-install-UCM-files.sh script, also referenced in that post) to the ucm folder (see below)
[*]delete the state file at /var/lib/alsa/asound.state
[*]reboot
[/LIST]

```

sudo cp -vrf UCM-master/bytcr-rt5640 /usr/share/alsa/ucm
sudo cp -vrf UCM-master/chtrt5645 /usr/share/alsa/ucm

```

---

### Post by shadoogie2960 on 2018-06-13
Thanks a lot ! Worked for me on my T100TA with Lubuntu 18.04

---

### Post by fundatillus on 2018-10-21
Thanks, @peridian! This got the sound working on my Acer Chromebook CB3-131.

---

### Post by greatbigbadger on 2018-11-21
Where do you download the UCM files from?

---

