---
title: "Disk Space and package uninstall"
date: 2008-08-02
forum: General Help
---

### Post by Cyber Akuma on 2008-08-02
Ok, I was installing several apps from the Synaptic Package Manager when the installs started to fail because of what I assume meant I ran out of space.

Ok, so, first of all, how do I check how much space I have left on my linux partition? Ubuntu just seems to treat the filespace as every storage device put together and only allows me to look into my home folder.

Second, how can I view what packages I have installed and choose which ones I want to uninstall?

Third, is there any way I can clean up the packages that were only part-way installed then failed because of lack of disk space?

I am surprised, I thought Ubuntu would warn me when I am about to install something but don't have the space for it.

---

### Post by Diabolis on 2008-08-02
For all this you can use synaptic

For a quick clean up, just:
```
sudo apt-get autoclean
sudo apt-get autoremove
```

---

### Post by Cyber Akuma on 2008-08-02
How do I use synaptic for this? I looked around but didn't see the option.

And tha tautoremove option said something about unmet dependencies and to use -f install

---

### Post by Diabolis on 2008-08-03
I don't think that synaptic has a "button" for all the command line options, as probably most of this things are handle internally.

Then try what the error message said.
```
sudo apt-get install -f
```

---

### Post by zvacet on 2008-08-03
To see how much free space do you have 

```
df -h
```

---

### Post by pbpersson on 2008-08-03
I was going to type "in Synaptic you can do these things" but I had better open the application first so I know what I am talking about.  ;)

Okay, I opened Synaptic and by default when you first open it, all applications are displayed.  CLicking on the very first column header sorts the packages so the ones you have installed are listed first, designated by the solid green checkbox.

I have 1839 packages installed on this machine.  :o  Well, they are all free and I have lots of disk space.  ;)

Anyway, you can highlight as many packages as you wish and then right-click and say "remove completely" to get your disk space back.

If you have any packages that are only half installed, they would be considered "broken packages" which you can fix by going to Edit-->Fix Broken Packages......which is highlighted on my machine so I think I have some.....no, on the bottom in the status bar it says 0 broken.....hmm...

I guess you can always click on that - it says "Successfully fixed dependency problems" although I didn't have any.  :confused:

---

### Post by rEbyTer on 2008-08-03
This would save several tenths of megabytes. Install the **localepurge** package and select the locales you use. Then run **localepurge** as root. localepurge will also run automatically after each **apt** run, cleaning unused localization data.

Install it with:
```
$ sudo apt-get install localepurge
```

---

### Post by Diabolis on 2008-08-03
> **pbpersson said:**
> 
Anyway, you can highlight as many packages as you wish and then right-click and say "remove completely" to get your disk space back.


Yeah that surely will work, but it will also uninstall his applications :-S

autoclean, will remove cached packages.

---

### Post by cariboo on 2008-08-03
You can also look at the history file in Synaptic to see what packages you have installed. There are some things that you have to use a terminal for that are a lot quicker and in most cases more concise than gui apps.

```
df -h
```

Will give a listing of your hard drive usage.

```
du -h
```

Will give disk usage in a human readable form

```
sudo apt-get clean
```

Will remove archived packages that you have installed.

Also check the contents of trash in your home directory and /root directory. to check /root/local/.Trash in a terminal enter:

```
sudo -i
```

When in /root enter:

```
du -h
```

to see if there any large files in that directory.

Jim

---

