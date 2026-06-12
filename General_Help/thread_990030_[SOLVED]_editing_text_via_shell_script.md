---
title: "[SOLVED] editing text via shell script?"
date: 2008-11-22
forum: General Help
---

### Post by civillian on 2008-11-22
I have a bit of time on my hands, and I've decided to add a few more linux skills to my belt (I'm an old hand, but I'm fairly competent) and I was thinking about making a shell script to remove apps that come as default under ubuntu and adding my own apps.

I can do all of this, however I wondered how I would go about adding lines to text files (primarily sources.list to add repos for apps like cinelerra and playonlinux). 

My plan is to have the script in three parts, one to remove stuff, the second to edit text files, add 3rd party repos, and then the third part to install everything, and it was just the second part I was having difficulty with.

Can anyone shed some light on the issue?

regards,
Civ

---

### Post by taurus on 2008-11-22
```
sudo nano -Bw /etc/apt/sources.list
```
<Ctrl>x to exit and Y to save it.

---

### Post by cmnorton on 2008-11-22
Have a look at basic unix/linux tools and bash commands.

I'd start with sed, but don't stop there. You can do a lot by prompting users from shell scripts and also manipulating parts of files and reasembling them into new files.

---

### Post by Idefix82 on 2008-11-22
> **taurus said:**
> ```
sudo nano -Bw /etc/apt/sources.list
```
<Ctrl>x to exit and Y to save it.

That's not very useful if he wants it to be in a script.
The command you are looking for is
```
echo deb include repository here >> /etc/apt/sources.list
```

---

### Post by civillian on 2008-11-22
so if I wanted to add
> deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe main restricted universe

then I'd use 
```
echo deb include "deb http://us.archive.ubuntu.com/ubuntu dapper universe main restricted"  here >> /etc/apt/sources.list
```?

---

### Post by Idefix82 on 2008-11-22
> **C!V!NT said:**
> so if I wanted to add


then I'd use 
```
echo deb include "deb http://us.archive.ubuntu.com/ubuntu dapper universe main restricted"  here >> /etc/apt/sources.list
```?

No, sorry, that was ambiguous. You would just write

```
echo deb http://us.archive.ubuntu.com/ubuntu dapper universe main restricted >> /etc/apt/sources.list
```

When you type in
```
echo Hello world
```
then the string hello world will be printed on the screen. If you use the output redirection operator >> then you can have it printed elsewhere, in this case into a file.

---

### Post by taurus on 2008-11-22
> **Idefix82 said:**
> No, sorry, that was ambiguous. You would just write

```
echo deb http://us.archive.ubuntu.com/ubuntu dapper universe main restricted >> /etc/apt/sources.list
```


Sorry to inform you but that would not work unless you log in as root.  Got to use sudo.

---

### Post by Idefix82 on 2008-11-22
> **taurus said:**
> Sorry to inform you but that would not work unless you log in as root.  Got to use sudo.

You are right, thanks! But the OP will need to run his script with sudo anyway if he wants to install and uninstall software.

---

### Post by taurus on 2008-11-22
> **C!V!NT said:**
> so if I wanted to add


then I'd use 
```
echo deb include "deb http://us.archive.ubuntu.com/ubuntu dapper universe main restricted"  here >> /etc/apt/sources.list
```?

Look at my #2 post on how to edit your /etc/apt/sources.list and once you're in /etc/apt/sources.list, just add this line to the end of it.

```

deb http://us.archive.ubuntu.com/ubuntu dapper universe main restricted universe 

```

---

### Post by geirha on 2008-11-22
In addition to /etc/apt/sources.list, /etc/apt/sources.list.d/*.list is also read, so I usually leave /etc/apt/sources.list alone and create a new file for third party repositories.

E.g.:
```

echo "deb http://packages.medibuntu.org hardy free non-free" | sudo tee -a /etc/apt/sources.list.d/medibuntu.list

```

---

### Post by civillian on 2008-11-22
> **taurus said:**
> Sorry to inform you but that would not work unless you log in as root.  Got to use sudo.

I was intending to run the script as root/using suda anyway, so this wouldn't matter so much.

> Look at my #2 post on how to edit your /etc/apt/sources.list and once you're in /etc/apt/sources.list, just add this line to the end of it.


I knew about that method, it's just I want it to be 99.9% automated, and in the order I wanted to do things in the script, editing the sources.list is somewhere in the middle.

Thanks for all the help!

I forgot about using echo >> to append text to files, and that was really what I was after.

Regards,
Civ

/thread

---

