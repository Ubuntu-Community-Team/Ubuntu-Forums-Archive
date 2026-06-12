---
title: "install files on PALm pda?"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by LucasLinard on 2005-10-23
hi
how can I install pdb and prc files on my Tungsten E?
Its syncs, but i don't know how to install files on it.
I tried to type > gpilot-install-file --later sheettogo_enus.prc
but it says:

> "(gpilot-install-file:9351): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
gpilotd-Message: Activating object OAFIID:GNOME_Pilot_Daemon

(gpilot-install-file:9351): fileconduit-WARNING **: Não pude ler nomes dos pilots"

Can anyone Help me?

---

### Post by SickTwist on 2005-10-24
Sorry, I don't have experience with GPilot. I hope that someone can help you figure it out but if that does not happen, there are some alternatives:

I use [J-Pilot]("http://www.jpilot.org/") with my Palm Vx and it is capable of installing files. There is also [KPilot]("http://www.kpilot.org/") which I have not tried out yet but it looks interesting. Best of luck!

---

### Post by prasys on 2005-10-24
I have tried Kpilot it works well with PalmOS 5. As a Palm developer , the gpilot tool does not work very well with PalmOS 5 Systems , it works with "classic" versions of PalmOS ( <5). I suggest you to move to Kpilot or use Jpilot , as suggested by SickTwist. But again , the results are vary , i heard some people managed to sync their Pilots with Gpilot..it depends..but as i said , if it fails , use Kpilot

---

### Post by cokhavim on 2005-10-24
does the "restore" function on the gpilot daemon work?  

this is a trick i do so i can avoid the command line to install files:

-create the directory $HOME/MyPilot/install/
-copy (not move) into this directory all the files that i want to sync to my palm
-right-click on the gpilotd icon in my panel
-select "Restore..."
-for "Directory", put $HOME/MyPilot/install/ and click "OK"
-sync
-remove all files from $HOME/MyPilot/install/ so i can do the same trick later

note: this only installs .pdb and .prc files, and doesn't backup or synchronise, obviously

however, i suspect that the "restore" function just calls the gpilot-install-files command.  so it may not solve your problem.  

jo

---

### Post by LucasLinard on 2005-10-25
Thanks for the help.
I solved the problem, I to install files logged as root...
:)
Thanks to you all..

---

### Post by nab on 2005-11-22
How do I setup the gpilotd icon?
Or how do I tell the conduit manager from where he should get the files to transfer to the palm.

I searched but without success :(


At the moment I transfer files with an shell-script:
cd $home/mypilot/install
gpilot-install-file -now *.*

---

### Post by pluisr on 2007-11-12
> **nab said:**
> How do I setup the gpilotd icon?
Or how do I tell the conduit manager from where he should get the files to transfer to the palm.

I searched but without success :(


At the moment I transfer files with an shell-script:
cd $home/mypilot/install
gpilot-install-file -now *.*
I think you right click on the gpilot icon on your deskbar go to restore and there you will find the route.

hope answer your question

---

### Post by pluisr on 2007-11-12
> **LucasLinard said:**
> Thanks for the help.
I solved the problem, I to install files logged as root...
:)
Thanks to you all..
Another way to do this is going to: 

system>preferences>gnome-pilot settings>conduits> file: enable. Close

Then just drag the file in the gpilot sync icon on the desk bar and synchronize.

Hope it helps others too!

---

### Post by aonegodman on 2008-04-01
> **pluisr said:**
> Another way to do this is going to: 

system>preferences>gnome-pilot settings>conduits> file: enable. Close

Then just drag the file in the gpilot sync icon on the desk bar and synchronize.

Hope it helps others too!

I tried this to send Sudoku.prc to my Palm Z, didn't work.

I don't have a gpilot sync icon on my desk bar, there is a PalmO/S Devices link under Preferences that opens the gpilot program. That's it.

Anyone else like to explain how to get software transfered to Palm Z device?   Thanks.

---

