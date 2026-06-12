---
title: "Getting xterm, emacs etc to use my Truetype Fonts"
date: 2008-07-17
forum: General Help
---

### Post by Amalaye on 2008-07-17
Basically I want xterm and emacs to be able to use the inconsolata font. The Gnome applications seem to be able to see the new fonts I added, but my 'generic' X applications cannot. They give out an error saying that font inconsolata cannot be found and they switch to a default font ...

---

### Post by Amalaye on 2008-07-17
The message I get is:

xterm:  unable to open font "inconsolata", trying "fixed"....

---

### Post by Amalaye on 2008-07-17
Still tinkering ... 

----

axo@ultramachine:~$ xlsfonts | grep incon

-unknown-inconsolata-medium-r-normal--0-0-0-0-p-0-iso10646-1
-unknown-inconsolata-medium-r-normal--0-0-0-0-p-0-iso8859-1
-unknown-inconsolata-medium-r-normal--0-0-0-0-p-0-iso8859-15


axo@ultramachine:~$ xterm -font -unknown-inconsolata-medium-r-normal--0-0-0-0-p-0-iso10646-1

xterm:  unable to open font "-unknown-inconsolata-medium-r-normal--0-0-0-0-p-0-iso10646-1", trying "fixed"....

-----

axo@ultramachine:~$ locate inconso

/etc/defoma/hints/ttf-inconsolata.hints
/usr/share/bug/ttf-inconsolata
/usr/share/bug/ttf-inconsolata/presubj
/usr/share/bug/ttf-inconsolata/script
/usr/share/doc/ttf-inconsolata
/usr/share/doc/ttf-inconsolata/OFL-FAQ.txt.gz
/usr/share/doc/ttf-inconsolata/README.Debian
/usr/share/doc/ttf-inconsolata/changelog.Debian.gz
/usr/share/doc/ttf-inconsolata/copyright
/usr/share/doc/ttf-inconsolata/incoshow.png
/usr/share/doc/ttf-inconsolata/textest.pdf.gz
/usr/share/fonts/truetype/ttf-inconsolata
/usr/share/fonts/truetype/ttf-inconsolata/Inconsolata.otf
/var/cache/apt/archives/ttf-inconsolata_001.009-1_all.deb
/var/lib/dpkg/info/ttf-inconsolata.conffiles
/var/lib/dpkg/info/ttf-inconsolata.list
/var/lib/dpkg/info/ttf-inconsolata.md5sums
/var/lib/dpkg/info/ttf-inconsolata.postinst
/var/lib/dpkg/info/ttf-inconsolata.prerm

---

### Post by Amalaye on 2008-07-18
Still tinkering with this ... any font gurus here ???

---

### Post by Amalaye on 2008-07-30
Never got feedback on this ...

---

### Post by gaussian on 2008-07-31
Cannot help you with xterm, but Emacs has a new development version that allows you use Truetype fonts. See:
[http://www.emacswiki.org/cgi-bin/wiki/XftGnuEmacs](http://www.emacswiki.org/cgi-bin/wiki/XftGnuEmacs)

---

### Post by olafbooij on 2008-09-12
If I'm correct Truetype fonts are used through the Freetype library. To use them in an xterm use -fa instead of -font or -fn. Thus:
```
xterm -fa -unknown-inconsolata-medium-r-normal--0-0-0-0-p-0-iso10646-1

```
should work.

EDIT: hmmm, I'm not really sure now: "xterm -fa notafont" also works... pfff, xterm should at least give a warning... notafont, is not a fontName, and switches to a default 
 
I know... an old thread

Olaf

---

### Post by centyx on 2008-09-26
xterm/uxterm -fa inconsolata works for me. So does 
xterm -fa inconsolata-12
 

xterm/uxterm -fa -unknown-inconsolata-medium-r-normal--0-0-0-0-p-0-iso8859-1 did not ( opened xterm w/ a default font ).

---

