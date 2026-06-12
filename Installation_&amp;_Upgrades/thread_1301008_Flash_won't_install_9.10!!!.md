---
title: "Flash won't install 9.10?!?!?!"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by boboman911 on 2009-10-25
When I manually install from adobe, it says, 

"Error: Dependency is not satisfiable: libnspr4-dev"

PLEASE HELP!!!

Thanks

Tony

---

### Post by johnzollo on 2009-10-25
Ok, forgive me ignorance -- I'm new to this.  Did you try installing the .deb from Adobe or the tar.gz?  Also, are you using the 32 bit or 64 bit version of Karmic?

-John

---

### Post by fancypiper on 2009-10-25
Personally, I would (and did) use the Adobe Flash Player plugin installer.

sudo apt-get install flashplugin-installer

Or, use Synaptic to install it.

---

### Post by coldReactive on 2009-10-25
> **fancypiper said:**
> Personally, I would (and did) use the Adobe Flash Player plugin installer.

sudo apt-get install flashplugin-installer

flashplugin-nonfree should include that.

---

### Post by Penguin Guy on 2009-10-25
[[SIZE="2"]Click here to install it.[/SIZE]]("apt:flashplugin-nonfree")
If that doesn't work, run [COLOR="Green"]sudo apt-get install flashplugin-nonfree[/COLOR].

---

### Post by m4tic on 2009-10-25
Go to synaptic and reload or just use Gnash, its better than adobe

---

### Post by coldReactive on 2009-10-25
> **Penguin Guy said:**
> [[SIZE="2"]Click here to install it.[/SIZE]]("apt:flashplugin-nonfree")

Firefox shouldn't have apt: handler by default if I'm mistaken (at least not in Jaunty.)

---

### Post by johnzollo on 2009-10-26
Where did he go?

---

### Post by bsntech on 2009-10-26
Random question -

is the flashplugin-nonfree and the deb on Adobe's website the same thing or different?

I installed the deb file directly from Adobe's website but I had always used the flashplugin-nonfree before.

---

### Post by coldReactive on 2009-10-26
> **bsntech said:**
> Random question -

is the flashplugin-nonfree and the deb on Adobe's website the same thing or different?

I installed the deb file directly from Adobe's website but I had always used the flashplugin-nonfree before.

flashplugin-nonfree is a metapackage that contains the flashplugin installer, ia32-libs, and all the deps that flash needs.

Before you install it though, MAKE SURE that swfdec and gnash are NOT on your system.

---

### Post by JeffP13 on 2009-10-31
> **boboman911 said:**
> When I manually install from adobe, it says, 

"Error: Dependency is not satisfiable: libnspr4-dev"

PLEASE HELP!!!

Thanks

Tony

I had the same problem at first. Try going to the update manager and see if there are a few updates for Firefox that can be installed. I did this and after restarting firefox it installed just fine.

Twitter- JeffP13

---

