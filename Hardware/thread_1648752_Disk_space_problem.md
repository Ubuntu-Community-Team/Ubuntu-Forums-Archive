---
title: "Disk space problem"
date: 2010-12-19
forum: Hardware
---

### Post by chitragurung on 2010-12-19
I have been using Dell Inspiron mini since last year. My machine capacity is 160 gb. But recently my free space is dropped to 5 gb. I had no any files that occupies lot of space, also has no such many program as well. Instead I am using cleaning all unused files. Still my computer being slower and slower. How can I fix these problem.

---

### Post by IcarusR on 2010-12-19
Use Disk Usage Analyser to find what is using space & delete anything not needed.

Web browser cache can get big if not cleared regularly.
Apt stores a copy of all downloaded & installed packages in /var/cache/apt/archives which can get big. 
To delete these run the following from terminal

```
sudo apt-get clean
```

---

### Post by sikander3786 on 2010-12-19
> My machine capacity is 160 gb

Unless you store some personal files on the same partition, I believe Ubuntu can never use up all the space there.

For freeing up some space, **IcarusR** have posted some suggestions above.

I would still like to see the output of this command.

```
df -h
```

---

### Post by Fafler on 2010-12-19
If the above doesn't solve your problems, the output of this command could also be interesting:
```
sudo du -hs /*
```

You can run the same command on you home directory or any other you would like to know about.

---

### Post by chitragurung on 2010-12-20
Hello,

I have following output using command you guys adviced.

chitra@chitra:~$ sudo apt-get clean
[sudo] password for chitra: 
chitra@chitra:~$ sudo apt-get clean
chitra@chitra:~$ 
bash: chitra1357: command not found
chitra@chitra:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             143G  121G   15G  90% /
varrun                501M  232K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M   52K  501M   1% /dev
devshm                501M     0  501M   0% /dev/shm
lrm                   501M  1.7M  499M   1% /lib/modules/2.6.24-27-lpia/volatile
gvfs-fuse-daemon      143G  121G   15G  90% /home/chitra/.gvfs
chitra@chitra:~$ 
chitra@chitra:~$

---

### Post by BbUiDgZ on 2010-12-20
dude, you might want to remove your password from your last post

---

### Post by sikander3786 on 2010-12-20
> /dev/sda2 143G 121G 15G 90% /

15GB space is available there. And I think your personal files are taking up all the space. What is there in your /home directory? Check the size of your /home as Ubuntu can't use 121GB itself ;-)

---

### Post by chitragurung on 2010-12-21
Here is out put of df -h

chitra@chitra:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             143G  121G   15G  90% /
varrun                501M  232K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M   44K  501M   1% /dev
devshm                501M   52K  501M   1% /dev/shm
lrm                   501M  1.7M  499M   1% /lib/modules/2.6.24-27-lpia/volatile
gvfs-fuse-daemon      143G  121G   15G  90% /home/chitra/.gvfs
chitra@chitra:~$ 

I am wondering what is gvfs-fuse daemon ? this directory taking all my space I think ? I could see this directory when I go to home directory. Only I saw .gvfs directory but it is all empty. So, it should be something wrong there.

---

### Post by sikander3786 on 2010-12-22
Yep gvfs seems to take up the space here. Do you need that?

See here for details.

[http://en.wikipedia.org/wiki/GVFS](http://en.wikipedia.org/wiki/GVFS)

And what is the output of command mentioned above in post # 4?

---

### Post by Elfy on 2010-12-22
chitragurung please run the command fafler posted above then paste that here 

```
sudo du -hs /*
```

gvfs only appears to take up the space

---

