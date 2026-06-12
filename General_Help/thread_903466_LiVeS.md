---
title: "LiVeS"
date: 2008-08-28
forum: General Help
---

### Post by metalmaniac248 on 2008-08-28
hi 

i am wanting to install LiVeS video editor on gusty 

i can not find it in synaptic, 

i tried compiling the source and hat didnt work

and i tried the deb but that was not available for gusty

apt-get isnt finding it 

what do i need to do?





thanks

---

### Post by Elfy on 2008-08-28
Have you looked at getdeb - there is a version for hardy, if not maybe you'll need to compile it.

---

### Post by metalmaniac248 on 2008-08-28
yer i tried compiling that didnt work.

and the get deb is for hardy not gusty


i thort i herd some1 say that they'd did it thru apt-get but they had to add a dependency, any idea what that is?

---

### Post by Elfy on 2008-08-28
Sorry - only went looking for you, never used it myself.

What errors do you get when compiling it or did it install but not run? If you get errors post them here but please make sure to put it in code tags - [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse]at the end.

Did you check that you had all the dependencies it gives on the download page, also did you have build-essential installed befreo you started.

---

### Post by metalmaniac248 on 2008-08-28
right 

i extracted the source, which went fine

then configured, that also worked

then make, which seemed to work

finally i did make install, it finished and didnt say anything about any errors, but it does not seem to have installed



any way 

this is the last few lines of the make process


```
make[1]: Leaving directory `/home/guest/Desktop/lives-0.9.9.1/lives-plugins'
Making all in po
make[1]: Entering directory `/home/guest/Desktop/lives-0.9.9.1/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/guest/Desktop/lives-0.9.9.1/po'
make[1]: Entering directory `/home/guest/Desktop/lives-0.9.9.1'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/guest/Desktop/lives-0.9.9.1'
nick@nick-laptop:~/Desktop/lives-0.9.9.1$ 
```

---

