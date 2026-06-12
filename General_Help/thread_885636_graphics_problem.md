---
title: "graphics problem"
date: 2008-08-10
forum: General Help
---

### Post by virudh on 2008-08-10
I am using ubuntu 8.04 everything is running smoothly with no desktop effects but
On choosing extras option on appearance preference window graphic properties slow down like scrolling,advance desktop effects,windows minimization and all.


plz help me to fix this problem..

---

### Post by gjoellee on 2008-08-10
you can fix xorg from this command:
```
sudo shutdown now
```[U][I][B][COLOR=Red]THIS WILL MAKE YOU GO TO A TEXT BASED "PLACE SO READ THE REST OF THE POST BEFORE USING THE COMMAND![/COLOR]
[/B][/I][/U]
You will see a menu, and one of the options have something with Xorg to do, it is called something with "xorg" in the name.
When finished with what you want to do, do a normal boot to get away from the text based
"place"

---

### Post by overdrank on 2008-08-10
> **virudh said:**
> I am using ubuntu 8.04 everything is running smoothly with no desktop effects but
On choosing extras option on appearance preference window graphic properties slow down like scrolling,advance desktop effects,windows minimization and all.
I have tried to reconfigure xserver by using following script
dpkg-reconfigure -phigh xserver-xorg
 but no improvement was there

plz help me to fix this problem..

Hi and what is the model of the graphics card?

---

### Post by overdrank on 2008-08-10
> **gjoellee said:**
> you can fix xorg from this command:
```
sudo shutdown now
```[U][I][B][COLOR=Red]THIS WILL MAKE YOU GO TO A TEXT BASED "PLACE SO READ THE REST OF THE POST BEFORE USING THE COMMAND![/COLOR]
[/B][/I][/U]
You will see a menu, and one of the options have something with Xorg to do, it is called something with "xorg" in the name.
When finished with what you want to do, do a normal boot to get away from the text based
"place"

Hi and the file is called /etc/X11/xorg.conf how will the shutdown command bring the op to edit this file?

---

### Post by Linux&amp;Gsus on 2008-08-10
Hi virudh.
Maybe tell us a little about your Hardware you are using. What video card, etc are you using. Just want to make sure that your computer can handle the extra workload.
At least I have some older computers around and all run just fine. But they can't handle things like compiz at all.

Cheers.

---

### Post by virudh on 2008-08-10
hi! i am using intel graphics media accelerator 950,1 GB RAM ,P4 3.00GHz processor

---

### Post by overdrank on 2008-08-10
> **virudh said:**
> hi! i am using intel graphics media accelerator 950

Ok the intel graphics are usually installed with ubuntu. You may look at the FAQ's link in my signature and try compiz-check as this helped me.
Edit how much memory on the system could cause some issues also. :)

---

### Post by virudh on 2008-08-10
i have read all dat in the link but it is slow now also..
ok i am sry dat i didnt mention dat i am using ubuntu 8.04 since june but its since last week this problem has arrived.

---

### Post by overdrank on 2008-08-11
> **virudh said:**
> i have read all dat in the link but it is slow now also..
ok i am sry dat i didnt mention dat i am using ubuntu 8.04 since june but its since last week this problem has arrived.

Ok well the compiz-check can maybe help you solve the issues
[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

