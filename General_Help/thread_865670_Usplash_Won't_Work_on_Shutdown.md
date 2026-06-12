---
title: "Usplash Won't Work on Shutdown"
date: 2008-07-20
forum: General Help
---

### Post by meoblast001 on 2008-07-20
Ok.... I'm really close to going off and ranting in the #ubuntu channel of Freenode. When I shut off my computer, Usplash does not start and a terminal is displayed for the majority of the shutdown process. During the last few seconds of the shutdown, Usplash will show. I want Ubuntu to function like new so this error is unacceptable to me. Don't tell me to reinstall Ubuntu because my crappy Dell CD drive is broken and I have no flash drive and i CANNOT afford a new computer. Thank you in advanced.

---

### Post by Polygon on 2008-07-21
if there are errors or warning messages then the usplash thing wont show, i know it happens to me too. for most people its network manager not shutting down properly and it throws warnings whenever you shut down

currently there really is no way for you to fix, it, even if you reinstall. Just hope that it gets fixed in the next ubuntu release ;)

---

### Post by coffeecat on 2008-07-21
[This is a known bug]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/216266"). About halfway down you'll find a fix posted:

> 
                 [FONT=monospace]I found a workaround! (courtesy of prinknash on ubuntuforums)
 Follow it word for word (cut the text..  Apply command change..  paste the text..  Apply command change)
 1. Go to System - Administration - Login Window.
 2. Under 'General', press "Edit commands ...'
 3. Select 'Halt command' - in 'Path' box, cut the text in quotes (I.e. "Shut down via gdm") - press "Apply command change" - paste the text back - press 'Apply command change'
 4. Select 'Reboot command' and do as for 3. above
 Try restarting a couple of times and see if this has fixed the problem.
Apparently this has fixed the problem for numerous people who have the boot splash but no shutdown splash.
Now, could the solution/workaround give us a possible avenue to explore which might lead to a fix?
 I think this makes my first presumption correct. The networkmanager bug has nothing to do with this at all. It's GDM not hiding the error.[/FONT][FONT=monospace]
[/FONT]
        

I can confirm that this works for me on my desktop Hardy installation. You'll still get the NM error messages visible on the first shutdown, but subsequent ones you'll get the usplash.

By the way, I've posted this for my benefit, not yours. :wink: This is affecting the latest Linux Mint which I've got on my laptop, so when I next boot into it, I can find this thread and fix Mint as well. :)

---

### Post by rainwalker on 2008-08-02
I have this happen occasionally; it somehow fixes itself and then starts again

---

### Post by mandrill on 2008-08-12
> **coffeecat said:**
> [This is a known bug]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/216266"). About halfway down you'll find a fix posted:

[FONT=monospace]
[/FONT]
        

I can confirm that this works for me on my desktop Hardy installation. You'll still get the NM error messages visible on the first shutdown, but subsequent ones you'll get the usplash.

By the way, I've posted this for my benefit, not yours. :wink: This is affecting the latest Linux Mint which I've got on my laptop, so when I next boot into it, I can find this thread and fix Mint as well. :)

Great for GDM. Any ideas on how to get there with KDM?

---

