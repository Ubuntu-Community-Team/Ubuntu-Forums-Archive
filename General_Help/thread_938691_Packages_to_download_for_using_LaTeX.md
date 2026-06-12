---
title: "Packages to download for using LaTeX"
date: 2008-10-05
forum: General Help
---

### Post by 7raTEYdCql on 2008-10-05
I have downloaded the 'texlive-latex-base' package. Are there any other important packages which i will need to install for doing comprehensive latex stuff.

---

### Post by mali2297 on 2008-10-05
I would recommend to install the meta package **texlive** which besides texlive-latex-base also includes texlive-fonts-recommended and texlive-latex-recommended. If you want to make presentations, I suggest installing **latex-beamer** as well.

Then there's the choice of editor...

---

### Post by Idefix82 on 2008-10-05
Also, if you want to use Gedit as your editor, there is a fantastic LaTeX plugin (just google for it) with code completion which even works with included bibtex files, predefined scripts for compilation and many other useful things.
If you want to use the predefined compilation scripts you also need to install rubber from the repositories.

---

### Post by tacutu on 2008-10-05
texlive-latex-extra, not necessary but recommended if you need more than the basic latex installation.

---

### Post by 7raTEYdCql on 2008-10-05
How is lyx as a latex editor. Is it still recommended to code for latex rather than using a gui?
I have downloaded the gedit latex plugin. How do i activate it?

---

### Post by Idefix82 on 2008-10-05
Go to Edit->Preferences and tick the box next to the Latex plugin.

Personally, I think that it takes much longer to create Latex files with a GUI than with a text editor, once you know the most common commands (which may well take some time to learn). The gedit latex plugin will offer you buttons for the most used commands like tables, lists and some more, once you tell it that you are editing a latex file (ie save it with the .tex extension).

Edit: sorry, I should have said that you have to unpack the downloaded files and copy them into the ~/.gnome2/gedit/plugins directory first. Create it if it doesn't exist yet.

---

### Post by schuster on 2008-10-06
Hi

im a n00b ubuntu user. im trying to install texlive on my ubuntu. I got the Universe repository enabled. i type in the following command:

sudo aptget install texlive-full

then it says

couldn't find package.

help?

---

### Post by schuster on 2008-10-06
had to post again to subscribe.

---

### Post by tacutu on 2008-10-06
try:

```
sudo apt-get install texlive
```

---

### Post by schuster on 2008-10-07
> **tacutu said:**
> try:

```
sudo apt-get install texlive
```

i did. same deal... :(

edit: also, when i go to the add/remove dialog box, i click "reload", and there's an error that doesn't allow it to reload the app list. the error has to do with a refused connection. related, maybe?

---

### Post by Stefan_K on 2008-10-12
Hi,

> **schuster said:**
> 
sudo aptget install texlive-full

there's a small mistake, it's written apt-get, but perhaps it's just a typo in the forum message.

Is your problem already solved now?

Stefan

---

### Post by schuster on 2008-10-13
> **Stefan_K said:**
> Hi,


there's a small mistake, it's written apt-get, but perhaps it's just a typo in the forum message.

Is your problem already solved now?

Stefan

yes, it's solved. thanks.

I got some personal help and had the problem solved. For some unkown reason, it worked for the person that helped me but not for me. 

Thanks anyways!

---

### Post by frisket on 2008-10-14
> **i.mehrzad said:**
> How is lyx as a latex editor. Is it still recommended to code for latex rather than using a gui?
I have downloaded the gedit latex plugin. How do i activate it?

But LyX is pretty good, but its representation isn't able to handle all packages yet, and it is more suited to non-mathematical work. 

Gedit is good, so is Kile, and of course Emacs (the editor of choice).

---

### Post by ad_267 on 2008-10-14
Gedit with the LaTeX plugin is awesome, also vim. What do people here use for handling references? I'm using gnome referencer at the moment (not the repo version) and it's working pretty well for me.

---

### Post by tacutu on 2008-10-14
> **ad_267 said:**
> What do people here for handling references? 

Jabref is my choice. Very cool software.

---

