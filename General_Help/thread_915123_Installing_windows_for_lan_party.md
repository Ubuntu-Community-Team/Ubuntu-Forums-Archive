---
title: "Installing windows for lan party"
date: 2008-09-09
forum: General Help
---

### Post by Morph-------------- on 2008-09-09
Hey all
I've a lan party soon and I want to install windows xp so I can play my games decently, but I was wondering how much this will **** up my current ubuntu installation. I'll just free up some space and make another partition to install windows on. So I guess it will at least set it's own partition to bootable so that I don't see my GRUB anymore, this can easily be changed by setting my partition with grub on it back to bootable?
Are there any other issues I should look at?

Thanks in advance

---

### Post by whitethorn on 2008-09-09
If I remember correctly, when you install Windows it'll rewrite it's MBR, so grub won't be on ur pc nemore.  You can just reinstall grub and it should find the Windows intallation, and give you an option to boot windows.  If after you reinstall grub and windows isn't there.  You can manually add it to your /boot/grub/menu.list

---

### Post by lswest on 2008-09-09
you can restore GRUB using this blogpost [http://lswest-ubuntu.blogspot.com/2008/06/installing-bootloader-how-to.html](http://lswest-ubuntu.blogspot.com/2008/06/installing-bootloader-how-to.html) (I realize the vanity of posting one of my own blog posts, but I reference another good thread from the forums here).

Gist of it is:
> For GRUB restore to MBR:
boot to the LiveCD (this is the easiest way IMHO) and then start a terminal (applications-->accessories-->terminal)and type:

    ```
sudo grub
    find /boot/grub/stage1
    root (hd?,?)
    setup (hd?)
    quit
```


where the (hd?,?) and (hd?) corresponds to the output of find /boot/grub/stage1 (first time round the (hd?,?) stands for the drive (hd?) and the partition (,?) at which Ubuntu (or any Linux) is located, and then the second time round (hd?) just stands for the drive, for the MBR).
If you would like a more detailed explanation catlett did a good job with his how-to here and also offers troubleshooting ideas.

---

### Post by Morph-------------- on 2008-09-09
Thanks all i'll try those!

---

