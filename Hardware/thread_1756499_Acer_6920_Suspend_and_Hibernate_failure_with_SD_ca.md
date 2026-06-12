---
title: "Acer 6920 Suspend and Hibernate failure with SD card in card reader."
date: 2011-05-12
forum: Hardware
---

### Post by triple.eh on 2011-05-12
I have an Acer 6920G and experienced some issues with the card reader and suspend/hibernate features in Ubuntu 10.04 i386.

The two problems I experienced are:
[LIST=1]
[*]Could not suspend/hibernate with an SD card mounted in the card reader.
[*]Could not mount an SD card if it was not in the reader at boot time.
[/LIST]

For the first problem, I found a solution to the suspend/hibernate when an SD card is in the card reader in the [http://ubuntuforums.org/showpost.php?p=3019416&postcount=3"][COLOR="RoyalBlue"]Ubuntu forums archive[/COLOR]](").  Adding "sdhci" to the MODULES list in /etc/default/acpi-support solved the issue and I do not get any errors on the console nor does the error the original post describe show up in my logs.  This issue does not appear to be limited to Acer 6920G, but other laptops and hardware may have the same issue.

I still have not resolved the second problem:  if there is no SD card present in the card reader at boot, Ubuntu 10.04 does not recognize the card reader.  This is why I typically keep an old 8MB SD card in the reader at all time to both minimize the dust build-up in the slot and for the card reader to be recognized at boot time.

I hope this thread helps anyone with the suspend/hibernate problem and if you have any insight into getting the card reader to be recognized at boot time without the need to have a media card in it I appreciate your advice!

---

