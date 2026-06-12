---
title: "Why is the Helvetica font bitmapped only"
date: 2008-11-22
forum: General Help
---

### Post by BattlePanic on 2008-11-22
I have been exploring the fonts in Ubuntu 8.10 Intrepid Ibex and it appears that the Helvetica font supplied with the distro is only offered in bitmapped form.  Is there a reason for this?

---

### Post by fragos on 2008-11-22
Linux supports a number of font formats. Most that you use today are True Type, TTF. The TTF version of Helvetica requires a paid license. I suggest you use the open source "DejaVu Sans" which has a similar appearance. The DejaVu family of fonts are are based on Bitstream fonts. Pre Vista Windows systems would normaly use "Arial".

---

### Post by kerry_s on 2008-11-22
cause it's a bitmap font?
it's a xserver font, it has no antialiasing or hinting, which makes them fast and low resource.
it's most commonly used in place of windows arial, if you have ever used any version of windows before windows xp clear type, that's what the font looks like.

---

### Post by BattlePanic on 2008-11-22
Thanks for the replies.  I should have been a bit more clear when posing my question.  

I have a decent understanding of the distinction between bitmapped fonts and outline fonts.  Within the realm of outline fonts, I also understand the concepts of font smoothing and font hinting, neither of which tend to apply to bitmapped fonts since they are encoded on a pixel by pixel basis and are rendered on-screen in a similar fashion.

I was surprised to see Helvetica offered at all since my understanding was that it was a proprietary font being sold by Linotype.  I was also puzzled by the fact that such a popular font was being offered in such an old-school format.  After coming across [this post]("http://ubuntuforums.org/showthread.php?t=918094") it seems my questions have been answered.  The bitmapped version of Helvetica must be the only format in which this font is freely available.

---

### Post by learningcurb on 2009-06-06
Where can we get the Helvetica font for Ubuntu by the way?  I can't seem to find it in the repos anywhere.

---

### Post by kerry_s on 2009-06-06
> **learningcurb said:**
> Where can we get the Helvetica font for Ubuntu by the way?  I can't seem to find it in the repos anywhere.

it's already installed. run> **sudo dpkg-reconfigure fontconfig-config**
enable bitmap fonts.
run> **sudo fc-cache -vf**
to make sure your fonts are all loaded.
log out and back in.

---

### Post by learningcurb on 2009-06-06
> **kerry_s said:**
> it's already installed. run> **sudo dpkg-reconfigure fontconfig-config**
enable bitmap fonts.
run> **sudo fc-cache -vf**
to make sure your fonts are all loaded.
log out and back in.

Is sudo dpkg-reconfigure fontconfig-config supposed to give you an interactive ncurses screen in the terminal?  I think I recall it doing that in Intrepid.  I just tried it now and I just got a newline back:

```
$ sudo dpkg-reconfigure fontconfig-config
$
```

I logged in and out and Helvetica is not showing up in the font list for Open Office, Leafpad or any other application. Do I need to take other steps or install/remove other packages first?  Maybe it conficts with the mscorefonts package?  I do have the xfonts-terminus package installed and it works and I think it is a bitmapped font.

---

### Post by kerry_s on 2009-06-07
looks like it's broke in ubuntu, i'm using debian testing, still works for me.

---

### Post by learningcurb on 2009-06-07
Oh well, it's good to know know that it's a bug.  I'll see if it works in Crunchbang later.

---

### Post by firfin on 2009-07-01
> **learningcurb said:**
> Is sudo dpkg-reconfigure fontconfig-config supposed to give you an interactive ncurses screen in the terminal?  I think I recall it doing that in Intrepid.  I just tried it now and I just got a newline back:

```
$ sudo dpkg-reconfigure fontconfig-config
$
```
 
It works fine for me in my Jaunty-install. I also have OOo and msttcorefonts so those should not be a problem.
):P

---

