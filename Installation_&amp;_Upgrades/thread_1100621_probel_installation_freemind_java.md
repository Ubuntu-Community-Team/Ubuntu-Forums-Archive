---
title: "probel installation freemind java"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by condore on 2009-03-19
hello , i try to install freemind on my pc i chose the version 9.0 because of problem installation with others versions. when i start :

java -jar /freemind-bin-0.9.0_RC_3/lib/freemind.jar 

it say me : Failed to load Main-Class manifest attribute from freemind.jar

why ??

thank you in advance for your answer.

---

### Post by taurus on 2009-03-19
> java -jar **[COLOR="Red"]/[/COLOR]**freemind-bin-0.9.0_RC_3/lib/freemind.jar 

Did you unpack it, freemind-bin-0.9.0_RC_3, in root directory--/?

```
ls -la /
```

---

### Post by condore on 2009-03-19
no i don't unpack on root direcotry but on my personnal folder i think that have not lot importance since even if i start freemind in root it don't  want start .

---

### Post by taurus on 2009-03-19
If you unpacked it in your $HOME, then you wouldn't include the / at the beginning.

What's the output of this command from a terminal?

```
ls -la ~
```

---

### Post by condore on 2009-03-19
ha ok Now I understand what you tried to say to me. No the freemind is unpack in my personnal folder but i was already in this folder but it's true he should not have the / it's because i write that without make copy-past. i threw well freemind with java on the good file :-)

here is like even the output of ls -la ~ :

total 144                                                     
drwxr-xr-x 26 root root 4096 mars 18 23:15 .                  
drwxr-xr-x 22 root root 4096 mars  2 16:07 ..                 
drwx------  2 root root 4096 mars 18 23:08 .aptitude          
-rw-------  1 root root 4903 mars 18 23:38 .bash_history      
-rw-r--r--  1 root root  412 déc. 15  2004 .bashrc            
drwxr-xr-x  4 root root 4096 févr. 13 22:58 .config           
drwx------  3 root root 4096 févr. 12 00:21 .dbus             
drwxr-xr-x  2 root root 4096 mars 18 23:09 .debtags           
drwx------  2 root root 4096 mars  2 15:17 Desktop            
drwxr-xr-x  2 root root 4096 mars 18 23:02 .freemind          
drwx------  2 root root 4096 mars 11 18:12 .gconf             
drwx------  2 root root 4096 mars 11 18:13 .gconfd            
drwx------  4 root root 4096 mars 15 23:51 .gnome2            
drwx------  2 root root 4096 févr. 12 21:58 .gnome2_private   
drwx------  4 root root 4096 mars  2 15:18 .googleearth       
drwxr-----  2 root root 4096 mars  3 15:19 .hplip
-rw-------  1 root root    0 mars 12 17:35 .ICEauthority
drwx------  2 root root 4096 mars  6 23:21 .irssi
drwx------  2 root root 4096 févr. 19 12:58 .john
drwx------  3 root root 4096 févr. 13 23:28 .kde
drwx------  3 root root 4096 févr. 12 13:39 .kde4
drwx------  3 root root 4096 févr. 13 22:57 .loki
-rw-r--r--  1 root root   88 mars 18 23:15 .mailcap
drwxr-xr-x  2 root root 4096 mars 14 15:44 .mc
drwxr-xr-x  3 root root 4096 févr. 13 23:28 .mcop
-rw-------  1 root root   31 mars 12 14:30 .mcoprc
-rw-r--r--  1 root root  230 mars 18 23:15 .mime.types
drwx------  4 root root 4096 mars 11 18:12 .mozilla
drwx------  3 root root 4096 mars 11 18:12 .mozilla-thunderbird
drwxr-xr-x  4 root root 4096 févr. 14 22:29 .msf3
-rw-------  1 root root   20 mars 18 23:30 .nano_history
-rw-r--r--  1 root root  110 nov. 10  2004 .profile
drwxr-xr-x  2 root root 4096 févr. 13 23:28 .qt
-rw-------  1 root root  218 févr. 12 21:20 .recently-used.xbel
drwxr-xr-x  2 root root 4096 mars  2 20:02 .VirtualBox
-rw-------  1 root root    0 févr. 14 18:45 .Xauthority
-rw-------  1 root root  186 févr. 12 00:22 .xsession-errors

---

### Post by taurus on 2009-03-19
If you're already in the directory where it is, no need to include the / in front because that means root filesystem, at the very top.

---

