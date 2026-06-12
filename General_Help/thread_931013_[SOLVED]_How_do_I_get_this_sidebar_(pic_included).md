---
title: "[SOLVED] How do I get this sidebar (pic included)?"
date: 2008-09-26
forum: General Help
---

### Post by abeautifulbeat on 2008-09-26
The transluscent bar on the right with system information on it.  I want it!

[http://bp3.blogger.com/_crimgO_xQv0/SDaNlMSDf1I/AAAAAAAAA_4/Z2ExnPqbwYk/s1600-h/My+Desktop.png](http://bp3.blogger.com/_crimgO_xQv0/SDaNlMSDf1I/AAAAAAAAA_4/Z2ExnPqbwYk/s1600-h/My+Desktop.png)

---

### Post by abeautifulbeat on 2008-09-26
(customizing Ubuntu is so fun) :KS

---

### Post by loomsen on 2008-09-26
Thats part of the screenlets...
```

sudo apt-get install screenlets

```

After installing, launch the screenlets manager and start the sidebar screenlet.

---

### Post by JECHO on 2008-09-26
> **abeautifulbeat said:**
> The transluscent bar on the right with system information on it.  I want it!

[http://bp3.blogger.com/_crimgO_xQv0/SDaNlMSDf1I/AAAAAAAAA_4/Z2ExnPqbwYk/s1600-h/My+Desktop.png](http://bp3.blogger.com/_crimgO_xQv0/SDaNlMSDf1I/AAAAAAAAA_4/Z2ExnPqbwYk/s1600-h/My+Desktop.png)



actually i think hes talking about the black transparent bar... in that case it would be conky. 

```
sudo apt-get install conky
```

---

### Post by loomsen on 2008-09-26
Yes he is, but no, its not ;)

It's the sidebar included in the screenlets package. Conky isnt capable of drawing images, just for example...

---

### Post by JECHO on 2008-09-26
> **loomsen said:**
> Yes he is, but no, its not ;)

It's the sidebar included in the screenlets package. Conky isnt capable of drawing images, just for example...


maybe youre right... it looks to me like hes running the screenlets as well as conky

---

### Post by ft23002 on 2008-09-27
> **abeautifulbeat said:**
> The transluscent bar on the right with system information on it.  I want it!

[http://bp3.blogger.com/_crimgO_xQv0/SDaNlMSDf1I/AAAAAAAAA_4/Z2ExnPqbwYk/s1600-h/My+Desktop.png](http://bp3.blogger.com/_crimgO_xQv0/SDaNlMSDf1I/AAAAAAAAA_4/Z2ExnPqbwYk/s1600-h/My+Desktop.png)

Hello,

The black bar & its info is included in Screenlets. Install & Run the manager and choose screenlet-"sys monitor".
Just Installed myself via synaptic package manager. Open spm & search for "screenlets". 2 items should be found, the app itself & documentaion. Check the 2, hit apply and after it installs, you can find the luancher in- system/preferences/screenlets.

---

### Post by abeautifulbeat on 2008-09-30
Thanks for all the replies, guys!  And by the way, it's "she". ;)

---

