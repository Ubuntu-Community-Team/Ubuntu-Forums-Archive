---
title: "HP All-in-one; error while printing, only half a page printed."
date: 2013-04-21
forum: Hardware
---

### Post by the big e on 2013-04-21
So I sometimes send a thing to the printer, and it dies after printing only half a page.
So far I have only experienced this when I print a thing that has a lot of color, off of a web page. In one case it was a Google map. In one case, it was a mail-in form that was in the form of a pdf (and using up excessive memory in terms of file size for what it was.

Why is this happening? Can I fix it by installing a better driver?

Also, in one case it wasted a lot of paper (and overpriced colored ink) by trying to print something out multiple times in a row.

---

### Post by oldfred on 2013-04-22
What version of hplip do you have? The default in the repository is pretty old.

HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by the big e on 2013-04-25
Thank you, oldfred. I tried it. Not quite there yet. Same quit-in-the-middle problem as before. Also the auto install script screwed something up resulting in a bad boot which I had to recover from by pulling the plug. 

(also, for some reason colors are not the same as when I print from Windows.)

---

### Post by oldfred on 2013-04-25
Never pull the plug, remember the elephants. :)

       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by tgalati4 on 2013-04-25
If you are printing wirelessly then sometimes there is wireless interference which will mess up the print job.  If your printer is connected with a USB or ethernet connector then try changing cables or checking connections.

Does your printer work reliably in Windows?  If it behaves strangely in Windows, then it could be a printer hardware problem.

---

### Post by the big e on 2013-04-28
As far as I've tried it, it works fine in Windows, but I feel more at home in Ubuntu, so I would not want to keep doing the shut-down-and-reboot dance every time I want to print something out.

After attempting the new driver install that OldFred suggested, I keep getting error messages at startup saying that the system tray is missing.

---

### Post by oldfred on 2013-04-28
I use gnome-panel or fallback, so I assumed the error on system tray was just due to that. I ignored it on reboot.

I thought the most recent update made that go away, but not sure as that printer is not the one I use at home.

---

### Post by tgalati4 on 2013-04-28
Some HP printers have a RAM setting in the advanced settings.  If your printer has less RAM then what is specificed in the default printer settings, then you might lose 1/2 a page.

---

### Post by the big e on 2013-04-28
What's a tray, and why do I fail to have one?
Also there were earlier error messages about a missing python package and a "System Problem Detected"

---

### Post by tgalati4 on 2013-04-28
Open a terminal and run:

```
hp-toolbox
```

Note any errors in the terminal and try to exercise all of the options in the graphical toolbox.  Also, you should have an HP icon in your system tray.  The system tray is the bar across the bottom or top of your screen with a bunch of icons.

---

### Post by the big e on 2013-05-06
On startup, the HP program gives me a message saying it can't detect the system tray, and then force-exits. (though for some reason it doesn't do that every time I boot)

When I try to print something, I get the same problem as before, with a crash in the middle of the job. (half a page if it's a color print of a web page, two-plus pages if it's a wordprocessing file, and then it hangs forever, perhaps printing out a last line or two after I cancel the job)

Also an erroneous message that the cartridge is empty (I replaced it very recently)

Works perfectly in Windows, though.

---

### Post by the big e on 2013-07-17
So I still have the same problem, even after attempting reinstall of HPLIP. Is there a way to roll back my printer driver to the previous state, in case what happened is some system file got mangled when I tried to instal something that wasn't ubuntu-specific?

What it still always does is give me a message that says "no system tray detected. exiting" and also occasionally a message that says "a system problem occurred" which is probably related. How do I roll back to the appropriate earlier state?

---

