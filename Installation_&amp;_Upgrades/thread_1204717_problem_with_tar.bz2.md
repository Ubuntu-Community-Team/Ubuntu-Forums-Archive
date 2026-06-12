---
title: "problem with tar.bz2"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by sultano on 2009-07-05
Hello 

my problem is I downloaded FireFox 3.5 as tar.bz2 file

then I open the terminal to install

then cd to my desktop (the file in my desktop)

after that I unpack the file with tar xvfj firefox-3.5.tar.bz2

evrything fine 

the I type cd to the unpack file cd  firefox
and it take me there 

now I type ./configure

but it tell me this 

> 
sultan@sultan-laptop:~/Desktop/firefox$ ./configure
bash: ./configure: No such file or directory
so what is the problem?

also i try same way on other file but same problem

I use jaunty and I want learn how to install file in that way 

THANK YOU

---

### Post by ibutho on 2009-07-05
You do not need to run ./configure because Firefox is already built for you. To run firefox, just do ./firefox or click on the icon labeled "firefox" from nautilus or whatever file manager you are using.

---

### Post by sultano on 2009-07-05
> **ibutho said:**
> You do not need to run ./configure because Firefox is already built for you. To run firefox, just do ./firefox or click on the icon labeled "firefox" from nautilus or whatever file manager you are using.

that fierfox 3 I want install 3.5

and want install other tar.bz2

---

### Post by ibutho on 2009-07-05
> **sultano said:**
> that fierfox 3 I want install 3.5

and want install other tar.bz2
Did you try what I said above? You should be able to run Firefox by doing
```
sultan@sultan-laptop:~/Desktop/firefox/firefox
```

---

### Post by sultano on 2009-07-10
thank you it work very good

but how I can install it ???????

---

### Post by ibutho on 2009-07-10
> **sultano said:**
> thank you it work very good

but how I can install it ???????

You just copy the directory called firefox to a location of your choice and then create menu links (or just update them).

---

