---
title: "Users HOME file being ignored"
date: 2008-08-19
forum: General Help
---

### Post by colobix on 2008-08-19
What is this for an error?
I get this when I login now.
It happend after I took a CD backup with Remastersys.
Plz help.

---

### Post by colobix on 2008-08-20
BUMP
Plz help!

---

### Post by CameO73 on 2008-08-20
Could you give the EXACT error message (i.e. is there a file specifically mentioned)?

I did fnd [this blogpost]("http://mihirknows.blogspot.com/2008/06/homedmrc-file-is-being-ignored-solved.html") that talks about the wrong permissions on your HOME folder (and how to reset them).

---

### Post by colobix on 2008-08-20
I don't remeaber exactly what it said and I can't copy it coz it's in the startup with the login screen.
It says something with sessions and language will not be saved.

---

### Post by Elfy on 2008-08-20
was it along the lines of HOME dmrc being ignored

[http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=home+dmrc+ignored&sa.x=0&sa.y=0](http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=home+dmrc+ignored&sa.x=0&sa.y=0)

[http://ubuntuforums.org/showthread.php?t=758126](http://ubuntuforums.org/showthread.php?t=758126)


Dug from one of the threads

```
sudo chmod 644 .dmrc
sudo chown username .dmrc
sudo chmod 755 /home/username
sudo chown username /home/username
```

---

### Post by CameO73 on 2008-08-20
Just make sure you execute the commands in the above post in your home directory (where the .dmrc file is located). And don't forget to replace **username** with your actual user name (3 times)!

---

### Post by colobix on 2008-08-20
Wow I can't beleve it worked. Thank you SO much you guys.
U r great folks :)

---

### Post by Elfy on 2008-08-20
Welcome - if I'd read the blogpost I wouldn't have posted lol

Can you mark thread solved please

---

