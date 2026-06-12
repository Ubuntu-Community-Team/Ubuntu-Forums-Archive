---
title: "Aaaaah!! Sane doesn't work, neither does xsane"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by GabrielWolff on 2006-11-23
Hey,

I got a scanner today, a BenQ S2W 3300U, and I tried to find software for it.

Attempting to install sane, I just run ino the following problem:
```
gabriel@gabriel:~$ sudo apt-get install sane
Reading package lists... Done
Building dependency tree... Done
sane is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
gabriel@gabriel:~$ sane
bash: sane: command not found

```
Whatwhat???

When trying to run xsane, I get the following message:
"No devices are available"

I got my scanner running and connected. How do I configure it?

thx

Gabriel

---

### Post by arkhitekton on 2006-11-24
Use:
sudo apt-get install sane-utils
to install the sane command line utilities.

I've been trying to debug a scanner installation and couldn't find the command line utilities either.  But I've now resolved my problem to a broken USB hub!

---

### Post by GabrielWolff on 2006-11-24
And still:
```
gabriel@gabriel:~$ sane
bash: sane: command not found
gabriel@gabriel:~$

```
Is "sane" the wrong command?

G

---

### Post by arkhitekton on 2006-11-24
I don't think sane is a command.  It's the name of the package.  The website is at:  [www.sane.org]("http://www.sane.org")

The commands that I've used are:
**sane-find-scanner**
to locate connected scanners.
Or you can use:
**scanimage -L**
to also report on connected scanners.

scanimage is the sane command line interface.  It has a number of command line options.  See:
**scanimage --help**
Or:
**man scanimage**

You can launch xsane from a terminal by typing:
**xsane&**
[The & runs the command as a separate thread from the terminal.  The consequence is you get your terminal prompt back immediately and can use the terminal for something else.]

---

### Post by Duroon on 2006-11-26
> **arkhitekton said:**
> I don't think sane is a command.  It's the name of the package.  The website is at:  [www.sane.org]("http://www.sane.org")

The commands that I've used are:
**sane-find-scanner**
to locate connected scanners.
Or you can use:
**scanimage -L**
to also report on connected scanners.

scanimage is the sane command line interface.  It has a number of command line options.  See:
**scanimage --help**
Or:
**man scanimage**

You can launch xsane from a terminal by typing:
**xsane&**
[The & runs the command as a separate thread from the terminal.  The consequence is you get your terminal prompt back immediately and can use the terminal for something else.]

The sane-find-scanner command locates my scanner (a Visoneer 8100) however scanimage -L says there is no scanner attached to my system. I guess maybe my scanner is not supported?

Edit: Well I did some checking and my scanner is definitely not supported. Oh well back to the drawing board I guess.

---

### Post by matchstich on 2006-12-15
ok, my scanner is detected how do i get the firmware installed, thanks

---

