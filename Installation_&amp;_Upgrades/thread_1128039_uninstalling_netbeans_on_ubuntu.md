---
title: "uninstalling netbeans on ubuntu"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by 10ghost on 2009-04-17
good morning dear reader if u at the same time zone as i am now else good day. 
i can of have a problem with my uninstalling of netbeans.

on typing the command 

*sudo aptitude remove NetBeans\ IDE\ 6.0.1*
 i gives me this output

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "NetBeans IDE 6.0.1"
Couldn't find any package whose name or description matched "NetBeans IDE 6.0.1"
The following packages are unused and will be REMOVED:
  linux-headers-2.6.24-19 linux-headers-2.6.24-19-generic 
The following packages have been kept back:
  gimp gimp-data gimp-gnomevfs gimp-python libgimp2.0 
  libgtksourceview2.0-common 
0 packages upgraded, 0 newly installed, 2 to remove and 6 not upgraded.
Need to get 0B of archives. After unpacking 68.3MB will be freed.
Do you want to continue? [Y/n/?] n
Abort.
oladele@oladele-laptop:~$ sudo aptitude remove netbeans-6.0.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "netbeans-6.0.1"
Couldn't find any package whose name or description matched "netbeans-6.0.1"
The following packages are unused and will be REMOVED:
  linux-headers-2.6.24-19 linux-headers-2.6.24-19-generic 
The following packages have been kept back:
  gimp gimp-data gimp-gnomevfs gimp-python libgimp2.0 
  libgtksourceview2.0-common 
0 packages upgraded, 0 newly installed, 2 to remove and 6 not upgraded.
Need to get 0B of archives. After unpacking 68.3MB will be freed.
Do you want to continue? [Y/n/?]


since it told me it could not find this application which is on my desktop and can be found here applications=>programming=>
i tried using names which where part of the program name like netbeans
but it gave me the same result again 
based on my search on uninstalling programs on ubuntu this was the only means by which i could go. the add and remove option could not work neither did the synaptic software manager becaUSE I DID not install from there.

can any one please kindly solve dis problem for me.

thanx for ur anticipated cooperation
hope 2 hear from u in the nearest future.

---

### Post by 10ghost on 2009-04-17
thou no one could have possibly replied that fast
but thanx any way
after i posted it, i search for neatbeans on my home directory
 on going thru the folders displayed for the result  i discovered a shell script uninstall.sh
so i just changed directory to the location of the shell script 
after which i ran the script
bye
in case some one has d same problem

---

### Post by sbrbot on 2009-08-10
Go to the directory where NetBeans was installed (e.g. netbeans-6.1 in your home directory or in /usr/local) and start ./uninstall.sh script.

```
/usr/local/netbeans-6.1$ sudo ./uninstall.sh
```

---

### Post by nipuna86 on 2009-08-16
I'm also having trouble with uninstalling NetBeans from Ubuntu. I installed it with the aid of Synaptic Package Manager. but now i cant find where the NetBeans installation folder is. it is not there in /usr/local. can someone help me to locate the uninstall.sh...

---

### Post by kanaqsasak on 2010-05-01
I was using karmic when I first installed NetBeans. Now I've moved to Lucid. And running this command, 

sudo ./uninstall.sh (in my NetBeans installation folder)

is work for me to uninstall it.

Happy Lucid-ing.. :)

---

