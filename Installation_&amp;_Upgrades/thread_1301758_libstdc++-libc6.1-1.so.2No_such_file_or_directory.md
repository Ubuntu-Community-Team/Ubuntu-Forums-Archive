---
title: "libstdc++-libc6.1-1.so.2:No such file or directory"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by yliu on 2009-10-26
Hi all,

I download PerlEdit-1.08 for Linux. When I run ./pe, it told me: 

./pe: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

There is on such a file when I search by "sudo find / -name  libstdc++-libc6.1-1.so.2". Under /usr/lib, when I run command "ls libstdc*", it only returns: 

/usr/lib/libstdc++.so.6  /usr/lib/libstdc++.so.6.0.10

I have installed the latest version of build-essential and sun-java6-jdk. I don't know why I still have this problem. I am using Ubuntu 9.04. 

Thanks for your help!

-Ying

---

### Post by yliu on 2009-10-26
ying@XXXX:/usr/lib$ ls -l libstdc*
lrwxrwxrwx 1 root root     19 2009-06-16 14:54 libstdc++.so.6 -> libstdc++.so.6.0.10
-rw-r--r-- 1 root root 950424 2009-03-16 20:28 libstdc++.so.6.0.10

still don't know how to solve the problem. 


-Ying

---

### Post by yliu on 2009-10-26
sudo apt-get install libstdc++6-4.1-dbg

run the above command, no change.

-Ying

---

### Post by freecru on 2009-10-26
From link referenced...
```

mkdir tmp
cd tmp
wget [ftp://fr2.rpmfind.net/linux/fedora/core/5/x86_64/os/Fedora/RPMS/compat-libstdc++-296-2.96-135.i386.rpm](ftp://fr2.rpmfind.net/linux/fedora/core/5/x86_64/os/Fedora/RPMS/compat-libstdc++-296-2.96-135.i386.rpm)
sudo alien --to-tgz compat*rpm
tar zxf compat*tgz
cd usr/lib
cp sudo cp libstdc++-2-libc6.1-1-2.9.0.so /usr/lib32/libstdc++-libc6.1-1.so.2

```


Further reading here: [http://ubuntuforums.org/showthread.php?t=237829](http://ubuntuforums.org/showthread.php?t=237829)

---

### Post by yliu on 2009-10-26
Thank you freecru. I run the wget command and there is no c...6-135.i386.rpm file over there. 

ying@othello:~/tmp$ wget [ftp://fr2.rpmfind.net/linux/fedora/c...6-135.i386.rpm](ftp://fr2.rpmfind.net/linux/fedora/c...6-135.i386.rpm)
--2009-10-26 15:38:41--  [ftp://fr2.rpmfind.net/linux/fedora/c...6-135.i386.rpm](ftp://fr2.rpmfind.net/linux/fedora/c...6-135.i386.rpm)
           => `c...6-135.i386.rpm'
Resolving fr2.rpmfind.net... 195.220.108.108
Connecting to fr2.rpmfind.net|195.220.108.108|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /linux/fedora ... done.
==> SIZE c...6-135.i386.rpm ... done.
==> PASV ... done.    ==> RETR c...6-135.i386.rpm ... 
No such file `c...6-135.i386.rpm'.


-Ying

---

### Post by yliu on 2009-10-26
I changed the ftp location to [ftp://fr2.rpmfind.net/linux/fedora/c...6-138.i386.rpm](ftp://fr2.rpmfind.net/linux/fedora/c...6-138.i386.rpm), but still no such a file. 

ying@othello:~/tmp$ wget [ftp://fr2.rpmfind.net/linux/fedora/c...6-138.i386.rpm](ftp://fr2.rpmfind.net/linux/fedora/c...6-138.i386.rpm)
--2009-10-26 15:41:54--  [ftp://fr2.rpmfind.net/linux/fedora/c...6-138.i386.rpm](ftp://fr2.rpmfind.net/linux/fedora/c...6-138.i386.rpm)
           => `c...6-138.i386.rpm'
Resolving fr2.rpmfind.net... 195.220.108.108
Connecting to fr2.rpmfind.net|195.220.108.108|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /linux/fedora ... done.
==> SIZE c...6-138.i386.rpm ... done.
==> PASV ... done.    ==> RETR c...6-138.i386.rpm ... 
No such file `c...6-138.i386.rpm'.

---

### Post by freecru on 2009-10-26
The link is clipped. The ... in the middle of the file name is actually different. Hover over the text and you can see that. Right click on the link, then paste it into the terminal. Hopefully this will help.


Edit: after checking the link it seems to be dead. Sorry about that. Didn't test this as I'm at work right now.

I'm guessing you've already tried ```
sudo apt-get install libstdc++6 
``` Hmm, not sure. I'll have some more looks at it later. Good luck with your issue.

---

### Post by yliu on 2009-10-26
I think there is no this rpm file under the ftp link. 

Thanks.
-Ying

ying@othello:~/tmp$ wget [ftp://fr2.rpmfind.net/linux/fedora/core/5/x86_64/os/Fedora/RPMS/compat-libstdc++-296-2.96-135.i386.rpm](ftp://fr2.rpmfind.net/linux/fedora/core/5/x86_64/os/Fedora/RPMS/compat-libstdc++-296-2.96-135.i386.rpm)
--2009-10-26 16:21:55--  [ftp://fr2.rpmfind.net/linux/fedora/core/5/x86_64/os/Fedora/RPMS/compat-libstdc++-296-2.96-135.i386.rpm](ftp://fr2.rpmfind.net/linux/fedora/core/5/x86_64/os/Fedora/RPMS/compat-libstdc++-296-2.96-135.i386.rpm)
           => `compat-libstdc++-296-2.96-135.i386.rpm'
Resolving fr2.rpmfind.net... 195.220.108.108
Connecting to fr2.rpmfind.net|195.220.108.108|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /linux/fedora/core/5/x86_64/os/Fedora/RPMS ... 
No such directory `linux/fedora/core/5/x86_64/os/Fedora/RPMS'.

---

