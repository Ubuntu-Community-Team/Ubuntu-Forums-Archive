---
title: "Software installation"
date: 2006-02-08
forum: Installation &amp; Upgrades
---

### Post by hellmaker on 2006-02-08
ive just learned to install software by hand in ubuntu 5.10.

So here are some newbie question:

ive been installing software on my buntu in the terminal window.

1. how do i startup those programs in the terminal with commands ?
2. how do i make a shortcut to the gui, so i can just klick on an icon to start it?

I have been tryin to install aegis through the menu, but it do not show up in my menu Programs->accessories. But it wont show up there, is that a bug ? and how do i start it

From windows xp iam used to the following partitions
c:system (for system windows)
d:programs (for software installation)
e:data (for storage)

And when i look on ubuntu it complete different. Is there any smart way or tips on how to set it up for easy accessing later ? is for eksample smart to install programs on the desktop ?!?, or is it smarter to make an folder under my user, i dont know just askin.

regards a newbie.

---

### Post by TrendyDark on 2006-02-08
Your question about software depends on  what software you installed and how it's supposed to be used.

As for your file system, Linux is a little different when it comes to different partitions or hard drives. In Windows, each is mounted as a drive with a certain letter, whereas in Linux, you choose where you want the drive to mount. 

For example, I have two 80gig hard drives, one has Ubuntu on it, the other I use to store my massive music collection. In Windows that other hard drive with my music would be something like Drive E:, but in Linux, I just have it mounted in my home directory under a folder called "Music".

---

### Post by hellmaker on 2006-02-08
Well my problem is to trying to make sence of... eks.. when i install in windows xp, it automatically give me an icon to klick and start the program,  and i am pointing the install to an location. 

i already know that ubuntu doesnt use letters like c-d-e etc.... here is an example.. iam using my menu in ubuntu programs-add application. I do install example gaim, and it shows up in my menu... but where is my files when i brows for it... where did it install.. can i browse the loction, has ubuntu an specified location for installation, and does all the software install at this location ?

antoher scenario when i use apt-get update, and apt-get install xxxxxxx

does this method install in the same location as program->add apps? 
lets say i do install gaim with the last method with apt-get, how can i start the software intalled. Does this method automatically provide me with an icon in the desktop menu ?

hehehe.... i hope this make sence... i think this questions is rather important to new beginners.... ubuntu is rather easy to use... but as an ex win xp user, we are used to just startup an exe file, and choose where to install

---

### Post by TrendyDark on 2006-02-08
makes perfect sense. I'm not an advanced linux user or a pro, I know a little bit. I've been using Ubuntu as my main distribution for about 3 months now and I had windows for gaming purposes up until Saturday last week. 

I'm pretty sure, although, that the files are installed under /usr/share/, which to browse you can do easily, if you want to change anything you'll have to be under root. To file browse as root type this in your terminal:

```
sudo nautilus
```

---

