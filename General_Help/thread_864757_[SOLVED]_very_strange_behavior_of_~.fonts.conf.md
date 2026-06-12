---
title: "[SOLVED] very strange behavior of ~/.fonts.conf"
date: 2008-07-20
forum: General Help
---

### Post by bajun on 2008-07-20
Solved: there is Lucida Grande font on ubuntu.com


Hello.
I dont know, I think, I'm not mentally disturbed, but what I'm see now makes me real crazy.
On Hardy in .fonts.conf.
If I delete a space between two words Lucida Grande in line ```
   <string>Lucida Grande</string>
``` and make this line look as:```
   <string>LucidaGrande</string>
```, all works ok.
But if I place this space back, as it generally should be, the font on page [http://start.ubuntu.com/8.04/](http://start.ubuntu.com/8.04/) in firefox loses hinting. Lucida Grande is not used there. Please, check images before and after. What is this? My computer scoffs over me? :?Lucida Grande

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

<!--
     Substitute unavailable and/or unwanted fonts.

     Aliases will not work if the actual fonts are installed.
     Replacing font family works in Firefox (FIXME: and other GTK-based apps?)
     QT-based apps also need font foundry replaced.
     Grouping fonts for substitution doesn't work in Firefox, so we need each
     font family replaced individually.
-->

<match target="pattern">
 <test qual="any" name="family" compare="eq">
  <string>System</string>
 </test>
 <edit name="family" mode="prepend" binding="same">
  <string>Arial</string>
 </edit>
</match>

<match target="pattern">
 <test qual="any" name="family" compare="eq">
  <string>Courier</string>
 </test>
 <edit name="family" mode="prepend" binding="same">
  <string>Courier New</string>
 </edit>
</match>

<match target="pattern">
 <test qual="any" name="family" compare="eq">
  <string>Fixedsys</string>
 </test>
 <edit name="family" mode="prepend" binding="same">
  <string>Courier New</string>
 </edit>
</match>

<match target="pattern">
 <test qual="any" name="family" compare="eq">
  <string>Monaco</string>
 </test>
 <edit name="family" mode="prepend" binding="same">
  <string>Courier New</string>
 </edit>
</match>

<match target="pattern">
 <test qual="any" name="family" compare="eq">
  <string>Terminal</string>
 </test>
 <edit name="family" mode="prepend" binding="same">
  <string>Courier New</string>
 </edit>
</match>

<match target="pattern">
 <test qual="any" name="family" compare="eq">
  <string>New Century Schoolbook</string>
 </test>
 <edit name="family" mode="prepend" binding="same">
  <string>Georgia</string>
 </edit>
</match>

<match target="pattern">
 <test qual="any" name="family" compare="eq">
  <string>New York</string>
 </test>
 <edit name="family" mode="prepend" binding="same">
  <string>Georgia</string>
 </edit>
</match>

<match target="pattern">
 <test qual="any" name="family" compare="eq">
  <string>Palatino</string>
 </test>
 <edit name="family" mode="prepend" binding="same">
  <string>Georgia</string>
 </edit>
</match>

<match target="pattern">
 <test qual="any" name="family" compare="eq">
  <string>Times</string>
 </test>
 <edit name="family" mode="prepend" binding="same">
  <string>Georgia</string>
 </edit>
</match>

<match target="pattern">
 <test qual="any" name="family" compare="eq">
  <string>URW Palladio L</string>
 </test>
 <edit name="family" mode="prepend" binding="same">
  <string>Georgia</string>
 </edit>
</match>

 <match target="pattern" >
  <test name="family" qual="any" compare="eq">
   <string>Helvetica</string>
  </test>
   <edit name="family" mode="prepend" binding="same">
   <string>Arial</string>
  </edit>
 </match>

<match target="pattern">
 <test qual="any" name="family" compare="eq">
  <string>Copperplate</string>
 </test>
 <edit name="family" mode="prepend" binding="same">
  <string>Impact</string>
 </edit>
</match>

<match target="pattern">
 <test qual="any" name="family" compare="eq">
  <string>Desdemona</string>
 </test>
 <edit name="family" mode="prepend" binding="same">
  <string>Impact</string>
 </edit>
</match>

<match target="pattern">
 <test qual="any" name="family" compare="eq">
  <string>Kino</string>
 </test>
 <edit name="family" mode="prepend" binding="same">
  <string>Impact</string>
 </edit>
</match>

<match target="pattern">
 <test qual="any" name="family" compare="eq">
  <string>Techno</string>
 </test>
 <edit name="family" mode="prepend" binding="same">
  <string>Impact</string>
 </edit>
</match>

<!--
     Provide required aliases for standard names.
-->
<alias>
 <family>sans-serif</family>
  <prefer>
   <family>Arial</family>
  </prefer>
</alias>

<alias>
 <family>serif</family>
  <prefer>
   <family>Georgia</family>
  </prefer>
</alias>

<alias>
 <family>cursive</family>
  <prefer>
   <family>Comic Sans MS</family>
  </prefer>
</alias>

<alias>
 <family>fantasy</family>
  <prefer>
   <family>Impact</family>
  </prefer>
</alias>

<!--
     Darstellungsoptionen
-->

<match target="pattern">
 <edit name="dpi" mode="assign">
  <double>96</double>
 </edit>
</match>

<!--
     Set minimum allowed size to avoid illegible fonts.
-->
<!-- 7pt in QT-based apps -->
<match target="pattern">
 <test qual="any" name="size" compare="less">
  <double>7</double>
 </test>
 <edit name="size" mode="assign">
  <double>7</double>
 </edit>
</match>

<!-- 9.4px (7pt) in GTK-based apps -->
<match target="pattern">
 <test qual="any" name="pixelsize" compare="less">
  <double>9.4</double>
 </test>
 <edit name="pixelsize" mode="assign">
  <double>9.4</double>
 </edit>
</match>

<!--
     TODO: Create rules limiting minimum sizes for these *bold* fonts:

     Andale Mono | Andale Mono IPA
     Arial
     Arial Narrow
     Berling Antiqua
     Book Antiqua
     Bookman Old Style
     Century Gothic
     Comic Sans MS
     Courier New
     Franklin Gothic Medium
     Frutiger Linotype
     Garamond
     Georgia
     Kartika
     Lucida Console
     Lucida Sans Typewriter
     Lucida Sans Unicode
     Microsoft Sans Serif
     Palatino | Palatino Linotype
     SylfaenARM
     Tahoma
     Times New Roman
     Trebuchet MS
     Verdana
     Vrinda
-->

<!--
     bold fonts no smaller than 10.7px (8pt)

     FIXME: for Firefox and other GTK-based apps?
-->
<match target="font">
 <test qual="any" name="family" compare="eq">
  <string>Arial</string>
 </test>
 <test qual="any" name="pixelsize" compare="less">
  <double>10.7</double>
 </test>
 <test qual="any" name="weight" compare="more">
  <const>medium</const>
 </test>
 <edit name="pixelsize" mode="assign">
  <double>10.7</double>
 </edit>
</match>

<!--
     Enable anti-aliasing.
-->

 <match target="font">
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
 </match>
 
<!--
     Set sub-pixel order if not detected.

     "X knows the sub pixel order already, and if this is enabled as well,
     Freetype produces some very strange results. However, if you do still
     have problems, consider (...) 'rgb' (the standard for LCD monitors),
     'bgr' (unusual), 'vrgb' (vertical rgb, if you have a monitor that
     has been rotated by 90 degrees[1]), 'vgbr' (as vrgb, but very rare)."
     <http://www.linuxquestions.org/linux/answers/Hardware/\
     LCD_TFT_Monitor_Configuration_in_X_Org>

     Find out your LCD's sub-pixel order:
     <http://grc.com/image/cleartype2c.gif>
-->

<match target="font">
 <test qual="all" name="rgba" compare="eq">
  <const>unknown</const>
 </test>
 <edit name="rgba" mode="assign">
  <const>rgb</const>
 </edit>
</match>

<!--
     Enable FreeType Auto-Hinter.

     Auto-Hinter is disabled by default if Bytecode Interpreter was compiled in.
     Some Linux "native" fonts look better hinted by Auto-Hinter,
     usually in sizes 11pt-13pt; others look better hinted by BCI.
-->

 <match target="font">
  <edit mode="assign" name="hinting">
   <bool>true</bool>
  </edit>
 </match>
 
<!--
     Set Auto-Hinter to full hinting style.

     'slight' and 'medium' hinting often produce pixel discoloration.
-->
 
 <match target="font">
  <edit mode="assign" name="hintstyle">
   <const>hintfull</const>
  </edit>
 </match>

<!--
     Sub-pixel hinting via BCI enabled by default if compiled in.

     "Whole-pixel anti-aliasing does not represent a useful solution for
     improving small point-size type. (...) By 'borrowing' sub-pixels from
     adjacent whole pixels, we can fine-tune the placement and width of typeface
     features with three times more horizontal accuracy then ever before!"
     <http://grc.com/ctwhat.htm>
-->

<!--
     Adjust anti-aliasing and hinting for select fonts based on size and style.
-->

<match target="font">
 <test qual="any" name="family" compare="eq">
   <string>Monaco</string>
  </test>
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
  <edit mode="assign" name="hinting">
   <bool>false</bool>
  </edit>
 </match>

<match target="font">
 <test qual="any" name="family" compare="eq">
   <string>Chicago</string>
  </test>
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
  <edit mode="assign" name="hinting">
   <bool>false</bool>
  </edit>
 </match>
 
<match target="font">
 <test qual="any" name="family" compare="eq">
   <string>Geneva</string>
  </test>
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
  <edit mode="assign" name="hinting">
   <bool>false</bool>
  </edit>
 </match>
 
<match target="font">
 <test qual="any" name="family" compare="eq">
   <string>Charcoal</string>
  </test>
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
  <edit mode="assign" name="hinting">
   <bool>false</bool>
  </edit>
 </match>

<match target="font">
 <test qual="any" name="family" compare="eq">
   <string>New York</string>
  </test>
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
  <edit mode="assign" name="hinting">
   <bool>false</bool>
  </edit>
 </match>

<match target="font">
 <test qual="any" name="family" compare="eq">
   <string>Apple Garamond</string>
  </test>
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
  <edit mode="assign" name="hinting">
   <bool>false</bool>
  </edit>
 </match>

<match target="font">
 <test qual="any" name="family" compare="eq">
   <string>Apple Garamond Light</string>
  </test>
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
  <edit mode="assign" name="hinting">
   <bool>false</bool>
  </edit>
 </match>
 
<match target="font">
 <test qual="any" name="family" compare="eq">
   <string>Aquabase</string>
  </test>
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
  <edit mode="assign" name="hinting">
   <bool>false</bool>
  </edit>
 </match>
 
<match target="font">
 <test qual="any" name="family" compare="eq">
   <string>Lucida Grande</string>
  </test>
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
  <edit mode="assign" name="hinting">
   <bool>false</bool>
  </edit>
 </match>
 
<match target="font">
 <test qual="any" name="family" compare="eq">
   <string>Lucida MAC</string>
  </test>
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
  <edit mode="assign" name="hinting">
   <bool>false</bool>
  </edit>
 </match>

<match target="font">
 <test qual="any" name="family" compare="eq">
   <string>LucidaMacBold</string>
  </test>
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
  <edit mode="assign" name="hinting">
   <bool>false</bool>
  </edit>
 </match>

<match target="font">
 <test qual="any" name="family" compare="eq">
   <string>MACGrande</string>
  </test>
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
  <edit mode="assign" name="hinting">
   <bool>false</bool>
  </edit>
 </match>
 
<match target="font">
 <test qual="any" name="family" compare="eq">
   <string>Gadget</string>
  </test>
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
  <edit mode="assign" name="hinting">
   <bool>false</bool>
  </edit>
 </match>

</fontconfig>

```

---

### Post by drs305 on 2008-07-20
Could it be that the <space> has a different value in the text editor you are using? Try copy/pasting another two word section ( 'Lucida MAC' would be a good choice) over the 'Lucida Grande' entry. The put the cursor on the M and retype Grande without ever hitting the space key. Then delete the 'MAC' using the delete key. Save and see if that changes things.

---

### Post by bajun on 2008-07-20
No, copy/past and rearrange was the first, that I have tried, without results. 

For test puproses:

1: I have maked following small fonts.conf:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

<match target="pattern">
 <edit name="dpi" mode="assign">
  <double>96</double>
 </edit>
</match>

 <match target="font">
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
 </match>
 
<match target="font">
 <test qual="all" name="rgba" compare="eq">
  <const>unknown</const>
 </test>
 <edit name="rgba" mode="assign">
  <const>rgb</const>
 </edit>
</match>

<!--
HINTING DECLARATION
-->

 <match target="font">
  <edit mode="assign" name="hinting">
   <bool>true</bool>
  </edit>
 </match>
 
 <match target="font">
  <edit mode="assign" name="hintstyle">
   <const>hintfull</const>
  </edit>
 </match>

<!--
END HINTING DECLARATION
-->

<!--
HINTING exception
-->

<match target="font">
 <test qual="any" name="family" compare="eq">
   <string>Monaco</string>
   <string>Chicago</string>
   <string>Geneva</string>
   <string>Charcoal</string>
   <string>New York</string>
   <string>Apple Garamond</string>
   <string>Apple Garamond Light</string>
   <string>Aquabase</string>
   <string>Lucida Grande</string>
   <string>Lucida MAC</string>
   <string>LucidaMacBold</string>
   <string>MACGrande</string>
   <string>Gadget</string>
  </test>
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
  <edit mode="assign" name="hinting">
   <bool>false</bool>
  </edit>
 </match>

<!--
END HINTING exception
-->


</fontconfig>

```

2. I have maked Lucida MAC as default firefox font and loaded [http://crca.ucsd.edu/~msp/techniques.htm](http://crca.ucsd.edu/~msp/techniques.htm) to be sure, that hinting exception works properly.

3. Then I've loaded [http://start.ubuntu.com/8.04/](http://start.ubuntu.com/8.04/) to test, that hinting works good for other fonts.

Then:

- If I place "HINTING DECLARATION" section from this file before "HINTING exception" section and delete this space between "Lucida" and "Grande", everething is ok, I have no hinting on the first site. On the second hinting works great. But this variant have problems with font name "LucidaGrande"
- If I place "HINTING DECLARATION" before "HINTING exception" section and use normal "Lucida Grande" fontname, I have no hinting on the both sites.
- If I place "HINTING DECLARATION" section after "HINTING exception" section I have hinting on the both sites. Fontname doesn't matter in this case.

Can somebody make this test?

Fonts: [http://www.osx-e.com/downloads/misc/macfonts.html](http://www.osx-e.com/downloads/misc/macfonts.html)

---

