---
title: "Xserver problem"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by Monkey-Dude on 2005-04-08
When i try to boot my Ubuntu OS, it goes through all the startup processes and says [Ok] to them all... then the screen blinks slowly 3 times and then it tells me that it couldn't start Xserver... And then i'm stuck with a lausy "dos" promt...

I don't understand why, because Ubuntu works flawless when i use the Live CD...

My PC specs:

P4 2,8 Ghz HT CPU
2x512 MB RAM
(FSB = 200x4)
Club3D GeForce 6600GT 128MB GDDR
"60 GB" Excelstor IDE HDD 
(10GB WindowsXP Pro, 40GB Games and apps, 1GB Swap and 6GB ubuntu)
"160 GB" Maxtor IDE HDD
(150 Storage)

Xserver version

XFree86 Version 4.3.0.1
XProtocolVersion 11, Revision 0, Release 6.6
OS Kernel: Linux 2.6.8.1 i686

(yes, i am aware that there is a 4.5.x.x version of XFree86 but i don't know have to get it and install it into Ubuntu with only the "dos" promt thingy at my disposal...)

Any help would be much appriciated....

Monkey-Dude

---

### Post by erkki70 on 2005-04-08
Hi,
You will probably get a lot of very useful information about your problem if you use the search tool on these forums.
For example:
[http://ubuntuforums.org/search.php?searchid=481104]("http://ubuntuforums.org/search.php?searchid=481104")
[http://ubuntuforums.org/search.php?searchid=481154]("http://ubuntuforums.org/search.php?searchid=481154")
I know it's a lot of reading but OTOH it will be a very good way for you to get to know more > the "dos" promt thingy and make your way. ;)

Basically, I guess you need to install the right drivers for your card and you will find install instructions in the posts.

Hope this helps.

Cheers,
Erkki

---

### Post by jobezone on 2005-04-08
For a start, try to re-configure x.org using the comand:

sudo dpkg-reconfigure xserver-xfree86

---

### Post by Monkey-Dude on 2005-04-09
Thanks for the replys guys....

But sadly, my computer still dosn't want to cooperate....
Either i set it up all wrong... 
Else Warty isn't very good at handling my GF6600GT...

My plans are now to download Hoary and try it out instead...
Think it might be a bit more compatible to my system....

---

### Post by pugrit on 2005-04-11
monkeydue:

edit the config.  but first look at the logs on what casued the problem. then simple erase that entry on the config. 

i think its on the X11 subfolder under etc..im not sure though..i had similar problems.. the config had "COLOR" in it an dthe log says its unidentified so i simply erased it.

then reboot.

---

### Post by elasticwings on 2005-04-11
Could you post what is in your /etc/X11/xorg.conf file?

---

### Post by Monkey-Dude on 2005-04-11
Oki..............................

I seem to be missing one xorg.conf in my /etc/X11 directory....

Do any of you suspect THAT might be the problem....?

---

### Post by erkki70 on 2005-04-11
Hi,
If you're using Warty and didn't change your X server then you don't have a xorg.conf file but a XF86Config file from your XFree server.
Post this file so people could see what's wrong maybe...
Cheers,
Erkki

---

### Post by Monkey-Dude on 2005-04-12
same dir...?

---

### Post by Monkey-Dude on 2005-04-16
Thanks for all the help all of you...

but none of it would work...

i've just installed Hoary and now it works...

---

