---
title: "Installed libmtp- how do I force mounting as MTP rather than MSC?"
date: 2006-07-16
forum: Hardware &amp; Laptops
---

### Post by ummagumma82 on 2006-07-16
I have a Sansa m240 MP3 player, which has two USB modes: "autodetect" (MTP, fallback to MSC) or strictly MSC.

I had been using it in MTP mode before installing Ubuntu at home. When I plugged in the MP3 player, it switched to MSC mode and worked perfectly. Except, it could not see any files saved in MTP mode or vice-versa.

So I copied the files over from the MTP side, and set it to always use MSC. This would have worked, if not for what I assume is a major firmware bug in the m240. In MSC mode, it refused to sort my WMA-formatted songs by track number. Instead, everything was sorted alphabetically by title. I ensured the filenames began with the track numbers, and that the extended info contained the tracks. I even tried reformatting and reflashing the firmware, but it didn't change. I finally gave up and copied my songs back over in MTP mode, and it went back to sorting by track numbers. 

So I compiled/installed libmtp. It created a udev rules file which contained a variety of USB players. It didn't have mine, so I got the info from lsusb and added the following line:

# Sandisk Sansa m240
SYSFS{idVendor}=="0781", SYSFS{idProduct}=="7400", SYMLINK+="libmtp-%k", MODE="666"

However I cannot get Linux to see it as an MTP device. It insists on mounting it as MSC instead. I tried many things including adding 'OPTIONS="last_rule"', renaming the rules file to start with "00-" so it gained precedence, etc. No matter what I do, the player switches to MSC mode. I watched the output of udevmonitor when I plugged it in, and that entry does not seem to change anything at all.

I finally tried adding 'OPTIONS="ignore_device"', and that *did* work. So I know I have the correct product ID, and that it is reading the rules file.

But what can I do to force udev to try using it as an MTP device rather than immediately assuming it's a mass storage device? Or does something else communicate with it before udev becomes involved, which I need to be looking at instead?

I am fairly experienced with Linux in the server environment, but USB autodetection and multimedia stuff is very new territory for me. Any help would be greatly appreciated. :)

---

