---
title: "My desktop became completely unaccessible, please Help!!"
date: 2008-11-09
forum: General Help
---

### Post by castawaybcn on 2008-11-09
Hi,

all of the sudden all my desktop icons dissapeared and my home folder keeps showing up and closing itself on an infinite loop.

I can access folders and programs from the panel and cairo-dock, but when I go to the desktop one it shows and closes in a split second. Also, nautilus right click does not work at all on an empty desktop.

Most strangely, I opened the terminal and launched nautilus as root, as I browsed for my home desktop it closed and... Changed my wallpaper!!

Restarting X or rebooting does not do the trick either :(

I have Hardy with gnome and Compiz. Everything worked just fine until now.

Please help, I don't know what to do and this is very, but very, annoying.

Any suggestions will be highly appreciated

---

### Post by aikiwolfie on 2008-11-09
Personally I'd take the sledge hammer approach. Boot into your PC with the Ubuntu CD/DVD and back up all your files. All the important stuff in your home folder. Then reinstall Ubuntu.

---

### Post by castawaybcn on 2008-11-09
dude, that also occurred to me, but I was wondering if there is any other option, or at least some hints about where I should be looking into (logs, error messages, etc. )
Also it is not only the files, but tons of packages I do not want to reinstall.

---

### Post by castawaybcn on 2008-11-09
I found what it was. Understanding why is a completely different issue though.
I started thinking what I was doing when the whole problem started and remembered I was downloading some svgs for a theme I am working on. Went to the console and moved them somewhere else. That did the trick.
Looking closely I found one of the files had a double svg extension, I think this may be the problematic one. Here's a link to the file in case any of you want to reproduce the bug.

[http://openclipart.org/people/dhartman/dhartman_fe-emboss.svg.svg](http://openclipart.org/people/dhartman/dhartman_fe-emboss.svg.svg)

Should I report this to gnome? And if so, where?

---

### Post by castawaybcn on 2008-11-09
I stay corrected, actually this is the file that made the whole thing go bonkers:
[http://openclipart.org/people/Chrisdesign/Chrisdesign_Brushed_Metal_Filter.svg](http://openclipart.org/people/Chrisdesign/Chrisdesign_Brushed_Metal_Filter.svg)

Whichever folder containing this file becomes inaccessible, at least in gnome.

Hope this helps someone.

---

### Post by soro2005 on 2008-11-09
I would think it's because of a preview/thumbnail generation that is failing and crashing nautilus. --> Nautilus restarts with the Home folder, and tries to generate the same thumbnail. --> the same crash again. Probably, the svg is screwed up, or a weird format.

---

