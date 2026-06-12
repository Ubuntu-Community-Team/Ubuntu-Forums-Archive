---
title: "Hp Omen Troubleshooting - Solved and Ongoing - Solutions will get posted!"
date: 2018-09-22
forum: Hardware
---

### Post by markackerman8@gmail.com on 2018-09-22
Ubuntu and Hp - Such a bad Combo these days!

I will post ALL Solutions, to this top post as they come in to help the world - PLEASE HELP ME Do the same

HDMI Sound was a big problem, 

Solved it  with a the help a patch to the kernel by Marj Freudenberg, but Sadly it stopped working after Suspend - FARGing Annoying.  So a re-install of Ubuntu-18.04.1 and now neither SOUND or WIFI Now Recognized!!!

Please Help

Wifi solved by this:

```
sudo apt remove bcmwl-kernel-source && sudo apt install git dkms
git clone -b extended [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```

Wow I hope this helps somebody.

Now back to SOUND - and it is not a driver issue it is clearly a KERNEL Issue!
The Solution which worked until an hour ago and may help others but sadly not me any more:

I can confirm that kernel module, posted by Maik Freudenberg ([https://bugs.freedesktop.org/show_bug.cgi?id=75985#c27](https://bugs.freedesktop.org/show_bug.cgi?id=75985#c27)), is working fine on my system. Thank you for the fix. The HDMI audio device now works as it should.
• The steps I did to enable HDMI audio device:
&#8227; 1. Download and extract the file nvhda.tar.xz.  (from above link)
&#8227; 2. Run these commands in Terminal,  in the location of the extracted folder 
• ```
make
sudo make install
```
What it showed
&#8728; mkdir -p /lib/modules/4.15.0-35-generic/misc/nvhda
&#8728; install -m 0755 -o root -g root nvhda.ko /lib/modules/4.15.0-35-generic/misc/nvhda
• ```
echo nvhda | sudo tee -a /etc/initramfs-tools/modules
echo "options nvhda load_state=1" 
sudo tee /etc/modprobe.d/nvhda.conf[]sudo update-initramfs -u
```

---

