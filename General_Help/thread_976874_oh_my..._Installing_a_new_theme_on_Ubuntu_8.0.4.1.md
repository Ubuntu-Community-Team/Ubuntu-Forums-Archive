---
title: "oh my... Installing a new theme on Ubuntu 8.0.4.1"
date: 2008-11-09
forum: General Help
---

### Post by StStiffy on 2008-11-09
Hi guys.

As all noobs I begin this by apologizing for my complete (thankfully something is complete...) lack of Linux knowledge.
Finally, after years of frustration and boredom in the MS (can I say that word in here?) universe, I broke out and came running to Ubuntu.

Alas, I cannot say that my first meeting with Ubuntu is a very plesant one so far, but this is obviously caused by my own confusion (I must "unlearn what I have learned" I guess...)

Anyways; I'm trying to do something as "simple" as installing a new desktop theme on my computer (ouch, I have an Intel graphics card, so it's not to fancy...).
I've tried installing Emerald without any effect (the ******* did install and I could even select my theme Black Ice that I downloaded, but nothing happened) and I've tried searching the net without any results.
Most posts seems to think I actually know what I'm doing yet...  :-)

I tried the CCSM (Compiz Config Settings Manager), but this does in no way whatsoever allow me to install a downloaded theme.

Thought I'd try to make my Ubuntu even more sweet before continuing working on it.

Any help, Please???

---

### Post by cl0ckwork on 2008-11-09
have you tried going System->Prefs->appearance and using the install button?

and emerald needs a **.emerald file to use with, and it only skins the window borders and title bar

---

### Post by GeorgeMurango on 2008-11-09
Emerald does nothing until you use the terminal to replace the default metacity themes. To do it once, hit alt+F2 hen type in: emerald --replace    

To make this happen automatically, add the command to the sessions menu in system->administration->sessions

---

### Post by StStiffy on 2008-11-10
Well, I tried Install button from System - Pref - Apperance, but it doesn't recognize the emerald file. Doesn't even see it unless I select All File Types. When I select it then I get an error reading "There was an error installing the selected file" and "'70284-Dark Ice.emerald' does not appear to be a valid theme.".

Thanks in advance you guys...

---

### Post by StStiffy on 2008-11-10
> **GeorgeMurango said:**
> Emerald does nothing until you use the terminal to replace the default metacity themes. To do it once, hit alt+F2 hen type in: emerald --replace    

To make this happen automatically, add the command to the sessions menu in system->administration->sessions

Actually I tried "emerald --replace" from the console yesterday and nothing happened even after restart, but now for some reason my windows are grey (dark ice) while the rest of my desktop is the same as before (???).
It got worse...  :-/

Any ideas on how to get my desktop to look like Dark Ice (or similar) with the bottom toolbar and the desktop background, etc.?

---

### Post by kg87 on 2008-11-10
to solve your toolbar issues, right click on the toolbar, go to properties, and select the image option..

in terms of the background.. Im pretty certain you've got to have the image seperate from the emerald file (i found that with an XP-style theme), then just right click the image, and set that as desktop background. Or alternatively, right click the the desktop, go to properties and select the image from there. 

i may be wrong as i dont have it infront of me ATM, and i wouldn't class myself as an experienced user. 

> Actually I tried "emerald --replace" from the console yesterday and nothing happened even after restart, but now for some reason my windows are grey (dark ice) while the rest of my desktop is the same as before (???).

I do know emerald is just a window decoration manager. So interms of desktop background, i think it has to be changed manually!

(please dont flame me if im wrong!!!)

---

### Post by DaSilva on 2008-11-10
I am new to Ubuntu (using 8.10) and Compiz.
Compiz is running fine here. Now I want to install a different theme for the desktop. GTK2 themes are easy to change but Emerald seems to have more possibilities. The problem is that I am a little bit confused about Emerald and Metacity. What is the difference between them? Because at deviantART are only GTK2 and Metacity themes and on compiz-themes.org are Metacity AND Emerald themes. Can I install both of them after "emerald --replace"?
Thanks.

---

### Post by cl0ckwork on 2008-11-10
> **DaSilva said:**
> I am new to Ubuntu (using 8.10) and Compiz.
Compiz is running fine here. Now I want to install a different theme for the desktop. GTK2 themes are easy to change but Emerald seems to have more possibilities. The problem is that I am a little bit confused about Emerald and Metacity. What is the difference between them? Because at deviantART are only GTK2 and Metacity themes and on compiz-themes.org are Metacity AND Emerald themes. Can I install both of them after "emerald --replace"?
Thanks.

Metacity is the default theme manager used by gnome. it skins everything, window decoration, gnome panel, any GTK applications, pretty much anything native to GNOME.

emerald is comtolled by compiz fusion and is only the window decorations (borders and titlebar and such) it replaces the metacity style BUT only for window decorations

for themes go to [gnome-look]("http://www.gnome-look.org/"), they have much more than deviantart.  havent found many good themes from dA

and yes, both have to be used to get a fully skinned desktop

---

### Post by Idefix82 on 2008-11-10
> **StStiffy said:**
> Actually I tried "emerald --replace" from the console yesterday and nothing happened even after restart, but now for some reason my windows are grey (dark ice) while the rest of my desktop is the same as before (???).
It got worse...  :-/

Any ideas on how to get my desktop to look like Dark Ice (or similar) with the bottom toolbar and the desktop background, etc.?

StStiffy, the main thing you are looking for is a GTK2 theme. That will control the look of your windows, control elements and so on. When you have downloaded a gtk2 theme, it is very easy to install it. Decompress it if it's compressed so that you obtain a tar ball, open the System->Preferences->Appearance dialog and just drag the tar ball onto the dialog.
Now you can change various other things separately: your desktop wallpaper is changed under the corresponding tab in the same Appearance window. Your icon theme is also changed separately. If you want to install a new icon theme, create a subfolder in your home folder, called .icons, download an icon theme, decompress it if it is compressed, so that you get a folder with various subfolders and copy this folder into the .icons directory you have created. Now, you can choose this icon theme in the icons tab of the Appearance dialog.
I hope, this helps. If anything is unclear, ask away.

---

### Post by DaSilva on 2008-11-10
> **cl0ckwork said:**
> Metacity is the default theme manager used by gnome. it skins everything, window decoration, gnome panel, any GTK applications, pretty much anything native to GNOME.

emerald is comtolled by compiz fusion and is only the window decorations (borders and titlebar and such) it replaces the metacity style BUT only for window decorations

for themes go to [gnome-look]("http://www.gnome-look.org/"), they have much more than deviantart.  havent found many good themes from dA

and yes, both have to be used to get a fully skinned desktop

OK, thanks.
And what is meant with "GTK 2.x" themes?
Isn't this the same as Metacity?

---

### Post by cl0ckwork on 2008-11-10
> **DaSilva said:**
> OK, thanks.
And what is meant with "GTK 2.x" themes?
Isn't this the same as Metacity?

sorry my mistake >_<
metacity is what has been replaced by emerald.

you need the GTK themes to skin your desktop, as i told you metacity did earlier (oops!)

it was a tough morning :lolflag:

---

### Post by StStiffy on 2008-11-11
> **Idefix82 said:**
> StStiffy, the main thing you are looking for is a GTK2 theme. That will control the look of your windows, control elements and so on. When you have downloaded a gtk2 theme, it is very easy to install it. Decompress it if it's compressed so that you obtain a tar ball, open the System->Preferences->Appearance dialog and just drag the tar ball onto the dialog.
Now you can change various other things separately: your desktop wallpaper is changed under the corresponding tab in the same Appearance window. Your icon theme is also changed separately. If you want to install a new icon theme, create a subfolder in your home folder, called .icons, download an icon theme, decompress it if it is compressed, so that you get a folder with various subfolders and copy this folder into the .icons directory you have created. Now, you can choose this icon theme in the icons tab of the Appearance dialog.
I hope, this helps. If anything is unclear, ask away.

Thanks a lot, Idefix!
That, put into one sentence, actually cleared things up. Let you know if I have more of these issues.  :-)

---

