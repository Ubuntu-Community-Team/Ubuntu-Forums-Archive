---
title: "Bluetooth + blueman + bluez + Intrepid = a mess."
date: 2009-05-09
forum: Hardware
---

### Post by acoccimi on 2009-05-09
I'm running Eeebuntu (Intrepid Ibex) on my EeePC 701. I have an unnamed bluetooth dongle attached. Before I upgraded to Intrepid Ibex, bluetooth was working very easily, but now it's a real problem.

hciconfig shows that the adapter is present, so after sudo hciconfig hci0 up I am able to do everything that hciconfig/hcitool can do (I believe). I have very little interest in attempting to do all of my bluetooth jobs via hcitool, so I want to get a sweet graphical interface running (either blueman or gnome-bluetooth). Problem is, neither of them can detect my adapter. Bluetooth applet does not show the icon, indicating that it can't see the adapter, and Blueman is acting even more buggy with it complaining that the bluez daemon is not running.

I've Googled as much as I could on the subject, and it seems many others have similar problems. There appears to be a module called hci_usb that some have modprobe'd, but it does not exist on my system. People say to downgrade bluez to version 3. Absolutely no clue how to do that without breaking my system further, so I'd like to keep it at version 4.

Currently the bluez-gnome package (and hence the gnome bluetooth applet) was uninstalled, as it can't coexist with blueman. Personally I think my system was better before I installed blueman. Is there anyone with any information? Help would be very much appreciated. I'll post the output of any commands upon request. Thanks in advance!

---

### Post by Parallel on 2009-05-23
I also had a cheap BT-dongle that was useless in Intrepid, no matter what i tried. This [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268502") seemed to be the culprit.

Good news is that it works perfectly with Jaunty + Blueman (From [http://blueman-project.org/](http://blueman-project.org/)).

Looking at the bug report, a fix will be released for Intrepid. But I don't know how closely the Eeebuntu project follows upstream Intrepid, so it might take a while for it to get to your installation.

---

