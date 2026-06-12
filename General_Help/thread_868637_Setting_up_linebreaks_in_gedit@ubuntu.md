---
title: "Setting up linebreaks in gedit@ubuntu"
date: 2008-07-24
forum: General Help
---

### Post by webstuff on 2008-07-24
Hi there everyone

I'm working in a team with to others, I'm using Ubuntu, and the two others is using windows/mac.
We're all editing the same PHP file, and keep them in order by using an SVN server. But the problem comes when I create/edit a file, and then when the mac-guy try to open my file he get's a message about using different linebreaks, and he will have to convert them to "LF Linebreaks" before he can see the file properly.

My question to you is if there's a way I can setup gedit (that I'm using for editing) to make the right linebreaks?

//webstuff

---

### Post by justleen on 2008-07-24
im not sure wether you can change gedit to do this - perhaps there is a pugin to do so, im not sure... You could use the cmdline util unix2dos to convert text files to a dos version (which has the right line breaks). it is in the package "tofrodos"

---

### Post by webstuff on 2008-07-24
hey justleen

Thank you for the comment, I'll look into that thing commandline.
But if there's anyone else out there with a solution I'll be glad!

//webstuff

---

### Post by justleen on 2008-07-24
I've just run into this post as well: 
[http://ubuntuforums.org/showthread.php?t=146291](http://ubuntuforums.org/showthread.php?t=146291)

---

### Post by webstuff on 2008-07-24
Thanks alot.. I'm not that familiar with Emacs, can you tell me if it has all the options that gedit has? like linenumber, highlighting etc.

//webstuff

---

### Post by justleen on 2008-07-24
i actually meant this bit "In gedit, you can search and replace-all "\r\n" with "\n" to remove the CR and convert from DOS to Unix format. Then when exporting back, you can replace all "\n" with "\r\n". It doesn't look any different in gedit on the screen, but in the saved file it does."

you problably wont like emacs  :))

---

### Post by webstuff on 2008-07-24
Ahh, allright... I'll try that, thanks again! :-)

---

### Post by savsav on 2008-07-24
Geany has what you are looking for.

In Geany, click on Document. Set Line Endings. Convert and Set to CR (Mac)

Now the guy with the Mac computer will be able to read your document with no problems.

---

### Post by cszikszoy on 2008-07-24
> **webstuff said:**
> is if there's a way I can setup gedit (that I'm using for editing) to make the right linebreaks?

The problem isn't that gedit makes the wrong line breaks.  The problem is that Mac's text files *use* the wrong line breaks! ;)

---

### Post by WRDN on 2008-07-24
For linebreaks gedit uses "\n", while some other text editors such as Notepad in Windows do not. This causes formatting problems, as has been mentioned.
For Windows, you can solve this problem by using Wordpad, as that uses the "\n" convention, and the formatting is correct.
For a Mac, you could use [Vim]("http://macvim.org/OSX/index.php").

This will remove any line break inconsistencies.

---

### Post by MathUHenry on 2009-08-26
Thank you WRDN. Switching to Wordpad in Windows solved my problem. I really didn't want to give up Gedit.

---

### Post by akranis on 2009-09-05
If you want a really good text editor for Windows, try Notepad++. You can easily see which linebreaks are present in the file and use a simple menu to change between dos, mac and unix.

I fixed a problem a moment ago where a config file on my linux server wasn't read properly because I had edited the file in Windows and had left bad linebreaks.

---

