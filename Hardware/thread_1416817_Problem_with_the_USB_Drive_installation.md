---
title: "Problem with the USB Drive installation"
date: 2010-02-26
forum: Hardware
---

### Post by frankyboy1984 on 2010-02-26
Hello all,

First and foremost i should point out that this is my first time trying out Ubuntu.

Here is my situation: I own a an Acer Aspire one ZG5. Originally it came with a 8 GB SSD drive (That was slow as hell) and windows XP.

The whole thing was rather slow so i opted to add some ram and change the SSD to a regular 1.8'' Samsung HS06THB Hard drive. 

All this has been done now,the screws in the laptop made me angry a bit but i prevailed :)

My problem is that now i wanna install Ubuntu 9.10 Netbook remix on it to try it out but i can't seem to make a bootable USB drive that can work. Below is how i tried doing it if you see where my fault is kindly point it out :)

Here is how i tried doing it: 

[LIST]
[*]Formatted my 1GB USB key with the Windows original program.
[*]Dowloaded the most recent Ubuntu Netbook Remix ISO file from [http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)
[*]Then i downloaded the unetbootin program from there [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[*]Got that info on that website : aroudn the middle of the page it under the title Copy files to USB key adn then under From Windows it say at the bottom to alternatively use Unetbootin to create a bootable USB drive.
[*]I then used the Unetbootin program to mount the whole ISO file on my USB key
[*]When it was done and Unetbootin asked me to reboot the computer i closed my computer and when it was closed, removed teh USB key  adn put it in my laptop USB drive.
[*]I then started my laptop, went in the BIOS boot priority option and put my USB key(which the BIOS detected) to number 1.
[*]Soon has i exited and saved changes, the BIOS message i keep getting is  No bootable device -- insert boot disk and press any key
[/LIST]

I should mention that the Hard drive i put in(Samsung HS06THB had no OS on it, so whatever i need to do to make it work needs to be done from my desktop computer that runs on XP.

Thanks in advance for the help and if you  need more info feel free to ask i will check this thread regularly.


P.S. If there is already a thread on that feel free to redirect me to it.

---

### Post by ubunterooster on 2010-02-26
many usb drives are not bootable. I know pny's and HP's aren't. sandisks are.

---

### Post by dabl on 2010-02-26
> **frankyboy1984 said:**
> 

Here is how i tried doing it: 

[LIST]
[*]Formatted my 1GB USB key with the Windows original program.

[/LIST]



Right there was probably a mistake, if you chose "NTFS" filesystem.

Here's a pretty good guide:

[http://kubuntuforums.net/forums/index.php?topic=3089474.0](http://kubuntuforums.net/forums/index.php?topic=3089474.0)

Note: There's no difference between Kubuntu and Ubuntu, for this topic, except the names of the text editor (gedit for Ubuntu, kate for Kubuntu) and the root mode launch command (gksu for Ubuntu, kdesudo for Kubuntu).

@ubunterooster, I've got a bootable PNY that says you can make them bootable!  ;)

---

### Post by ubunterooster on 2010-02-26
@dabl: ?! really! sorry.
-humbledrooster

---

### Post by dabl on 2010-02-26
> **ubunterooster said:**
> @dabl: ?! really! sorry.
-humbledrooster

Heh heh heh.  Yep, and if you want to get fancy with your PNY stick, here's your guide:

[http://kubuntuforums.net/forums/index.php?topic=3107512.0](http://kubuntuforums.net/forums/index.php?topic=3107512.0)

;)

---

### Post by frankyboy1984 on 2010-02-26
Wow thanks for the quick reply i'll be sure to try it out tomorow once i'm done work and done reading the link you gave me dabl.

---

### Post by ubunterooster on 2010-02-26
@dabl: that helps. thanx

---

### Post by frankyboy1984 on 2010-03-02
Problem fixed thanks for all your help

---

