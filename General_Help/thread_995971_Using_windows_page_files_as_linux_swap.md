---
title: "Using windows page files as linux swap"
date: 2008-11-28
forum: General Help
---

### Post by jnw222 on 2008-11-28
is there any way to have windows and linux use the same swap/paging files?

to much of a waste to have a 2 gig windows page file and a 1.5 gig swap

---

### Post by PocketDog on 2008-11-28
No. Windows uses pagefile.sys, Ubuntu uses a dedicated partition. You can change the location of Windows' paging file but not to the swap partition - Windows won't be able to see it.

---

### Post by Seq on 2008-11-28
You can have Linux use a swap file instead of a partition. You can also have Windows (via something like [SwapFS]("http://www.acc.umu.se/~bosse/")) use a swap partition and move your pagefile.sys to it.

I have never done either of these and am not sure what the potential issues would be (I'd definitely do some research before doing this). It would probably screw up hibernate on Windows (I believe it uses the pagefile).

---

### Post by albandy on 2008-11-28
It's possible, but I don't recomend it to you.


Assuming you've mounted your windows partition in /mnt/windows do this:

sudo mkswap /mnt/windows/pagefile.sys
sudo swapon /mnt/windows/pagefile.sys


Make sure to set a fixed size to your pagefile.sys in Windows system properties.

You can do a script in /etc/init.d/

Something like this:

create a file with filename "pagefile" in /etc/init.d/

This file should contain this:

```

#! /bin/bash

case $1 in 

start)
sudo mkswap /mnt/windows/pagefile.sys
sudo swapon /mnt/windows/pagefile.sys

;;

stop)
swapoff /mnt/windows/pagefile.sys
;;
restart)
/etc/init.d/pagefile stop
sleep 1
/etc/init.d/pagefile start

;;

esac


```

Change the file attributes to make it executable:

sudo chmod 755 /etc/init.d/pagefile

and link it to your default runlevel

ln -s /etc/init.d/pagefile /etc/rc2.d/S02pagefile

---

### Post by PocketDog on 2008-11-28
Crikey

---

### Post by jnw222 on 2008-11-28
albandy's method looks best

no downsides right?

---

### Post by Seq on 2008-11-28
> **jnw222 said:**
> albandy's method looks best

no downsides right?

[QUOTE=albandy]It's possible, but I don't recomend it to you.[/QUOTE]

Nobody here will say it will work properly for you. Windows might have a fit if the pagefile is messed up (but it *might* not). Albandy's method just creates a brand-new swap file called pagefile.sys on your windows drive every time Linux boots. Windows would need to do whatever is necessary to fix it as well when it boots (maybe it does anyway)

You would also need to ensure that your windows drive is mounted rw, AND mounted before your 'pagefile' init script runs.

Personally, I'd look at limiting my swap file size according to demand and usage patterns, or buy a larger disk.

---

### Post by jpr82 on 2010-03-24
Well I use my windows xp pagefile in the swap partition via Swapfs. It works fine for windows. The only problem with linux is that it forces file system check sometimes after I ' ve used windows. I think is every time windows  needs to use it's virtual memory (wich is not so often). So it works.
Bye
Good luck

---

