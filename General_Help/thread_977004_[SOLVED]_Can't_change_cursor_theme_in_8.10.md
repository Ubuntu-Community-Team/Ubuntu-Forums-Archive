---
title: "[SOLVED] Can't change cursor theme in 8.10"
date: 2008-11-09
forum: General Help
---

### Post by sjnims on 2008-11-09
Hi all~

I had some trouble changing the cursor theme from the default to the custom one that I wanted, no matter how many times I tried changing it from the System -> Preferences -> Appearance -> Theme Tab (default) -> Customize -> Pointer menu in my 8.10 64-bit installation of Ubuntu.

I found this tip [in the archives]("http://ubuntuforums.org/showthread.php?t=597855") that I decided to try out. After trying what the thread says and restarting, it worked!

Hope this helps anyone else running into this problem!


Steve

---

### Post by th89 on 2008-11-09
Glad you got it!
Please remeber to mark the thread sovled.

---

### Post by eks on 2008-12-22
> **sjnims said:**
> I found this tip [in the archives]("http://ubuntuforums.org/showthread.php?t=597855") that I decided to try out. After trying what the thread says and restarting, it worked!


That worked for me also, but it took me a little why to find that the Cursor Theme was now inside the General Options of CompizConfig Settings Manager, instead of the old Advanced Effects Desktop Settings.

That was a bit counter-intuitive...

---

### Post by epidenimus on 2008-12-22
The GUI on this task could really be better organized.  I found that extracting and copying (as root) the new cursor folder to my /usr/shared/icons folder allowed me to use my new cursors only if I also installed a theme that linked to it.  If I changed my Compiz General settings, it worked on the desktop, but the cursors reverted back to the default in applications like Firefox.

_**Solution:**_

1.  Download the cursor theme package (usually a .tar.gz file) from your site of choice (e.g.[www.gnome-look.org]("http://www.gnome-look.org")) to an easily accessible location on your computer (desktop or home folder are good picks).  Do not extract or unpack it.

2.  Start the Appearance app by going to **System-->Preferences-->Appearance**.

3.  In the window that pops up titled **Appearance Preferences**, select the **Theme** tab.  Click the [COLOR="Red"]**Install...**[/COLOR].  

4.  Locate the cursor theme package (.tar.gz) you just saved and click **Open**.  This will install the cursor theme on your machine.

5.  To use your cursors, start **Appearance Preferences** by going to **System-->Preferences-->Appearance** then clicking **[COLOR="Red"]Customize[/COLOR]**, then selecting the **[COLOR="Red"]Pointers tab[/COLOR]**.  

You should find your new cursor set as well as all the others listed in this tab.  Select the one you want, and click **Close**.  You should now see the pointer cursor from your new set.

---

