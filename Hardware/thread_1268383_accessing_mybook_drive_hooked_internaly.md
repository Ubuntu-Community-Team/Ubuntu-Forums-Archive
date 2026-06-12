---
title: "accessing mybook drive hooked internaly"
date: 2009-09-16
forum: Hardware
---

### Post by z80 on 2009-09-16
I have a Mybook world edition 1Tb that i would like to gain access to so as to retrieve important files befor i reformat it and use it in another enclosure.  I have taken the wd drive out of the mybook case and plugged it into my demension 8400 through the sata.  now im trying to access it but the mybook uses something wierd to make it so i cant access it through my windows 7 or the ubuntu witch are now dual booting on that machine.  i have found other forums saying that ubuntu can access the drive and the file format, but they give some terminal stuff to do it and it makes no sense to me and dosnt just work the way they say it should.  it looks like this:

$ sudo modprobe md
       (i get a fail here-  FATAL: Module md not found.)
$ sudo mknod /dev/md4 b 9 4
$ sudo apt-get install mdadm
$ sudo mdadm --assemle /dev/md4 /dev/sdb4
$ sudo mkdir /media/xyz
$ sudo mount /dev/md4 /media/xyz
$ sudo chmod -R 777 ?media/xyz

i should also point out that i think they had thiers plugged in via usb sata adapter but here is the link i found this stuff on and so far this is by far the most promising out of months of searching for answers...       
[http://mybookworld.wikidot.com/forum/t-90514/how-to-recover-data-from-wd-my-book-world-edition-nas-device](http://mybookworld.wikidot.com/forum/t-90514/how-to-recover-data-from-wd-my-book-world-edition-nas-device)
now i can make windows xp and 2000 do backflips through hoops, but i am now so retardedly dependent on graphical systems that i cant seem to understand any of this terminal stuff and its even more frustrating when the first line dosnt work.  i know that ubuntu is big with scripts and they are super easy to use, i feel slightly more comfortable using those since i have at least minimal experiance with them.  i only yesterday installed ubuntu and know nothing so far. i got my evolution and firefox and totem movie player, and most of the other simplistic things working but i absolutly cant find any advanced doohykies for the disks and system settings and such.  any help is much appreciated thank you!
z80

---

### Post by rob-ward on 2009-09-17
I arn't sure but isn't md in the kernel not a module???

Once you have entered all of the commands what is in the /media/xyz directory

You can find out by doing 

```
cd /media/xyz
```

then

```
ls
```

---

### Post by z80 on 2009-09-18
> **rob-ward said:**
> I arn't sure but isn't md in the kernel not a module???
 
Once you have entered all of the commands what is in the /media/xyz directory
 
You can find out by doing 
 
```
cd /media/xyz
```
 
then
 
```
ls
```
 
 
well truthfully your question is more confusing than the problem im having, i am fermiliar with the term kernel and thats it.  are you suggesting that i should just skip the first command and see what happens with the rest of it? and then type in the cd command line? remember i am only a day old in the linux world, so most of it is just gibberish right now. in time ill understand more but i have a pretty steep learning curve for the moment.

---

### Post by z80 on 2009-09-18
i have uninstalled the ubuntu dual boot and am going to redo it via wubi, and try it all again.

---

### Post by rob-ward on 2009-09-18
> **z80 said:**
> well truthfully your question is more confusing than the problem im having, i am fermiliar with the term kernel and thats it.  are you suggesting that i should just skip the first command and see what happens with the rest of it? and then type in the cd command line? remember i am only a day old in the linux world, so most of it is just gibberish right now. in time ill understand more but i have a pretty steep learning curve for the moment.

The bit about the kernel wasn't actuially meant as a direct question to you more of a general question incase someone who looked at the thread knew for sure.. But yes I was suggesting you ignore the first command and do the rest and see what happens.

> **z80 said:**
> i have uninstalled the ubuntu dual boot and am going to redo it via wubi, and try it all again.

Well if you have any trouble once you have it reinstalled then let me know.

---

### Post by z80 on 2009-09-20
ok well in my original post i didnt know what all the extra crap was for and i still dont, but i finaly got it to work after checking out device storage manager and seeing that the drive i wanted was in fact sda4 not md4,  so i ended up typing this

 	Code:
 	$sudo mkdir /media/xyz
$sudo mount -t ext3 /dev/sda4 /media/xyz



 and whamo it worked!  i was just foolin around typing in one of the other suggestions further down the page and then i realized i didnt have a md4 and that it looked alot like my sda4 so i did the switcharoo and it worked, it was plain dumb luck that i even thought of it.  so here it is for anyone who needs to access a dead mybook world ed. with ubuntu, in the add remove prog, add device storage manager and check what your disk is called then type those things up there and substitute sda4 for whatever you found in the manager...  that shouldnt have been so damn difficult and mind boggling for me.

---

### Post by PTlinux1 on 2010-01-24
I am currently feeling like the village idiot.  I am new to ubuntu, and this is not the way I like to start learning something.  I recently installed ubuntu, which is lucky for me.  right after installing the new os on an old machine I had laying around, my my book world edition took a dump.  in searching the net i ran across this post.  I have been trying to no avail to follow the directions here and have had little success.  the machine i am using has an ide drive, and the two 500gb drives hooked up to the sata on the mobo.  I am hoping that someone can walk me thru getting my system information so that I can make some more sense out of what I am doing. :confused:

---

### Post by z80 on 2012-01-12
> **PTlinux1 said:**
> I am currently feeling like the village idiot.  I am new to ubuntu, and this is not the way I like to start learning something.  I recently installed ubuntu, which is lucky for me.  right after installing the new os on an old machine I had laying around, my my book world edition took a dump.  in searching the net i ran across this post.  I have been trying to no avail to follow the directions here and have had little success.  the machine i am using has an ide drive, and the two 500gb drives hooked up to the sata on the mobo.  I am hoping that someone can walk me thru getting my system information so that I can make some more sense out of what I am doing. :confused:
sorry i havnt had much reason to be back on this site in a long time. did you ever figure it out?  i could try to help you out if your still havve a problem...

---

