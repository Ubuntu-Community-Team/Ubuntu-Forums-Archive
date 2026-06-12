---
title: "[SOLVED] Login gdm theme causing problems"
date: 2008-07-26
forum: General Help
---

### Post by simplebeep on 2008-07-26
Hello.  I just installed the [sunset login theme]("http://tinyurl.com/sunsetgdm/"), and ever since, I have been having some weird login-related problems:

First, I downloaded the package to the desktop, went to the login options, and installed it.  I chose it, and logged out so I could see it.  My screen went black, and put about eight lines of text on the screen, each of them ending with **[OK]**.  The little _ underscore just sat there blinking for about a minute.  I pressed **return**, and the underscore just moved down a line.  I pressed the power button (didn't hold it down), and my computer continued to shut down, just as if I had selected it from the **Quit** dialog.

I started up, and was brought to that ugly "circles" theme.  I logged in, and everything worked fine.  Figuring the theme was defective (and Ubuntu was defaulting to "circles"), I went to change it back to **Human**; but right when I clicked the login window item in the System menu, before the window even appeared, my screen went black again, with the same eight-or-so lines, all **[OK]** again.  I shut down properly, just as before.

So how do I change the theme back?  How do I totally wipe this rogue theme from my system?
Thanks for any advice.

---

### Post by pauper on 2008-07-28
Before gdm login prompt press Ctrl-Alt-F2. Login to text console. Now, simply
remove the offending theme: 

```
ls /usr/share/gdm/themes
sudo rm -rf /usr/share/gdm/themes/Sunset
```

Compare GraphicalTheme values from gdm.conf and gdm.conf-custom, revert custom
value to default from gdm.conf, restart gdm:

```
grep -E ^GraphicalTheme /etc/gdm/gdm.conf
grep -E ^GraphicalTheme /etc/gdm/gdm.conf-custom
sudo nano /etc/gdm/gdm.conf-custom
sudo /etc/init.d/gdm restart
```

When you back in X session, use the virtual console to preview any new theme:

```
sudo apt-get install xnest
gdmflexiserver --xnest
```

It won't open fullscreen though and some items could be displaced. But at
least you'll get an idea whether you can run it or not.

You can always edit particular theme's *.xml file to suit your needs.

---

### Post by simplebeep on 2008-07-29
Thank you very much, pauper.  Your solution worked seamlessly.  I was a little worried, as not all of the GraphicalTheme parameters in the .conf files matched.  But I pushed ahead, restarted GDM, and the Human login popped up!  Hooray!  Login works perfectly now.

For anyone reading this thread who can't quite figure out what all that grepping and pseudo-nanoing is, well, just leave a post here and I'll explain it all in full-gory-unix detail.

---

### Post by lunatico on 2008-07-29
Dude!!!
Thanks!
You totally saved me here with this, nice done!!!
I was playing with different login screens and doing ctrl+alt+backspace to see them and one failed and it was just hanging with the pointer thing waitting and no login screen...
Thanks!

---

