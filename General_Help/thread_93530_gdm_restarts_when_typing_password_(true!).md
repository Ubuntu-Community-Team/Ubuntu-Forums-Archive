---
title: "gdm restarts when typing password (true!)"
date: 2005-11-22
forum: General Help
---

### Post by guimou on 2005-11-22
Hi,

Up until yesterday, my Breezy was working perfectly well. Here is exactly what I did yesterday and what happened:
- I wanted to try to correct some font problems on MythTV (not related to the problem, just to set up the crime scene...)
- I installed the package msttcorefonts (installation OK)
- in my /usr/share/fonts/, I copied some other ttf fonts from a Windows install
- I issued the command fc-cache -v /usr/share/fonts/ to reload the font cache
- CTRL+ALT+Backspace to restart X
And then:
- I have a logon screen (that's OK)
- I enter my login (still OK)
- as soon as I type any key for entering the password, gdm restarts! It seems to start OK, but just after the icon showing that it is loading Metacity, it goes black and then back to the logon screen...

I tried to reboot: same behaviour...
I tried numerous time to logon: after a few tries, some message tells me there is a problem with the logon and that it will try another method. It gives me the standard Gnome logon screen, but it does exactly the same.

Back to the console, I had a look at some logs:
- when booting, just before starting X/gdm, I have an error about DUMPKEYCODES, stating it cannot find some elements (sorry, I forgot the exact message I noted back at home). Something about not able to map keycodes aa, ef and something else to code 256 (or something like that)
- in the gdm log, I have some messages about fonts (.pcf, ....) already handled by something else with priority 0 (whatever that means).

I also tried to remove the msttcorefonts package, then re-run fc-cache, reboot, but no luck...

So I am stuck out of my box (at least out of gnome), and that's pretty annoying. :( 

If someone has a clue, I'd be very pleased (especially since my wife has important documents to finish tomorrow at the latest, and I'm too tall for the sofa:smile: 

Thanks,
Guillaume

---

### Post by aysiu on 2005-11-22
I know it's probably a problem with GDM specifically, but it may be an X problem, too. Have you tried control-alt-F1, logging in, and then typing ```
sudo dpkg-reconfigure xserver-xorg
```?

---

### Post by guimou on 2005-11-22
No, I did not try this one. But that's worth the try though as everything "seems" to be related to some font problem and there is also some font related configuration in X. I'll try and post the result, thanks.
If others have something else to try they can think of, please don't wait for this result. As I am at work I won't be able to test anything until tonight and report tomorrow if this does not work. So the more options I have tonight, the most chances I have to send my thanks :D 

Guillaume.

---

### Post by aysiu on 2005-11-22
[QUOTE=guimou]
If someone has a clue, I'd be very pleased (especially since my wife has important documents to finish tomorrow at the latest, and I'm too tall for the sofa:smile: [/QUOTE] Do you dual boot or have some other working computer? Those files your wife has to work on can be fetched, even if you can't log onto GDM. You could copy them to the other computer for her to work on until you get this problem fixed.

---

### Post by guimou on 2005-11-22
[QUOTE=aysiu]Do you dual boot or have some other working computer? Those files your wife has to work on can be fetched, even if you can't log onto GDM. You could copy them to the other computer for her to work on until you get this problem fixed.[/QUOTE]

I have dual boot (for games you know, otherwise I use VMWare inside Linux for Windows apps that don't Wine or don't have equivalent and that I need: Dreamweaver MX 2004...). And I still could boot on a LiveCD. So that's not really a problem, more a joke. The real problem is: it does not work! The subsequent (and also real problem) could be: "Honey, I broke the computer and don't know how to fix it..." :???: Shame on me...

---

### Post by kbas on 2005-11-22
I have exactly the same problem. I also installed new fonts using
```
aptitude install xfonts-intl-european msttcorefonts gsfonts-x11
fc-cache -f -v
```
so it seems related to this. The xorg configuration files have not been changed.
Console contained similar messages like:
```
KDSETKEYCODE: No such device
failed to set scancode ... to keycode 256
```
Otherwise I have not found any other error messages in any log file.

What actually works to run Gnome is to switch to the console (e.g. by Ctrl-Alt-1), log on with your user and issue *startx* command but that is definitely not the way I would like to use my box. Any ideas? Google did not help this time :(

---

### Post by guimou on 2005-11-22
Hehe! I managed to get myself out of troubles...

So all the evidence pointed to some fonts problem, that apparently could not be handled well. I tried the suggestion from aysiu with no luck (thanks anyway!).
So back at home I tried to step backward:
- boot up in recovery mode to be sure X and all the graphical stuff do not start
- removed all the ttf files I copied yesterday
- re-run a ```
fc-cache -f 
```to reconstruct the fonts cache
- reboot, and... bingo!

But strange still, I kept the Dumpkeycodes error during boot... Maybe I did not notice it before as everything worked right...

So kbas, what I could suggest based on my little experience is:
- uninstall your font packages
- maybe clean a little bit your font dirs
- boot in recovery mode to be on the safe side
- run ```
fc-cache -f
```
- pray...

Keep us posted!

---

### Post by kbas on 2005-11-23
Yep, it worked!! And I found the cause of the evil - Microsoft! ;)  No, not really. It's Verdana or to be more specific the exact file verdana.ttf (171792 bytes). If this file is removed from the font directory and the font cache is regenerated (fc-cache -fv) the gdm works correctly again. I did not uninstall any packages nor removed any other fonts. I also did not look for the keycode messages since this was not the real problem.

Thank you all for your hints and hopefully this thread will help others to get rid of this very annoying error.

---

