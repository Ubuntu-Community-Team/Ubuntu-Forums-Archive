---
title: "Unreadable character display (9.10 upgrade)"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by JohnESimpson on 2009-11-08
Hello -

Have been with Ubuntu since Edgy, upgraded with every cycle. This is the first time I was really glad to have retained my Windows partition. :)

After the (apparently trouble-free) upgrade from 9.04 to 9.10, display of ANY character data is completely hosed: not just the contents of files, etc., but launcher labels, dialog box text (title bars and everything else), URLs, menu options... Every single character displays on the screen as a small 1emx1em rectangular box (empty/outline). The login screens display fine, for what that's worth.

*[It just now occurred to me that I should have checked the terminal window/command line. Will try that after I post this -- not that it will be much help in the short term, haha.]*

Have no idea even how to approach this problem, since I can't read a single thing.

System is a Dell Dimension 4550, Dell flat-panel monitor, nVidia GeForce 6200 card, 1GB RAM.

---

### Post by JohnESimpson on 2009-11-08
Right, so I'm back in (I guess!) 9.10 right now. Some additional information:

[LIST]
[*]Terminal window also munged.
[*]As I mentioned, browser GUI stuff -- URLs, menus, tab labels, and such -- are garbled. In Firefox, at least, the garbling of everything but the title bar makes all text invisible, as though white-on-white. (Title bar has the little rectangles.)
[*]...BUT the content of Web pages themselves apparently display just fine, except for form widgets like Submit buttons. (These display as though they contained no text at all.)
[*]At login screen, I noticed that my language is set to English-US, Keyboard to English/US, and the third option ("Session"?) to gnome. All of which sounds proper to me.
[*]At the GRUB menu, tried one of the recovery-mode options. The text there displays just fine, but I couldn't interact with the menu at all.
[/LIST]
So, still stumped. Anybody?

---

### Post by sc30317 on 2009-11-08
do a 

sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade

to make suure that everything is updated.

---

### Post by JohnESimpson on 2009-11-09
> **sc30317 said:**
> do a 

sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade

to make suure that everything is updated.

Thanks for the suggestion, sc30317. Unfortunately it didn't work.

It was tricky even issuing the command, because I knew I wouldn't be able to see what was happening. So I changed my Sessions setting (bottom of login screen) to xterm. This at least gave me a terminal window which behaved normally. OTOH, invoking Firefox or other GUI programs still gave me munged title bars, menus...

BUT when I first opened Firefox under xterm, the terminal window threw up a bunch of error messages relating to something called Pango. They were moving too fast to read, but they referred to a broken Bitstream font and said that the condition meant the Firefox display would be "ugly."

Apparently, not just the font which the Firefox GUI uses but all other GUI fonts are corrupted somehow.

Suggestions?

---

### Post by JohnESimpson on 2009-11-09
Attaching some photos I took of various areas of the screen, to give you a more concrete idea what I'm talking about.

Really hoping someone can give me a hand on this!

---

### Post by JohnESimpson on 2009-11-10
Does anyone have ANY ideas?

Should I post this problem in a different forum, maybe?

I have got SO much freaking work to do this week, which I can do only in Ubuntu. I'm on the verge of nervous collapse here.

If nothing else, can someone point me to a resource that explains how to reinstall Jaunty? Especially given that I may not be able to read any on-screen prompts?

Suggestions? Knowledgeable sympathy?

Thank you!

---

### Post by Peter K Nicol on 2009-11-21
Sympathy yes, but I don't know if I can help much.
One thing I had to do was right click on the desktop; Change Desktop Background; Visual Effects; None.
Even then I still can't see System Monitor -just a lot of blues and reds in a box.
Open Office had all the menu headings greyed out. It was tricky but once anti-aliasing was turned off I could see them again (info from Open Office forum).
There was a text rendering bug in 9.04 - see the thread [http://ubuntuforums.org/showthread.php?t=1160441](http://ubuntuforums.org/showthread.php?t=1160441)
I haven't tried that yet as it seems a bit different this time.

---

### Post by JohnESimpson on 2009-11-21
Thanks so much for the reply, Peter. I had read about the reported text-rendering problem in Jaunty but alas, that didn't help in my case.

Ultimately, I abandoned what was shaping up to be a futile goal (fixing the upgrade). Instead, I just did a complete clean install of Karmic -- including a re-formatting of the Ubuntu partition -- and then restored the backups of all my data files. I had failed to do a recent backup of my OO templates, but recreating them felt fairly trivial after banging my head against this display problem (and -- *ack!* -- working in Windows) for over a week. ;)

(Haven't changed this to [RESOLVED] since the question still lacks a definite answer, but it's not a problem for me anymore. Should anyone reading this have any insights, I'd still love to hear them!)

Thanks again,
JES

---

### Post by kenklay on 2009-12-01
Our organization has a OpenOffice extension that does not load on 9.10.  In researching the problem I found that Karmic dropped a package named ttf-bitstream that was a default install in previous versions.  If you had a Bitstream font selected for Gnome and did an upgrade in place, it may have not known how to substitute a different font.  I am not an expert, so maybe someone more knowledgeable could verify.

---

### Post by srs713 on 2009-12-22
I have been searching for a fix for my OO dialog boxes and other notifications being unreadable since the 9.10 upgrade. After reading several threads like this one I suspected a font problem, so I went into System>Preferences>Appearance and on the Fonts tab clicked the Details button. After changing the smoothing & hinting settings I closed that & started OO... I can now read the dialog boxes. They are still a little munged as far as background on the buttons, but the menus are usable now. Perhaps a bit more tweaking in appearances will show more improvement. I'm just happy to have functionality for now.

Karmic on a Dell C610 laptop.

---

