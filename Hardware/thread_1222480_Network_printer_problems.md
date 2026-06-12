---
title: "Network printer problems"
date: 2009-07-24
forum: Hardware
---

### Post by MJBose on 2009-07-24
I am trying to install my Brother HL2070n printer. It's located on my wireless network. I followed the directions [[COLOR="Blue"]here[/COLOR]]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/BrotherPrinters/2070NLaser"). Everything went well. I have the printer on the list and it prints to it. The only problem is...it is printing nonsense characters and keeps printing until the paper runs out or you turn off the printer! During the install of the CUPS driver I got this error:

[COLOR="Purple"]mike@mike-laptop:~$ sudo dpkg -i --force-overwrite ./cupswrapperhl2070n_1.0.0-1_i386.deb
(Reading database ... 122296 files and directories currently installed.)
Preparing to replace cupswrapperhl2070n 2.0.1-2 (using .../cupswrapperhl2070n_1.0.0-1_i386.deb) ...
 * Restarting Common Unix Printing System: cupsd                                                                      [ OK ] 
Unpacking replacement cupswrapperhl2070n ...
Setting up cupswrapperhl2070n (1.0.0-1) ...
/usr/local/Brother/cupswrapper/cupswrapperHL2070N-1.0.0: 54: cannot create /usr/share/cups/model/brhl2070n_cups.ppd: Directory nonexistent
rm -f /usr/lib/cups/filter/brlpdwrapperHL2070N
 * Restarting Common Unix Printing System: cupsd                                                                      [ OK ] 
lpadmin: Unable to copy PPD file! [/COLOR]

If anyone can tell what this means and how to fix the problem...I would be eternally grateful [COLOR="Green"](or at least everytime I want to print :P )[/COLOR]

---

### Post by rdsnc on 2009-07-25
Does the directory /usr/share/cups/model exist?
Sounds like the install can't find the directory, or doesn't like the permissions on it.
Brute force it, I'd say.
sudo mkdir usr/share/cups/model
sudo chmod 755 usr/share/cups/model
Then, try again.


[COLOR=Purple]/usr/local/Brother/cupswrapper/cupswrapperHL2070N-1.0.0: 54: cannot create /usr/share/cups/model/brhl2070n_cups.ppd: Directory nonexistent
rm -f /usr/lib/cups/filter/brlpdwrapperHL2070N
 * Restarting Common Unix Printing System: cupsd                                                                      [ OK ] 
lpadmin: Unable to copy PPD file! [/COLOR]

---

### Post by MJBose on 2009-07-26
I tried making the dir in  sudo then tried as root: 

[COLOR="Purple"]mike@mike-laptop:~$ sudo -i
root@mike-laptop:~# mkdir usr/share/cups/model
mkdir: cannot create directory `usr/share/cups/model': No such file or directory
root@mike-laptop:~# exit
logout
mike@mike-laptop:~$ 

 [/COLOR]

It still didn't allow me. I'm a total noob at linux command line so I'm not sure what to do next. It seems even as root I can't make a directory.

---

### Post by MJBose on 2009-08-06
I figured it out. I used the wrong syntax to make the directory. I should have used [COLOR="Purple"]"mkdir /usr/share/cups/model"[/COLOR] The folder  [COLOR="Purple"]/model[/COLOR] wasn't there. It all works now.

---

