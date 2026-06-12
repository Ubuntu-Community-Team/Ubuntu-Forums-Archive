---
title: "rar-file asks for password at the very end"
date: 2008-11-30
forum: General Help
---

### Post by hachel on 2008-11-30
hello,
Sometimes when I unrar a file protected by a password it starts unpacking until it would normaly be finished and then asks me for the password, and starts unpacking all over again. It will unpack all files eventually, but it always takes twice the time, which is kinda annoying if you unpack 2-3 gb of data.
I use the unrar-nonfree (the free wouldn't unpack at all) package, because that would integrate with the "extract here"-contextmenuitem, not sure if this is the best to use. So if there's a better (non commandline) tool please tell me.
It doesn't happen all the time and I haven't really analyzed when and with which kind of rar files it happens.
It just happend now with a 1 gb rar which contains ~70 split-rarfiles, if thats of any help. 

thanks,

hachel

---

### Post by sonicb00m on 2008-11-30
Did the rar successfully extract when putting in the password?

I've only experienced problems with it asking for a password during extraction when an archive is corrupt.

---

### Post by hachel on 2008-11-30
i did just fine after i put in the password.

---

### Post by hachel on 2008-12-02
i just found out that it only happens with password-protected rar-files that have been split into multiple files. Not multiple rar-files, but one rar-file that has been split into multiple files.
Any ideas?
Which rar-tools do you use? Is it unrar-nonfrees fault? 
thanks,
 hachel

---

### Post by binbash on 2008-12-02
unrar them at terminal : 

unrar e filenameasdasdasd.rar

then put the password there when it asks

---

### Post by hachel on 2008-12-04
i'd rather have a comfortable click click solution

anyway, just now I had a single rarfile and it still asked for the password at the end, so I was wrong about it only happening with split files.
seems to be completely random #-o

---

### Post by raymanlololo on 2008-12-04
Install Winrar under wine. Then use it like if you were in Windows. 

Maybe this solution doesn't like to somebody, but it's easy and it works.

see u

---

### Post by happyhamster on 2008-12-04
> **hachel said:**
> i'd rather have a comfortable click click solution

anyway, just now I had a single rarfile and it still asked for the password at the end, so I was wrong about it only happening with split files.
seems to be completely random #-o
Perhaps the difference is caused by partial encryption. If the file *names* are encrypted as well as the data, you will be prompted for a password immediately (because there can't even be an attempt to decrypt without a password), but if the file or folder names are public then a partial decryption will succeed, until the program notices it can't completely access the data itself. (This is just speculation though, haven't really tested it.)

BTW, you can choose "Open with Archive Manager" --> "Edit" --> "Password", instead of "Extract here" when right-clicking an archive. Not ideal, but it does save some time.

---

### Post by hachel on 2008-12-11
> **happyhamster said:**
> Perhaps the difference is caused by partial encryption. If the file *names* are encrypted as well as the data, you will be prompted for a password immediately (because there can't even be an attempt to decrypt without a password), but if the file or folder names are public then a partial decryption will succeed, until the program notices it can't completely access the data itself. (This is just speculation though, haven't really tested it.)

i think thats it, i tried it with some files and it happend exactly like you said.

Sad...

---

### Post by networm1230 on 2008-12-11
rar files sometimes have are encryption bye the your how made the file to try to bay pass this you may wont to try Winzip to try to open the rar files. warning this mite not work
but it is a shot in the dark hop this helps

---

