---
title: "Phonetic fonts"
date: 2008-08-30
forum: General Help
---

### Post by mack27 on 2008-08-30
Hiya!
Does anybody know where I can get phonetic fonts (IPA) that would run on Ubuntu? Thanks!

---

### Post by coffeecat on 2008-08-30
If you put 'phonetic' into the search field in Synaptic, among the packages listed is 'texlive-fonts-extra'

The description includes:

> TeX Live: Extra fonts 
All sorts of extra fonts

This package includes the following CTAN packages:

<snip>

 phonetic -- MetaFont Phonetic fonts, based on Computer Modern.Is this what you were after? Beware though. There are dozens of fonts in that package, some quite weird and wonderful. For instance, "allrunes -- Fonts and LaTeX package for almost all runes" or "dancers -- Font for the Sherlock Holmes `Dancing Men' " or "semaphor -- Semaphore alphabet font in METAFONT"or even "trajan -- Fonts from the Trajan column in Rome." Hours of fun. :?

---

### Post by eggdeng on 2008-08-30
```
sudo apt-get install ttf-gentium
``` will install the gentium font which supports IPA characters. The only way that I know of, however, of using the symbols in a document is via the insert menu.

---

### Post by tacutu on 2008-08-30
mack27, try [http://www.sil.org/](http://www.sil.org/) they have several goodies on their site.

---

### Post by mack27 on 2008-08-30
> **eggdeng said:**
> ```
sudo apt-get install ttf-gentium
``` will install the gentium font which supports IPA characters. The only way that I know of, however, of using the symbols in a document is via the insert menu.

installed it, however cannot see it in the fonts list and hence cannot apply it even through the instert menu. neither does it help displaying the correct characters on in a saved file. the way i used to use special characters instead of using the insert menu was to create keybord shortcuts for those i needed most. i'm not sure how to do that wih open office yet.

---

### Post by mack27 on 2008-08-30
> **coffeecat said:**
> If you put 'phonetic' into the search field in Synaptic, among the packages listed is 'texlive-fonts-extra'

The description includes:

Is this what you were after? Beware though. There are dozens of fonts in that package, some quite weird and wonderful. For instance, "allrunes -- Fonts and LaTeX package for almost all runes" or "dancers -- Font for the Sherlock Holmes `Dancing Men' " or "semaphor -- Semaphore alphabet font in METAFONT"or even "trajan -- Fonts from the Trajan column in Rome." Hours of fun. :?

did this too, but it didn't change anything.

---

### Post by mack27 on 2008-08-30
> **tacutu said:**
> coffeecat, this is ridiculos! why would you direct the OP to (La)TeX fonts? I am 100% sure if (s)he wanted LaTeX fonts, (s)he would've mentioned it! The OP probably wants some TTF fonts for OpenOffice or the like.

mack27, try [http://www.sil.org/](http://www.sil.org/) they have several goodies on their site.

well, i just need IPA fonts for editing and reading files using them. i do use open office. thanks for the sil website tip.

---

### Post by eggdeng on 2008-08-30
> installed it, however cannot see it in the fonts list
?? Restart openoffice.

---

### Post by mack27 on 2008-08-30
> **eggdeng said:**
> ?? Restart openoffice.

oh yeah, it's there. :)

---

### Post by mack27 on 2008-09-01
ok guys, i still need your help with this one. so i have the font and yes, i can insert the characters i need but still, the documents i open which already contain phonetic symbols don't display them, there's just brackets instead. what can we do? it's important to me.

---

### Post by eggdeng on 2008-09-01
Could you send me one of these docs to check it out? I'll send you my email by PM.

---

### Post by oldHat on 2008-10-02
I've been fighting with this, too.  I've tried a little bit of everything I could find on any related thread here.

One thread recommended using SCIM.  It helps, but only if you have the right fonts.

For fonts, the last thing I tried was: ** sudo apt-get install ttf-sil-doulos**.  (This after downloading the latest *.deb from [http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&item_id=DoulosSIL_download](http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&item_id=DoulosSIL_download), then receiving a gdebi warning that an older version was already available in the repositories.) 

I think it helped.  The font is visible as "Doulos SIL" in OpenOffice.

I'm still learning the diacritics.  I haven't found the superscripted "h" yet.  Any hints?

---

