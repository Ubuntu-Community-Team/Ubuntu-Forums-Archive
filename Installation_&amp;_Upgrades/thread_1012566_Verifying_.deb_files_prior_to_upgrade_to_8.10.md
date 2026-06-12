---
title: "Verifying .deb files prior to upgrade to 8.10"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by oygle on 2008-12-16
I have Hardy on a computer that only has dialup. All updates are applied, as at today.

I wanted to upgrade to 8.10, however it would take days with the dialup connection. Here is the plan ..

1. Set the 8.04 to upgrade to 8.10 . It will go and get a heap of info about Intrepid, and show me all the (many) updates to do.

2.  I press 'cancel'. and exit Synaptic.

3.  Then go to package manager, it should show all the same updates, that are need to go to 8.10

4. I use the option to generate a script. This will contain all the .deb files to download, in a shell/bash script file, with all the 'wget' commands. Everything in the script to get all the necessary files.

5. I transfer the script to a computer that has a wireless connection, a lot faster than dialup. It is Win XP (yuk), but will be able to run the script as a .bat file, and as long as I have 'wget' on the XP box, all the files should download okay.

Now, if the above sounds okay, my only concern is to verify those .deb files that have been d/loaded by XP.

Can I just run MD5 checksum or similar on all the files, and then check them against some other file/s that will have the MD5 checksum for each file.

I want to be sure the files downloaded by XP are (a) Virus free (can run Comodo on them, and (b) Are an exact copy of the .deb files downloaded from the Ubuntu site.

Then, .... I can transfer all the .deb files to 'apt cache' , and let the computer upgrade to 8.10, I'm 99% sure it will look in the cache first, so _should_ be no need to go out to the internet for the upgrade to 8.10

Oygle

---

### Post by Partyboi2 on 2008-12-16
If you have slow internet you can download the alternate cd from a faster connection and upgrade.
[http://releases.ubuntu.com/intrepid/](http://releases.ubuntu.com/intrepid/)

---

### Post by oygle on 2008-12-16
I already have the 8.10 CD, but that will not provide me with a complete and up to date 8.10.

---

### Post by Partyboi2 on 2008-12-16
After you have upgraded to intrepid you can get all the updates by a few different methods. One way is to use [[COLOR=Blue]"Generate package download script"[/COLOR]]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript") as you have mentioned, or you could use [[COLOR=Blue]keryx .[/COLOR]]("http://keryx.betaserver.org/") I am not sure if gathering all the packages before the upgrade would work.

---

### Post by oygle on 2008-12-16
> **Partyboi2 said:**
> After you have upgraded to intrepid you can get all the updates by a few different methods.

The last time I tried to upgrade from the CD, it wanted to create a new partition, or 'clobber' the current one, so I cancelled it. That was a while ago, can't remember all the details, possibly I tried 'installing' from the CD, instead of adding the CD in as a 'source', and then upgrade. Does doing the upgrade that way, look at the CD first ?

> **Partyboi2 said:**
> 
One way is to use [[COLOR=Blue]"Generate package download script"[/COLOR]]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript") as you have mentioned, or you could use [[COLOR=Blue]keryx .[/COLOR]]("http://keryx.betaserver.org/")


Okay thanks. I looked at keryx a while back, and it was still in alpha I think (bit risky for me).

> **Partyboi2 said:**
> 
I am not sure if gathering all the packages before the upgrade would work.

I was thinking of setting the Synaptic config to 'look for the latest' (rather than LTS), and then let it go and get all the new package info, and then cancel it, then go into package manager, and generate the download script.

I don't know if it would work either.  :)

---

### Post by Partyboi2 on 2008-12-16
> Okay thanks. I looked at keryx a while back, and it was still in alpha I think (bit risky for me). Fair enough, from what I have been told the beta should be released sometime in the near furture. Could be something useful to keep an eye on.

To upgrade you need to use the alternate cd and stick it in the cdrom drive and a window should open with the option to upgrade. If a windows does not open you can press Alt+F2 and in the box enter
```
gksu "sh /cdrom/cdromupgrade"
```

---

### Post by oygle on 2008-12-16
So, the [alternate CD]("http://releases.ubuntu.com/intrepid/ubuntu-8.10-alternate-i386.iso") will be able to upgrade from 8.01 to 8.10.

Of course, there will be updates to then apply, since the 28th oct I assume.

---

### Post by Partyboi2 on 2008-12-16
> **oygle said:**
> So, the [alternate CD]("http://releases.ubuntu.com/intrepid/ubuntu-8.10-alternate-i386.iso") will be able to upgrade from 8.01 to 8.10.

Of course, there will be updates to then apply, since the 28th oct I assume.
Correct.

---

### Post by oygle on 2008-12-16
Would I have to have the 8.01 computer fully 'updated' prior to using the 8.10 alternate CD ?

Just that there is a 64 bit Ubuntu with 8.04, about nearly 3 months behind in updates, and I'd like to get that to 8.10 also

Thanks,

Oygle

---

### Post by Partyboi2 on 2008-12-16
Yes you will need to have your 8.04 up to date. Use the generate package download script and a ubuntu live cd to update  them.

---

