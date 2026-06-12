---
title: "anyone using opera, what fonts do you use?"
date: 2005-11-04
forum: General Help
---

### Post by pickarooney on 2005-11-04
Most pages display fine for me, with every font option in Opera changed to Tahoma (the default was helvetica, which doesn't exist ??). However, pages like [The Register](www.theregister.co.uk) display all ugly. 
Is this because I've told Opera to use Tahoma everywhere or for some other reason (note: the fonts display fine in Firefox and Epiphany). 
Can someone with Opera go to the site above and see how the fonts look, maybe take a screenshot and list their font preferences for Opera?

Thanks a million in advance.

---

### Post by Moonbuzz on 2005-11-04
These are my definitions, I don't think I changed anything from the default though.

Interface compose = Courier new [monotype]
Interface display e-mail = Courier new [monotype]
Interface menus = helvetica [Adobe]
Interface toolbars = Arial [monotype]
Interface dialogs = Arial [monotype]
Interface panels = Arial [monotype]
Webpage normal text = Times New Roman [monotype]
Webpage <pre> = Courier new [monotype]
Forms text field multi-line = Courier new [monotype]
Forms text field single-line = Arial [monotype]
Forms button text = Arial [monotype]
CSS font-family serif = Arial [monotype]
CSS font-family cursive = Impact [monotype]
CSS font-family fantasy Comic Sans MS [Microsoft]
CSS font-family monospace = Courier new [monotype]
Webpage <h1> = Times New Roman [monotype]
Webpage <h2> = Times New Roman [monotype]
Webpage <h3> = Times New Roman [monotype]
Webpage <h4> = Times New Roman [monotype]
Webpage <h5> = Times New Roman [monotype]

The Register looks just fine, I couldn't send you the image for some reason, though, but if it's really importand, I'll email it to you or someth.

---

### Post by Xian on 2005-11-04
[QUOTE=pickarooney]Most pages display fine for me, with every font option in Opera changed to Tahoma (the default was helvetica, which doesn't exist ??). However, pages like [The Register](www.theregister.co.uk) display all ugly. [/QUOTE]
1. Use Times New Roman, Tahoma, or Bitstream for your webpage font.
2. Add this entry in "[User Prefs]" in your ~/.opera/opera6.ini file.

Enable Core X Fonts=0

3. Make sure the font size is large enough to render the page correctly.
If the minimum font size is too small the headlines appear graveled.

---

### Post by pickarooney on 2005-11-05
[QUOTE=Xian]
2. Add this entry in "[User Prefs]" in your ~/.opera/opera6.ini file.

Enable Core X Fonts=0
[/QUOTE]

That's exactly what I was missing. Everything looks great now :)
This should be in more stickies :D

---

### Post by prince_niceguy on 2008-03-05
thank you...

Enable Core X Fonts=0

worked for me too...

however any idea how to make opera use the fonts which i use in system setting as i have to adjust now the fonts in opera everytime i change the font defaults...

---

### Post by daris on 2008-06-03
Thanks, Xian

Opera now renders Helvetica and Courier New fonts smoother

---

