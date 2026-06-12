---
title: "So I installed ubuntu with /home on its own partition ..."
date: 2008-10-23
forum: General Help
---

### Post by Castlef on 2008-10-23
Hi

when I installed ubuntu I put / on one partition, /home on another... and /swap on another.

I did this beceause I like reinstalling ubuntu rather than using distro upgrade.. and I thought it was a good way to keep user files such as created documents and such from upgrade to upgrade.

My question is how exactly does this work. If i install ubuntu again how will i tell it not to overwrite the home partition but use the one I already have? Is this a common thing to do?

One other question I have.... my processor is a tri core phenom athlon... I was wondering if i compiled my own kernel if there would be a noticeable gain in performance.... but also if i compiled it only as a 32 bit kernel? Because I feel im still not ready for 64 bit as things are still broken with it..... from what I hear.

Also if you do compile your own kernel.... how do you keep everthing from breaking when you use the updater?

---

### Post by ilrudie on 2008-10-23
Its common to have home on a separate partition.  To keep it when the installer asks about partitions just select the partition that you home is on and make sure to chose not to format that partition.  Tell it to reformat the root partition so you start with a clean slate and you should be fine.  As always its a good idea to have a backup of anything you can't stand to lose.

There is no reason to compile your own kernel.  The generic kernel is already compiled with SMP (multi-processor) support.  Any gains you might see would be negated by the hassle.

I run 32-bit on 32-bit hardware and 64-bit on 64-bit hardware.  I haven't had problems.  Flash works, Java works.  Unless there is an application you require which only works under 32-bit use the x86_64 version.

---

### Post by drs305 on 2008-10-23
Here's a screenshot of the current Hardy install process with the settings for saving an existing /home partition. These settings will point to the particular partition and identify it as the /home partition.
Note the "Format the partition" is ***NOT*** checked.

---

### Post by Castlef on 2008-10-24
Ty sounds good. What would you all recommend for a backup system? The only important files really are mostly just pictures.... What is a good way to back those up? an external hard drive?

---

### Post by The Cog on 2008-10-24
I use an external hard drive. I use rsync to do the copy because it only copies the changed files so its really fast. Also I usually install the whole thing to just one partition to begin with, and only reconfigure it to use the other /home partition once I'm sure its not going to completely pooh all over it. A kind of quarantined trial.

---

