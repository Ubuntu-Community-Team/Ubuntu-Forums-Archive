---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the p"
date: 2008-08-19
forum: General Help
---

### Post by robsie on 2008-08-19
now when i run this in a terminal i get: dpkg: parse error, in file `/var/lib/dpkg/updates/0003' near line 1:
 newline in field name `#padding'

does anyone know how to help ??

---

### Post by Ryadt on 2008-08-19
> **robsie said:**
> now when i run this in a terminal i get: dpkg: parse error, in file `/var/lib/dpkg/updates/0003' near line 1:
 newline in field name `#padding'

does anyone know how to help ??

```
sudo dpkg --configure -a
```

---

### Post by robsie on 2008-08-19
ive done that but i get that come up after               /var/lib/dpkg/updates/0003' near line 1:
newline in field name `#padding'

---

### Post by Ryadt on 2008-08-19
> **robsie said:**
> ive done that but i get that come up after               /var/lib/dpkg/updates/0003' near line 1:
newline in field name `#padding'

Try ```
nano /var/lib/dpkg/updates/0003
```
then again
```
sudo dpkg --configure -a
```

---

### Post by robsie on 2008-08-19
that didn't work....      dont worry i found a solution elsewere

---

### Post by coffeecat on 2008-08-19
> **robsie said:**
>       dont worry i found a solution elsewere

And are you going to share this so that others can benefit?

---

### Post by Gondee on 2008-08-19
When that happend to me my boot partiton was out of space

---

### Post by kcpoole on 2008-11-25
> **robsie said:**
> that didn't work....      dont worry i found a solution elsewere

So where is the answer?
Typical. people come here and use the knowledge, but do not bother to give back! dickhead!
 
I have the same issue as my boot partition ran out of disk space

---

### Post by ExodusP on 2009-04-15
This is an old post, but I had the same problem so others may as well.  My solution was to open the given file in vim, then remove all the #padding lines.  In this case it would be...

```
sudo vim /var/lib/dpkg/updates/0003
```

Then remove all the lines that have #padding (There were about 25 in my case).

Then run:
```
sudo dpkg --configure -a
```

---

### Post by solvision on 2009-07-19
Hey Guys

OK i had this same error. Computer froze while updating.

I tried all the fixes i could find (sudo nano /var/lib/dpkg/updates/0012) which didn't work. Kept getting a parse error msg on running: sudo dpkg --configure -a

People had mentioned their being padding in their broken files, but i couldn't find any in mine. When i saw mine it was just gibberish.

I navigated to the /var/lib/dpkg/updates/ directory and saw that the last 3 files were "unknown" in file type. So i then deleted them from within the terminal:

cd /var/lib/dpkg/updates/
ls
sudo rm 0012
sudo rm 0013
sudo rm tmp.i

then ran:
sudo dpkg --configure -a 

without problems.

Hope this helps.

---

