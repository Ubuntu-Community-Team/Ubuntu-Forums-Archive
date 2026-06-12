---
title: "DarkRoom theme for Hardy Heron?"
date: 2008-11-30
forum: General Help
---

### Post by mavix on 2008-11-30
Is there any way to download and install the DarkRoom theme from Intrepid on Hardy? I would use Intrepid, but it doesn't want to work with my dial-up, and I like the theme...
Thanks.

---

### Post by Forlong on 2008-11-30
Add this to your sources:
```
deb http://ppa.launchpad.net/kwwii/ubuntu hardy main
```

It contains the theme under another name (can't remember what it was).

---

### Post by Ivo Moelans on 2008-11-30
There you go. I copied it from my Intrepid system. Simply drag in *System&#8594;Preferences&#8594;Appearance*.

---

### Post by mavix on 2008-11-30
Ah thanks for the file. I'll try it out as soon as I get back to my Ubuntu PC.

---

### Post by OrangeCrate on 2008-11-30
<deleted>

I gave some incorrect info. Sorry.

---

### Post by mavix on 2008-12-01
Thanks it worked!
But it doesn't have the correct colors...
Would someone be so kind as to get the color values for the windows etc for me?

---

### Post by Ivo Moelans on 2008-12-01
For the color values:

Have you tried *Appearance Preferences&#8594;Customize...&#8594;Colors&#8594;Reset to Default*?

---

### Post by mavix on 2008-12-01
I have but it wouldn't make any difference any way because it defaults the controls and colors to 'Raleigh'.

---

### Post by Ivo Moelans on 2008-12-01
Strange. It *should* reset the colors to defaults specified in the theme and it has nothing to do with the controls. I would advise to at least try it again.

---

### Post by mavix on 2008-12-01
It's grayed out. If I change the colors it becomes available, but it just resets it back to the default colors for Raleigh.

---

### Post by Forlong on 2008-12-01
The software source I posted above is the official PPA of the dev that is responsible for Ubuntu's artwork, so it's safe to add it. When I was on Hardy, it worked fine. Give it a try.

---

### Post by mavix on 2008-12-01
> **Forlong said:**
> The software source I posted above is the official PPA of the dev that is responsible for Ubuntu's artwork, so it's safe to add it. When I was on Hardy, it worked fine. Give it a try.
Err... What do I do after I've added it to my sources?
BTW, I physically went to the link, found a package with three themes (Dust, Kin, New Wave). No DarkRoom or anything resembling it though.

---

### Post by mavix on 2008-12-01
Nevermind, I'll just boot up 8.10 from the Live CD and get the colors myself.

---

### Post by mavix on 2008-12-01
I got the colors, and after playing around a bit it seems that the Human-Clearlooks contol works nicely.

---

### Post by Ivo Moelans on 2008-12-01
Sorry, reply was for another thread.

---

### Post by Ivo Moelans on 2008-12-01
I looked into it and there seem to be a few problems with the DarkRoom theme. However, I have 2 *possible* workarounds.

1) Change to another theme and *there* set the colors to default (maybe you will have to change them a little first). This should reset all the themes to their default color.

2) Open a terminal and type:

```
sudo gedit /home/your-name/.themes/DarkRoom/index.theme
```

In the file that opens insert the following line at the end:

```
GtkColorScheme=fg_color:#ebebe0e0cece,bg_color:#4c4c40403939,text_color:#14140d0d0a0a,base_color:#ffffffffffff,selected_fg_color:#ffffffffffff,selected_bg_color:#d7d78e8e4949,tooltip_fg_color:#ffffffffffff,tooltip_bg_color:#47473d3d3737
```

I hope one of these solves your problem.

---

### Post by murdochay on 2009-01-20
> **mavix said:**
> Err... What do I do after I've added it to my sources?
BTW, I physically went to the link, found a package with three themes (Dust, Kin, New Wave). No DarkRoom or anything resembling it though.

You have to install package **human-theme**:
```
sudo apt-get install human-theme
```
and choose **NewHuman** theme from *System -> Preferences -> Appearance*

---

### Post by Machiavelli on 2009-01-25
> **Ivo Moelans said:**
> There you go. I copied it from my Intrepid system. Simply drag in *System&#8594;Preferences&#8594;Appearance*.

thank you!

---

