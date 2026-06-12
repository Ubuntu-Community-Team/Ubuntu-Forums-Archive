---
title: "Re-use the stuff downloaded from apt-get"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by Tomás Ó hÉilidhe on 2009-06-26
I want to install Open Office, so I can just do:

```

apt-get install openoffice.org

```

However I need to install it on a few different machines, but my internet connection isn't great so I only want to download Open Office once.

It would be brilliant if I could do something like the following on my main PC:

```

apt-get just-download-the-stuff-needed openoffice.org

```

This would download Open Office for me so that I would be able to copy the installation files to a USB stick for use on other computers. Then I can go to another computer and do:

```

apt-get install-from-stuff-already-downloaded openoffice.org

```

Can this be done? Even if it isn't as easy as I've outlined here, could someone in the know please give me some steps to follow (and be as technical as you like in your explanation).

By the way I realise I can just go download OO from their website and save the installation file to USB, but I want to be able to do this for all apt-get*able* programs.

---

### Post by howefield on 2009-06-26
Use Synaptic to download your .debs and something like

```
sudo dpkg -i package_file.deb
```

to install them on each machine.

The .deb files will download to /var/cache/apt/archive/

---

### Post by mcduck on 2009-06-26
> **Tomás Ó hÉilidhe said:**
> I want to install Open Office, so I can just do:

```

apt-get install openoffice.org

```

However I need to install it on a few different machines, but my internet connection isn't great so I only want to download Open Office once.

It would be brilliant if I could do something like the following on my main PC:

```

apt-get just-download-the-stuff-needed openoffice.org

```

This would download Open Office for me so that I would be able to copy the installation files to a USB stick for use on other computers. Then I can go to another computer and do:

```

apt-get install-from-stuff-already-downloaded openoffice.org

```

Can this be done? Even if it isn't as easy as I've outlined here, could someone in the know please give me some steps to follow (and be as technical as you like in your explanation).

By the way I realise I can just go download OO from their website and save the installation file to USB, but I want to be able to do this for all apt-get*able* programs.

When you install something using apt, the downloaded packages are cached into /var/cache/apt/archives. You can simply copy the .deb packages from there to new machines, and apt will use them instead of redownloading the same packages again. (or you can juts install the .deb packages on other machines with dpkg, if you want).

Also, take a look at [Apt-On-CD]("http://aptoncd.sourceforge.net/")

---

### Post by Tomás Ó hÉilidhe on 2009-06-26
> **mcduck said:**
> When you install something using apt, the downloaded packages are cached into /var/cache/apt/archives. You can simply copy the .deb packages from there to new machines, and apt will use them instead of redownloading the same packages again.

That sounds fantastic, gonna go try it out, thanks a million :D

---

