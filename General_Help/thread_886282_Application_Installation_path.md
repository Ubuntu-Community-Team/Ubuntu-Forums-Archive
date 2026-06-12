---
title: "Application Installation path"
date: 2008-08-11
forum: General Help
---

### Post by virus2 on 2008-08-11
Where does Adept Package manager in Kubuntu install the softwares??
Like for eg,in windows,there is a common path of C:/Program files for most of the application.Similarly,is there any common path for application installation path in kubuntu??
And if there is,then is that path configurable in adept manager??

---

### Post by tuxxy on 2008-08-11
/usr/lib/ ?

---

### Post by cariboo on 2008-08-11
In adept has a properties button like it does in synaptic highlight the file click the properties button then click the installed files tab. If you just want to know where the program you just installed is located, in a terminal type:

```
which <programname>
```

Where <programname> is the name of the program you are looking for. 

Jim

---

### Post by virus2 on 2008-08-11
Thanks for your replies...
But,I have read somewhere that Linux installs libraries in _lib_ folder,documentation files somewhere in _man_ folder,and executable files in users home directories
Unlike windows,which installs all the files in the particular application folder in C:\Program files.
Pls elaborate on this.......

---

### Post by luctor on 2008-08-11
it takes a while to get used to the file system hierarchy in linux (no drive letters for example), but after a while you get used to it and now I find the windows system hard to grasp and inflexible :-)

open a konsole

type 'man hier' (without the quotes)
press enter

use your home directory for normal files only (mp3,documents,images etc)

---

### Post by Vivaldi Gloria on 2008-08-11
Use the command

```
dpkg-query -L <package_name>
```

to get a list of installed files. See

```
man dpkg-query
```

for more info.

---

