---
title: "Multiple .Rar Archeives"
date: 2008-07-28
forum: General Help
---

### Post by itztex on 2008-07-28
Recently I just finished downloading around 26 rar archives, each around 100mb in size. 
But the thing is, its an ISO and I need it to extract all of the files. When one file is extracted it asks for the password for the same file (multiple times..).. 

So is there anyway to get them all extracted ? I know you can do it on windows but I am not sure how to do it on Ubuntu..

Any help would be helpful. Thanks.

---

### Post by RuleMaker on 2008-07-28
You must install rar:
```
sudo apt-get install rar
```
Then right click on the first part->Extract here (if prompted for password enter it) and it will extract all parts and merge the files as it should.
If this doesn't happen then something's wrong with your rar files.

---

### Post by itztex on 2008-07-28
Yes I have it already. Thanks for your help though =]

---

### Post by Gun_Smoke on 2008-07-28
or you can do

```
unrar e filename.rar
```

note not -e just plain e

and when it's done, you can clean things up a bit with

```
rm *.rar
```

I haven't tried it but in theory you should be able to pipe it together.. 

```
unrar e filename.rar && rm *.rar
```

---

### Post by geirha on 2008-07-28
> **Gun_Smoke said:**
> 
I haven't tried it but in theory you should be able to pipe it together.. 

```
unrar e filename.rar | rm *.rar
```

No no no. don't do that. That will delete the rar files while extracting them, which will most likely fail. The safe way is 
```
unrar x filename.rar && rm *.rar
``` which will delete the rar files if and only if unrar completed successfully.

@itztex

Sometimes when the archive manager asks for password, it's not because it's password protected, but because one or more of the rar files are corrupt. It's a bug with the archive manager.

---

### Post by Gun_Smoke on 2008-07-28
You are correct.  && is what should be done.

Why x and not e?

---

### Post by geirha on 2008-07-29
> **Gun_Smoke said:**
> Why x and not e?

To keep the proper path.

```
unrar --help
...
<Commands>
  e             Extract files to current directory
...
  x             Extract files with full path

```

---

### Post by Gun_Smoke on 2008-07-29
Nice.. Good to know.

---

