---
title: "i need help with codes"
date: 2008-11-11
forum: General Help
---

### Post by rayz321 on 2008-11-11
ok i just downloaded pacasa beats for ubuntu how do i get the code to run in the terminal:confused:

---

### Post by taurus on 2008-11-11
Is it a binary or do you have to unpack and build it first?  If not sure, post the exact name of the file or where you downloaded it.

---

### Post by phidia on 2008-11-11
You might want to provide more info on that package. What format is it in and did you unpack it? If it was in tar.gz format unpack it by right clciking and selecting extract then look at the README file.

---

### Post by rayz321 on 2008-11-11
it was in deb and here is a link [http://picasa.google.com/linux/download.html#picasa30]("http://picasa.google.com/linux/download.html#picasa30")

---

### Post by taurus on 2008-11-11
Make sure you are in the directory where that file is.  Then install it with

```
sudo dpkg -i filename.deb
```

Replace filename.deb with picasa_3.0-current_i386.deb if that is the one that you downloaded.

---

### Post by rayz321 on 2008-11-11
i got a error

---

### Post by taurus on 2008-11-11
And would you mind sharing that error message?

Picasa should be available from the repos so search for it in System -> Administration -> Synaptic Package Manager.

---

### Post by rayz321 on 2008-11-11
this is the error

---

### Post by Tony Flury on 2008-11-11
The error message implies that the deb file is not in the same directory that you are currently in 

```

ls *.deb

```

Will tell you all of the deb files in your current directory.

Did you download the deb to your Desktop - if so :

```

mv ~/Desktop/picasa_3.0-current_i386.deb ~/picasa_3.0-current_i386.deb 

```

will move it to your home folder 

and you can then use 
```

sudo dpkg -i picasa_3.0-current_i386.deb

```

to unpack and install it

---

### Post by rayz321 on 2008-11-11
omg thanks for the help that war really good

---

