---
title: "Font clarity issue"
date: 2009-03-07
forum: Hardware
---

### Post by frankwakeman on 2009-03-07
I have Mint on my laptop with a screen resolution of 1280 x 800, and Ubuntu on my pc, with a resolution of 1024 x 768 on its old 15 inch TFT monitor. I've never been completely happy with how the screen fonts look, whether in the panel or e.g. in Firefox and OpenOffice. Recently I read a post somewhere suggesting some sudo trick to optimise fonts' appearance (I remember the word config being in there), but I've lost the details, and maybe it wasn't relevant. I didn't get round to trying it out to find out.

I think most versions of Linux I've tried have had initial settings of 'Best Appearance', 'greyscale', and 'full' hinting. I usually change it to 'LCD', 'Subpixel smoothing' and 'slight', but that suits the roman-type fonts I use with Writer more than anything - everything still looks a bit smudgy. When I run Vista everything is fine, so I know the machines are up to clear font display. The initial font settings I described suit the 'sans'-type fonts, but they don't display Garamond or Times New Roman, etc, that well. 96 dpi is the norm, though Fedora had 98 dpi. I've tried both.

Any tips? And which settings are people here using?

I ran through quite a few live CDs yesterday to check the problem was the same with them and it is - older Ubuntus, Xubuntu 6, 7 and 8, OpenSolaris.  It's aggravating my eyesight a bit and I may have to head back to Vista....

Much thanks.

---

### Post by ddrichardson on 2009-03-08
This might not be right for Ubuntu as I've never done it but on my Arch based systems I use:
[http://wiki.archlinux.org/index.php/Fonts#Fonts_with_LCD_filter_enabled](http://wiki.archlinux.org/index.php/Fonts#Fonts_with_LCD_filter_enabled)

You'd need to build the packages from source because Ubuntu hasn't got AUR but the difference is unbelievable - shot taken from my Aspire One @ 1280x600.

---

### Post by Chibone on 2009-03-08
I actually like "smudgy" (read: Mac OS X) style fonts as I find them quite more readable than the defaults.

You might have some luck adding items in your fonts.conf file (open your home folder and check "show hidden files" in the View menu to reveal it.)

Here's mine for reference:

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
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>false</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintnone</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

```

And the attached image shows the results:

[ATTACH]105736[/ATTACH]

My settings in System -> Appearance -> Fonts (I think some of these overlap with fonts.conf):

Sans 8 on Application, Desktop, and Document fonts.
Sans Bold 8 on Window Title font.
Liberation Mono 10 on Fixed Width Font.
"Best shapes", "Grayscale", "Medium Hinting" as the rendering settings.

---

