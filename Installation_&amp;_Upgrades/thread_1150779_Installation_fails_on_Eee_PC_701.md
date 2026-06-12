---
title: "Installation fails on Eee PC 701"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by DarkTxS on 2009-05-06
Hello :)

I'm using a USB device to install the 9.04 Netbook Remix on my Eee PC 701 (4GB). I wrote the image file to the device via ImageWriter (as suggested in the help section). Everything was good, the live version was running on the Eee, I ran the install, filled all settings, and then clicked the "Install" button. The installation began and when it showed that it was in the part of creating the partitions on the Hard Drive, it just stopped the installation and showed a package error.

In the installation preparation, I selected to overwrite the entire disk, format it and install the new system. I even tried again with other settings. Same error occurred. 

What can be the problem?

Thanks a lot! :)

---

### Post by rdsherwood on 2009-05-06
I did exactly what you did on an EEE PC 701 and an EEE PC 900A, and both worked flawlessly. Could it be possible that you have a corrupted file on the USB? If you didn't verify the checksum after the download (I never do and have never had a problem), maybe it's worth downloading the install package again and recopying it to your USB.

---

### Post by sgosnell on 2009-05-06
Did you run the Check CD option, or whatever the exact name is? That can check for a corrupt install file.  I agree that you should also check the md5sum to make sure you got a good download.  There can be errors both in the file download and in the image writing.

---

### Post by DarkTxS on 2009-05-07
After checking the md5sum, the hashes do not match, so it's probably an error with the file.
And the Check CD option returns that there are problems.
I'll try to download again.

Thanks :)

---

