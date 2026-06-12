---
title: "Restoring evolution without &quot;backup file&quot;"
date: 2008-10-16
forum: General Help
---

### Post by thabo on 2008-10-16
I stupidly decided to change my heatsink without backing up- I needed to remove the motherboard etc...
Anyway- I have lost grub and access to my XP drive (not important). I am now running from a live cd and able to see the ubuntu drive but obviously cant run evolution- is there a place where I can locate the evolution data, back it up and then reinstall ubuntu etc.

Thanks

---

### Post by Elfy on 2008-10-16
This might help in retrieving your evolution data - [http://ubuntuforums.org/showpost.php?p=5395383&postcount=9](http://ubuntuforums.org/showpost.php?p=5395383&postcount=9)

You will need to get your old partitions mounted and then navigate to the folder, you might be able to copy the original into the livecd evolution, if that does work use the evolution backup - it's a lot easier :)

However, you might find that you can get your install to boot with the new mobo, if grub has been lost you can reinstall grub using the livecd.

To reinstall grub - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick) Start

---

### Post by thabo on 2008-10-16
Thanks forestpixie.

I will try that and see what happens- will let you know.

---

### Post by thabo on 2008-10-22
I eventually reinstalled ubuntu on a new harddrive and was then able to access the "broken" drive. Then I copied the hidden .evolution folder and pasted it into the new install drive. Worked perfectly. Thanks for your help forestpixie.:)

---

