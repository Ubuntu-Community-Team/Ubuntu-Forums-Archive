---
title: "How do you change theme engines, and themes?"
date: 2008-09-14
forum: General Help
---

### Post by sexyclient on 2008-09-14
I've been checking out the Ubuntu Incoming Artwork wiki and there are a few themes that I'd love to apply to my own desktop.  The problem is that I have no Idea how to do so...

I'd like to change my theme engine, and theme ([to this one, NewWave]("https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/NewWave")) but I can't figure out how I go about doing that.  Can someone help me out?  I know that it's possible to install a theme by loading it from the "Appearance" system property, but it won't install a new theme engine that way.  I'd like to know how to switch theme engines, and how to switch back to the standard Ubuntu theme engine and theme settings (just in case I mess up, or don't like it).  I figure that one of Linux's strong points is its customization, but my desktop is being wasted as I don't know how to change what I want to.  But I'd like to change that with your help. :)

---

### Post by kokkus on 2008-09-14
On your dekstop, click on Change background, and then on Themes.
GTK 1x, GTK 2x and Metacity themes.

[IMG]http://www.scumbox.com/ubuntu/2.png[/IMG]

---

### Post by sexyclient on 2008-09-15
Thanks for the response, but I can't change the theme engine that way - like say to emerald.  Also, on a side note, I managed to apply the NewWave theme, but the implemention leaves a bit to be desired, so I'm trying to test out other themes (emerald themes).

---

### Post by rigol2000 on 2008-09-18
Hi, I was searching with the same question in mind.  I had used synaptic to install what appeared to be themes.  When I went to the Appearance Preferences, I did not see them.  I went to my Themes directory and they were there, but I didn't know how to activate them.

usr/share/themes

A few minutes ago, after reading kokkus' reply, I was poking around the Appearance Preferences window and discovered how to activate what I had installed via synaptic.

In the Appearance Preferences window, select the Theme tab
Select the Custom theme
Click the Customize button
In the Customize Theme window that pops up, click on the controls.

In my case, these were the themes I installed with synaptic.  To complete the theme, it looks like I need to download the icons and wallpaper separately. If there is a better theme manager out there, I hope someone replies with how to get it going.

Good Luck.  :)

---

### Post by jp73107 on 2008-09-18
In the Themes dialog, if you click customize you can select different gtk engines (controls tab) if you're askin what i'm thinking you're askin

---

### Post by Nitefang on 2008-09-18
Ok I was about to ask how to install themes so I read this and I still have no clue(sorry). So could i get a step by step from the start? I have not done anything yet so if I need to install an app or place a folder or something please incluid in the instructions, or point me in the direction of a tutorial (I already checked some but there must be hundreds)
Here is the theme i want

[http://www.gnome-look.org/content/show.php/Googol?content=89208]("http://www.gnome-look.org/content/show.php/Googol?content=89208")


Thank you very very much!

---

### Post by mc4100 on 2008-09-18
> **Nitefang said:**
> Ok I was about to ask how to install themes so I read this and I still have no clue(sorry). So could i get a step by step from the start? I have not done anything yet so if I need to install an app or place a folder or something please incluid in the instructions, or point me in the direction of a tutorial (I already checked some but there must be hundreds)
Here is the theme i want

[http://www.gnome-look.org/content/show.php/Googol?content=89208]("http://www.gnome-look.org/content/show.php/Googol?content=89208")


Thank you very very much!
This is just a metacity theme (Meaning only the window decorations will be themed!), but simply download the file (.tar.gz), and drag it into the appearance window. Now you'll have to customize an already existing theme -- for example clearlooks, so click the customize button, and then the Window Border tab, and find the "googol" decorations.

Edit:
Sexyclient, if you want the NewWave theme:
[http://www.gnome-look.org/content/download.php?content=87134](http://www.gnome-look.org/content/download.php?content=87134)
Find the download (.tar.gz), right-click -> extract here
You'll have a new folder "New Wave Pack 0.5.10"
Open that folder, find new-wav0510.tar.gz -- drag **this archive** into the appearance window.

---

### Post by Nitefang on 2008-09-19
> **mc4100 said:**
> This is just a metacity theme (Meaning only the window decorations will be themed!), but simply download the file (.tar.gz), and drag it into the appearance window. Now you'll have to customize an already existing theme -- for example clearlooks, so click the customize button, and then the Window Border tab, and find the "googol" decorations.

o ok thank you. So all metacity themes are just window decorations. What type are more. You mentioned emerald what all does that change?

 Thanks again for asking all of my newbie questions, once I get better with linux Ill make sure i give back to this great community!

---

### Post by mc4100 on 2008-09-19
> **Nitefang said:**
> o ok thank you. So all metacity themes are just window decorations. What type are more. You mentioned emerald what all does that change?

 Thanks again for asking all of my newbie questions, once I get better with linux Ill make sure i give back to this great community!

**Metacity** is a window manager, it's shipped by default because it's lightweight and works on many different computers, the author of it says, "[A] Boring window manager for the adult in you." 

**Compiz** is a far more bleeding-edge, up-to-date window manager, with fancy effects, and ...
**Emerald**, sort of bleeding-edge, it's a Window Decorator which works together with Compiz, and also is favored because it can do fancier things, and is highly configurable. 
It can be installed by opening a terminal (Applications -> Accessories), and typing:
```
sudo apt-get install emerald
```

Bear in mind that these are only window managers, and while they can do fancy things with [compositing]("http://en.wikipedia.org/wiki/Compositing_window_manager"), they still are only manager of the **windows**, not their contents; that is up to [GTK+]("http://en.wikipedia.org/wiki/Widget_toolkit")
If you want to change the buttons, scrollbars, text-fields, then you will need a [GTK 2.x theme]("http://www.gnome-look.org/index.php?xcontentmode=100").
To install one of these themes, generally you download a ".tar.gz", and just drag it into the Appearance application, however some of those special ".tar.gz" archives are contained within **other** .tar.gz archives, so they can include extra things like Login Window themes, and still be easy to download in one go.
So it's always a good idea to look at the notes the Author has written about installing.

---

### Post by Nitefang on 2008-09-19
That helps a lot, thank you. That is exactly what I needed to know. But after I posted my last question i found another theme that I want. It is from a Compiz Theme website so i think I can use it but it requires certain things.
here is the link so you can see exactly what I mean


[http://www.compiz-themes.org/content/show.php/Crystal?content=13969]("http://www.compiz-themes.org/content/show.php/Crystal?content=13969")

I know it must get annoying having another question asked when you just answered one but you really are helping me and this will be my last one, promise!

  Thanks again!

---

### Post by Ms_Angel_D on 2008-09-19
In add/remove programs Search for compiz then install Advanced Desktop Effects Settings (ccsm) and the compiz fusion icon. Those two things will allow you to configure desktop effects. Launch the Icon and it will allow you to access theme settings for emerald.

The crystal theme is available in the synaptic package manager search for kwin-style-crystal

---

