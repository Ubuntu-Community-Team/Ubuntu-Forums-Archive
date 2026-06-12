---
title: "Cant install Java aplication"
date: 2008-12-10
forum: Installation &amp; Upgrades
---

### Post by hjmalves on 2008-12-10
Hello all

I posted this in the general help area but the number of threads is so high that in few minutes it disappears and its almost impossible for someone to see it. So I decided to post again here.

I have a Java app for remote access to a Xerox iGen3 printer called "FreeFlow Remote Print Server" that works well on Solaris 10.
I tried to install in Ubuntu and I got this errors:

> helder@ubuntu:~$ /home/helder/install.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
exec: 2314: /tmp/install.dir.6224/Solaris/resource/jre/bin/java: not found
After some Googling I found the LD_ASSUME_KERNEL issue and tried:
> helder@ubuntu:~$ cp ./install.bin ./install.bin.bak
helder@ubuntu:~$ sed -i "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" install.bin
helder@ubuntu:~$ ./install.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

exec: 2314: /tmp/install.dir.6887/Solaris/resource/jre/bin/java: not found
The shared libraries errors are gone but the installer stop with same error.
Anyone knows a solution for this.
Any help would be highy apreciated.

Thanks in advance
Helder Alves

---

### Post by hjmalves on 2008-12-17
Thank you all for your help and time lost.

For someone like me that always worked with Microsoft Windows and decided to try Linux (in this case Ubuntu - the most popular distribution - I thought) this is something never happened to me in Microsoft forums: simply to be ignored.

Also a forum where we put a thread and after some minutes that thread disappears with 2 or 3 new pages in front of it cannot IMHO work. There is an evident bad categorization of this forum that makes many people post in the same area at the same time.

But as I said maybe this is the way things work to this new world - new at least to me - of open source software.

Once again sorry for all the trouble.

Helder Alves

---

### Post by joff13 on 2008-12-17
> **hjmalves said:**
> Thank you all for your help and time lost.

For someone like me that always worked with Microsoft Windows and decided to try Linux (in this case Ubuntu - the most popular distribution - I thought) this is something never happened to me in Microsoft forums: simply to be ignored.

Also a forum where we put a thread and after some minutes that thread disappears with 2 or 3 new pages in front of it cannot IMHO work. There is an evident bad categorization of this forum that makes many people post in the same area at the same time.

But as I said maybe this is the way things work to this new world - new at least to me - of open source software.

Once again sorry for all the trouble.

Helder Alves

hummm... almost all the time I ask something on a forum, nobody answer me. this may be because to difficult stuff.. and I think we should keep in mind that here are all not-paid volunteers that decide to spend some of their own time to freely help people.... But if you want a rapid support, I think you can go [here]("http://www.ubuntu.com/support/paid")


anyway, to get back to your problem...

generally this will not work
```
helder@ubuntu:~$ /home/helder/install.bin
```

because you have no admin right... try with this

```
helder@ubuntu:~$ sudo /home/helder/install.bin
```

---

### Post by lovelyvik293 on 2008-12-17
Use
```

cd /home/helder
chmod +x install.bin
./install.bin

```
And 
> 
exec: 2314: /tmp/install.dir.6887/Solaris/resource/jre/bin/java: not found 

This error shows that this software is using a path which is in solaris only.

---

### Post by joff13 on 2008-12-17
> **lovelyvik293 said:**
> Use
```

cd /home/helder
chmod +x install.bin
./install.bin

```


the file is already executable, i think... but it worth to check

```

ls -l  /home/helder

```

but again, use sudo.

---

### Post by lovelyvik293 on 2008-12-17
The problem is with the software i think.
Can you tell us the name of the software so can we can give a try?

---

### Post by hjmalves on 2008-12-19
**Thank you all for your help**

> **joff13 said:**
> hummm... generally this will not work
```
helder@ubuntu:~$ /home/helder/install.bin
```

because you have no admin right... try with this

```
helder@ubuntu:~$ sudo /home/helder/install.bin
```

**Already tried with:**
> helder@ubuntu:~$ sudo ./install.bin
[sudo] password for helder:
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

exec: 2314: /tmp/install.dir.10832/Solaris/resource/jre/bin/java: not found
helder@ubuntu:~$
Same error... installer stops
[B]
And also as root[/B]
> root@ubuntu:/home/helder# /home/helder/install.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

exec: 2314: /tmp/install.dir.10607/Solaris/resource/jre/bin/java: not found
root@ubuntu:/home/helder#
Stops again with same error

I think its not a permission problem. It says the file does not exist but in fact its there in that exact directory.

> **lovelyvik293 said:**
> Use
```

cd /home/helder
chmod +x install.bin
./install.bin

```
And 

This error shows that this software is using a path which is in solaris only.

Had already tried your suggestion and happens the same:
> helder@ubuntu:~$ cd /home/helder
helder@ubuntu:~$ chmod +x install.bin
helder@ubuntu:~$ ./install.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

exec: 2314: /tmp/install.dir.18560/Solaris/resource/jre/bin/java: not found
helder@ubuntu:~$
Again checking that directory it exists and also that file.

> **joff13 said:**
> the file is already executable, i think... but it worth to check

```

ls -l  /home/helder

```

but again, use sudo.

**Trying your code:**
> helder@ubuntu:~$ ls -l  /home/helder
total 37744
drwxr-xr-x 2 helder helder     4096 2008-12-05 00:50 Área de Trabalho
drwxr-xr-x 2 helder helder     4096 2008-12-05 00:07 Documentos
drwxr-xr-x 2 helder helder     4096 2008-12-05 00:07 Imagens
-rwxrwxrwx 1 helder helder 38572394 2008-12-05 01:57 install.bin
drwxr-xr-x 2 helder helder     4096 2008-12-05 00:07 Modelos
drwxr-xr-x 2 helder helder     4096 2008-12-05 00:07 Música
drwxr-xr-x 2 helder helder     4096 2008-12-05 00:07 Público
drwxr-xr-x 2 helder helder     4096 2008-12-05 00:07 Vídeos
helder@ubuntu:~$ 

> **lovelyvik293 said:**
> The problem is with the software i think.
Can you tell us the name of the software so can we can give a try?
The JAVA software name is FreeFlow Remote Print Server and it purpose its to remote access and manage all the workflow, print queues and printer management of a Xerox iGen3 printer.

I uploaded it to this URL, you can download it to try if you want.

[http://www.graficapacense.pt/java/install.bin]("http://www.graficapacense.pt/java/install.bin")

This are the instructions included with the installer:
> For Solaris Users:

Execute the install.bin program found in the directory/folder path
/cdrom/cdrom0/Disk1/InstData/Solaris/VM.
For example, the following command entered at a command prompt (here, a dollar sign) will begin the installation process: 

 $ /cdrom/cdrom0/Disk1/InstData/Solaris/VM/install.bin

Again thank you for your help
Helder Alves

---

