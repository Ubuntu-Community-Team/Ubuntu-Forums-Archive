---
title: "touchpad not recognised acer aspire e15 e5-572g-5577"
date: 2014-09-14
forum: Hardware
---

### Post by orestiskotsas on 2014-09-14
Hello!
I recently bought an acer aspire e15 e5-572g-5577 notebook, I have installed Ubuntu 14.04 and the touchpad doesn't work at all..
It is not even recognised as a device..

The results of the command ```
xinput
``` gives:[COLOR=#3C3B37][FONT=Lucida Grande]
[/FONT][/COLOR]```

[COLOR=#3C3B37][FONT=Lucida Grande]&#9121; Virtual core pointer                       id=2   [master pointer  (3)][/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande]&#9116;   &#8627; Virtual core XTEST pointer                 id=4   [slave  pointer  (2)][/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande]&#9116;   &#8627; Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)   id=13   [slave  pointer  (2)][/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande]&#9116;   &#8627;                                            id=11   [slave  pointer  (2)][/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande]&#9123; Virtual core keyboard                      id=3   [master keyboard (2)][/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande]    &#8627; Virtual core XTEST keyboard                id=5   [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande]    &#8627; Power Button                               id=6   [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande]    &#8627; Video Bus                                  id=7   [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande]    &#8627; Power Button                               id=8   [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande]    &#8627; Sleep Button                               id=9   [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande]    &#8627; Video Bus                                  id=10   [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande]    &#8627; HD WebCam                                  id=12   [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande]    &#8627; AT Translated Set 2 keyboard               id=14   [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Lucida Grande]    &#8627; Acer WMI hotkeys                           id=15   [slave  keyboard (3)][/FONT][/COLOR]
```[COLOR=#3C3B37][FONT=Lucida Grande]

Any advice!
Thank you very much![/FONT][/COLOR]

---

### Post by orestiskotsas on 2014-09-17
any suggestion??

---

### Post by stefano21 on 2014-09-20
Same problem here? Did you manage to solve?
Thanks

---

### Post by orestiskotsas on 2014-09-22
> [COLOR=#000000]Same problem here? Did you manage to solve?[/COLOR]
[COLOR=#000000]Thanks[/COLOR]
No I didn't...
I have reported it on bugs.launchpad.net ...

---

### Post by gwmcvay on 2014-10-14
Just for the record - Same problem on E5-551-89TN

Will

---

### Post by tjqt06 on 2014-11-19
Finally, landing on a right thread.

I will share to you how my touchpad works. we have the same unit and my ubuntu version is 14.04 32bit

[HTML]For command line, you can run below commands one by one to download and install the new kernel:


1. For 32-bit system:
cd /tmp/

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-headers-3.16.0-031600-generic_3.16.0-031600.201408031935_i386.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-headers-3.16.0-031600_3.16.0-031600.201408031935_all.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-image-3.16.0-031600-generic_3.16.0-031600.201408031935_i386.deb

sudo dpkg -i linux-headers-3.16.0-*.deb linux-image-3.16.0-*.deb2. For 64-bit system:
cd /tmp/

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-headers-3.16.0-031600-generic_3.16.0-031600.201408031935_amd64.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-headers-3.16.0-031600_3.16.0-031600.201408031935_all.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-utopic/linux-image-3.16.0-031600-generic_3.16.0-031600.201408031935_amd64.deb


sudo dpkg -i linux-headers-3.16.0-*.deb linux-image-3.16.0-*.deb
Reboot and done.
If for some reason this kernel release doesn’t work properly for you, reboot into previous kernel (Grub -> Advanced -> select previous kernel) and run this command to remove Linux Kernel 3.16:
sudo apt-get remove linux-headers-3.16.0-* linux-image-3.16.0-*Finally update grub menu:
sudo update-grub
[/HTML]

credit goes [here]("http://ubuntuhandbook.org/index.php/2014/08/install-upgrade-linux-kernel-3-16/")

check if it works for you. mine is fully working, BUT



Now, my problem is my mouse pointer is now distorted/garbled. Updating the proprietary drivers doesn't load the session. Please help me also with this. Thanks.

---

### Post by chief-running-lemur on 2014-11-22
I have the same issue as above. I updated the kernel on my Acer E15 and now I have a semi-working trackpad (doesn't support two finger motions). However mouse pointer is all squashed. Anybody have any insight into that ?

---

### Post by aaror2 on 2015-02-17
[COLOR=#333333][FONT=monospace]You can use the Trackpad on the Acer Aspire E15 if you enter the BIOS by holding F2 at startup and changing the Trackpad setting from Advanced to Basic under the Main tab. This solved my issue with the Trackpad. Now I'm exploring why the BIOS is preventing Ubuntu from booting from an external drive - I believe the secure boot option is responsible.[/FONT][/COLOR]

---

### Post by aaror2 on 2015-02-17
Actually I just found out that if you wanted to leave the trackpad in advanced settings you could just run the following command:

sudo apt-get install i2c-tools

---

### Post by en666 on 2016-01-30
> **aaror2 said:**
> Actually I just found out that if you wanted to leave the trackpad in advanced settings you could just run the following command:

sudo apt-get install i2c-tools

I have an Acer ex2519 (xubuntu 14.04 lts) and i2c-tools worked like a charm!

---

### Post by Damian_Kober on 2016-03-13
> **aaror2 said:**
> [COLOR=#333333][FONT=monospace]You can use the Trackpad on the Acer Aspire E15 if you enter the BIOS by holding F2 at startup and changing the Trackpad setting from Advanced to Basic under the Main tab. This solved my issue with the Trackpad. Now I'm exploring why the BIOS is preventing Ubuntu from booting from an external drive - I believe the secure boot option is responsible.[/FONT][/COLOR]

this worked for me

---

