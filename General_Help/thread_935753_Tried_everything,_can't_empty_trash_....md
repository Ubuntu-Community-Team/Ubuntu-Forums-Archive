---
title: "Tried everything, can't empty trash ..."
date: 2008-10-02
forum: General Help
---

### Post by Bucky Ball on 2008-10-02
I have found a gazillion threads concerning this and all looks really straightforward. Have tried 'em all and nothing works.

Copying a windoze installation disk for a friend after spending an unsuccessful week trying to get Ubuntu up on their computer, aborted the process as it stalled for about half an hour on 80% and deleted the files. Emptied the Trash but what do you know, one folder left called:

**mui**

When I say one folder, one folder containing several other equally stubborn folders and files. Tried all on this page:

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

... plus a whole lot more. Won't budge. :confused:

---

### Post by Ms_Angel_D on 2008-10-02
Hi, not sure if this will work but you might want to try booting in with a live disk

and running 
```
gksu nautilus
```

then going into the users

```
/home/USERNAME/.local/share/Trash
```

folder and see if you can delete in that manner. 

Might work, might not, just a thought.

Angel

---

### Post by Bucky Ball on 2008-10-02
> **MetalHellsAngel said:**
> Hi, not sure if this will work but you might want to try booting in with a live disk

and running 
```
gksu nautilus
```then going into the users

```
/home/USERNAME/.local/share/Trash
```folder and see if you can delete in that manner. 

Might work, might not, just a thought.

Angel

Thanks for that, but I can see without the live cd that the Trash folder from that location is gone. The trash folder in the bottom right of my screen though still contains the folder 'mui'. I have logged out and in, maybe I will restart or switch off and back on and see if that makes a difference.

---

### Post by Ms_Angel_D on 2008-10-02
Are you sure it's not owned by root? if thats the case it could be located in a different folder

Sorry I can't be of more assistence. You may want to have a look at [THIS]("http://ubuntuforums.org/showthread.php?t=898573") thread, step number 6 talks about trash folders.

Angel

---

### Post by hansdown on 2008-10-02
Hi Bucky Ball.

A google search shows, amiga os and windows server 2003, and xp.

Can you do a clamav scan?

---

### Post by iaculallad on 2008-10-02
While logged on your account, try dropping to your terminal and issuing the command below:

If you're in Hardy:
```
sudo rm -r ~/.local/share/Trash/files/*
```

If you're in Gutsy:
```
sudo rm -r ~/.Trash/*
```

(Just assuming that you had not tried that command though).
HTH

---

### Post by FourBrane on 2008-10-02
> **Bucky Ball said:**
> Emptied the Trash but what do you know, one folder left called:

**mui**


Inability to delete from Trash is almost always a permissions problem, suggesting that root owns the mui directory and probably all the files inside. So, you need to take ownership back.

sudo chown -R ben ~/.local/Trash/*

The -R will cause chown to recursively change ownership all the way down the chain of subdirectories to make them owned by "ben."

---

### Post by Bucky Ball on 2008-10-02
> **iaculallad said:**
> While logged on your account, try dropping to your terminal and issuing the command below:
```
sudo rm -r ~/.local/share/Trash/files/*
```

```
skulker@HPLappy:~$ sudo rm -r ~/.local/share/Trash/files/*
rm: cannot remove `/home/skulker/.local/share/Trash/files/*': No such file or directory
```It's well and truly gone already from that location at least.

[quote=FourBrane]Inability to delete from Trash is almost always a permissions problem, suggesting that root owns the mui directory and probably all the files inside. So, you need to take ownership back.

```
sudo chown -R ben ~/.local/Trash/*
```[/quote]Is the /share missing from that last command?

[quote=MetalHellsAngel]Are you sure it's not owned by root? if thats the case it could be located in a different folder

Sorry I can't be of more assistence. You may want to have a look at [THIS]("http://ubuntuforums.org/showthread.php?t=898573") thread, step number 6 talks about trash folders.
[/quote]

That is the thread I have been following. :)

And finally, HansDown; What is clamav scan? Will have a look at that now.

Thanks one and all ... :o

Update: HansDown, it would be a bug in that folder in the trash which came from a Windoze install disk (my own, which I have used plenty) designed to affect Linux machines. Not sure clamav scan is going to be of help. Tnx.


* UPDATE: Here's something insteresting ...

Nothing here:

[B]~/.local/share/Trash
[/B][B]/root/.local/share/Trash

[/B]... but the can on my desktop tells me the folder 'mui' is in it. Have switched off and on. Nothing. If I search for the folder 'mui' with hidden folders showing, not there. But it's there.  :confused:

---

### Post by Bucky Ball on 2008-10-02
The result of the following command:

```
skulker@HPLappy:~$ sudo find / -type d -iname *Trash* | grep Trash
/media/bigboy/.Trash-1000
/media/bigboy/.Trash-0
find: /home/skulker/.gvfs: Permission denied
```

Become root to get into .gvfs and attempt to see the directory:

[EMAIL="root@HPLappy:/home/skulker/.gvfs"]```
[/EMAIL][EMAIL="root@HPLappy:/home/skulker/.gvfs"]root@HPLappy:/home/skulker/.gvfs[/EMAIL]# dir
dir: cannot open directory .: Permission denied
```

I have no idea. :confused:

---

### Post by iaculallad on 2008-10-02
Topics related to GVFS:

[Superuser cannot access ~/.gvfs folder when mounted]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/225361")
[Root user can not access .gvfs]("http://bugzilla.gnome.org/show_bug.cgi?id=534284")

---

### Post by Bucky Ball on 2008-10-02
Thanks for the links iaculalladd. I see no workaround for this from these pages so maybe I should just join the queue. That file may be there until I do a full install over christmas.

I need root permission to delete the file but can't find it to change permissions on it (except when I open the garbage and I am not root). When I try to open the garbage bin in nautilus, it won't let me even see the file!

---

### Post by Bucky Ball on 2008-10-02
Here's a twist. 

```
skulker@HPLappy:~$ locate /home/skulker/.local/share/Trash
/home/skulker/.local/share/Trash
```It finds a Trash folder, even though I've deleted 'em all. I go to have a look:

```
skulker@HPLappy:~$ cd /home/skulker/.local/share/Trash
bash: cd: /home/skulker/.local/share/Trash: No such file or directory
```I pull one back to check the /share directory:

```
skulker@HPLappy:~$ cd /home/skulker/.local/share
[EMAIL="skulker@HPLappy:%7E/.loca"]skulker@HPLappy:~/.loca[/EMAIL]l/share$ dir
applications  audacious  desktop-directories  mime  openbox  tracker
```Takes me back to*** ~/.local/share*** ... No sign of trash or even the path, though it shows up when I do a 'locate' on it! :-k

What am I missing? 

iaculallad, I did exactly the same thing as the person on one of these pages - installed but left the previous home and moved all files over. I didn't think it was the problem though because in 6 months I haven't had an issue or 'stuck' trash. But this has got me thinking there might be some mix up between the two. I'll have a further dig in the links you posted. Thanks.

[Superuser cannot access ~/.gvfs folder when mounted]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/225361")
[Root user can not access .gvfs]("http://bugzilla.gnome.org/show_bug.cgi?id=534284")

---

### Post by opm595 on 2009-02-23
I have exactly the same problem when I copied and stored a 610mb MS Win folder temporarily onto my Ubuntu machine, then sent it to the garbage bin after copying it to a CD. Six months on, after trying everything it still beats me as to how to get rid of it from the garbage bin.

Obviously something to do with permissions and/or MS Win related files.

---

### Post by Bucky Ball on 2009-02-23
Yea, I've toyed with that anomoly on and off since I started this thread. What you're describing is exactly it. It's still in my garbage, I have had no success to this point. Think I will be reinstalling on that machine pretty soon, that should fix it!

Good luck.

---

### Post by yqdm on 2009-03-08
from Desktop click to "file" in "Trash" folder, right click, select "permissions" and adjust your permissions. Close.

that worked for me.

---

### Post by Rallg on 2009-03-08
Did you try this, in Terminal:

sudo rm -rf /root/.local/share/Trash/

WARNING: Never use sudo rm unless you are certain of the consequences. The above script goes to the Trash folder in root's home directory, and directly removes all contained subfolders and files. If the problem is in your user home directory, you would edit the path accordingly.

The command works for me, and I created a shell script that can be chosen from the application menu, so that I don't have to remember the code (a good idea, due to the hazard of mistyping when using sudo rm).

---

### Post by impert on 2009-10-06
Hi,
This is an old thread, but I'm posting because the following may help someone.
I had the same problem with a folder in my Trash that had subfolders owned by root. No amount of **sudo chown**-ing or **chmod**-ing or **rm -Rf**-ing would budge it. The answer was to **sudo su** first, then to drag and drop the offending folder into the terminal. (Dragondropping avoids typos) 
It seems you're only half-way root with **sudo** unless you follow it with **su** and become the real thing.

It's a real pleasure to use **rm -Rf** from time to time; of course you have to be careful, but I've done more damage with unconsidered use of other commands, for instance **cp** **dd** and **tar -x**
I don't know why **rm** seems to freak people out. It's there because it's necessary, so I say use it. Carefully.

---

