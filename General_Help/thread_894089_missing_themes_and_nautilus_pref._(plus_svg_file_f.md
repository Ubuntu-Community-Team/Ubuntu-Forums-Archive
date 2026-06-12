---
title: "missing themes and nautilus pref. (plus svg file format recognition error - solved)"
date: 2008-08-18
forum: General Help
---

### Post by naaiya on 2008-08-18
Hey,
Asking google hasnt helped, if there is any solution to this out there ive obviously missed it and im sorry for producing yet another post.
I also lost my linux virginity only 2 days ago = n00b = sorry again.

So here it goes - my ubuntu 8.04 crashed while installing the updates, after rebooting i got an error - "couldn't recognize the image file format (blabla).svg" when the human theme was being loaded. I also wasnt able to run gnome-control-center => appearance, apparenty for the very same svg thingy reason (ran it via terminal and had a peek). Anyway, I then tried to apt-get librsvg2-2, found out it was already installed, and finally compiled and installed librsvg-2.22.2 which fixed the svg recognition error. 

Now, for my actual problem
1) i can open apprearance preferences just fine, thing is all the default themes are gone. Ive tried reinstalling quite a lot of gnome-related stuff i found in synaptic, installing new themes - nothing changes, the only theme present in the theme tab is the custom one.
2) preferences in nautilus are grayed out, so i have no access to all those handy icon preferences etc. either. 

If theres any additional info i could give in order to be offered any help, please let me know, tia.

---

### Post by epictetus on 2008-09-03
I am having a very similar problem:

1)  I receive an error message before the login window pops up saying that the file /usr/share/gdm/themes/Human/bottom_bar.svg cannot be opened due to the file type being unrecognized and

2)  When I go to the top menu and select Places > Computer, I get an error message that says

`Couldn't display "computer:".
Nautilus cannot handle computer: locations' .

3)  All of the default themes in Appearance are gone.  The only one remaining is Neutronium Gilouche, which I had installed separately before the problem occurred.


My situation differs in that I could open Control Center (even before fixing the svg issue).

I looked for librsvg-2.22.2, and it does appear to fix the svg problem (issue 1) though I'm still having the issues with Nautilus and the missing themes.

The problem occurred while I was installing Anjuta-2.4.2 and a large number of packages that the configuration script said it required (after I entered ./config into Terminal).

Naaiya, if you have had any more progress in addressing the problem, please (please please) let me know what you did or what advice you received.

If anyone else knows what I might do to fix this, please let me know!  The whole thing is very frustrating as it makes the user interface look similar to Win95/98.  (Barf)

---

### Post by epictetus on 2008-09-04
I don't at all have the technical knowledge to know why this is necessary, but I figured out how to get my themes back.

For some reason, the Appearance manager can only install themes when they are in a package form.  If you've installed a theme through Synaptic, it should be in /usr/share/themes/ as a folder.  If you use the Appearance manager and attempt to "Install..." a new theme and select something like index.theme in one of the theme folders, Appearance won't recognize it as a theme.  However, you can right click on the folder for the theme that you want (say, Human-Clearlooks, the default theme) and select Create Archive.  Make an archive of the folder somewhere that you have read/write access, like your desktop.  Then, in Terminal, change your directory to the desktop (by typing "cd /home/*yourusername*/Desktop/") and then type "sudo mv Human-Clearlooks.tar.gz /usr/share/themes/".  The package should now be in /usr/share/themes/.  Finally, go to the Appearance manager, and select "Install...".  Browse to /usr/share/themes/ and choose Human-Clearlooks.tar.gz.  It should say that the package is installed correctly, and you should now be able to use the theme.

If anyone knows a way to actually *fix* the problem without this workaround, please let me know.

(But I'm still having issues with Nautilus and can't access my Computer, Network, or Trash.)

---

