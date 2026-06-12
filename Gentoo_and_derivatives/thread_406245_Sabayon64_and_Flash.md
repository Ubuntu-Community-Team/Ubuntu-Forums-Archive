---
title: "Sabayon64 and Flash"
date: 2007-04-10
forum: Gentoo and derivatives
---

### Post by spinflick on 2007-04-10
Hello, as some of you know (hiya Mips) ;) I installed Sabayon 64 onto my pc a couple of days ago, but cannot get flash to work. Here is what I have done so far.....

emerge -av netscape-flash
emerge -av nsplugin
emerge -av jre

As you can see there is no ebuild for nsplugin and I dont know how to config the files, the emerge --help configure was useless or maybe it's just me.

---

### Post by igknighted on 2007-04-10
> **spinflick said:**
> Hello, as some of you know (hiya Mips) ;) I installed Sabayon 64 onto my pc a couple of days ago, but cannot get flash to work. Here is what I have done so far.....

emerge -av netscape-flash
emerge -av nsplugin
emerge -av jre

As you can see there is no ebuild for nsplugin and I dont know how to config the files, the emerge --help configure was useless or maybe it's just me.

You can try searching in Kuroo, perhaps he had the package name wrong.  I thought it was ndispluginwrapper myself, but I've never used it so i can't tell you what to do with it.

---

### Post by spinflick on 2007-04-10
The ndiswrapper is installed, and netscape-flash?

---

### Post by mips on 2007-04-11
> **igknighted said:**
> You can try searching in Kuroo, perhaps he had the package name wrong.  I thought it was ndispluginwrapper myself, but I've never used it so i can't tell you what to do with it.

A thanks.

It is actually called **nspluginwrapper** (not to be confused with the wireless ndis ones).
[http://gentoo-portage.com/net-www/nspluginwrapper](http://gentoo-portage.com/net-www/nspluginwrapper)

If you can't find something then just do a **emerge -s nsplug** and it will list all packages starting with **nsplug***.  Sometimes mere morrtals like me make mistakes but if you seach you can find what we mean :)


But before you start that do the following to ensure you are up to date with portage & sabayon overlay (It's a good idea to do the first two steps often, the third might not be required if it is up to date):

```
layman -S
emerge --sync
emerge -v portage
```



The mini edition does NOT come with kernel sources. I would advise you to install them, it's not always required but I have needed them. Beware though as it takes LONG, so start it and go have a cup of tea.

```
/scripts/emerge-kernel.sh
```



Now do:

```
emerge -av netscape-flash
emerge -av nspluginwrapper
emerge -av jre
```


Sometimes after you have used emerge you are told that some config files need updating. To do this run:

```
etc-update
```

Select the config file to update by selecting its number. If I did not manually mess with the config file I simply select the option to overwrite the config file. Carry on with the next config file.

---

### Post by spinflick on 2007-04-11
Yippeeeee! it works, thank you Mips. From now on you shall be known as "The Amazing Mips" thanks again :)

---

### Post by mips on 2007-04-11
Glad to hear it's working.

Just one last thing, in Konqueror remember to go to the configuration and rescan for plugins under the plugins section.

---

### Post by spinflick on 2007-04-11
Thanks Mips just done it.  :)

---

### Post by LookTJ on 2007-04-12
[LEFT]try this

```
emerge net-www/netscape-flash
```
[/LEFT]

---

