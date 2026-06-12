---
title: "Creative X-Fi xtrememusic"
date: 2008-11-08
forum: Hardware
---

### Post by apollo23 on 2008-11-08
I am new to ubuntu and I am trying to get my Creative Labs X-Fi Xtrememusic sound card working.  I have download the latest linux driver ([http://support.creative.com/downloads/welcome.aspx?nDriverType=1#type_1](http://support.creative.com/downloads/welcome.aspx?nDriverType=1#type_1)).  I am not sure how to install this.  I have extracted the package, and then the readme tells me to do the following: 

> In terminal,


1) Goto source directory

2) Execute make command as root

   make

   make install

I have gone to the terminal.  Gotten into the extracted creative folder.  I typed 'make' and I got this:  

> make -C /lib/modules/2.6.27-7-generic/build M=/home/matt/Desktop/creative
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'

I don't know what this means.  I then I tried to type make install and I get this:

> matt@matt-desktop:~/Desktop/creative$ make install
Copy module files...
mkdir: cannot create directory `/lib/modules/2.6.27-7-generic/kernel/drivers/ssound': Permission denied
make: *** [install] Error 1


How do I get this "Permission denied" thing to go away?  Thanks for all your help, it is very much appreciated.

---

### Post by Fjatle on 2008-11-08
When you use Ubuntu, you are not logged in as root (like Commander in Chief). 
So to get permissions to do such things, you have to type in 'sudo' first.

So your line would be: sudo make install

Then when you are asked to type your password, just type in even if it looks like nothing happens.. The terminal will not put in **** while you type a password.

---

### Post by apollo23 on 2008-11-08
Thank you so much for the information.  I did that and it worked...or atleast it installed.  So now Ubuntu has sound...but when I play an mp3 it sounds pretty terrible.  The music sounds unclear and muffled.  I am currently using Amarok.  Any suggestions with this issue?  Also, completely unrelated...does Ubuntu have a 'recycling bin' or once I delete something is it permanent gone??  Thanks for all the help.

---

### Post by Fjatle on 2008-11-09
One fix I remember a while ago when Ubuntu started to use the new sound server Pulse Audio was to do the following:

Download gnome-alsamixer

Now you will find it in Applications - Sound & Picture (or whatever it says in english :)

Open it, and turn Digital (or everything) down to about 40-50%.
Is the sound ok now? If so, turn it back up to whatever you want.

And yes, there is a trash can.
After a fresh install, you will see it at the bottom panel to the right.
But if you open any folder, it should be in the menu to the left.

One thing about trash can that can be nice to know:
If you delete something on a memory card, you are not in fact deleting it. On a memory card, you will only put you 'delete' files in a hidden folders, named .Trash1000 (or something like that.)

So to delete thing completely, go to the root of the memory card, click View - view hidden folders (Ctrl+H), and delete the folder.

I do believe it ask you to empty the trash when you click the 'eject' button, but sometimes you need to delete thing completely before copying new files on to the card... 
Just some OK info to know :)

---

### Post by apollo23 on 2008-11-09
Thanks so much! That helped out a ton!  I really appreciate it. 

Is there any program that will enable 5.1 surround sound on the creative card?

One other questions.  

I have an XP partition and a Linux partition.  I don't want to have to keep all my music in 2 different places.  When I get into Ubuntu it see my xp partition as "Media"... When I use Amarok, it doesn't remember to search in media unless I got to 'Places' and then 'Media' and put the icon on the desktop.  Is there anyway to make this 'Media' icon always show up on my desktop?

Thanks for all the help, it is very much appreciated!

---

### Post by rapsball4 on 2008-12-19
I am also glad to have my sound card working in Linux - last time I tried they didn't give very good drivers and it was very frustrating and ended up going nowhere.  Mine's also only in stereo, though, so if anybody knows the answer to the question about getting it back in 5.1, that would be great.

For the other question, you'll have to mount the other drive, which is something I'm also trying to figure out how to do right now.

---

