---
title: "QUESTION: Does Ubuntu carry any Screenlets/Desklets ? Clean Ubuntu 8.10 . . ."
date: 2008-11-19
forum: General Help
---

### Post by DaBigWig809 on 2008-11-19
I have a clean version of Ubuntu 8.10 and would like some screenlets/desklets/sidebar, what ever you want to call it. It would give my desktop a different image with a little widgit like that.

Is there a way, I am new to Ubuntu, please any help would be great.

:)

---

### Post by DaBigWig809 on 2008-11-19
I just read there aren't any, thanks anyways.

If there are and I'm wrong then let me know, I'll check the thread again.

---

### Post by alwayshere on 2008-11-19
sudo gedit /etc/apt/sources.list


Add this line to the end of the file
Now 
deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) hardy main universe
-----------------------------------------------------------------

Save and close the text editor
Now
sudo apt-get update
-----------------------------------------------------------------

Install the Screenlets 
Now
sudo apt-get install screenlets
-----------------------------------------------------------------

Now
sudo apt-get install python-feedparser
-----------------------------------------------------------------

Gtkmozembed needs to be installed
Now
sudo apt-get install python-gnome2-extras
-----------------------------------------------------------------

Now 
sudo apt-get update
------------------------------------------------------------------

Rightoo ya sorted now find screenlets icon under applications
to pick a screenlet double click it and if you want it to start on start up 
tick the Auto start on logon. 

I chosse the trash can ,main menu and sysmonitor 

ya can right click on sreenlet which is on ya desktop to edit prefrences etc .

see this address 

[http://www.gnome-look.org/index.php?xcontentmode=6700&PHPSESSID=bac24026c76e5427cac8068acf7b7628](http://www.gnome-look.org/index.php?xcontentmode=6700&PHPSESSID=bac24026c76e5427cac8068acf7b7628)

to get lots of extra sreenlets to choose from

---

