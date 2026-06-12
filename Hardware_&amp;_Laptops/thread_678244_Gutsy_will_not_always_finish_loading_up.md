---
title: "Gutsy will not always finish loading up"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by showgun22 on 2008-01-25
Since I have updated from Feisty to Gutsy it seems that Ubuntu will not complete loading up on my Laptop.
It is always happening if the background Desktop image comes up before the Gnome panel come up at this stage nothing else happen the mouse is available even the screen saver will start after time,  but nothing else. My only recourse is to unplug and remove batteries and restart. This does happen every few starts. Maybe 1 in 10 ???

Is this a known problem?
Is there a solution?
Thanks

---

### Post by Mikecore on 2008-01-25
instead of powering down try switching to a counsel 

```


ctrl+alt+backspace


```

that will restart xorg. And your system should come up then. You stated you upgraded to Gusty. if you did it through the package manager instead of a fresh install. sometimes its when you have issue like this its better to do a fresh install using a Gusty boot disk.

---

### Post by showgun22 on 2008-01-27
It finally happened again and did as suggested it did re-initialize but unfortunately when the login screen appears on the monitor and a small pop up hides the login that states 
"Autentification falilure"  I do click the OK button hoping I will be able to try login in but unfortunately that pop up does not go away???

Any idea if I could had this in a file so I do not have to Unplug and diconnect the batteries?
THanks

---

### Post by Mikecore on 2008-01-27
I'm sorry the command I gave you kills X and restarts it I mis typed. I did want you to restart X so the command was fine. this time try actually switch to another counsel with 

```


ctrl+alt+F2


```

you will now be at a command line terminal. log in as you normally would. One in 

```


sudo /etc/init.d/gdm stop && etc/init.d/gdm start


```

this will restart your login manager see if that works. don't forget to switch back to the 
counsel F2 and log out 

```


exit


```

then to switch back to the GUI 

```


ctrl+alt+F7


```

I would then try to search your log files for the problem.

/var/log/messages
/var/log/demseg
/var/log/Xorg.0.log

you need to figure out why this is happening. Again if you upgraded to gusty with the update manager, I would back up your system and do a fresh install. Your problems will probably go away.

---

### Post by showgun22 on 2008-01-27
I think I will do as you suggest backup format system file keep my home and reinstall than restore I hope this will solve it..
Thanks

---

