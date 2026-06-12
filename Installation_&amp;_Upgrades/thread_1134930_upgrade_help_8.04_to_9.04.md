---
title: "upgrade help? 8.04 to 9.04"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by ghostofzuul on 2009-04-24
hello... 

i downloaded and burned the iso image succesfully to disc... i know it works b/c if i try and use it as a boot disc it works and i can either live disc or install... i want to do neither... instead i just want to upgrade... both instructions i found said if you're using the disc to use this command

kdesudo /media/cdrom/cdromupgrade

it's not working... 

i get the error msg "command not found!"


if i click on the disc directly on the desktop it takes me to synaptic package manager and then does nothing?

thanks in advance for your help!!

---

### Post by pmlxuser on 2009-04-24
hey you should have downloaded the alternate-cd 

[http://releases.ubuntu.com/releases/9.04/ubuntu-9.04-alternate-i386.iso](http://releases.ubuntu.com/releases/9.04/ubuntu-9.04-alternate-i386.iso)

its easier to upgrade from an alternate -cd than a normal cd which is easier to use when doing a clean install..

---

### Post by ghostofzuul on 2009-04-24
> **pmlxuser said:**
> hey you should have downloaded the alternate-cd 

[link]http://releases.ubuntu.com/releases/9.04/ubuntu-9.04-alternate-i386.iso[/link]

its easier to upgrade from an alternate -cd than a normal cd which is easier to use when doing a clean install..

thanks for the tip!!

:)

---

### Post by Sef on 2009-04-24
>  its easier to upgrade from an alternate -cd than a normal cd which is easier to use when doing a clean install..

The only thing that would be difficult with the alternate cd is manual partitioning, if you need to do it.  It is not hard to manually partition, but the first time takes patience.

---

### Post by Teatro on 2009-04-24
> **Sef said:**
> The only thing that would be difficult with the alternate cd is manual partitioning, if you need to do it.  It is not hard to manually partition, but the first time takes patience.

can you tell me what file system should be used for the 9.04 partition?

---

### Post by Sef on 2009-04-24
> can you tell me what file system should be used for the 9.04 partition? 	

Use ext3, which is the default.

---

### Post by ghostofzuul on 2009-04-24
so getting the alt disc was the key! upgrade successful! all i did was follow the prompts and although it took a really long time (not sure of the elapsed time b/c i went to bed and woke up and finished the install) it seems to have upgraded with no errors and i'm using it now. it even upgraded my minefield which i have admittedly haphazardly installed... not only that... now the true type fonts work on minefield whereas before they did not!!

the only question i have is about the network stuff.... obviously i'm on my network b/c i can connect to the internet and from my mac i can see the ubuntu box and log into it. however the network icon on my menu bar has an "x" in a red box on it... anyone know why that is? 

thanks!

---

### Post by emshains on 2009-04-27
> **Sef said:**
> Use ext3, which is the default.

Why shouldn't he use ext4 which is like one of the major upgrades found in 9.04. It's faster, it's stable, what more could you want ? Ext4 is the future, unless sun opens up its own filesystems.

---

