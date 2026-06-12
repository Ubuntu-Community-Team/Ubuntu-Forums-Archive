---
title: "firefox 2 in intrepid"
date: 2008-11-07
forum: General Help
---

### Post by kboy on 2008-11-07
Hi,
I've recently installed Ubuntu 8.10, it comes with firefox 3 which I love, but I also need firefox 2 for some greasemonkey scripts that don't work on firefox 3.

I downloaded the tar.gz firefox 2 file from the mozille site, but I have no idea how to install it without erasing firefox 3 (if it's even possible).

In short I need help in installing firefox 2 on ubuntu 8.10 while maintaining my firefox 3 for usual web surfing.

Thanks,

---

### Post by sonicb00m on 2008-11-07
i think you can extract the tar and place the files in /opt/ and then run it from that location. It will probably use your firefox 3 profile though.

---

### Post by beno1990 on 2008-11-07
Scroll to the bottom to download this:

[http://packages.ubuntu.com/gutsy/web/firefox]("http://packages.ubuntu.com/gutsy/web/firefox")

Then open a terminal and navigate to the folder you put it in, and then:

```
sudo dpkg -i <filename>
```

(<filename> is the name of the .deb file you download, don't include the <> braces)

This is the old gutsy Firefox 2 package, but it should install if you use dpkg, and should leave your Firefox 3 install untouched.

---

### Post by kboy on 2008-11-07
> **beno1990 said:**
> Scroll to the bottom to download this:

[http://packages.ubuntu.com/gutsy/web/firefox]("http://packages.ubuntu.com/gutsy/web/firefox")

Then open a terminal and navigate to the folder you put it in, and then:

```
sudo dpkg -i <filename>
```

(<filename> is the name of the .deb file you download, don't include the <> braces)

This is the old gutsy Firefox 2 package, but it should install if you use dpkg, and should leave your Firefox 3 install untouched.

It doesn't work, when i try to install the package it conflicts with the older version of firefox. It gives me an error and exits....

---

### Post by Xgen on 2008-11-07
I have no problem running both Firefox 2 & 3 together and occasionally  updating them from the Firefox site (mostly  the development version). In Nautilus I just right click on the tar file, extract the  firefox folder, rename it (firefox-2 or 3)  and place it in a common folder (BROWSERS) where I keep the other browser versions. Create a launcher pointing to that folder's executable. You can run the browser versions using a common profile, or separate ones with -P added to the launcher command line and the name of the profile that you created with the -P switch. You can even run separate versions at the same time if you add -no-remote to the command line. Lots of options...

---

