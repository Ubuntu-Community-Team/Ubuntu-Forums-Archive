---
title: "PreInstall Questions"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by fairyliquidizer on 2005-12-23
Hi! :KS 

I'm considering installing Ubuntu.  At the moment my disk space is all allocated as NTFS and I want to keep my Windoze install for gaming.  

Does the install process for Ubuntu have a decent disk partioner like DiskDrake on Mandrake/Mandriva?

Also, I have an nForce 3 motherboard does this distro include support for the nVidia NIC and nVidia video cards?

Thanks,
Fairy

---

### Post by DevilsAdvocate on 2005-12-23
To not answer your question, I don't know if the installer can resize NTFS partitions which is what would be required.  I doubt it though.  I suggest using partition magic or using a FOSS alternative from the LiveCD or Knoppix.  

If nothing else, hopefully my response will bump your thread back up again so someone who knows may see it.

---

### Post by aamukahvi on 2005-12-23
I just installed dapper aside a Win XP install. All I did was pop in the install CD and tell the Dapper installer to resize the windows partition. It then asked me how much space to use and proceeded to install.

I don't think it lets you choose the file system to use when using the auto resize, however. Defaults to Ext3.

---

### Post by az on 2005-12-23
[QUOTE=fairyliquidizer]Hi! :KS 

I'm considering installing Ubuntu.  At the moment my disk space is all allocated as NTFS and I want to keep my Windoze install for gaming.  [/QUOTE]

Most people do that.

[QUOTE=fairyliquidizer]
Does the install process for Ubuntu have a decent disk partioner like DiskDrake on Mandrake/Mandriva?[/QUOTE]

Well all of the above use parted and the associated libraries, and so does the Ubuntu installer.  The interface is curses (text) but it is very straghtforward.  The default behaviour is to see that you already have an os installed and offer to shrink that partition.  All you have to do is enter the saze you want and you are good to go.

Yes, it can safely resize ntfs.  You can also do the partitioning by hand and select alternate filesystems, if you want to.


[QUOTE=fairyliquidizer]
Also, I have an nForce 3 motherboard does this distro include support for the nVidia NIC and nVidia video cards?[/QUOTE]

Yes.

---

### Post by az on 2005-12-23
[QUOTE=DevilsAdvocate]To not answer your question, I don't know if the installer can resize NTFS partitions  ...
...

  I suggest using partition magic [/QUOTE]

Yes, it can resize ntfs.  Partition Magic is not recommended for linux filesystems.

---

### Post by fairyliquidizer on 2005-12-23
Thanks for all the help, especially to Azz.  Excuse my Noobness :-) Believe it or not I used to be an HP-UX programmer for HP but it's all a long time ago now and I am but a child about to risk a stable XP install out of curiosity :)

---

### Post by fairyliquidizer on 2005-12-23
Well it's installed and running.  Now to get it setup to automount my NTFS data disk...

---

