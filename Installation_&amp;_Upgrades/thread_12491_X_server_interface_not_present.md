---
title: "X server interface not present?"
date: 2005-01-24
forum: Installation &amp; Upgrades
---

### Post by Sefyroth on 2005-01-24
Hi,
I am a complete newbie with linux based software, and I decided to install Ubuntu with my already existing Windows XP, installation went okay, but after the reboot, I get a command line login and a message tells me that my X server interface (or something close to it) is missing or not installed, they refer to XFree86.org for help, but I didn't know exactly what was the problem, can someone help?


Thanks in advance, Sefyroth

---

### Post by hardcandy on 2005-01-25
What type of video card do you have? During installation did you have a graphical interface?

---

### Post by Sefyroth on 2005-01-25
I have an ATI radeon 9200 (that's 128mb of memory), almost new (4 months) and the graphical interface during the installation was limited to colours and text, similar to a windows installation (not the same interface as a complete installation or as in the "Live CD" thing) thanks again and Oh, is there a way to get Windows to be the first choice in the GRUB boot loader? the one that is highlighted by default and loads if you dont touch anything? thanks!

---

### Post by grj on 2005-01-25
To get Windows to be the first entry in Grub:

Perform the following as sudo
Using a text editor open /boot/grub/menu.lst
Scroll down to the bottom
There will be some obvious blocks of text
One of them will contain the information to start Windows
Move it to the top of the other text blocks

If you look back at the top of the file, there is a line
default 0
this tells grub to use the first entry in its list.


X Problems:
Perform the following as sudo
Using a text editor open /etc/X11/XFree86Config-4
Scroll down to the bottom and look for section 'Device'
Make note of the 'Identifier'
Scroll further down to the 'Screen' section and check to make sure it is using that device

If that looks ok, copy /etc/X11/XFree86Config-4 to a reply here and people can look at it.

---

### Post by Sefyroth on 2005-01-25
Sorry to ask, but I'd need a much more detailed walkthrough... As i told, I can only use the command line and know nothing about that... What do you mean by text editor??? is there one by default with Ubuntu? thanks a whole lot for this information though! I'll try this with what i know and feedback, thanks

---

### Post by grj on 2005-01-25
Sorry, it is easy to assume someone knows more than they do. Nano is a text editor that is rather easy to use.

At the command line type

sudo nano /boot/grub/menu.lst <enter>
If prompted for password, enter your password.
make the changes above.

sudo nano /etc/X11/XFree86Config-4 <enter>
If prompted for password, enter your password
follow above notes.

<enter> means press the Enter key.

/etc/X11/XFree86Config-4 may be /etc/X11/XF86Config-4

Linux is case sensitive so watch for that.

Here are some basic commands:

ls - That is an ell, will list the files in a directory
cat /etc/X11/XF86Config-4 | less - will display the contents of text files on the screen in a way that they can be viewed with the <Page Up> and <Page Down> keys. It will be read only.

---

### Post by Sefyroth on 2005-01-25
[QUOTE=grj]Sorry, it is easy to assume someone knows more than they do. Nano is a text editor that is rather easy to use.

At the command line type

sudo nano /boot/grub/menu.lst <enter>
If prompted for password, enter your password.
make the changes above.

sudo nano /etc/X11/XFree86Config-4 <enter>
If prompted for password, enter your password
follow above notes.

<enter> means press the Enter key.

/etc/X11/XFree86Config-4 may be /etc/X11/XF86Config-4

Linux is case sensitive so watch for that.

Here are some basic commands:

ls - That is an ell, will list the files in a directory
cat /etc/X11/XF86Config-4 | less - will display the contents of text files on the screen in a way that they can be viewed with the <Page Up> and <Page Down> keys. It will be read only.[/QUOTE]
 thanks a lot, i just needed to know how to start text editor and use it :P thanks a lot lot, I'm going to try it and come back here if it works!

---

### Post by Sefyroth on 2005-01-25
Hum... I kinda don't know what's happening, but when I open the file and try to modify stuff, it works but I can't "Write out" my work... Have no clue what's happening...

And I might have found the problem for the X thing.. There is no XFree86Config-4 file....

Where can I get it???

And by the way, it would be nice that someone write some kind of basic guide to basic commands such as Is (to get the feeling for the command line interface, cause I can't do nothing right now, since I'm a newb :P) thanks a lot in advance again

---

### Post by hardcandy on 2005-01-25
[http://ubuntuguide.org/](http://ubuntuguide.org/) for some basic stuff, look in the Grub/bootloader section. 
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto) for the ATI driver. 
[http://www.ubuntuforums.org/showthread.php?t=3567](http://www.ubuntuforums.org/showthread.php?t=3567) for ATI acceleration.

---

### Post by Sefyroth on 2005-01-26
Okay, I got the thing for the GRUB loader, but my XFree86Config-4 folder (or file) is still missing... If i need to install it, will I have to do it from a floppy, a cd, or can I do it from my windows XP? thanks a lot for the rest of the info though!

edit: little update,:
I found that it's not the folder XFree86Config-4, but really "XF86Config-4" instead

And I did look at the Device Identifier which was Ati technologies Inc, Radeon 9200, etc and it was the same as in  the screen part, I guess there is no problem there....

I would have liked to post the XF86Config-4 file here, but don't know how to copy it to a floppy disk (and will windows be able to read it?)... I can try stuff, but I probably won't get far without any knowledge of command line stuff... I hate black and white screens :P

And, when i type the "sudo apt-get install fglrx-driver" it tells me that e: is not something and that the package doesn't exist... don't know if that has something to do with it!

---

### Post by Sefyroth on 2005-01-27
it still doesnt work...

---

