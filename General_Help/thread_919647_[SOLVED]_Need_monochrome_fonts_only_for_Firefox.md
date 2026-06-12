---
title: "[SOLVED] Need monochrome fonts only for Firefox"
date: 2008-09-14
forum: General Help
---

### Post by itsjareds on 2008-09-14
Solved, here is how I did it:

Edit the fonts file:
```
sudo gedit /etc/fonts/conf.avail/51-local.conf
```

Then add the part in bold:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
	<!-- Load local system customization file -->
	<include ignore_missing="yes">local.conf</include>

[B]       <!-- Make fonts render as sharp -->
       <match target="font">
                <test qual="any" name="family">
                        <string>Verdana</string>
                </test>
                <edit name="antialias" mode="assign"><bool>false</bool></edit>
                <edit name="autohint" mode="assign"><bool>false</bool></edit>
        </match>
        <!-- End override -->[/B]
</fontconfig>
```

--------------------Original post--------------------

Hi, I installed the msttcorefonts package and all of the MS fonts look fine, but my only problem now is they only look "normal" if I set fonts for my whole computer to monochrome. This makes the rest of my fonts look horrible, like the Applications Places System taskbar at the top. My computer shows fonts the best under Best contrast.

How can I set the fonts only to show as monochrome *inside* the webpages on firefox, but not the menu items/URL bar?

[Here is a picture comparing them]("http://i35.tinypic.com/10mr4ee.png")

---

### Post by itsjareds on 2008-09-14
Bump.. :shock:

---

### Post by itsjareds on 2008-09-14
Bump again.. help?

---

### Post by kerry_s on 2008-09-14
maybe try changing your fonts to something that looks good with the settings you want.

from your pic, i don't know what is what, but the 1 on the left looks good.

---

### Post by itsjareds on 2008-09-14
Yeah, what I mean is that "Best contrast" looks the best on my computer, but "Monochrome" looks best inside a web page, mainly on the Verdana MS font.

What I'm asking is how can I change only web pages to use monochrome fonts?

---

### Post by kerry_s on 2008-09-14
> **itsjareds said:**
> Yeah, what I mean is that "Best contrast" looks the best on my computer, but "Monochrome" looks best inside a web page, mainly on the Verdana MS font.

What I'm asking is how can I change only web pages to use monochrome fonts?

in firefox> edit> preferences> content> fonts&colors, advanced
then just set the font you want, if you only want it to use your fonts, uncheck "allow pages..."

i don't use smooth fonts so mine are set to the bitmap fonts, but i do have the ms fonts and just allow the page to use if it wants, see pic

---

### Post by itsjareds on 2008-09-14
I don't have that option in my options. The window is exactly the same except for that checkbox.

Either way I figured it out, check my first post.

---

