---
title: "How to search through ALL files and folders?"
date: 2008-09-10
forum: General Help
---

### Post by Buttons840 on 2008-09-10
Is there a way to search through ALL files on the Ubuntu file system?  For example, I discovered some huge files hiding out in a trash folder under /root/.local/....

I could just go delete them, but I want a comprehensive way of searching through all folders and files.  I've read a few posts on the subject, but for something so simple it's sometimes hard to get an answer because everyone takes it for granted.  (Like trying to find help on this forum about how to turn your computer on, nobody has written a guide on it, nor do they need to.  You get the point though.)

A graphical display of these files is preferred, but I'm not afraid of the terminal, just a little new.

Thanks.

---

### Post by HermanAB on 2008-09-10
# cd /
# grep -r -e whatever *

---

### Post by HermanAB on 2008-09-10
Grep?
# cd /
# grep -r -e whatever *

---

### Post by kokkus on 2008-09-10
An easier way is in Nautilus, click on show hidden files, and click ctrl+f to search in folders. That goes faster I guess.

---

### Post by SeanHodges on 2008-09-10
Well if it's disk usage you're looking for, what about the Disk Usage Analyser?

It should already be installed, Applications -> Accessories -> Disk Usage Analyser.

Click on the second icon (Entire filesystem) and it will give you a graphical representation of your hard disk usage.

---

### Post by Buttons840 on 2008-09-10
> **kokkus said:**
> An easier way is in Nautilus, click on show hidden files, and click ctrl+f to search in folders. That goes faster I guess.

Is there no way to show which folder they are located in?  Also, I don't think this works, as it didn't find the "Trash" folder located in /root/.local/...

Also, I've seen the disk usage analyzer, very cool.

---

### Post by kokkus on 2008-09-10
To find files located in root u have to login to nautilus as root
gksudo nautilus, show hidden files, search. Check properties for location.

---

### Post by russlar on 2008-09-10
you could also do ```
sudo find / -name insertnamehere
```

---

### Post by Dougie187 on 2008-09-10
you can also use locate. Although you have to update the database before you do this to make sure it is accurate.

```
sudo updatedb
locate filename
```

---

### Post by zorkerz on 2008-10-14
whats the deal with the places->search for files... thingy. It can be set to search the whole filesystem but it can't find anything. Ive been searching for a file on my desktop with its exact name and it still cannot find it.

---

### Post by porchrat on 2008-10-14
> **zorkerz said:**
> whats the deal with the places->search for files... thingy. It can be set to search the whole filesystem but it can't find anything. Ive been searching for a file on my desktop with its exact name and it still cannot find it.

Rather just use the "find" command it works 100% of the time.

---

### Post by porchrat on 2008-10-14
> **Buttons840 said:**
> Is there a way to search through ALL files on the Ubuntu file system?  For example, I discovered some huge files hiding out in a trash folder under /root/.local/....

I could just go delete them, but I want a comprehensive way of searching through all folders and files.  I've read a few posts on the subject, but for something so simple it's sometimes hard to get an answer because everyone takes it for granted.  (Like trying to find help on this forum about how to turn your computer on, nobody has written a guide on it, nor do they need to.  You get the point though.)

A graphical display of these files is preferred, but I'm not afraid of the terminal, just a little new.

Thanks.

I think the real problem here is that no one actually knows what you are trying to do.  Are you trying to automatically search for one particular file that is hiding somewhere in your system?

Are you trying to find a way to manually search through everything on your system?

What is it exactly that you want to do, because I don't think you have explained yourself very well, if perhaps you could give an example that would probably allow people to help you a little more.

In order to search your entire system for one particular file you use this command:

"sudo find / -name filename_you_want"

Be aware that you must include the filetype as well, for example: file.txt, either that or use something like "file*" to indicate that anything can follow after the word "file" in the filename of the file you  are looking for.

In order to manually search through your whole system going from one directory to the next I would recommend you use the console (it is the quickest way to get around the system) and use the "cd" command to move around from one directory to the next and then just use the "ls" command to view the contents of the file you currently find yourself in.  If you wish at any point to view the size on disk of a certain file, or perhaps you want to see how large all the files within that directory are use this command:

```
ls -lh
```

Another possibility is :
```
du -sh
```

Both are very helpful.  Anyway I hope this helps.

---

