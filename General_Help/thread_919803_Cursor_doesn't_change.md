---
title: "Cursor doesn't change"
date: 2008-09-14
forum: General Help
---

### Post by DOSIX on 2008-09-14
My mouse cursor won't change when i change it in the appearance editor.
however, when it hovers above my firefox window, all of a sudden it shows the new cursor i picked. this is getting extremely annoying to me. i've been dealing with it for months.
any help would be appreciated.

---

### Post by Casper Hansen on 2008-09-14
How did you install the cursor theme? A simple reboot should do it after the installing of the cursor theme.

---

### Post by DOSIX on 2008-09-15
i just dragged it into the appearance editor. i can't uninstall it though.

---

### Post by Casper Hansen on 2008-09-16
> **DOSIX said:**
> i just dragged it into the appearance editor. i can't uninstall it though.

Do you have a link to the cursor theme?

---

### Post by mb_webguy on 2008-09-16
If you're using Compiz effects, you have to set the cursor theme both in Appearances and in the Compiz General plugin.

---

### Post by DOSIX on 2008-09-17
> If you're using Compiz effects, you have to set the cursor theme both in Appearances and in the Compiz General plugin.

how would i do that, ccsm? if so, what menu under ccsm?

---

### Post by mb_webguy on 2008-09-17
Yes, it's under General Options.  In the "Cursor theme" line, type exactly what you have selected for the cursor theme.

---

### Post by NeverHide on 2010-05-19
i have 10.04 and under the general options in compiz there is no "cursor theme" option....plz help i have the same problem with the poster

---

### Post by lanetherif on 2010-05-22
> **NeverHide said:**
> i have 10.04 and under the general options in compiz there is no "cursor theme" option....plz help i have the same problem with the poster

check the post #45 in here:  [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/459647](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/459647)

---

### Post by Mi11z on 2010-10-08
> **lanetherif said:**
> check the post #45 in here:  [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/459647](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/459647)

Thanks, this helped me, just open a terminal and copy and paste:

```
gnome-control-center
```

hit enter and then find the cursor options in the relevant fields.

:)

---

### Post by OvidiuZeicu on 2011-08-23
A more easy solution that worked for me in all tested windows:

[LIST=1]
[*]open System > Preferences > Appearance, make your changes and save the custom profile with a name of your choice;
[*]in the same window press Customize buton and, under Cursor tab, look for the name of your prefered cursor;
[LIST]
[*]another way to find out this (especialy if you just manualy installed a cursor) is to go to /usr/share/icons and look for the folder containing your prefered cursor;
[/LIST]
 
[*]open terminal and type or paste: 
   ```
sudo gedit /etc/alternatives/x-cursor-theme
```
[*]in x-cursor-theme replace DMZ-White (or whatever you have there) with the name of the cursor from step 2 ```
[Icon Theme]
Inherits=Your-Cursor-Name
```
[*]save the file and log out/in
[/LIST]
There is no guarantee that this workaround will work for everybody, but is a very simple workaround that might just work and worth to try before more elaborate and complicated solutions.

---

### Post by drillerccg on 2011-09-28
This worked for me in Ubuntu Natty 11.04. 
I never had any use for eye-candy hence no need to change themes or
cursor icons. That is until my 78 year-old mother-in-law complained
that the cursor was too small. I tried to change the size on default
cursor and it did in some windows but not on desktop or system
windows. The search began and I came across this you tube video that
solved my problem, the link at the end. Here is a step by step of what
I did courtesy of AbhiramH on you tube:

1-Go to [http://gnome-look.org/](http://gnome-look.org/) , click on X11 Mouse Themes in the left
margin, and download a pointer theme you like. I needed a large cursor
so I downloaded Large Mouse Cursor 1.0
 [http://gnome-look.org/content/show.php/Large+Mouse+Cursors?content=140787](http://gnome-look.org/content/show.php/Large+Mouse+Cursors?content=140787)

2-go to download folder and extract to desktop, you now have a folder
on desktop named as the downloaded theme

****MY extracted folder was named Large Mouse Cursor and I had to
rename it Large-Mouse-Cursor (with dashes) to get this to work, it
seems like spaces don't really work in this process. Themes without
spaces worked without renaming.

3-Fire up the terminal, type sudo nautilus, enter password
4- once browsing as root in the file browser, copy the folder on the
desktop and paste to usr/share/icons folder
5-close nautilus and terminal
6- Fire terminal again and type sudo gedit
/usr/share/icons/default/index.theme
7-enter password
8- when the file opens, you will see Inherits=name of your current
pointer theme, change that to Inherits=name of new pointer theme which
is the name of the extracted folder you copied in step 4. Mine was
Inherits=Large-Mouse-Cursors  (again note the lack of space and
addition of dashes)
9-save and exit.
10- now go to system/preferences/appearance, click customize, click
pointer tab, and choose your new pointer theme, and exit
11- shut down and restart. Log in and out did not work for me. That's
it, it should work.

Other than a few exceptions above, I take no credit for this. All the
credit goes to this dude AbhiramH on you tube

[http://www.youtube.com/watch?v=CvS9kh_bMyM](http://www.youtube.com/watch?v=CvS9kh_bMyM)

---

