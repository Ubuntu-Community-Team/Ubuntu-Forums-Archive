---
title: "how to install Wine"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by muryali on 2009-03-17
Hi all,
     problem solved now. after posting the problem i have checked it and now it's ok.

Many thanks,

Regards

---

### Post by Partyboi2 on 2009-03-17
wine is in the ubuntu repositories, you can open Add/Remove (Applications>Add/Remove) and search for it and install or you can open a terminal (Applications>Accessories>Terminal) and install with
```
sudo apt-get install wine 
```

---

### Post by upchucky on 2009-03-17
I don't think you need to use the gziped version, pretty sure ubuntu repositories has everything you need and this will set it up automatically.

```
sudo apt-get install wine
```

---

### Post by muryali on 2009-03-17
Hi,
   I want to connect my [COLOR="Blue"]windows based laptop to ubuntu based desktop computer[/COLOR] through ethernet

Many thanks,

Regards[/QUOTE]

---

### Post by dunkar70 on 2009-03-17
The Ubuntu repositories does have an old version of Wine available. To get the latest stable version, execute the following commands to install Wine from the development site:
> wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list](http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/winehq.list
sudo apt-get install wine cabextract msttcorefonts
In short, these commands will:
1. Install the authentication key for the new source
2. Install a file containing the new source location
3. Install the newest version of Wine along with the Microsoft fonts and a utility for extracting files from CAB files.

---

### Post by dunkar70 on 2009-03-17
> **muryali said:**
> Hi,
   I want to connect my [COLOR="Blue"]windows based laptop to ubuntu based desktop computer[/COLOR] through ethernet

Many thanks,

Regards[/QUOTE]
Muryali,

You should move your request to the appropriate thread. This thead is about Wine, not networking. When you move this to the correct thread, you should add more details about what you want to do, such as:

Connect a Windows XP Professional laptop to an Ubuntu 8.04 Desktop via Ethernet to:
1. share files
2. share printer
3. view web content
4. remotely manage the Ubuntu desktop
...

---

### Post by muryali on 2009-03-17
Thank you i am doing so

Connect a Windows XP Professional laptop to an Ubuntu 8.04 Desktop via Ethernet to:
1. share files
2. share printer
3. view web content
4. remotely manage the Ubuntu desktop
...[/QUOTE]

---

