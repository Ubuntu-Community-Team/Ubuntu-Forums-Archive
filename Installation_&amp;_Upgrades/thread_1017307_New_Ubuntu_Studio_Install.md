---
title: "New Ubuntu Studio Install"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by Perumexican on 2008-12-20
Hi all,

I installed Ubuntu Studio (7/08 release, I believe) on my HP dv5237cl and upon reboot I was met with Grub. I chose Ubuntu and I got a bunch of DOS-like text. I was asked for my user name and password. Did that and then saw "username@ubuntu:~$" and something about commands. What is this and what should I do? Should my install have gone straight to a graphical log-in screen like this: [HTML]http://news.softpedia.com/images/reviews/large/ubuntustudio-large_031.png[/HTML]? How do I reboot from where I'm at? (Writing from desktop at the moment and the notebook's hung up.)

Thank you!

---

### Post by taurus on 2008-12-20
What happens if you run this command after you log in with your username and password?

```
startx
```

---

### Post by Perumexican on 2008-12-20
I typed in startx and I got "The program 'startx' is currently not installed. You can install it by typing: sudo apt-get install xinit [and next line] -bash: startx: command not found".

---

### Post by bs0409 on 2008-12-21
yes
it happened to me also..........

---

### Post by Partyboi2 on 2008-12-21
have you got the ubuntustudio-desktop installed?
```
dpkg -l ubuntustudio-desktop
```

---

### Post by Perumexican on 2008-12-21
That was the only software package I was able to install. I didn't know how to check more than one package to install during installation.

---

### Post by Cyphnar on 2008-12-31
I also have this problem! 

Did anyone find a solution? How do i install many packages during the install?

This is my first post btw, so hello :) I'm  bit of a linux noob! i'm trying to get the whole family onto linux, check out our [blog](http://www.brayblog.co.uk) :D

-Cyph

---

### Post by jarett on 2009-01-04
I also had this problem...So I went and reinstalled it but i did some stuff different.When I got to the part where it says something about partitioning go down to manuel.Then erase the data and delete the partition that you had studio in.Then go back untill where you get to the first page of where it starts to talk about partitioning.Then do the same partitioning that you had selected when you originally installed it the first time. Then do the same thing untill you come to the part where it ask what you download (I recomend that you download everything, theres alot of cool stuff) BUT YOU HAVE TO SELECT THE PART WHERE IT TALKS ABOUT THE DESKTOP PRESS SPACE BAR AND IT WILL STAR IT SAYING THAT ITS GOING TO DOWNLOAD THAT PART.Then follow through with the rest of the installation like you did the first time you tried.

---

