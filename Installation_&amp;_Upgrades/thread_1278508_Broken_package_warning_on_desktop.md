---
title: "Broken package warning on desktop?"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by MajorDamo on 2009-09-29
SOLVED

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 55 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

Recently installed Jaunty, was trying to get more effects out of compiz, and added additional ones per directive in Ubuntu forum?  Then red circle with above warning appeared on desktop.

I cannot access synaptic, add/remove or Terminal to try and correct (haven't a clue HOW to correct anyway as warning is vague) posted bug report, but hope someone can explain in non-technical, easy to follow way to correct this as I have my version of Jaunty set the way I want it and hate to have to start over, thanks****

---

### Post by diesch on 2009-09-29
There is an error in line 55 of the file /etc/apt/sources.list. Most likely you added some command that was meant to be run on the command line to /etc/apt/sources.list

Please attach  /etc/apt/sources.list.

---

### Post by MajorDamo on 2009-09-29
Solved, after spending hours reading through forum, tried a related idea which was to simply remove "sources.list" from /etc/apt and then sudo apt-get update and upgrade.  Red warning icon went away, so hopefully I am back to where I was.  I really have no idea what I am doing as I am NOT a computer tech nor comfortable with the command line.  

All I was trying to do in the first place was to get more effects out of compiz because compiz seems anemic in Jaunty compared to other distros so I followed the advice of another submission on the forums on how to add additional function to compiz.  Bad move on my part, cannot trust info on forums I have learned.

---

### Post by diesch on 2009-09-29
/etc/apt/sources.list holds information about where the package manager gets the packages from. If you remove it you can not install additional packages or updates.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) tells you how to restore the file with the default software repositories.


> 
Bad move on my part, cannot trust info on forums I have learned.     
You have to be a little careful about what's written in a forum as sometimes some important details are missing or hidden somewhere on the thread. And sometimes less knowledgeable people give tips they don't really understand or don't really match the problem. But at least here in the Ubuntu Forums most tips are quite helpful.

Trust me ;-)


In your case it seems to be a misunderstanding: The 'sudo' in the error message is a hint that you added a line to your repositories that really is a command you should run on the command line, most likely one that adds some repositories.

---

