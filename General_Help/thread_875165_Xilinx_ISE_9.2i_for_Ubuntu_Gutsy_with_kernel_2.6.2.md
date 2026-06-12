---
title: "Xilinx ISE 9.2i for Ubuntu Gutsy with kernel 2.6.22-14-generic"
date: 2008-07-30
forum: General Help
---

### Post by naelmusleh on 2008-07-30
I'm using Ubuntu Gutsy, with kernel version 2.6.22-14-generic. I'm trying to install the Xilinx ISE 9.2i.  I followed the instructions given in the following french article, (translated by google's language feature

[http://translate.google.com/translate?u=http%3A%2F%2Fharded.free.fr%2Fsite%2F%3Fp%3D55+&sl=fr&tl=en&hl=en&ie=UTF-8](http://translate.google.com/translate?u=http%3A%2F%2Fharded.free.fr%2Fsite%2F%3Fp%3D55+&sl=fr&tl=en&hl=en&ie=UTF-8)

and I do download the single file from Xilinx.com, but the article talks about some ".sh" file, and I don't know where this file is, and/or how to get it.

If someone can help me with this I would really appreciate it.

Thank you.

Nael

---

### Post by Shazaam on 2008-07-31
From the page it looks like a zip file. You will need to extract it (right-click or open Archive Manager/File Roller). Once it is extracted you should find the .sh file. Substitute your version number for the one in the instructions and follow the rest of the directions.

---

### Post by naelmusleh on 2008-08-01
I went back to the zip folder, and I extracted it, and found a shell script file, called setup. Well, I tried to run the script file the same way the tutorial said. 

I got this problem and error when I did this:

$ chmod +x setup.sh
$ sudo ./setup.sh

after entering the password

The following error came up:

error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

What am I supposed to do. I tried to do the following but I dunno if it actually helps.

:~/Desktop/Documents/WebPACK_SFD_92i$ sudo updatedb
:~/Desktop/Documents/WebPACK_SFD_92i$ locate libstdc++.so
/usr/lib/libstdc++.so.6
/usr/lib/libstdc++.so.6.0.5
:~/Desktop/WebPACK_SFD_92i$ cd /usr/lib
:/usr/lib$ sudo ln -s libstdc++.so.6.0.4 libstdc++.so.5
:/usr/lib$ sudo ldconfig

Then I went back to the run the setup.sh file and still got the same error as before.

Help please.

Nael

---

### Post by Shazaam on 2008-08-01
Check Synaptic and see if you have libstdc++5 installed.

---

### Post by naelmusleh on 2008-08-01
libstdc++5 is installed. Is there another reason for the error.

---

