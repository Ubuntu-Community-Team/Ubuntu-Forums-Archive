---
title: "Ubuntu On Fake RAID, I found out it's simple but..."
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by markcynt on 2009-04-11
It's not! ( at least for me it's not) Here's the rundown:

At first I couldn't get Ubuntu to install on fake RAID using the Ubuntu "Fake RAID How To" so I set up a multi-boot with RAID disabled with Vista, openSUSE, and Ubuntu, in that order. That was easy.

So yesterday after being fearful of it for the longest time I decided to try the 9.04 Alternate CD install.

I set up a RAID0 and at first I just installed it by itself and it worked beautifully so then I tried setting up the same triple-boot as before, but when I did that and installed Grub to the MBR I lost the ability to boot into openSUSE. It was gone from the boot menu.

So then I tried a Vista, Ubuntu, openSUSE install, in that order and openSUSE took away the ability to boot into Ubuntu.

There were other options for installing GRUB in the Alternate CD but none of the examples worked. I tried using Lilo since that was an option but that didn't work either.

I am installing on seperate partitions by the way.

I'm sure there is a way to make this work. Any ideas?

Let me add that I'm still fairly new to Linux (about 7 or 8 weeks) , but I'm really liking it.

Thanks

Mark

Edit: I'm also posting this at the openSUSE and PCPitstop forums to get other ideas.

---

### Post by ronparent on 2009-04-11
Some ideas. You might first reconfigure to boot from the ubuntu boot (it seems to be the more flexible of the two). Look first at the meierfra post to the following thread that explains a differences between the suse and ubuntu grubs:  [http://ubuntuforums.org/showthread.php?t=1122335](http://ubuntuforums.org/showthread.php?t=1122335)

I would then suggest you simply edit the ubuntu menu.lst to add the suse install to it. You could get the suse terminolgy by examining the suse menu.lst.

---

### Post by markcynt on 2009-04-11
I found the solution. The solution begins to take shape at post #24.

[http://forums.pcpitstop.com/index.php?showtopic=167533&hl=](http://forums.pcpitstop.com/index.php?showtopic=167533&hl=)

---

