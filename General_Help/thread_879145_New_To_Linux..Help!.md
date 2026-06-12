---
title: "New To Linux..Help!"
date: 2008-08-03
forum: General Help
---

### Post by rraffii on 2008-08-03
Hi guys..im trying to switch from Windows to Linux..im tired of having to reinstall windows .. Linux looks like a great platform..alot of room for customization.but having no previous experience with Linux.the transition is very hard for me...

My problems are..i can't install any program..i have no idea how..

so far i downloaded

Ati driver,RPM,a theme..i don't know how to install any of that..

im not even sure wat RPM is..but it was recommended by ati..i think its required to install other programs..so please HELP ME..

I love watching Movies i have a Creative surround sound 5.1..do u have any programs that support that?

All suggestions welcome..i would love to be able to use this platform. once again HELP!!

---

### Post by bholliday72 on 2008-08-03
This website may help you out a whole lot.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

So far, this is my main gripe with Linux - - if it wants to be mainstream friendly, it really has to make installing software a breeze, not a complicated rethinking process for a Windows user.

---

### Post by arvevans on 2008-08-03
Go to a terminal screen and type:

[INDENT]apt-get install *program_name*[/INDENT]

It doesn't get much simpler than that.

Alternatively, use the System Menu, go to Administration, then to Synaptic Package Manager and scroll down until you see the program you want, click on the Selection box, click on "mark for installation", then go to the top of the Synaptic screen and click on "APPLY".

You don't even have to search for programs that are in the Ubuntu repositories.  It knows where to find them, how to download them, and how to install them.

Arv
_._

---

### Post by arvevans on 2008-08-03
Maybe I should give you a little more information that relates to programs that you may have found and downloaded from non-Ubuntu web locations...?

[LIST=1]
[*]Programs that are in .rpm format are basically set up for loading on some other non-Debian-based versions of Linux.  However you can still install them by using a program called "alien".  To see how this is done, go to a terminal screen and type "man alien" .  Use your keyboard arrows to scroll up & down while reading this man page.
[*]Programs you download that have a .deb suffix are already in the proper format for installation on your computer.  Just find them on a file browser and double-click them.
[*]Programs that are in .tar.gzip format are usually source code which needs to be un-compressed and then compiled to run on your particular computer.
[*]There are several other program formats you may encounter, including .bin and un-defined program formats.  Each of these should have an associated READ_ME file that walks you through the installation process.
[/LIST]

As you get more familiar with Linux, you come to realize that "Linux is not just another version of Windows".  It is significantly different, and as a result new ways of doing things can be a bit overwhelming when your first start to use it.  However, hang in there because much of this difference involves more powerful ways to do things and much more system configuration  options that let you customize your Linux computer to do more for you.

Arv
_._

---

### Post by Ingenue on 2008-08-03
I have found that if you come to a brick wall with Ubuntu or any other Linux distro, someone els has already had almost the same problem before.
Quite often by searching the forums I can find a guide or other helpful post for my issue. There are also a plethora of great guides on the internet, such as :

[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

[http://www.linux-books.us/ubuntu_0002.php](http://www.linux-books.us/ubuntu_0002.php)

[http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/](http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/)

I wish I could help more, but I'm still pretty new here. :)

---

### Post by mb_webguy on 2008-08-03
> **bholliday72 said:**
> \So far, this is my main gripe with Linux - - if it wants to be mainstream friendly, it really has to make installing software a breeze, not a complicated rethinking process for a Windows user.
I think installing software on Linux systems, at least on distributions with good repositories, is actually much easier than on Windows.  All you have to do is select the application from the list and click a button, or else enter one command in the terminal.  It doesn't get much easier than that.

True, installing software that isn't in the repositories can be a bit more tricky, but only a bit.  At worst, it's still just three commands in the terminal, and they're always the same: *./configure*, *make*, and *sudo make install*.  

For those new to Linux, here's an invaluable resource on "[How to install ANYTHING on Ubuntu]("http://monkeyblog.org/ubuntu/installing/")".

---

