---
title: "Console as Background"
date: 2008-08-17
forum: General Help
---

### Post by soxs on 2008-08-17
Is there a way to make my background a console (or even multiple consoles?) (Note: No compiz plx, no screenlets fuss)

---

### Post by bingoUV on 2008-08-17
What do you mean by console?

1. A graphical terminal emulator? e.g. xterm, gnome-terminal etc.
2. The command line environment you get when you press ctrl-alt-F1 ?
3. Any interface to operate a machine?


What do you mean by background?
1. A static image, which does not interact i.e. a picture of a console(any of the 3 meanings above) as a wallpaper?
2. When you minimize all applications, you want the console to be shown. Do you want to be able to minimize this "background" to reveal, maybe a wallpaper?

---

### Post by fooman on 2008-08-17
i used devilspie to do that. ...pretty cool.

haven't tried it in awhile,  but this is the thread i used as a guide:

[http://ubuntuforums.org/showthread.php?t=202249&highlight=devilspie](http://ubuntuforums.org/showthread.php?t=202249&highlight=devilspie)

its a bit tricky,  but worked well for me once i got it right.

---

### Post by ooobuntooo on 2008-08-17
Screenlets works perfectly!

[http://www.gnome-look.org/content/show.php/Terminal+Screenlet?content=74844](http://www.gnome-look.org/content/show.php/Terminal+Screenlet?content=74844)

---

### Post by soxs on 2008-08-17
> **ooobuntooo said:**
> Screenlets works perfectly!

[http://www.gnome-look.org/content/show.php/Terminal+Screenlet?content=74844](http://www.gnome-look.org/content/show.php/Terminal+Screenlet?content=74844)

I don't want to use screenlets, but if nothing else will work, I will have to stick with that


> **bingoUV said:**
> What do you mean by console?

1. A graphical terminal emulator? e.g. xterm, gnome-terminal etc.
2. The command line environment you get when you press ctrl-alt-F1 ?
3. Any interface to operate a machine?

like gnome-terminal, just in background/ and without borders

> **bingoUV said:**
> 
What do you mean by background?
1. A static image, which does not interact i.e. a picture of a console(any of the 3 meanings above) as a wallpaper?
2. When you minimize all applications, you want the console to be shown. Do you want to be able to minimize this "background" to reveal, maybe a wallpaper?
Like the standard wallpaper, but not being a wallpaper but a console

---

### Post by x1a4 on 2008-08-17
Hi,

On my system I run a terminal inside 'alltray'--a tool that puts applications inside the tray.  I also run the terminal without borders which makes it look as if the terminal was on the desktop. I have numerous screenshots showing this [here]("http://hex1a4.net/xubuntu/screenshots/?gallery=_default-gui_xfce/")
At least one has [two ]("http://hex1a4.net/xubuntu/screenshots/?cmd=imageform&gallery=_default-gui_xfce/&image=Screenshot-hardy5-newboot-afterlogin.jpg") terminals on the desktop, several have [just one]("http://hex1a4.net/xubuntu/screenshots/?cmd=imageform&gallery=_default-gui_xfce/&image=Screenshot-hardy5_5-19jul2008.jpg")

I do it like so:
```

/usr/bin/alltray -x --sticky --geometry 500x955-0+90 --show --skip-taskbar --no-alltray "xfce4-terminal --working-directory=/home/hex1a4 --hide-menubar --hide-borders --hide-toolbars"

```
If the terminal you want to use doesn't have a means to remove borders, use devilspie.

devilspie and its GUI gdevilspie are in the repositories.

---

