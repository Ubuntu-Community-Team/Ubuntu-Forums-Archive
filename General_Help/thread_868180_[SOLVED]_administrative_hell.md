---
title: "[SOLVED] administrative hell"
date: 2008-07-23
forum: General Help
---

### Post by PCessna on 2008-07-23
Hello, I need to know how to run a .run file with administrative privileges. Wow Microsoft owns with this one (like right click the file and and couple and clicks and apply w/ password ftw) 

I also did the same with ubuntu, figured it out myself, Very easy :-)

Thanks for your help
-PCessna

---

### Post by tamoneya on 2008-07-23
Its easiest to do in terminal (applications -> accessories -> terminal)
```
cd /some/directory
sudo chmod +x myfile.run
./myfile.run
```

I am being rather explicit to make sure that it has the correct permissions so some of the above commands arent always necessary but I wanted to make sure it worked.  If you get any complaints from terminal about permissions you should change "./myfile.run" to "sudo ./myfile.run"

---

### Post by PCessna on 2008-07-23
Response: 

[sudo] password for pcessna:

Cannot type in password. Another way?

---

### Post by tuxxy on 2008-07-23
Your password will be invisible as you type for security reaons but it is still there, type it as normal and hit enter

---

### Post by PCessna on 2008-07-23
I finally fixed the problem. Thank you two guys for your help.

---

### Post by dentaku65 on 2008-07-23
You can bypass password typing if .run file needs sudo command

Create a text file 
```
nano ~/mymeme
```

Write in it your sudo password and save

Create a shell script
```
nano ~/myrun.sh
```
Put something like this:
```
sudo -S myfile.run < ~/mymeme
```
Save this file, then chomod it
```
sudo chmod +x ~/myrun.sh
```
Execute it
```
~/myrun.sh
```

---

