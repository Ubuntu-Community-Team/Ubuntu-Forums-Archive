---
title: "How does Ubuntu detect flash drives?"
date: 2008-11-19
forum: General Help
---

### Post by Masterofpsi on 2008-11-19
Just as the title says. The reason is that I have a Bash script that I would like Ubuntu to execute whenever a flash drive is plugged in.

Thanks in advance.

---

### Post by volaer on 2008-11-19
as far as i know if you have 8.04.1 hardy, it should detect your flash drive automatically whenever you attach it into your machine. Then you can unmount it by right clicking the temporary icon on your desktop then click unmount. 

Again, it should be automatically detected...

---

### Post by Masterofpsi on 2008-11-20
Right, and it does. I want to know where the code is that does that, so that I can append a script to it.

---

### Post by OutOfReach on 2008-11-20
I think it is HAL (Hardware Abstraction Layer) that automounts USB drives (I may be wrong) so it must be somewhere in HAL's source code.

---

### Post by mc4man on 2008-11-20
I really can't answer your question but if nothing else arises can give you a way in.
(am using 8.04 tonight

edit: a better way
[http://ubuntuforums.org/showthread.php?t=502864](http://ubuntuforums.org/showthread.php?t=502864)

If you create an empty text file on the usb drive named autorun that will trigger a different event. (autorun prompt

Ubuntu will not allow software autorun without confirmation, hence the empty file.
The event is reflected by this mimeapps line 'x-content/software='

The only default options for this are "do nothing", "open folder", "ask what to do", "open autorun prompt"

What you can do to bypass the prompt is to create a new option which runs your script and choose it as the default action (nautilus -> edit -> preferences -> media -> software.

Basically all you need to do is take a .desktop in ~/.local/share/applications and simply change it's Exec= to your script. (works very well if your script is in your home dir. (Exec=./scriptname

Then you open ~/.local/share/applications/mimeapps.list and add your .desktop to the x-content/software= line. First listed is default action.

After that inserting your flash drives will run your script. (as long as they have an autorun file in root dir. (just don't put in a folder

What .desktop you use or how it gets into ..../applications is fairly open ended. There are 3 ways, use an existing one that your not using for any of the default actions on removable media, or copy one from /usr/share/applications with a name change on the way in, or create a new one.

The only things that matter are that the .desktop is 'valid', you change the Exec=,  and that when adding the .desktop to mimeapps.list that you use the .desktop's real name. (what's displayed in .../applications is not always the .desktops name, when you open it in gedit note what it is. (i'm referring to what's displayed in the text editor tab, not name= in the .desktop


That line is not created by default in mimeapps.list. You can either force it's creation or just manually enter it. EX. how I set it to run a auto rip script using the 'borrow .desktop' method for dvd's (obviously no need to use a flash drive to trigger, the .desktop and script were just handy to test this method

```
x-content/software=gxine.desktop;nautilus-autorun-software.desktop;
```

In this case I'm using gxine's .desktop to run a script named rip (Exec=./rip

To force the line creation open the ..../preferences/media/software and switch from what's set to something else, close, reopen, repeat a time or two and end up on "open autorun prompt". The line should now be there with 1 entry

Some basic info and Ex. of copy .desktop method

[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)

---

