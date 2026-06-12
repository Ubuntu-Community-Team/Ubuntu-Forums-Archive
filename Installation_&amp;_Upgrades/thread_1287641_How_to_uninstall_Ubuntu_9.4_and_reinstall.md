---
title: "How to uninstall Ubuntu 9.4 and reinstall"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by yosmir on 2009-10-10
Hi guys,  I have installed Ubuntu 9.4 next to Windows Vista. Somehow the partition which was created during the installation of Ubuntu is too small, and I cannot add or download anything. Can I delete Ubuntu AND the partition and start all over again without creating problems for Windows Vista. If so, how? I have limited computer knowledge. Thanks!

---

### Post by chris_andrew on 2009-10-10
I'd download GParte on a Live-CD and this gives you the option to re-size partitions without destroying them.  It's very good:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Cheers,

Chris.

---

### Post by alexandermdevereux on 2009-10-10
be careful with Gparted it can do strange things with vista. I recommend getting [http://www.easeus.com/product.htm](http://www.easeus.com/product.htm) partition manager to resize the vista partition and then use gparted for the ubuntu partition

---

### Post by raymondh on 2009-10-10
> **yosmir said:**
> Hi guys,  I have installed Ubuntu 9.4 next to Windows Vista. Somehow the partition which was created during the installation of Ubuntu is too small, and I cannot add or download anything. Can I delete Ubuntu AND the partition and start all over again without creating problems for Windows Vista. If so, how? I have limited computer knowledge. Thanks!

Yes you can. There are, however, other options as mentioned above

You can use gparted to delete or resize.  When using gparted, you can access it from the liveCD and in live session (system> admin > partition editor). Or, as I prefer, download a [live gparted CD.]("http://gparted.sourceforge.net/livecd.php")  Gparted ought to unmount the partitions automatically.  To double check, right click on each partition and if given the option to unmount, do so.  For swap, select swap-off.  When using gparted to RESIZE Vista to make space for extending Ubuntu, make sure you uncheck the "round-to-cyclinder" box.

Defrag windows first before taking space from it to give to ubuntu.

If you choose to delete-then-reinstall, I suggest you defrag first windows then use gparted to delete ubuntu.  Also, if you do not have a Vista original install disc (not the  recovery disc provided by the manufacturer), I suggest you download and burn this [recovery CD]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") just in case something borks and you need to recover windows.

As always, back-up files first and foremost.

Safe Ubuntu-ing.

---

### Post by raymondh on 2009-10-10
Another option is to boot into windows to:

- defrag
- resize/shrink using Vista's disk management tool.  That will create an empty/unallocated space between windows and ubuntu
- boot into the ubuntu liveCD to access gparted 
- extend ubuntu to occupy the empty space.  

How to extend Ubuntu will depend on whether you have root inside an extended partition or not.  If so, enlarge the EXTENDED partition first and then enlarge root.

---

### Post by yosmir on 2009-10-10
[FONT=&quot]Hello again,  I feel a bit embarrassed because I have discovered that without knowing it, I had installed Ubuntu on an _external_ disk instead of what I had intened, on the hard drive. That makes it much easier to resolve my problem. 
Thank you all for your quick response and suggestions! [/FONT]

---

### Post by raymondh on 2009-10-10
> **yosmir said:**
> [FONT=&quot]Hello again,  I feel a bit embarrassed because I have discovered that without knowing it, I had installed Ubuntu on an _external_ disk instead of what I had intened, on the hard drive. That makes it much easier to resolve my problem. 
Thank you all for your quick response and suggestions! [/FONT]

:)

safe ubuntu-ing, yosmir.

---

