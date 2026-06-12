---
title: "post-update bugs: no UserSwitcher, gdm mess etc"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by rcopper on 2009-10-30
So, I upgraded Ubuntu from 9.04 to 9.10 by means of the alternative iso downloaded through the torrent, everything seems to have gone ok except for the following issues that appeared after reboot:

1) on reboot I get a black screen with the xcfe mouse, then the gdm xubuntu blue screen, and then the login again is not the one I used to have before the update, but some xcfe theme.. (beides gnome I also had xcfe, although was not using it too frequently)
q: how can I fix this so that I have my gnome gdm and login screen?

2) after login I get an error about the FastUserSwitchApplet that failed to load
error: OAFID:GNOME_FastUserSwitchApplet
so now I don't have that button with the user name in the upper right corner... how do I fix this?

3) in Firefox I had TinyMenu plugin which allowed me to reduce the space used by the meny bar by making it smaller and putting it on the samebar with the other buttons (fowrward, home, etc.) now the menu is still tiny but, after restarting firefox the menubar doesn't stay on the same toolbar with the other buttons..

thanks in advance for the help in fixing all this.

---

### Post by cyprys on 2009-11-02
1) You can check this to change background, font and theme of the gdm login:
[http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html](http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html)

Maybe it's somehow similar for XFCE.

2) Same problem here after official upgrade (from Jaunty to Karmic using built-in update manager). No fix yet. Some say "sudo apt-get install --reinstall gnome-applets gnome-applets-data" helps but it didn't work for me.

3) Using Tiny Menu 2.0.1, Firefox 3.5.4 - no problem here.

---

### Post by cyprys on 2009-11-13
2) solution:

```
sudo apt-get install indicator-applet libempathy30 indicator-session indicator-applet-session
```

then context on panel -> Add to Panel... -> Indicator Applet Session -> Add -> Close.

---

