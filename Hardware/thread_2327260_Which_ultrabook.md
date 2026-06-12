---
title: "Which ultrabook?"
date: 2016-06-09
forum: Hardware
---

### Post by st_ab on 2016-06-09
Hello,

I'm returning my Lenovo Yoga 900 Business Edition because the ssd is not recognized by neither Ubuntu nor Clonezilla. This seems to be caused by a BIOS-bug (see [https://forums.lenovo.com/t5/Linux-Discussion/Yoga-900-13ISK2-BIOS-update-for-setting-RAID-mode-for-missing/td-p/3339206](https://forums.lenovo.com/t5/Linux-Discussion/Yoga-900-13ISK2-BIOS-update-for-setting-RAID-mode-for-missing/td-p/3339206) for more details).

Do you have any recommendations for an ultrabook which works with linux?

---

### Post by Linuxisfast on 2016-06-09
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime) works out of box with 16.04

---

### Post by st_ab on 2016-06-09
The Zenbook Prime seems hard to get (at least in Europe).

Any thoughts about the HP Spectre 360 or Dell XPS 13? I've read about issues with both models. Are these issues resolved?

---

### Post by X-RED_Tech on 2016-06-09
The issues relate to the new [COLOR=#000000]NVME PCIe [/COLOR]M2 drives, not the models themselves. One workaround is to change the mode from the default RAID to AHCI but one user commented about a "locked BIOS(???)" in the Yoga 900: [http://ubuntuforums.org/showthread.php?t=2326622](http://ubuntuforums.org/showthread.php?t=2326622)

The links there might be useful for you.

---

### Post by st_ab on 2016-06-09
> **X-RED_Tech said:**
> The issues relate to the new [COLOR=#000000]NVME PCIe [/COLOR]M2 drives, not the models themselves. One workaround is to change the mode from the default RAID to AHCI but one user commented about a "locked BIOS(???)" in the Yoga 900: [http://ubuntuforums.org/showthread.php?t=2326622](http://ubuntuforums.org/showthread.php?t=2326622)

The links there might be useful for you.

Thanks for the Links. The BIOS is not locked - there is simply no option to switch from RAID to AHCI in the BIOS (only very few settings). So there seems to be no way to switch from RAID to AHCI :(

What annoys me is that Lenovo sells different hardware under almost the same name. The older version seems to work with linux the newer ones are not working. Before buying the Yoga 900 I did some research about ultra books and came to the conclusion that the Yoga 900 works acceptable. Now that I got a non working model from Lenovo I am quiet frustrated. :(

---

### Post by X-RED_Tech on 2016-06-09
Not that I recommend doing that - it's up to you - but you can probably replace that drive...

---

### Post by st_ab on 2016-06-09
> **X-RED_Tech said:**
> Not that I recommend doing that - it's up to you - but you can probably replace that drive...

I will just return the whole computer.

---

