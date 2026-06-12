---
title: "Installing Eagle (.run file)"
date: 2008-10-15
forum: General Help
---

### Post by raiderleaf on 2008-10-15
I am trying to install this CadSoft software called eagle on my PC version 5.02, and I cannot get it to install or run or anything. Can anyone help me? Here is the link to the download page, maybe someone will figure out how to install this. 

Thank you,

raiderleaf

---

### Post by wilbbe01 on 2008-10-15
You didn't give a link.  Not knowing much about your specific software I would suggest trying the following at a terminal.

```
sh [nameOfFile].run 
```

and if that doesn't allow you access I would try

```
sudo sh [nameOfFile].run 
```

if it complains about permissions.  Again though, I don't know what this file is or anything so that is just my gut instinct.

---

### Post by Yellow Pasque on 2008-10-15
Eagle is available in the repo, but it's an older version.
If you downloaded from their site, go to the directory where you downloaded the install file and:
```
./eagle-lin-5.2.0.run
```

---

### Post by raiderleaf on 2008-10-15
> **Temüjin said:**
> Eagle is available in the repo, but it's an older version.
If you downloaded from their site, go to the directory where you downloaded the install file and:
```
./eagle-lin-5.2.0.run
```

I don't understand how to actually do that... here is the link by the way. What version does the repositories currently have?
[http://www.cadsoft.de/download.htm](http://www.cadsoft.de/download.htm)

---

### Post by raiderleaf on 2008-10-15
> **wilbbe01 said:**
> You didn't give a link.  Not knowing much about your specific software I would suggest trying the following at a terminal.

```
sh [nameOfFile].run 
```

and if that doesn't allow you access I would try

```
sudo sh [nameOfFile].run 
```

if it complains about permissions.  Again though, I don't know what this file is or anything so that is just my gut instinct.

This way ended up working actually. Just curious, what version is in the repository? I know that i installed 5.02 but I was looking for 4.16r2 ...

EDIT: I installed it, but I cannot run it for some reason, I can't find where to open it. I go to the directory it installed to and I can't find it. I went to the terminal and typed in eagle, and it said it wasn't installed but I know it is referring to a different edition...

---

### Post by Ayuthia on 2008-10-15
> **raiderleaf said:**
> This way ended up working actually. Just curious, what version is in the repository? I know that i installed 5.02 but I was looking for 4.16r2 ...

EDIT: I installed it, but I cannot run it for some reason, I can't find where to open it. I go to the directory it installed to and I can't find it. I went to the terminal and typed in eagle, and it said it wasn't installed but I know it is referring to a different edition...

You can try the following:
```
sudo updatedb
locate eagle
```This is assuming that eagle is the name of the application.

---

### Post by raiderleaf on 2008-10-15
> **Ayuthia said:**
> You can try the following:
```
sudo updatedb
locate eagle
```This is assuming that eagle is the name of the application.

That produced a bunch of files when I ran that, but how do I know which one is the executable?

---

### Post by Ayuthia on 2008-10-15
> **raiderleaf said:**
> That produced a bunch of files when I ran that, but how do I know which one is the executable?

Do you see any that contain eagle without any extensions(ex. /usr/local/bin/eagle)?  Usually the executable is just the application name without an extension.

---

### Post by raiderleaf on 2008-10-16
> **Ayuthia said:**
> Do you see any that contain eagle without any extensions(ex. /usr/local/bin/eagle)?  Usually the executable is just the application name without an extension.

No, I can't find that. Plus when it installed it installed into home/username directory... does this matter?

---

### Post by Yellow Pasque on 2008-10-16
The binary is in the /home/<username>/eagle-5.2.0/bin directory, so:
```
cd ~/eagle-5.2.0/bin
./eagle
```

---

### Post by raiderleaf on 2008-10-16
Everything works, thanks! The command above did the trick just fine!

---

