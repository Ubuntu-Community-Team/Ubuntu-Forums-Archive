---
title: "[SOLVED] Download Error?"
date: 2008-09-08
forum: General Help
---

### Post by jimi_hendrix on 2008-09-08
My math teacher at school puts all of our homework on the school website unfortunately i get this error when i try and download it...its a .doc file...what should i do?

```
/tmp/Geo Chapter 1 Homework-2.doc could not be opened, because the associated helper application does not exist. Change the association in your preferences.
```

---

### Post by WRDN on 2008-09-08
Open OpenOffice Writer, click File > Open and navigate to the file. It seems it cannot find the OpenOffice executable.
To resolve this, open the File Manager, right click on the file, select Properties then the Open With tab. Now, click Add and find Open Office Writer in the list of applications, or add the custom command "oowriter".

---

### Post by drs305 on 2008-09-08
jimi,

Depending on how you are trying to download and/or open the file, it is possible you might be having problems due to the file name. I gather the file name is:
Geo Chapter 1 Homework-2.doc

In linux, you can designate this in one of the following ways:
'Geo Chapter 1 Homework-2.doc'
"Geo Chapter 1 Homework-2.doc"
Geo Chapter\ 1\ Homework-2.doc

In the command line, you can also type the first couple of letters and it will complete the rest. For example, if you wanted to copy the file, you would type: cp Ge and then tab. Bash would complete the filename with this result: cp Geo\ Chapter\ 1\ Homework-2.doc

If you have downloaded the file, either of these commands should open it in openoffice:
```
ooffice /tmp/Geo\ Chapter\ 1\ Homework-2.doc
ooffice /tmp/"Geo Chapter 1 Homework-2.doc"
```

I suppose it might hurt your grade to tell your teacher to use a better naming system... ;-)

---

### Post by jimi_hendrix on 2008-09-09
thanks it worked...the file name is "Geo Chapter 1 Homework.doc" what was the offending character?

---

### Post by drs305 on 2008-09-09
> **jimi_hendrix said:**
> thanks it worked...the file name is "Geo Chapter 1 Homework.doc" what was the offending character?

It's just the spaces in the name. When you ran the following it hit the space after Geo:
```
**/tmp/Geo** Chapter 1 Homework-2.doc could not be opened, because ... 
```
Anytime a space is encountered the system thinks it's the end of something (command, etc) and starts interpreting the next entry based on what it has already read.

Here is an example: if you typed **cp /home/Chapter 1** it would try to copy **Chapter** and name it **1**. It won't find a file called "Chapter" so it generates an error.

In your case, for what you were trying to do, just remember that a space must be enclosed in quotes or preceded by a \ if process is not supposed to think it is at the end of an input.

---

