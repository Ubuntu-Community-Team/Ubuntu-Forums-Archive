---
title: "Mathematica problems"
date: 2005-11-13
forum: General Help
---

### Post by posco on 2005-11-13
There were a few threads posted in the Breezy dev forums concerned with problems with Mathematica 5.0 that surfaced after upgrading to Breezy, but as those are now closed, I need to ask here: has anyone found a solution to the problem of Mathematica 5.0 crashing when trying to open new dialogs (Help, Save, ...)?

Additionally, for whoever wants it, there is a solution to the "translation table syntax error: unknown keysym name...." problem. Namely, rename the /usr/share/X11/XKeysymDB file to something else, and also (if necessary) delete or move your ~/.Mathematica directory.

Edit: It looks like the real solution to the translation table problems is to copy /usr/share/X11/XKeysymDB to /usr/X11R6/lib/X11/. The previous attempt got rid of the window that pops up, but there were still errors output to stdout if it was started from the command line. Anyway, it still crashes. 

Posco

---

### Post by mikelito on 2005-11-16
For those who had problems installing Mathemathica under Breezy, I finally managed to have it up and running thanks to a bug report
[http://bugzilla.ubuntu.com/show_bug.cgi?id=14173]("http://bugzilla.ubuntu.com/show_bug.cgi?id=14173").

To make things clearer, these were the problems:
* error complaining about the locale settings
* lots of lines repeating various blends of "Warning: translation table syntax error"
* window list applet got stuck when the splash screen appeared
* segmentation fault & mathematica death

These are the steps I followed to make things work:
* the locale and translation table errors are due to some X11 directories having been moved around out to their "hystorical" location. just go to 
$ cd /usr/X11R6/lib/X11/
$ sudo rm locale
$ sudo ln -s  /usr/share/X11/XKeysymDB XKeysymDB
$ sudo ln -s /usr/share/X11/locale/ locale
* run mathematica with -noSplashScreen option to avoid the crash-the-window-list  problem

i hope this helps, I had quite a hard time finding these tips on the net.

michele

---

### Post by yioan on 2005-12-06
thanks... it works.

there is an article in ubuntu wiki. You should also post it there.

---

### Post by mssm on 2006-01-28
Oh man, thanks a lot. I gave up hopes. I never searched through this forum for mathematica. It solved my problem too.

---

### Post by LordMelkor on 2006-02-23
I got mathematica installed and running (thanks to these workarounds :D ) but when I am entering equations I find that I am unable to edit what i have written, and if I press backspace a square appears, how can I fix this? :confused:

---

### Post by Schrollini on 2006-02-26
[QUOTE=LordMelkor]I got mathematica installed and running (thanks to these workarounds :D ) but when I am entering equations I find that I am unable to edit what i have written, and if I press backspace a square appears, how can I fix this? :confused:[/QUOTE]

Try turning off NumLock.  There's probably a better way to fix this, but that's what works for me.

---

### Post by LordMelkor on 2006-02-28
thanks that seems to work!

---

### Post by Simon Bridge on 2006-03-07
Mikelito: this is great. I have a user here with this problem. However, when he makes the "locale" link in the suggestion, he gets font errors and still crashes.

Any ideas?

The issue is posted here:
[http://www.linuxquestions.org/questions/showthread.php?p=2139083#post2139083](http://www.linuxquestions.org/questions/showthread.php?p=2139083#post2139083)

---

### Post by samba on 2006-05-25
Hi,

Thanks a lot for the workarounds! Using the suggestion in the 'Edit' part of the first post, and using the -noSplashScreen option I am now able to run mathematica 5.1 on my laptop!

However there is a crucial problem; i can't read anything on mathematica! for some reason, the fonts just don't appear in the notebooks... i see like half a line everything else becomes white on white and i don't see anything... has anyone else got the same problem? I'm running Ubuntu Dapper Beta, and I'm also running Compiz and AIGLX.

Thanks,
Vincent

---

### Post by samba on 2006-05-25
Well I just understood the problem, which is probably related to the use of Compiz. Basically, the inside of the mathematica window is somehow transparent;  in particular, text inside the window appears the color of what is below that window. so if I have a white window open below mathematica, text appears white, so i can't read anything, but if I run mathematica directly on top of my desktop (the background image of my desktop is black), then i can see.

this is strange, but at least it solves the problem for me at the moment. :-)

vincent

---

### Post by baradwaj on 2006-07-08
Thanks to all for this solution.But is there some other solution for this numlock thing.I mean  I dont get backspace or delete working until i turn numlock off.The problem is that I am accustomed to typing nos using the numpad.I have a similar problem with xcircuit-a circuit drawing package where in without turning off numlock i cant get menus working.Are these by any chance related?BTW,I am using Dapper and this solution works on Dapper as well

Thanks

---

### Post by Rui Pais on 2006-07-17
Hi,
there is at wolfram's technical support faqs a page about how to solve the question of Numlock without have to turn it off when using Mathematica:
[http://support.wolfram.com/mathematica/systems/linux/general/configurenumlock.html]("http://support.wolfram.com/mathematica/systems/linux/general/configurenumlock.html")
this worked for me with Mathematica 5, linux version.

About the Xgl+Compiz, i read on another forum that do:
```
export XLIB_SKIP_ARGB_VISUALS=1
```
before start mathematica (or add it to ~/.bashrc or mathematica start script) solve the problem. 
I removed all xgl from my computer so i couldn't not check it here... but maybe it helps others.

---

### Post by Celil Rifat on 2006-10-10
Thank's alot. The fix worked for me too.

---

### Post by jamesrl on 2006-11-02
The 
export XLIB_SKIP_ARGB_VISUALS=1 
works for me with my problem of Mathematica text being transparent when running Beryl.  However, I didn't realize it worked at first, as the launcher shortcut to Mathematica doesn't work, even if its in the .bashrc (and has been run); I have to start Mathematica from the bash terminal.  [I just wrote a bash startup script, that does both for me].
Just thought this might save someone some hassle.

---

### Post by kholsheimer on 2006-12-06
ok, so mathematica does not crash (anymore), but somehow my mathematica window looks so crappy that i almost can't read anything in it.

any suggestions..?

---

### Post by yioan on 2006-12-06
try to install msttcorefonts package.

that is, issue the following command supposing you have the right repositories entries:

sudo apt-get install msttcorefonts

---

### Post by ntetreau on 2007-02-23
Hi, I am having the same font problem as yioan and msttcorefonts is already installed.  I get this error message when starting Mathematica 5.2 which I'm sure is related:

Unable to find font with family Times, weight Plain, etc

I am trying to change the font in the settings but to no avail, any help appreciated.

Nic

---

### Post by dstubb on 2007-03-10
Is there a step-by-step somewhere on how to get Mathematica installed (in my case it's 4.1, which says it supports PPC Linux) on ubuntu?  What extras do I need to get it working?  How do I run the installer properly?

I am from the mac world, so a lot of this is new to me.  

Thanks for any help.

iMac G3, 400mhz, Dapper - ubuntu breathed new life into this old machine.

---

### Post by hardhu on 2007-03-16
> **jamesrl said:**
> The 
export XLIB_SKIP_ARGB_VISUALS=1 
works for me with my problem of Mathematica text being transparent when running Beryl.  However, I didn't realize it worked at first, as the launcher shortcut to Mathematica doesn't work, even if its in the .bashrc (and has been run); I have to start Mathematica from the bash terminal.  [I just wrote a bash startup script, that does both for me].
Just thought this might save someone some hassle.

I am trying to use this trick, that is the export XLIB_SKIP_ARGB_VISUALS=1 to run Mathematica 5.0 in a 32bit chroot of my Feisty 64bit, but it doesn't work and the text is still transparent; I am using beryl 0.2.0 and xgl and I have an ati x700 video card, using fglrx proprietary driver.
Can anybody help me?

---

