---
title: "cannot run script"
date: 2008-11-13
forum: General Help
---

### Post by creta on 2008-11-13
hello to everyone

i am trying to run a script (rapidget) (in order to download from rapidshare
i had no problems till i started to do some chmod staff in order to run
openFOAM. Anyway now every time i try to execute the script i get a message:
sh: Can't open rapidget
Moreover i although i can see the contents of the file where i extracted the script in the graphical interface, whenever i type dir to the directory tha the script is extracted, from the terminal, it doesn't seem to have anything inside.

creta@creta-desktop:~$cd rapidshare
creta@creta-desktop:~/rapidshare$ sh rapidget -f down.txt
sh: Can't open rapidget
creta@creta-desktop:~/rapidshare$ dir
creta@creta-desktop:~/rapidshare$

the rapidget script has
owner:creta
access:r and w
group:creta
access:r
otehers
access:r

and i have allowed executing the programm

....and after posting the prblm
found out that i cannot see the contents from the terminal of any directory i create at my desktop

thanks in advance

---

### Post by taurus on 2008-11-13
Are you sure ~/rapidshare is not an empty directory?

```
ls -la ~/rapidshare
```

---

### Post by creta on 2008-11-13
the result of ls -la ~/rapidshare is
total 8
drwxr-xr-x  2 creta creta 4096 2008-11-01 15:23 .
drwxr-xr-x 74 creta creta 4096 2008-11-13 21:10 ..

:S

---

### Post by taurus on 2008-11-13
I guess you either remove the contain in ~/rapidshare or you have moved them somewhere else.

Run this from a terminal and see what is the output.

```
sudo find / -name rapidget -print
```

---

### Post by creta on 2008-11-13
the  output was 
/home/creta/Desktop/rapidshare/rapidget
so i was not at the correct Desktop folder

thanks a lot taurus

---

### Post by binbash on 2008-11-13
forget that script and navigate to jdownloader.org ;)

---

### Post by creta on 2008-11-13
hmmmm surely will check it out thanks

---

### Post by taurus on 2008-11-13
Actually, it's in ~/Desktop/rapidshare, not ~/rapidshare.

```
cd ~/Desktop/rapidshare
sh rapidget -f down.txt
```

---

