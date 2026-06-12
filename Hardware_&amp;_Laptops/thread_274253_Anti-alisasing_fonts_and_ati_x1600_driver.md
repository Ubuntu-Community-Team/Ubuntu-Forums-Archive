---
title: "Anti-alisasing fonts and ati x1600 driver"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by quisoc on 2006-10-09
Hi,
   I installed the latest version of the ati's driver. It's seems ok, i'm working with a resolution of 1280x800, but i can't apply anti-aliasing and fonts look very bad.
   I tried to change some parameters, but in the ati's control panel there aren't no options, and display parameters in system settings are disabled cause it's managed by another aplication.

---

### Post by ltmon on 2006-10-09
Hi,

If you are using KDE (it sounds as if you are) first check out "System Settings -> Appearance -> Fonts".  This has a checkbox for antialiasing, and you can configure subpixel hinting there also.

If that isn't producing results you're happy with then continue on...

I have the x1600, and set up my fonts with a config file in my home directory.  Make the file ```
.fonts.conf
``` in your home directory and copy and paste the following into it:
```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="autohint" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintmedium</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

```
Then restart your desktop environment (log out, log in).

If you aren't happy with the results then search the forum for "fonts".  There are a number of tutorials for setting up fonts to look their best.

L.

---

### Post by quisoc on 2006-10-10
Thanks!!
I reinstalled kubuntu and now I can acces display settings in system settings. I modified my .fonts.conf and added some lines from your code (the first <match>) and changed the <const> of rgba to rgb, and now fonts look fine.
But another question: my screen refresh is only 60 hz? It's ok for a lcd screen or it must to be higher?

> **ltmon said:**
> Hi,

If you are using KDE (it sounds as if you are) first check out "System Settings -> Appearance -> Fonts".  This has a checkbox for antialiasing, and you can configure subpixel hinting there also.

If that isn't producing results you're happy with then continue on...

I have the x1600, and set up my fonts with a config file in my home directory.  Make the file ```
.fonts.conf
``` in your home directory and copy and paste the following into it:
```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="autohint" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintmedium</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

```
Then restart your desktop environment (log out, log in).

If you aren't happy with the results then search the forum for "fonts".  There are a number of tutorials for setting up fonts to look their best.

L.

---

### Post by ltmon on 2006-10-10
My laptop screen is refreshing at 60Hz also.  I'm not sure whether this is the proper rate or not, but it doesn't cause me any problems or eye strain.

L.

---

