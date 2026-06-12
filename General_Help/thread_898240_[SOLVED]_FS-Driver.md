---
title: "[SOLVED] FS-Driver?"
date: 2008-08-23
forum: General Help
---

### Post by Yezinki on 2008-08-23
I did a dual boot of Vista & Ubuntu.......when I installed the FS-Driver,

it wont show the Ubuntu partitions/drives in the windows ...My Computer!

Hoping to hear from you, Regards!

---

### Post by carolinason on 2008-08-23
I've used an older version you didn't have to install, worked pretty good.

I looked in the screenshot on the web site section and there is step by step tutorial.

---

### Post by Yezinki on 2008-08-23
Hi there,

You mean this..........[http://www.fs-driver.org/screenshots.html](http://www.fs-driver.org/screenshots.html)

What about these images?

Thanks.

---

### Post by Yezinki on 2008-08-23
I thought you smart guys new about FS Driver..........

---

### Post by WRDN on 2008-08-23
Have you installed Ubuntu on your machine now Yezinki, and created the partitions using the scheme you PM'd me about?

---

### Post by Yezinki on 2008-08-23
yes

---

### Post by Yezinki on 2008-08-24
Hi there WRDN,

I have installed a dual boot & created partitions.......you  haven't replied to the FS- Driver issue......not showing the partitions in the windows environment?

Hoping too hear,

Thanks in advance.

Regards!

---

### Post by WRDN on 2008-08-25
Sorry for taking a while to reply. You could try using an older version of the driver, or removing it and reinstalling it. You could also try using [explore2fs]("http://www.chrysocome.net/explore2fs"). Alternatively, if you are using a shared partition, then format it to NTFS so both Windows and Ubuntu can read/ write to it. The issue here is that the files will become much more fragmented than if you were using the ext3 filesystem.

---

### Post by Yezinki on 2008-08-25
Thanks in the screen shot you can see the partitons.

5 total, 2 NTFS, 2 Ext 3, 1 Linux swap.

---

### Post by Yezinki on 2008-08-25
Do realize that it is a dual boot of Vista & not XP with Ubuntu!

---

### Post by WRDN on 2008-08-25
> **Yezinki said:**
> Do realize that it is a dual boot of Vista & not XP with Ubuntu!

Ah, thanks for the info :)

That has opened the path to another possible solution.

First, uninstall the FS- Driver. Now, right click on the executable used when installing, and click Properties. Now, select Compatibility and force the executable to run in compatibility mode for Windows XP. Now, start the executable and reinstall the driver. Hopefully this will solve the issue. I know the driver works in XP, but I've had no experience using it in Vista.

---

### Post by Yezinki on 2008-08-25
Thanks I shall let you know.

I appreciate your knowledge & my input lol.

---

### Post by Yezinki on 2008-08-25
I did as you suggested, but still no luck .

Any how thanks!

---

### Post by mc4man on 2008-08-25
I've used that driver also (in xp) so not exactly sure about vista but are you first going into the 'control panel', opening up the IFS Drives and setting a drive letter(s) for the partition(s)? If you don't give it/them a letter then nothing will show in 'my computer'

---

### Post by Yezinki on 2008-08-25
hi........ does not highlite the option to change or give drive letters........only Delete Volume & Help.

---

### Post by mc4man on 2008-08-25
Are you sure your looking in right place? (control panel -> ifs drives

Just tried on a vista box - installed fine and while i have no ext2/3 partitions it did allow me to pick a drive letter on an unlettered partition (dell media whatever

See screen for how it looks on this box (where I occasionally use it with xp

Shows drop down for ext3 partition (atm no linux partitions are set - shows 'none'

---

### Post by Yezinki on 2008-08-25
Thanks got em at last but when I click right for properties > windows shows file system as ext 2 while actually is ext 3.......probably old driver......or non compatible with Vista......it shows them as partition/drives with letters E,F......not tvol......as shown in images on FS-Driver link.

Thanks again!

---

