---
title: "Problems installing updates"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by mortalapeman on 2009-09-23
Not enough free disk space

The upgrade needs a total of 404M free space on disk '/'. Please free at least an additional 404M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

i get this error when trying to install update for ubuntu jaunty notebook remix. I've tried doing as it says and that doesn't help. I'm guessing it has something to do with the fact it is trying to save to a disc that doesn't exist. I'm new to linux so a very detailed explanation would probably be best if you have anything you can give that might help me.

Anything is appreciated! Thanks.

---

### Post by Partyboi2 on 2009-09-23
Hi, can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
df -h
```

---

### Post by mortalapeman on 2009-09-23
eric@eric-laptop:~$ df - h
df: `-': No such file or directory
df: `h': No such file or directory
df: no file systems processed
eric@eric-laptop:~$ df-h
bash: df-h: command not found
eric@eric-laptop:~$ df- h
bash: df-: command not found
eric@eric-laptop:~$ sudo df- h
[sudo] password for eric: 
sudo: df-: command not found
eric@eric-laptop:~$ 

Like this? I think  typed in right at least once in there xD

---

### Post by Partyboi2 on 2009-09-24
Sorry my typo  mistake, I put the - in the wrong place, it should be
```
df -h
```

---

