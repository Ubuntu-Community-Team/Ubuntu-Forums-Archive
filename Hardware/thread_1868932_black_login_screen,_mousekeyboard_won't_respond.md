---
title: "black login screen, mouse/keyboard won't respond"
date: 2011-10-25
forum: Hardware
---

### Post by noodles19 on 2011-10-25
toshiba satellite l355-s9700. running ubuntu 11.04 no dual boot just linux. So after some great times getting use to using linux this happens.... hit power button, bios starts up, enter bios pswd, purple ubuntu sceen comes up then it goes to my login screen... BUT no sound was made. My custom background no longer shows up (a little paper icon with a red x does) and even the login gray box is different and my keyboard or mouse wont respond. The mouse is also stuck at the lower right corner. Show the correct date and time up at the top middle. I have no clue what to do??? If I hit left shift key when starting, it will let me run the shell but I have no clue how to fix this in there. PLEASE HELP

---

### Post by varunendra on 2011-10-25
Can you boot normally from a live cd? If yes, maybe posting contents of syslog, dmesg in /var/log directory may give us some clue.

When you press the shift key, do you get the option the option to boot in 'Recovery' mode? Try that and in the recovery menu, select 'dpkg' option. That will try to repair broken packages if any. You can also do it manually from the shell by
```
sudo dpkg --configure -a
```

From the same recovery menu, try to boot with failsafeX to see if it lets you.

---

### Post by noodles19 on 2011-10-26
okay so after putting in the dpkg --configure -a code it runs for a second or two then just repeats like a mad man until i hit scroll lock 

(gtk-update-icon-cache-3.0:1359): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file ' /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache' : No such file or directory

and it just keeps going on forever.... ?

---

### Post by noodles19 on 2011-10-26
oh and I don't know where this failsafex is that you speak of....

my options are 

ubuntu, with linux 2.6.38-11-generic
ubuntu, with linux 2.6.38-11-generic (recovery mode)
previous linux versions
memory test (memtest86+)
memory test ("",serial console 115200)

---

### Post by noodles19 on 2011-10-26
as far as booting up from the live cd it isnt a probably... what exactly do you need from the /var/log directory?

---

### Post by varunendra on 2011-10-26
> **noodles19 said:**
> I don't know where this failsafex is that you speak of....

my options are 

ubuntu, with linux 2.6.38-11-generic
[COLOR=Red]**ubuntu, with linux 2.6.38-11-generic (recovery mode)**[/COLOR]
previous linux versions
memory test (memtest86+)
memory test ("",serial console 115200)You will see the 'failsafeX' option in the next menu which comes after selecting the (recovery mode) option highlighted above.

> **noodles19 said:**
> as far as booting up from the live cd it isnt a probably..
I couldn't understand this part of your post, can you please explain it to me? Whether you can boot successfully into a live session using a Live cd or not?

From **/var/log** directory, the contents of the **syslog** and **dmesg** files 'may' provide some clues. Since there would be a huge wall of text in those files, it is a good idea to copy-paste their contents in pastebin ([here]("http://paste.ubuntu.com/")), and post only the link of the pastebin page (generated after you post your contents there) in your next post here.

---

### Post by noodles19 on 2011-10-26
Sorry I meant to say it was not a problem to start up using my live cd.....

there appears to be two dmesg files one named dmesg and the other dmesg.0 and two syslogs
here is dmesg
[HTML]http://paste.ubuntu.com/719843/[/HTML]and here is dmesg.0
[HTML]http://paste.ubuntu.com/719845/[/HTML]and here is syslog
[HTML]http://paste.ubuntu.com/719853/[/HTML]and here is syslog.1
[HTML]http://paste.ubuntu.com/719868/[/HTML]

---

### Post by varunendra on 2011-10-26
First off, please remove those 'html' tags from your links to make them normal 'click-to-go' links. :)

About the multi-file confusion. The ones without suffix are the most recent ones (dmesg is created fresh every time you boot your system). The ones with suffix are older (the higher the suffix number, the older the file is). After a few ones are created, even older ones are started to be stored in 'gz' archives (in case you need to see a much older log of a category).

So if a system boots, but crashes after a certain point, the most recent logs may contain some relevant info. In some cases, the one 'before' the most recent one may have that kind of info. Hence those .0, .1 files.

I will look into those files when I get enough time to dig them, and will try to see if there is something I can understand ;) (to be honest, I don't understand most of their part, so the only chance when I may come up with something useful is if they contain something too obvious to miss..)

---

### Post by noodles19 on 2011-10-26
THANK YOU SO MUCH.... I appreciate any help you can give me. I love the linux community it is such a breath air seeing how the linux community flows :D

---

