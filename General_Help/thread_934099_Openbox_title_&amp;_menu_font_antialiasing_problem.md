---
title: "Openbox title &amp; menu font antialiasing problem"
date: 2008-09-30
forum: General Help
---

### Post by adios on 2008-09-30
Ok, I recently installed Ubuntu. I also installed Openbox, tweaked it a little... Soon I noticed, that something was badly wrong with font antialiasing.

[http://img221.imageshack.us/my.php?image=kuvakaappausid4.jpg]("http://img221.imageshack.us/my.php?image=kuvakaappausid4.jpg")

As you can see, in ObConf (and every other program) fonts are ok, but when openbox renders them, they look quite odd.

So... wtf?! As I said, this problem presents only in Openbox. Using version 3.4.6.1.

EDIT: And no, it's not just Zekton. Zekton just shows the problem most clearly.

---

### Post by urukrama on 2008-09-30
I'm not sure why it is only in Openbox, but have you configured your font settings in ~/.fonts.conf? Here is mine:

> <?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">

<!-- the cathectic LCD tweaks, from linuxquestions.org,
 [http://www.linuxquestions.org/questions/showthread.php?postid=1361098#post1361098](http://www.linuxquestions.org/questions/showthread.php?postid=1361098#post1361098) -->

<fontconfig>

<!-- Disable sub-pixel rendering.
 X detects it anyway, and if you set this as well, it just looks really horrible  -->
<match target="font" >
	<edit mode="assign" name="rgba" >
	 <const>none</const>
	</edit>
 </match>
 <match target="font" >
	<edit mode="assign" name="hinting">
	 <bool>true</bool>
	</edit>
 </match>
 <match target="font" >
	<edit mode="assign" name="hintstyle">
	 <const>hintfull</const>
	</edit>
 </match>

<!-- The first part of the 'magic.'
 This makes the fonts start to look nice,
 but some of the shapes will be distorted, so hinting is needed still -->
 <match target="font" >
	<edit mode="assign" name="antialias">
	 <bool>true</bool>
	</edit>
 </match>

<!-- Autohinter is not turned on automatically.
 Only disable this if you have recompiled Freetype with the bytecode interpreter,
 which is run automatically.<br />  -->
 <match target="pattern" >
	<edit mode="assign" name="autohint">
	 <bool>true</bool>
	</edit>
 </match>
 <match target="font">
		 <test name="weight" compare="more">
				 <const>medium</const>
		 </test>
		 <edit name="autohint" mode="assign">
				 <bool>false</bool>
		 </edit>
 </match>
<!-- Helvetica is a non true type font, and will look bad.
 This replaces it with whatever is the default sans-serif font -->
 <match target="pattern" name="family" >
	<test name="family" qual="any" >
	 <string>Helvetica</string>
	</test>
	<edit mode="assign" name="family" >
	 <string>sans-serif</string>
	</edit>
 </match>
<match target="font" >
  <test compare="more" name="pixelsize" qual="any" >
   <double>12</double>
  </test>
  <edit mode="assign" name="autohint" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="pattern" >
  <test name="family" qual="any" >
   <string>Bitstream Vera Sans</string>
  </test>
  <edit mode="assign" name="family" >
   <string>Arial</string>
  </edit>
 </match>
 <match target="pattern" >
  <test name="family" qual="any" >
   <string>Helvetica</string>
  </test>
  <edit mode="assign" name="family" >
   <string>Arial</string>
  </edit>
 </match>
 <match target="pattern" >
  <test name="family" qual="any" >
   <string>Palatino</string>
  </test>
  <edit mode="assign" name="family" >
   <string>Georgia</string>
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
 <dir>~/.fonts</dir>
</fontconfig>


---

### Post by adios on 2008-09-30
It's better! Whoa. It still has the terrible subpixel rendering, but I can probably turn it off myself. Thanks <3

ukukrama, btw, your guide originally made me use Openbox. It's just awesome. :)

---

### Post by adios on 2008-09-30
Agh. Now I can't disable subpixel rendering, or the fonts become screwed once again. How I make Openbox render font just like every other application :|

---

### Post by adios on 2008-10-07
Ok, solved it! Finally.

Had to do font config in /etc/fonts/local.conf instead ~/.fonts.conf. So, removed ~/.fonts.conf and created local.conf file like this:

> 
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font" >
<edit mode="assign" name="rgba" >
<const>rgb</const>
</edit>
</match>
<match target="font" >
<edit mode="assign" name="hinting">
<bool>true</bool>
</edit>
</match>
<match target="font" >
<edit mode="assign" name="hintstyle">
<const>hintfull</const>
</edit>
</match>


Shoudn't it work also in ~/.fonts.conf? Is this bug? :)

---

