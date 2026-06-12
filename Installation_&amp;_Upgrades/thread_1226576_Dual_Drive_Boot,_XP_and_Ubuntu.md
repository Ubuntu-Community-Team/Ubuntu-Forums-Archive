---
title: "Dual Drive Boot, XP and Ubuntu"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by DeadlyAura on 2009-07-29
I currently have Ubuntu 9.04 installed on my main hard drive.

Yesterday I formatted and installed Windows XP on a second drive.

When I try to boot from my second drive into XP I get the error:

"Non system disk error, insert system disk and press enter"

If I press enter, it boots Ubuntu fine.

I have been unable to complete my XP install because I cannot boot to the second drive.

Does anyone know what I can do to successfully do a dual-drive boot?

---

### Post by merlinus on 2009-07-29
Are you wanting to use grub to boot both oses?  What is the boot order of the hdds in bios?

---

### Post by DeadlyAura on 2009-07-29
I would ideally like to use GRUB to load the OSes, but that is not my main issue.

Boot priority for drives currently is:

Ubuntu Drive
XP Drive
2 Other storage drives

---

### Post by merlinus on 2009-07-29
> 
When I try to boot from my second drive into XP I get the error:
I assume you are selecting to boot from this hdd by pressing a key on startup?  If so, then perhaps your xp install did not work correctly.

---

### Post by hyperAura on 2009-07-29
is it possible that u specified something wrong as it concerns the drive where windows exist in the grub? maybe a storage drive instead of the windows drive.. if not then as merlinus said perhaps something went wrong with the xp installation..

---

### Post by DeadlyAura on 2009-07-29
Sorry, I should have mentioned that this is not the first time I've attempted this.

I tried doing this same thing a few weeks ago and got the same error. I ended up un-plugging all the drives but the Windows drive, and the error continued.

I reformatted and installed again the other day.

---

### Post by gypsumwolf on 2009-07-29
> **DeadlyAura said:**
> Sorry, I should have mentioned that this is not the first time I've attempted this.

I tried doing this same thing a few weeks ago and got the same error. I ended up un-plugging all the drives but the Windows drive, and the error continued.

I reformatted and installed again the other day.

Is your slave/master jumper in the right place?

---

### Post by DeadlyAura on 2009-07-29
With the jumper in the CS position, this happens.

I swapped it to the Slave position and this same issue happens.

I swapped it to Single/Master and the entire system fails to boot.

---

### Post by DeadlyAura on 2009-07-30
I attempted to reformat and re-install Windows once again on the same drive and received the same error.

```

Drive boot failure, insert system disk

```

I booted up into Ubuntu again and am now copying the contents of a storage drive over to this drive.

When that is complete, I am going to attempt to install XP on what used to be the storage drive to see if it will boot for me.

---

### Post by oldfred on 2009-07-30
Take a look at this site that has instructions on installing windows after Linux.
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)
If you are unplugging hard drives you change the order in Linux and Grub. That will cause the problem of the system not booting since (hd1,0) becomes (hd0,0) and partitions may be different on the different drives.

---

### Post by DeadlyAura on 2009-07-30
My last plan failed just as miserably as the first.

My next step is to use the guide that oldfred posted, and resize my Ubuntu partition and install XP on the same drive and load it all up with GRUB.

---

