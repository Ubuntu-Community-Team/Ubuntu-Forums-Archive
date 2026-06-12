---
title: "Uninstall Ubuntu from Dual Boot Computer"
date: 2009-02-06
forum: Hardware
---

### Post by jimwinfrey on 2009-02-06
My wife inherited my old laptop with dual boot of WinXP and Ubuntu.  This laptop has two hard drives (60Gig each).  Need to recover the second drive for expanding her Windows data.  Windows partitioner obviously doesn't see the Ubuntu disk.  Any suggestions for getting it back?

Thanks,

Jim

---

### Post by cariboo on 2009-02-06
Use the LiveCD to backup, delete, resize and reformat the hard drive.

Jim

---

### Post by martinbaselier on 2009-02-06
I'm wondering what you're planning. If you want to remove ubuntu completely you would need to rewrite the MBR and put the windows bootloader there, since grub will look for it's config file on the ubuntu drive. I wonder how well windows would handle that. Maybe grub could be redirected to use your ntfs-drive. I don't know about that though. You can easily check this (non-destructive) by entereing grub on the command line. Then 
root (hd
Now press tab for available options, Choose your xp-hdd and then your xp-partition. Use tab to show options again. Then enter quit to quit.

If it is visible and you want to keep using grub (it's rather inefficient though.) You can easily run setup after the root -command. Make sure the boot directory is copied to the xp-partition. 

By the way, there are drivers for windows xp for using a linux drive. See [http://www.howtoforge.com/access-linux-partitions-from-windows]("http://www.howtoforge.com/access-linux-partitions-from-windows"). Haven't read it myself. I just used google to find it.

I know this wasn't your question and cariboo allready gave you the answer you probably will need. I just made me wonder and since I removed windows from my machine completely I can't test it myself.

---

