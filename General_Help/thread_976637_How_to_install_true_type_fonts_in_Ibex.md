---
title: "How to install true type fonts in Ibex?"
date: 2008-11-09
forum: General Help
---

### Post by Afkpuz on 2008-11-09
Ibex seems to not follow the same method for installing true type fonts than previous versions.  

~/.fonts doesn't exist and there is no "goto fonts folder" option that I can find.  Can anyone help?

---

### Post by 73ckn797 on 2008-11-09
I have installed them through Synaptics/msttfonts in Intrepid. The Applications/Add/Remove also lists the Microsoft font package.

---

### Post by BUSHYBOB on 2008-11-09
If ~/.fonts doesn't exist, just create it.

---

### Post by Afkpuz on 2008-11-09
But does it do any good to create a ./fonts folder?  Is ibex even set up to function that way?  

P.S. I have downloaded some truetype fonts that I know are not in the repos.  Otherwise, I'd use synaptic

---

### Post by ciscosurfer on 2008-11-09
> **Afkpuz said:**
> But does it do any good to create a ./fonts folder?  Is ibex even set up to function that way?  

P.S. I have downloaded some truetype fonts that I know are not in the repos.  Otherwise, I'd use synapticYou're good to go.  Create ~/.fonts, put 'em in there, then run```
fc-cache -fv ~/.fonts
```Check any application that uses or provides for different font selection (Applications > Accessories > Character Map is a good place to check), and your new fonts will show up.  You can do the same if you want to place your fonts in say /usr/share/fonts/truetype, etc.

---

### Post by eel on 2009-04-01
I did put some .ttf fonts in urs/share/fonts and BOY did that FF up my whole system! Had to use the live cd to restore the fontsfolder, and i haven't found a way to install fonts without funny side-effects yet. Tried installing a ./fonts folder but that didn't do that much either...

---

### Post by BUSHYBOB on 2009-06-06
The ~ in ~/.fonts is shorthand for your home directory 

i.e. if your username is eel the full path would be /home/eel/.fonts

---

### Post by theozzlives on 2009-06-06
I copied several fonts in /home/ozzie/.fonts and they work just fine, it's just I'm the only user that can use them.

---

