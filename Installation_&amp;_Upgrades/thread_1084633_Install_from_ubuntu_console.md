---
title: "Install from ubuntu console?"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by Deddly on 2009-03-02
I have succeeded in installing just the text console of Ubuntu. I have mounted my external CDROM with a xubuntu cd inside it (I cannot boot from this device)

Since I can't boot from the CDROM, can I install xubuntu from the command-line I already have installed? If so, how? (Be gentle...)

--
Ed

---

### Post by taurus on 2009-03-02
Is your machine connected to the net?

```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

---

### Post by Deddly on 2009-03-02
> **taurus said:**
> Is your machine connected to the net?

```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

Sadly it isn't, which makes the process rather more complicated...

---

### Post by taurus on 2009-03-02
Insert the CD into the drive.  Then from a terminal, run

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

---

### Post by Deddly on 2009-03-02
> **taurus said:**
> Insert the CD into the drive.  Then from a terminal, run

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

Thanks very much for that. But when I type it, it tries to access the built-in CDROM (that doesn't work) instead of the USB one - sorry to ask such a newbie question, but... what should I do now? The USB CDROM is mounted as cdrom1

--
Ed

---

### Post by taurus on 2009-03-02
You can redirect it to point to your external cd drive.  What are the outputs of these commands?

```
cat /etc/fstab
ls -la /media
df -h
```

---

### Post by Deddly on 2009-03-02
> **taurus said:**
> You can redirect it to point to your external cd drive.  What are the outputs of these commands?

```
cat /etc/fstab
ls -la /media
df -h
```

"cat /etc/fstab":
amongst other things, it says:

/dev/scd1/        /media/cdrom1 ...

"ls -la /media":
it says something like:
cdrom -> cdrom0
cdrom0
cdrom1


How do I get cdrom to point to cdrom1?

---

### Post by taurus on 2009-03-02
```
cd /media
sudo rmdir cdrom
sudo ln -s cdrom1 cdrom
ls -la
```

---

### Post by Deddly on 2009-03-02
> **taurus said:**
> ```
cd /media
sudo rmdir cdrom 
```

This returns the error message:

rmdir: failed to remove 'cdrom': Not a directory

---

### Post by taurus on 2009-03-02
```
cd /media
sudo rm cdrom
sudo ln -s cdrom1 cdrom
```

---

### Post by Deddly on 2009-03-02
OK! Thanks for that. Now cdrom1 is cdrom.

Going back to the instructions, then:

> **taurus said:**
> Insert the CD into the drive.  Then from a terminal, run

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

I get as far as the last step, where I get the following error:

E: Couldn't find package xubuntu-desktop

---

### Post by taurus on 2009-03-02
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by Deddly on 2009-03-02
> **taurus said:**
> Post your /etc/apt/sources.list.

deb cdrom:[Xubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030.3)]/ intrepid main multiverse restricted

deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030)]/ intrepid main restricted

---

### Post by taurus on 2009-03-02
I guess you only have two lines in /etc/apt/sources.list.

Edit /etc/apt/sources.list

```
sudo nano -Bw /etc/apt/sources.list
```
and place a # in front of the second line.

```

**[COLOR="Blue"]#[/COLOR]**deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030)]/ intrepid main restricted

```
Save it and exit with <Ctrl>x.

Then run

```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

---

### Post by Deddly on 2009-03-02
> **taurus said:**
> I guess you only have two lines in /etc/apt/sources.list.

Edit /etc/apt/sources.list

```
sudo nano -Bw /etc/apt/sources.list
```

This returns:

sudo: nano: command not found

---

### Post by taurus on 2009-03-02
How about vi?

```
whereis vi
```

---

### Post by Deddly on 2009-03-02
> **taurus said:**
> ```
whereis vi
```

vi: /usr/bin/vi /usr/share/man/man1/vi.1.gz

---

### Post by taurus on 2009-03-02
```
sudo vi /etc/apt/sources.list
```
Then press i to get into insert mode and when you are done inserting # in there, press Esc and then :wq! to save and exit.

---

### Post by Deddly on 2009-03-02
> **taurus said:**
> ```
sudo vi /etc/apt/sources.list
```
Then press i to get into insert mode and when you are done inserting # in there, press Esc and then :wq! to save and exit.

OK that seemed to edit ok. 

But when I do:

```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

I get:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package xubuntu-desktop

---

### Post by Deddly on 2009-03-03
I still haven't figured it out..any ideas?

---

### Post by taurus on 2009-03-03
How did you manage to install the server (text only) on your machine?  There are other ways to install Ubuntu on your machine if it can't boot from the CD.

[https://help.ubuntu.com/community/Installation/](https://help.ubuntu.com/community/Installation/)

---

### Post by Deddly on 2009-03-03
> **taurus said:**
> How did you manage to install the server (text only) on your machine?  There are other ways to install Ubuntu on your machine if it can't boot from the CD.

Well I have a wierd problem with my internal DVDROM where it only reads DVDs, not CDs. I downloaded the Ubuntu DVD and it failed to install, presumably because I only have 255MB. So I installed text version thinking it meant text version of the installer...voila: Ubuntu console...

I don't know where to go from here since I don't know the console lol

---

