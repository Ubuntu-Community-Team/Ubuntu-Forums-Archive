---
title: "Terminal type &quot;rxvt-unicode&quot; is unknown."
date: 2008-09-13
forum: General Help
---

### Post by e2k on 2008-09-13
Hi there!

When I ssh to the host at my school with urxvt and try to fire up pine I get this ```
% pine
Terminal type "rxvt-unicode" is unknown.
```How would I go about to make it recognize my terminal? When I login I also get this message (that I normally don't get with other terminals) ```
tcsh: using dumb terminal settings.
```Any thoughts?

---

### Post by Corin-EU on 2008-09-13
In your ${HOME}/.tcshrc on your school account, why not put

if (${TERM} == "rxvt-unicode") setenv TERM "xterm"

since rxvt is very close/identical to xterm in its vt102 capabilities.

Obviously you could run into conflict if you wish to use unicode features whilst logged into your school account.

The other alternative would be just to fire up an xterm instead of an rxvt-unicode for doing your ssh session.

The reason you are getting this problem is because the remote system does not have an appropriate entry for rxvt-unicode in its terminfo database (see /lib/terminfo directories on Ubuntu)

You could always try politely asking the system administrator to add the necessary details for rxvt-unicode.

---

### Post by e2k on 2008-09-14
> **Corin-EU said:**
> In your ${HOME}/.tcshrc on your school account, why not put

if (${TERM} == "rxvt-unicode") setenv TERM "xterm"

since rxvt is very close/identical to xterm in its vt102 capabilities.

Obviously you could run into conflict if you wish to use unicode features whilst logged into your school account.

The other alternative would be just to fire up an xterm instead of an rxvt-unicode for doing your ssh session.

The reason you are getting this problem is because the remote system does not have an appropriate entry for rxvt-unicode in its terminfo database (see /lib/terminfo directories on Ubuntu)

You could always try politely asking the system administrator to add the necessary details for rxvt-unicode.Thanks for explaining it to me, I decided to use an other terminal for ssh:ing to it while waiting for an answer from the admin! 8-)

---

### Post by Mischa on 2011-05-03
**sudo apt-get install ncurses-term**

will fix it for you.

this is because it will fill /usr/share/terminfo, which is probably empty at the moment.

grtz,

MIscha[CENTER][COLOR=#000000][/COLOR][/CENTER]

[LEFT][COLOR=#CCCCCC][FONT=Trebuchet MS][/FONT][/COLOR][/LEFT]
[CENTER][COLOR=#000000]AfrikaansAlbanianArabicArmenianAzerbaijaniBasqueBelarusianBulgarianCatalanChinese (Simplified)Chinese (Traditional)CroatianCzechDanishDetect languageDutchEnglishEstonianFilipinoFinnishFrenchGalicianGeorgianGermanGreekHaitian CreoleHebrewHindiHungarianIcelandicIndonesianIrishItalianJapaneseKoreanLatinLatvianLithuanianMacedonianMalayMalteseNorwegianPersianPolishPortugueseRomanianRussianSerbianSlovakSlovenianSpanishSwahiliSwedishThaiTurkishUkrainianUrduVietnameseWelshYiddish[COLOR=lightgrey]**&#8644;**[/COLOR]AfrikaansAlbanianArabicArmenianAzerbaijaniBasqueBelarusianBulgarianCatalanChinese (Simplified)Chinese (Traditional)CroatianCzechDanishDutchEnglishEstonianFilipinoFinnishFrenchGalicianGeorgianGermanGreekHaitian CreoleHebrewHindiHungarianIcelandicIndonesianIrishItalianJapaneseKoreanLatinLatvianLithuanianMacedonianMalayMalteseNorwegianPersianPolishPortugueseRomanianRussianSerbianSlovakSlovenianSpanishSwahiliSwedishThaiTurkishUkrainianUrduVietnameseWelshYiddish[LEFT]Detect language » English[/LEFT]


[/COLOR][/CENTER]

---

### Post by icfantv on 2011-09-02
The problem is that by default SSH will transfer the current value of TERM for you (on your source system) to the target system and the termcap file for rxvt-unicode is not present.

I have this problem at work all the time.  The easiest solution is to simply create a ~/.ssh/environment file on the machine you are SSHing from (your normal workstation, perhaps) and add a line like "TERM=xterm-color" - this will tell SSH to redefine the value of TERM for your session and keep you from having to modify every box into which you end up SSHing.

If the target machine doesn't like "term-color" you can just use "vt100" - but as mentioned above, you will not get Unicode support for either of these term types.

Hope this helps.

---

