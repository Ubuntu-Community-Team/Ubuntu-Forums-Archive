---
title: "Ubuntu splash.rle"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by moonoo on 2009-02-22
HI all, 

Not sure if I am in the right forum but if I am not could some please direct me to right place!

For giggles and laughs (and just because) I am 'remixing' Ubuntu for my own needs, and following the excellent write found here:
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch").

I have taken the commands, manipulated them to run as some scripts but I hit a problem I creating the splash screen.

The article make reference to ```
^Xsplash.rle
``` being at the start of the isolinux.txt. My script creates the isolinux.txt but I cant seem to get the splash screen to work :(

I think(?) it is because the ^X is suppose to be a control character not just a '^' followed by a 'X', but I am not sure...

The isolinux.txt file is created by ehco'ing the contents to the isolinux.txt file.

```
echo "
^Xsplash.rle
This is an Ubuntu Remix Live CD.

For the default live system, enter "live".  
To verify the CD for errors, enter "check".  
To run memtest86+, enter "memtest"
" > image/isolinux/isolinux.txt
```

So my question is:
Is the '^X' part of the isolinux.txt file just that or is it some hidden character control?
How would I replicate this in a simple echo?

According to the instructions in the article the characters are : control + V and then control + X which for when trying to recreate this in 'editor' does nothing then exits...

Hope someone can help!

---

### Post by moonoo on 2009-02-22
Ah!

Sorted it.

Open a terminal:

Type 'echo' then press control V then X then type '>a.txt'

This pipes out the 'control character' to a text file.

My splash screen now works and I have the scripts I need to create a new Live CD whenever needed :p

---

