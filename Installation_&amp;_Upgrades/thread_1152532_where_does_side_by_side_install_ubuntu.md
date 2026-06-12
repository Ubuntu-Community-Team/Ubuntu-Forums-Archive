---
title: "where does side by side install ubuntu?"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by irishbreakfast on 2009-05-07
It is not clear to me what will happen if I choose "side by side"? On what partition will 9.04 be put? And what will happen to my current 8.04?

Cheers

---

### Post by HyRax on 2009-05-07
Is this during installation? It means that it will shrink whatever is already installed to make space for Ubuntu and will install it "side by side" on the same physical drive as the existing operating system.

ie: if you had one hard-drive with one partition on it containing Windows, then that partition would be shrunk down and a second partition created on that drive to put Ubuntu on, thus one drive, two partitions - installed "side by side".

---

### Post by irishbreakfast on 2009-05-08
Thanks, that helps. And I could have been provided more info...

In my case, I have Vista and 8.04 in separate partitions. So if I choose 'side by side" during 9.04 install, what happens? It seems sensible that it would install side-by-side in the partition where 8.04 is installed, and change the grub menu for the 3 operating systems. Is that right?

If so, then I presume I have the choice to protect some directories, like /home and /opt?

Thanks

---

### Post by HyRax on 2009-05-08
That's correct.

Ubuntu will only ever make use of the partitions it is told to use and what it is told to mount them as, unlike Windows which simply allocates drive letters in the order it sees all the partitions.

So for arguments sake, if you had 10 partitions comprising of 3 windows installs, 3 Linux root filesystems, three /home partitions and one Linux swap partition, then Ubuntu could be made to only use the second root filesystem partition and the third /home partition plus the swap partition and totally ignore the rest, or mount them with alternate names such as /fred /lucy and /bob so the system never makes practical use of them.

In the case of Ubuntu 9.04, if Windows is detected, it now automatically creates a mountpoint called /windows to allow you to access the Windows drive from Ubuntu without any further effort (though personally I build people's systems with /media/windows instead so that it automatically appears as a drive icon on the desktop).

The possibilities are endless.

---

### Post by irishbreakfast on 2009-05-08
Thank you for clarifying all that. It has helped and I will start the install soon.
cheers

---

### Post by demon36 on 2009-08-31
Hi 
I just want to know the difference between side by side installation and wubi or lubi installation

And If I chose side by side installation on any partition .. Is there a possability to lose dat on it

thnx

---

### Post by HyRax on 2009-08-31
A side by side install has the Windows and Ubuntu operating systems natively installed to their own partitions on the hard-drive, completely independent of each other.

Think of it like a bookshelf with your Windows-related books on one shelf and all your Ubuntu related books on another shelf. They are both independent on their own shelves, but those shelves are part of the one physical bookshelf.

A Wubi installation installs Ubuntu in a big virtual hard-drive that is simply a big file within Windows. As far as Windows is concerned, Ubuntu is simply another application. This allows you to install Ubuntu and run it "natively" without the need to repartition your drive to make space for a native install.

In our bookshelf example, it's one shelf full of Windows books and one Ubuntu book inserted which you can remove and put back whenever you want without upsetting the rest of the shelf.

---

### Post by demon36 on 2009-08-31
Many thanx dude
I appreciate that

---

### Post by sivadgiarc on 2010-08-12
I think the biggest confusion comes from the fact that the "side by side" option is the only one that says it will let you choose which OS to boot into.

Maybe a note for clarification on the setup verbiage.

---

