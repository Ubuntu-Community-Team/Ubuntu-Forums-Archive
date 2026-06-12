---
title: "Vista Ubuntu Dual Boot Issues."
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by mfiume on 2009-02-12
I know you guys must get tons of these, but can anyone help me get Vista and Ubuntu 8.10 dual booting?

I have Vista booting on the first partition of my second SATA Drive. This is the primary drive.
I have installed Ubuntu on the second partition of my first IDE drive. I made sure Grub installed on this partition and not on (hd0,0)

I want to use Vista's bootloader to prevent me losing my Vista install again.

I've used easyBCD to add Unbuntu to Vista's Bootloader, but when I select it on startup, it gives me an error saying:
> Cannot load from harddisk.
Insert System Disk and press any key.

This leads me to believe it can't find the bootable partition.

I've been reading that Ubuntu Install might have problems with mixed SATA and IDE drive setups, as unix and windows numbers them differently or something. 

Anyone know how to fix this?

---

### Post by caljohnsmith on 2009-02-12
Can you set your BIOS to boot the Ubuntu IDE drive instead of the Vista drive on start up? If you are open to that possibility, it would be easy to add an entry in your Grub's menu.lst to boot Vista from your Ubuntu drive, and your drives would still be independent of each other (Grub would be on the Ubuntu drive, not the Vista drive). But either way you decide, it would help to get a clearer picture of your setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by mfiume on 2009-02-12
Ok, did that (was planning on it eventually :P).

Now I'm getting a Grub Error 22 on load. After a bit of research that seems to mean it can't find the partition Unbuntu is installed on.

Any more ideas? Could it be the device numbering? How can I check that?

---

### Post by mfiume on 2009-02-12
Sorry guys, just one bump and that's it.


Can anyone help me with the above? Am I on the right track thinking it's an difference in drive numbering? Anyone think of anything else?

---

### Post by caljohnsmith on 2009-02-12
How about running the script I linked to from your Live CD and posting the results.

---

