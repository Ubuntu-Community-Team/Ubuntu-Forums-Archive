---
title: "Quintuple booting with Grub?"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by ultrafez on 2009-03-20
Hi all!

I'm currently quad booting 4 OS's with partition layout as so:

1: Dell Recovery partition
2: Windows Vista
3: Windows XP
4: (unallocated)
5: Extended partition
  6: Ubuntu
  7: (linux-swap)

I would like to install Windows 7 but I have realised that I already have 4 primary partitions - so would anyone know if I can install Windows 7 inside my extended partition and chainload it from there?

Thanks.

---

### Post by meierfra. on 2009-03-20
> I would like to install Windows 7 but I have realised that I already have 4 primary partitions - so would anyone know if I can install Windows 7 inside my extended partition

Yes, you can. Win 7 will take over the Vista boot loader.  So if you choose Vista at the Grub menu, you should get a Win 7 boot menu letting you choose between Win 7 and  Vista.

---

### Post by ultrafez on 2009-03-20
Thanks for your reply. I forgot to mention that I was using Grub for the boot menu, and chainloading the BCD Vista and Win 7 loaders from it. I didn't know if Windows would throw a wobbly from being booted from a logical partition, but I'll give it a go - cheers for your help!

---

### Post by meierfra. on 2009-03-20
> I didn't know if Windows would throw a wobbly from being booted from a logical partition

You can install Windows to a logical partition, as long as you have a primary ntfs or fat partition, where Windows can put the boot files.

> I was using Grub for the boot menu, and chainloading the BCD Vista and Win 7 loaders from it.

Chainloading the Win 7 boot sector will not work, since the Win 7 boot files will be on Vista (or XP) partition. 
But if you want I can show you how to copy the boot files to the Win 7 partition and  how to configure   BCD and Grub, so that you can chainload Win 7 directly from the  Grub menu.

---

### Post by ultrafez on 2009-03-20
Ah I didn't think of that; I would really appreciate it if you would show me how to copy those boot files over... thanks! :D

---

### Post by meierfra. on 2009-03-20
I have  written up similar instruction before, but never with all three: Vista, Win 7 and XP.  So just to be on the cautious side, I like to request some   information:  ([B]Do this after  you installed Win 7)
[/B]

1)  Boot into  Ubuntu and download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. 

2)  Boot into  Win 7.  Go to "Start" and type "cmd". Press "Ctrl+Shift+Enter". This will open  the command line as administrator. Type
```
bcdedit
```

and post the output.

---

### Post by ultrafez on 2009-03-22
OK I shall do that after I've installed Win 7 - I haven't done that yet and I don't intend to do it for about a week or so, so I'll get back to you when I've got it installed :) thanks once again!

---

