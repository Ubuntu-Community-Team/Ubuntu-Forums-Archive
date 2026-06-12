---
title: "[SOLVED] Synaptic error"
date: 2008-11-24
forum: General Help
---

### Post by mynydd on 2008-11-24
["http://ubuntuforums.org/showthread.php?p=6240993#post6240993"]("http://ubuntuforums.org/showthread.php?p=6240993#post6240993")

Hi, I am running 8.10. I clicked on a link in the above thread.Now synaptic and 'add / remove' programs won't work.
I get the following error message :

[COLOR="DarkOrange"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report[/COLOR]

I do not know how to fix it, please help.:)

---

### Post by Bucky Ball on 2008-11-24
Do just that. Open a terminal and type in

```
sudo [COLOR=DarkOrange]dpkg --configure -a[/COLOR]
```Something is not finished downloading (interupted or some other problem) and that command will finish downloading all unfinished packages. :)

You can also fix broken packages in Synaptics by Edit->Fix Broken Packages. 

Let us know how you go.

---

### Post by mynydd on 2008-11-24
> **Bucky Ball said:**
> Do just that. Open a terminal and type in

```
sudo [COLOR=DarkOrange]dpkg --configure -a[/COLOR]
```Something is not finished downloading (interupted or some other problem) and that command will finish downloading all unfinished packages. :)

You can also fix broken packages in Synaptics by Edit->Fix Broken Packages. 

Let us know how you go.

Yep spot on synaptic now working.
As I had clicked on a link, I was worried about typing in the terminal incase I made anything worse.
I have only just binned 'vista' a week ago. And learning all the time.
But that was fantastic. Here I am in Wales then a hero in Australia saves my bacon in just one minute.
1 thanks to you:)

---

### Post by Bucky Ball on 2008-11-24
You are most welcome, mynydd, and welcome to the forums. :)

---

