---
title: "Font causing system Crash"
date: 2008-08-18
forum: General Help
---

### Post by Stan_1936 on 2008-08-18
I downloaded this font:
[http://www.fontica.com/font/handelgotdlig](http://www.fontica.com/font/handelgotdlig)

and then I did this:

Created .fonts folder in the home directory, extracted theme and placed the only file in the extracted folder(a TTF file) into the .fonts folder.  I then logged out and logged back in, selected the font from Windows Manager and all seemed well.  After a few minutes of using the font, I got a balloon popping up saying that a Crash had occurred on the system and to click on the balloon for details.  I clicked and the balloon gave me no information....i.e. nothing happened.  I then closed the balloon and sitting underneath was another balloon saying that software updates were ready for download.  Again, clicking this second balloon gives me nothing.  I then went back to one of the pre-installed fonts(that came with Xubuntu) and all is fine now....no Crashes.

I am using Xuubntu Hardy(8.04) with Compiz Fusion installed(and running well, as far as I can tell with an NVIDIA GeForce 5200X AGP graphics card) and am not using either AWN or conky.

Is there anyway to use the font?  What am I doing wrong?

---

### Post by silkstone on 2008-08-18
After installing new fonts, you should either log out and in again, or...

sudo fc-cache -fv

If you've done that and still have a problem, it may be that the ttf file is corrupt or non-standard, but I'm only guessing there.

---

### Post by Stan_1936 on 2008-08-18
> **silkstone said:**
> ...it may be that the ttf file is corrupt or non-standard.....

That would be really harsh!!!  PATHETIC!!!

I logged out, restarted X (Ctrl+Alt+Bkspce) and then logged back in.

What does ```
sudo fc-cache -fv
``` do?

---

### Post by silkstone on 2008-08-18
That command reconfigures your font cache so the new fonts are recognised. Logging out and in achieves the same.

Have you had any problems with other ttf files copied to ~/.fonts? If other font files work OK, I can't think of an explanation other than a defect with this particular file.

---

### Post by Stan_1936 on 2008-08-18
Actually, this is my first try at installing fonts.  I'll have to try some others before I know if all TFF files are giving problems.

Could it be that this is a font designed for Gnome only and is giving problems since I am trying to install it on XFCE?

---

