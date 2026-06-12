---
title: "Error with update managers."
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by abu123 on 2008-12-16
I'm new to Linux and this forum.

I installed ubunto studio 8.1  2 days ago. 

in the process of installing dvdcss protection removal I inadvertantly damaged something and get the following error message when ever trying to update thru either the GUI or the terminal

I have tried suggestions of variuos other threads but continue to the the same error:

E: Type ‘rm’ is not known on line 56 in source list /etc/apt/sources.list

please kindly assist

Thanks

---

### Post by taurus on 2008-12-16
There is something wrong with line 56 in your /etc/apt/sources.list.  So, you need to edit it

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and either remove it or place a # in front of it to comment it out.  Then, save it and close down the gedit window.  

Now run

```
sudo apt-get update
sudo apt-get upgrade
```
And if you are not sure which line it is, just post your /etc/apt/sources.list here.

---

### Post by abu123 on 2008-12-16
thank you for speedy reply.

I did try this prior to posting and agin after your suggestion but at your first step.

Getedit open in the GUI with following error

[B]Could not open the file /etc/apt/sources.list.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Character encoding. {scroll down list with}  current locale UTF-8 or weestern  ISO -8859-15 or other.
[/B]

please assist thanks

---

### Post by taurus on 2008-12-16
What happens when you run this command from a terminal?

```
cat /etc/apt/sources.list
```

---

### Post by abu123 on 2008-12-16
a very long page loads and scrolls for 40-60 seconds.

looks jibberish

---

### Post by taurus on 2008-12-16
You mean it doesn't look something like this?

```

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

```

---

### Post by abu123 on 2008-12-16
not at all that I can read. 
mine I cannot... last few lines are as follows:

Ü0;st1§docst: ßst1§docst:ß$ 62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c
Ü0;st1§docst: ßst1§docst:ß$

---

### Post by taurus on 2008-12-16
Looks like you mess up your /etc/apt/sources.list big time.  Remember what you did to your /etc/apt/sources.list?

Let's see if you have a backup copy of /etc/apt/sources.list.  What's the output of this command?

```
ls -la /etc/apt/sources.list*
```

---

### Post by abu123 on 2008-12-16
I need to go to work now will be back in about 4.5hours.  I will try any recommendations on returning.. Thnaks again

---

### Post by Casper Hansen on 2008-12-16
Type

```
sudo gedit /etc/apt/sources.list
```

---

### Post by abu123 on 2008-12-16
> **Casper Hansen said:**
> Type

```
sudo gedit /etc/apt/sources.list
```



some result as per my second post above,

PLease what can I do?

 is it possible to replace this file?

Does Linux offer a restore like M$?

---

### Post by abu123 on 2008-12-16
BUMP

Really could do with some help on this.  Sorry to sound impatient.

---

### Post by taurus on 2008-12-16
Have you looked at the post #8?

---

### Post by abu123 on 2008-12-16
Sorry missed it the first time.

result as follows:

[B]-rw-r--r-- 1 root root 11624875 2008-12-15 22:41 /etc/apt/sources.list
-rw-r--r-- 1 root root        0 2008-12-14 23:45 /etc/apt/sources.list~
-rw-r--r-- 1 root root     3166 2008-12-15 22:41 /etc/apt/sources.list.save

/etc/apt/sources.list.d:
total 12
drwxr-xr-x 2 root root 4096 2008-12-16 13:51 .
drwxr-xr-x 4 root root 4096 2008-12-15 23:11 ..
-rw-r--r-- 1 root root  230 2008-08-18 21:13 medibuntu.list
[/B]

---

### Post by taurus on 2008-12-16
Try these.

```
sudo cp /etc/apt/sources.list  /etc/apt/sources.list.bak
sudo cp /etc/apt/sources.list.save  /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by abu123 on 2008-12-16
Thank you immensely  Taurus

Done the trick.

---

### Post by taurus on 2008-12-16
You're welcome.  It's safe to remove this one, /etc/apt/sources.list.bak, since it's junk anyway.

```
sudo rm /etc/apt/sources.list.bak
```

---

### Post by abu123 on 2008-12-16
have done!

Is there a backup and restore programme for linux. 

like System Restore for M$ which takes an image copy of current states.

---

