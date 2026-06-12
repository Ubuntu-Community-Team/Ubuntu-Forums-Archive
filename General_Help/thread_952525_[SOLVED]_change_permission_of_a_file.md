---
title: "[SOLVED] change permission of a file"
date: 2008-10-19
forum: General Help
---

### Post by charanpreethu on 2008-10-19
hi i installed apache.i have to edit the file 
/usr/share/tomcat5.5/conf/tomcat-user.xml.

but i am not allowed to do that.how can i change permission of that file?

---

### Post by Idefix82 on 2008-10-19
Generally, to change permissions you do
```
sudo chmod 755 /folder/file
```
where 755 can be replaced by any suitable permissions string.
However, you normally shouldn't change permissions on files outside your home folder. To modify the file, just type in
```
gksudo gedit /usr/share/tomcat5.5/conf/tomcat-user.xml
```

---

### Post by Monotoko on 2008-10-19
You don't need to edit the permissions

Type in the terminal
```

gksudo nautilus

```
Type your password

you now have root access to your PC, and can edit anything, as soon as you have done what you need to, make sure you close it and only use it when you need it.

---

### Post by Sam on 2008-10-19
Idefix82's idea is better than Monotoko's. There are less chances to mess up the system.

---

### Post by charanpreethu on 2008-10-19
i used
sudo chmod 755 conf
 still i am not able to edit the file

---

### Post by Idefix82 on 2008-10-19
Have you not read any of the posts? Don't change permissions on that file. I gave you a command with which you will be able to modify it.

---

### Post by charanpreethu on 2008-10-19
thank you.......

---

