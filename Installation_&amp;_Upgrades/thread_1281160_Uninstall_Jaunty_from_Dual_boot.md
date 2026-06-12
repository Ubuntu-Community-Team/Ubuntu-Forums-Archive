---
title: "Uninstall Jaunty from Dual boot"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by johnjoy on 2009-10-03
I will state my problem crisply,

I have 2 operating systems, Jaunty and Vista(home premium) on separate partitions in Dell 1440 inspiron

When I boot my system, in the fist boot menu i see 3 operating systems 2 Jaunty's and 1 Vista
If I click Vista, then again I see 2 operating systems Ubuntu (this one doesn't work) and Vista

In the first boot window, both Jauntys open the same OS, with all file settings same.

I want to remove all this clutter. I just want ONE boot window Jaunty and Vista. What should I do? I want time tested advises, not maybe it will work kind of answers, because I am a student, and I don't have much time to sit on my lappy for long time. Else I will screw my acads.

I think so many Jauntys came because I installed Jaunty again, on the same partition which had an 'older' Jaunty.

Ubuntu guruji's please help. Any help will be rewarded with loads of hugs and kisses!

John

---

### Post by presence1960 on 2009-10-03
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by theozzlives on 2009-10-03
Sounds like your GRUB is showing 2 kernels, and you tried to install VIA WUBI (under Windows). 

You can get rid of the WUBI by first going to Programs and Properties in your Vista Control panel. If that don't work you can edit your boot.ini by going to start > run > type msconfig and hit enter.

The other Kernal is there as a "fall back" in case a new kernel goes foobar on you. It's normal.

---

