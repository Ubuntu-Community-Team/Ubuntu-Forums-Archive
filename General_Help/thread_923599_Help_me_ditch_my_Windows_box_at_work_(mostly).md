---
title: "Help me ditch my Windows box at work (mostly)"
date: 2008-09-18
forum: General Help
---

### Post by CaptSaltyJack on 2008-09-18
I use Mac OS X at home and love it.  As such, I've grown to hate working on Windows at work.  My company probably wouldn't care if I started working on a Linux box, as long as I could still get all my work done.  Here's what I use day to day:

[LIST]
[*]Dreamweaver (though I hate it and could use something else for web work, I don't need WYSIWYG, in fact I prefer working in straight code these days)
[*]Outlook 2003
[*]Word, Excel 2003 (but I need to be able to open 2007 docx/xlsx files)
[*]Photoshop CS2
[*]Fireworks 8
[*]Illustrator CS2 (infrequently)
[*]Subversion
[/LIST]

So would it be possible for me to ditch Windows entirely?  I'm thinking probably not, and I'd just have to buy a KVM and switch to my Windows box once in a while to do graphics work.

Given my list above, I'm looking for:

[LIST]
[*]a SUPERB email program that supports Exchange
[*]a really good text editor that supports syntax highlighting, auto indent, etc (a programmer's editor) - OR - an editor geared towards web development that allows you to define several web sites, choose an upload method (FTP, WebDAV, LAN, SFTP), and lets you upload your changes; built in SVN support would be icing on the cake
[*]a good SVN client would be nice; TortoiseSVN on Windows is the best, IMO
[/LIST]

Thoughts?

---

### Post by wykedengel on 2008-09-18
Allow me to preface this by saying that I am the average PC user. I am mosdef not a techie so bear with me.

I would install XuEduKuU(buntu)then install Virtualbox. Inside VB, you can install your Windows OS and whatever proprietary software that you may find yourself needing, until you can find good open-source alternatives for Linux.

This way, you can still be sure to get your work done like you need to, but also begin experimenting with your Linux box at the same time.

I hope that it helps.

---

### Post by TheLions on 2008-09-18
> **wykedengel said:**
> Allow me to preface this by saying that I am the average PC user. I am mosdef not a techie so bear with me.

I would install XuEduKuU(buntu)then install Virtualbox. Inside VB, you can install your Windows OS and whatever proprietary software that you may find yourself needing, until you can find good open-source alternatives for Linux.

This way, you can still be sure to get your work done like you need to, but also begin experimenting with your Linux box at the same time.

I hope that it helps.

if he install VirtualBox he would still using Windows!

if you ask me, you should stick with windows. Why? you'll mess with company PC, possibly broke it, lose a lot a time to set-up ubuntu instead working and moust of your programs wouldn't work well without VirtualBox(Windows)

---

### Post by CaptSaltyJack on 2008-09-18
> **TheLions said:**
> if he install VirtualBox he would still using Windows!

if you ask me, you should stick with windows. Why? you'll mess with company PC, possibly broke it, lose a lot a time to set-up ubuntu instead working and moust of your programs wouldn't work well without VirtualBox(Windows)

Huh?  I already have a Windows box at work.. I would NOT be reformatting it or changing it at all.  I'm buying a separate box for Ubuntu.  So that's not an issue.  My plan is to use the Ubuntu box as much as possible for web development work, and use the Windows box when I really need it.

---

### Post by bingoUV on 2008-09-18
Email: Evolution supports Exchange, but I wouldn't call it superb. It also faces problems with Exchange sometimes. No other email client for linux comes close. Better use the windows box for Email.

Text Editor: You will be spoiled for choice. Vim and Emacs; or one of their derivatives will be more than up to the job.

SVN: Never worked with svn but you'll face no problems. Search repositories for svn. Vim and Emacs also have plugins to work with svn.

---

### Post by CaptSaltyJack on 2008-09-18
> **bingoUV said:**
> Text Editor: You will be spoiled for choice. Vim and Emacs; or one of their derivatives will be more than up to the job.


Syntax color-coding?  Auto indent?  Find matching braces/brackets/parens?  Didn't know vim could do that.  And I knew emacs could auto indent, but what about color coding?  Emacs is too bloated for my tastes, though.

---

### Post by bingoUV on 2008-09-18
It can do this and much much more. All features are a google away. Just install vim-full. Ubuntu installs vim-minimal by default

1. Syntax of popular languages is color-coded automatically. Plugins for many obscure languages are available.

2. Auto indent is in-built. 
```

:set autoindent

```

3. Matching parentheses etc
```

:set showmatch

```

---

### Post by CaptSaltyJack on 2008-09-18
Hmm, a couple things bug me about vim's auto indent:

- it doesn't tab/space inward after I type "{" followed by new-line
- it doesn't outdent when I type "}" so it lines up with the opening brace

Ideal auto-indent should know what language I'm using and tab accordingly.  In Javascript, PHP, C++, if I just type "if (condition)" and hit return, it should indent.  But if I type "{", it should outdent immediately.  Basically, I should never have to even think about hitting the tab key.

---

### Post by CaptSaltyJack on 2008-09-18
Ah, nevermind.  "set smartindent".  Nice.  I'll have to go through the full list of vim options.  I assume cream (the GUI version of vim) follows all the same options and rules?

---

### Post by amersault on 2008-09-18
> **CaptSaltyJack said:**
> 
[LIST]
[*]Dreamweaver (though I hate it and could use something else for web work, I don't need WYSIWYG, in fact I prefer working in straight code these days)
[*]Outlook 2003
[*]Word, Excel 2003 (but I need to be able to open 2007 docx/xlsx files)
[*]Photoshop CS2
[*]Fireworks 8
[*]Illustrator CS2 (infrequently)
[*]Subversion
[/LIST]


based on your list, i would recommend - 

DW - NVU is a really good text editor that i've used to replace DW
DOC/XLS files - OpenOffice does an excellent job of opening all these 
PSD - GIMP (except you might have problems w/ Vector files, still working that issue out)
FW - none that i know of so far...
AI - Seashore i believe handles vector work, i'd have to check again

what does Subversion do?

---

### Post by michael@cgl on 2008-09-18
hey man, Ive just done that today and managed to get everything working;
email. IM (which ties into msn), graphics, office which opens MS word docs easy. 
Its supposed to connect to my msn mailbox but ive not worked that out yet.
Ubuntu seems to be a much cleaner faster system so far and the community are great

just keep your old box as planned until you find yourself not using it anymore

mick

---

### Post by bingoUV on 2008-09-18
> **CaptSaltyJack said:**
> Ah, nevermind.  "set smartindent".  Nice.  I'll have to go through the full list of vim options.  I assume cream (the GUI version of vim) follows all the same options and rules?

Yeah, cream is vim, though I never liked it more than the real vim. 

I don't like smartindent too, but it is there.

---

### Post by CaptSaltyJack on 2008-09-18
NVU is cool but I hate DW :)  No WYSIWYG for me.  Actually, I tried Geany and it totally rocks.  It actually has codesense for PHP!  Slick!  I think I've found a winner for my code editor.

As far as Gimp goes, I'll give it a shot and see how it works out.  I use Fireworks 8 more than Photoshop, though.  For those not familiar, it's a combination vector/bitmap editor, leaning towards web design.  It's slick stuff.

---

### Post by amersault on 2008-09-18
> **CaptSaltyJack said:**
> NVU is cool but I hate DW :)  No WYSIWYG for me.  Actually, I tried Geany and it totally rocks.  It actually has codesense for PHP!  Slick!  I think I've found a winner for my code editor.

As far as Gimp goes, I'll give it a shot and see how it works out.  I use Fireworks 8 more than Photoshop, though.  For those not familiar, it's a combination vector/bitmap editor, leaning towards web design.  It's slick stuff.

yeah i do the same and i've found there's no replacement for the Flash and vector so i'm still tethered to my Mac so to speak.

to solve the vector problem, i've used Seashore but be warned it's a very basic Paint that supports vector. nothing like GIMP.

---

### Post by CaptSaltyJack on 2008-09-18
Wait, Seashore is for Mac only, it looks like.  I don't see a Linux version.

Inkscape is a pretty great vector based app for Linux, by the way.

---

### Post by amersault on 2008-09-18
> **CaptSaltyJack said:**
> Wait, Seashore is for Mac only, it looks like.  I don't see a Linux version.

Inkscape is a pretty great vector based app for Linux, by the way.

oops mea maxima culpa

just noted that Seashore is OS X. i'll have to try Inkscape to handle vector files. can't be worse than working w/ Seashore, hahahah

---

