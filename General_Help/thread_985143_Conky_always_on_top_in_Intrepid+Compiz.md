---
title: "Conky always on top in Intrepid+Compiz"
date: 2008-11-17
forum: General Help
---

### Post by sssimon on 2008-11-17
I can't get conky to work with compiz on Intrepid. The conky window is always on top. If I start it from the terminal at first it's below other windows, but after some time it's above them.

This is from my .conkyrc:
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_page
double_buffer yes

---

### Post by binbash on 2008-11-17
It was working perfect at me BUT after this i am getting near same thing as you : 

IF you add conky to your startup it is on top of ALL windows, but if you kill conky and start it, it is normal.Weird

---

### Post by sssimon on 2008-11-19
I have changed the following line in the configuration file:
own_window_type normal

It seems to work better now.

---

### Post by duanedesign on 2008-11-21
after installing Conky this is what I did to my .conkyrc file to make it appear in the background with a transparent window and to align it to the right hand side of the screen so it does not cover your icons.

background yes
own_window no
own_window_transparent yes
double_buffer yes
alignment top_right

here is a blog post on installing Conky.

---

### Post by sssimon on 2008-11-21
> **duanedesign said:**
> after installing Conky this is what I did to my .conkyrc file to make it appear in the background with a transparent window and to align it to the right hand side of the screen so it does not cover your icons.

background yes
own_window no
own_window_transparent yes
double_buffer yes
alignment top_right

here is a blog post on installing Conky.

This doesn't work for me - conky doesn't show up on the desktop.

---

### Post by duanedesign on 2008-11-22
hmm. have you tried own_window_type desktop

these links might be usefull-

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865) (examples of .conkyrc file)

[http://conky.sourceforge.net/faq.html](http://conky.sourceforge.net/faq.html) (this has solutions to common problems)

---

### Post by sssimon on 2008-12-09
> **duanedesign said:**
> hmm. have you tried own_window_type desktop


Yes, I have tried that. It doesn't work. Conky stays on top.

Only "own_window_type normal" works OK.

---

### Post by Forlong on 2008-12-09
If all else fails, you can use the **Window Rules** plugin of Compiz Fusion.

If you are having troubles setting it up, let me know. I don't use Conky myself, though.

---

### Post by fukid on 2009-03-23
> **Forlong said:**
> If all else fails, you can use the **Window Rules** plugin of Compiz Fusion.

If you are having troubles setting it up, let me know. I don't use Conky myself, though.

what should i type in the match window??

---

### Post by Forlong on 2009-03-23
I'll install conky and let you know later in the day.

Please bump this thread if I forget about it.

---

### Post by squid636 on 2011-02-24
I had this problem with my conky configuration too.  Everytime I clicked on the title bar in chrome conky would change from being always below my open windows to always above.  I fixed it by using the suggestion from above.  Go into compiz and enable the widows rules plugin.  Then open your conkyrc file and change your ```
own_window_type normal
``` and save.  This will make a window that you can maniuplate on your desktop.  Now go back to compiz and to the windows rules plugin settings.  On the first tab "Matches"select ```
Below
``` and then click on the plus symbol.  Select window name and then grab.  Now go down to your conky window and click on it somewhere in the window. The Below function should now be filled in with the words ```
name=
``` so click on back and close to exit compiz.  Now go back to your conkyrc file and change your window type to override and save. Enjoy.

---

