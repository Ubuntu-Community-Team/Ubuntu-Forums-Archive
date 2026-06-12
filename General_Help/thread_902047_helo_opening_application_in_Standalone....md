---
title: "helo opening application in Standalone..."
date: 2008-08-26
forum: General Help
---

### Post by swirlz on 2008-08-26
Hi all, I am new to ubuntu, and have the hardy operating system.

My problem is this, I just installed Matlab (yea), the installation went smoothly and directly after the installation i was given the option to open matlab (I did) and it opened perfectly.

However, I then closed the program and now I don't know how to open it again. Help!!

Any input is appreciated.

Best, Swirls

---

### Post by LateNiteTV on 2008-08-26
> **swirlz said:**
> Hi all, I am new to ubuntu, and have the hardy operating system.

My problem is this, I just installed Matlab (yea), the installation went smoothly and directly after the installation i was given the option to open matlab (I did) and it opened perfectly.

However, I then closed the program and now I don't know how to open it again. Help!!

Any input is appreciated.

Best, Swirls

```
find / -name "*atlab"
```

---

### Post by swirlz on 2008-08-26
> **LateNiteTV said:**
> ```
find / -name "*atlab"
```

I added a "m" and put my name in and nothing happened but a lot of lines of files

---

### Post by swirlz on 2008-08-27
wait I added ```
find / j "*matlab" 
```

and got this

```
find: j: No such file or directory
find: *matlab: No such file or directory

```

---

### Post by prshah on 2008-08-27
> **swirlz said:**
> I added ```
find / j "*matlab" 
```
[/CODE]

Try```
locate matlab
sudo find / -iname matlab
```

---

### Post by swirlz on 2008-08-27
thanks for the help...

it get this  ```
j@j-desktop:~$ locate matlab
/usr/share/apps/katepart/syntax/matlab.xml
/usr/share/mime/text/x-matlab.xml
j@j-desktop:~$ sudo find / -iname matlab
[sudo] password for j: 
/home/j/.kisotmp/ISO/update/pd/matlab
/home/j/.kisotmp/Mount/update/pd/matlab
find: /home/j/.gvfs: Permission denied
/home/j/Documents/MATLAB
/home/j/matlab
/home/j/matlab/bin/scripts/matlab
/home/j/matlab/bin/glnx86/MATLAB
/home/j/matlab/bin/matlab
/home/j/matlab/X11/app-defaults/Matlab
/home/j/matlab/java/jar/toolbox/matlab
/home/j/matlab/update/pd/matlab
/home/j/matlab/help/pdf_doc/matlab
/home/j/matlab/toolbox/compiler/mcr/matlab
/home/j/matlab/toolbox/nnet/nnresource/nnet6/icon/general/matlab
/home/j/matlab/toolbox/eml/lib/matlab
/home/j/matlab/toolbox/matlab
j@j-desktop:~$ 

```


what do i do next?

---

### Post by prshah on 2008-08-27
> **swirlz said:**
> thanks for the help...

j@j-desktop:~$ sudo find / -iname matlab
/home/j/matlab/bin/scripts/matlab
/home/j/matlab/bin/glnx86/MATLAB
/home/j/matlab/bin/matlab
/home/j/matlab/X11/app-defaults/Matlab
/home/j/matlab/java/jar/toolbox/matlab
[/CODE]
what do i do next?

Post output of this command ```
ls -l `find ~ -iname matlab`
```

Note the "`" are the one in the upper left hand corner of keyboard, with "~", not single quotes "'", which are with the double quote character ", near the right hand middle of the keyboard.

This is so that we can find out which files have "x" (execute) permissions on them.

---

