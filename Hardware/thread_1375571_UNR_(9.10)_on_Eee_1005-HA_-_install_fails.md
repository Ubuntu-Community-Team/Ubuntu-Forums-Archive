---
title: "UNR (9.10) on Eee 1005-HA - install fails"
date: 2010-01-08
forum: Hardware
---

### Post by teh-walrus on 2010-01-08
I have tried running this about 3 times now, and it fails each time. I am running the live CD and then installing from there (even if you choose the other option at boot, UNR seems to boot into the full GUI OS anyway).

The install seems to stop about half way through - it finishes copying files, tries activating apt, and then stalls. This means it has (at least) failed to install the bootloader, so unsurprisingly when I restart I get "no valid boot disk".

One quick note, when I started the process I specified custom partitions in a "new partition table" (I wanted seperate / and home partitions, and to be able to add a second / partition in case I want to install another flavour side by side). I noticed that XP that was on here before was on an EFI partition table, and am aware that ubuntu will probably have written a new MBR partition table. Do you think this could be the problem stopping the BIOS seeing the new partitions? I have the recovery DVD so I should be able to restore the original partitions and delete them one by one in the interface instead of starting again.

Otherwise, could this be a dud disk, or is the UNR interface just not showing me a popup window showing continuing progress while I restart the machine (there is def no HDD activity at this point - the hardware LEDs seem to be working fine in every other situation).

Thanks for your time...

---

### Post by teh-walrus on 2010-01-09
I post an update from the installed system itself!

I changed 3 things - 

 * BIOS update to the DEC 09 version,
 * Connect the liveCD environment to the internets before running the installer (I just connected to my home wifi)
 * Delete the partitions one by one instead of clicking on "new partition table".

Don't know which of these made the difference (but since it seemed to crash while apt was waking up and installing things, I guess it is most likely to have been the internet connection).

Happy netbooking...

---

