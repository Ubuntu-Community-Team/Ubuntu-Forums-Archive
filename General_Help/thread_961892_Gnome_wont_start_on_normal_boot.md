---
title: "Gnome wont start on normal boot"
date: 2008-10-28
forum: General Help
---

### Post by Johnsie on 2008-10-28
When I boot Ubuntu normally it gets to GDM, I type my username and password in and then there is a  plain brown background.

At this point the hard disk light is flashing like crazy but the mouse gets slower until the mouse completely stops working. Hard disk light is still going though but nothing further happens.

Gnome starts fine when I boot up in 'recovery mode' and startx

Anyone have any idea what might be going on? It's been doing this from about Dapper though to Intrepid.

---

### Post by soro2005 on 2008-10-28
I think there's a program in your gnome session that causes the hang up. You might get it solved by simply deleting your /home/youruser/.gnome2/session file

---

### Post by Johnsie on 2008-10-31
Thanks, I tried that but it didn't work. I also tried creating a completely new user and the same thing happened with that account. I do think that program is causing the crashes. I just have no idea which one. Is there some sort of script that manages which services start up other the one you mentioned?

---

### Post by larryn28 on 2008-10-31
i am having the same problem & am very new to ubuntu. how would i go about [COLOR="Teal"]simply deleting my /home/youruser/.gnome2/session file[/COLOR] if i can't get past the empty brown screen?

---

### Post by Johnsie on 2008-10-31
press escape when your computer is starting up to bring up the boot menu

choose 'recovery mode'

choose 'root terminal'  when the menu comes up

that should put you into a terminal/command line where you can delte the file

I'm not 100% sure how to delete a folder in the terminal so you might need to look google 'deleting folders in linux terminal'

---

### Post by Johnsie on 2008-10-31
bump. Anyone know how gnome launches programs/services while starting after gdm? Is there a script other than the one in the users home folder?

---

### Post by Johnsie on 2008-10-31
last bump before i install windows instead lol. A desktop OS isn't much good without a GUI.

---

### Post by soro2005 on 2008-11-02
Sorry for the delay! I'm not quite sure about that, but I believe that gdm normally starts as specified in /etc/gdm/gdm.conf. The thing is that this should really be renewed every time you upgrade to a new distribution, at least. Besides, your gdm seems to start, only your session is screwy. And not only yours, but that of new users as well. On the other hand, you say that you can have a Gnome session if you circumvent gdm, meaning that it's got to be somewhere there.

Have you tried issuing a:
```
sudo dpkg-reconfigure gdm
```
--> Will probably not do anything. After all, you've upgraded several times you say.

For diagnostics: You could have a look into the gdm log files at /var/log/gdm, and the Xsession error log at /home/youruser/.xsession-errors

The thing you describe sounds like there's a memory leak somewhere. So after some moments, the CPU is so busy pushing stuff into swap and out of it, that everything gets slower and slower. Or some process generates a massive amount of data to be written out to the harddrive. What you could try to do is to observe that while it happens and try to identify likable culprits. To do so, you could, before you log into the Gnome session, open a terminal session and issue "top", then log into the Gnome session, then quickly change back to your terminal and see whether there's something running wild, or spawning a lot of processes, etc. Step by step:

1. At the gdm greeter, change to tty1 by pressing ctr+alt+F1 (don't do before you've understood that you get back to the gdm greeter with ctr+alt+F7 or F8 or F9)
2. Log into tty1
3. type ```
top
```
4. ctr+alt+F7 to get back to tty7 where you open the gnome session
5. log in
6. Quickly hit ctr+alt+F1 to get back to your observing post. You may have to be quick before everything slows down.
7. As soon as you see that there is some process running wild, or a lot of processes by the same name, make a note on paper of what you see in the "command" column.
8. Act quickly to try to shoot down the perpetrators. Terminate top by typing "q" and then issue ```
killall -9 name-of-command-to-kill
```. This might leave your gnome session in complete disarray, but perhaps it stops the bleeding so that you can have a look at the log files, etc. You might also just use ```
sudo killall gdm
``` to interrupt the experiment. You can start X from the terminal, you should not need to use a recovery session.

Finally, you could try to install Xubuntu (sudo aptitude install xubuntu-desktop), which will leave you with the xubuntu greeter, I believe. You should be able to log into gnome from the xubuntu greeter, perhaps even without running into the problem...

To delete the session file, get to a terminal (ctr+alt+F1 at the greeter), log in, then issue
```
rm ~/.gnome2/session
```
You can reboot your computer from the terminal with
```
sudo reboot now
```
or go back to your X session with ctr+alt+F7. Cycle through the F keys if you don't find the tty you are looking for.

---

### Post by soro2005 on 2008-11-02
And then: If you have a file called .gnomerc in your home directory, you may also want to move or delete that one. Some of the things that start with X and a gnome session should do so from /etc/X11/Xsession.d/. But if startx works without a problem, then I would believe that the problem is elsewhere.

---

