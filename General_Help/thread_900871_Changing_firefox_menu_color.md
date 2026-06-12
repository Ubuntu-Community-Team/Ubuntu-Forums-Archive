---
title: "Changing firefox menu color?"
date: 2008-08-25
forum: General Help
---

### Post by kidwithshirt on 2008-08-25
[[IMG]http://img510.imageshack.us/img510/3030/screenshot1gm8.png[/IMG]](http://imageshack.us)
[[IMG]http://img510.imageshack.us/img510/3030/screenshot1gm8.3db2ca3e5b.jpg[/IMG]](http://g.imageshack.us/g.php?h=510&i=screenshot1gm8.png)

I've googled about 30 minutes already and no usable answer.

i know to change the chrome css file

But what options do I add? As you see I just need to change the black menu text to white, that's all. Nothing else should be white.

---

### Post by kidwithshirt on 2008-08-25
hey. i just opened a bunch of other programs

turns out open office does the same thing. however banshee works fine, the menu is white already

---

### Post by nicolai.rostov on 2008-09-28
Just add the following to chrome/userChrome.css (Got from [here]("http://ubuntuanswers.wordpress.com/2008/01/03/change-font-color-in-firefox-to-suite-your-theme-ubuntu/"))

```

menubar, menubutton, menu, menuitem, menupopup, popup > * {
 color: white !important;
}

```

Cheers,
 NR

---

