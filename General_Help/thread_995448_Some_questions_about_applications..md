---
title: "Some questions about applications."
date: 2008-11-27
forum: General Help
---

### Post by 123456789mike on 2008-11-27
Well, I have Ubuntu running, I am pleased with almost everything, I love the desktop effects :thumbsup:

But I am having soem trouble with a few things:
1)Flash, I have yet to try anything, but I would really love having it installed(Adobe Flash)(I was unsure of what to do becasue I am a beginner with Linux.
2)Recording your desktop, etc. I am sure users of Windows have used/heard of Hypercam. It records what you are doing on screen. Well, I was wondering if there were any programs like that out there for Linux/Ubuntu.
3)Lastly, I was wondering about ASCII/Unicode strings-&#9786;&#9787;&#9829;&#9830;&#9827;&#9824;•&#9688;&#9675;
Is there a way to get these to work on Ubuntu?(I am on Windows, that is how I put those up ;))

*Oh, I was wondering also, what is the standard word processor on Ubuntu? And do you think it would be compatible with an Epson Printer?

Thank you guys so much!-again ;)

---

### Post by binbash on 2008-11-27
1-Add medibuntu ([http://help.ubuntu.com/community/Medibuntu](http://help.ubuntu.com/community/Medibuntu) just follow the link, instructions there) to your sources.list .and give this command : sudo apt-get install flashplugin-nonfree
2-Recording your desktop : if you are using gnome install gtk-recordmydesktop, if you are using kde : krecordmydesktop (BUT PLAY with the settings if you want to get a good fps)

---

### Post by mechanicalturk on 2008-11-27
OpenOffice.org Writer is the word processor installed by default in Ubuntu. but any word processing package should be able to print if the printer is compatible with linux and configured properly.  Have a look _[here]("http://www.openprinting.org/printer_list.cgi?make=Epson")_ for a list of Epson printer compatibility.

---

### Post by binbash on 2008-11-27
I suggest installing Abiword as word processor and use it instead of openoffice.

---

### Post by 123456789mike on 2008-11-27
Thanks, and do you one you by any chance have AIM? I am having some really strange difficulties... earlier, I forget where, but I tried installing Java and soem other applications with Terminal. Well, it stopped after some time, and know when I go to applications> Add/Remove> It loads then I get an error message"This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'." Well, I can do the update fine in terminal. But then when I do the install -f I get really strange results, well it is hard to explain. The first time both commands worked, but the installation one took my to a page and I didn't quite know what to do, so I closed it. Here is the error I get for both of them:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I am really started to get annoyed -__- and the first time for the installation command, it took me to a blue page in the terminal and it said 
<ok> at the bottom, and I couldn't click it or hit enter.. it wouldn't do anything, so I closed the terminal... :( any ideas? Thanks!

---

### Post by binbash on 2008-11-27
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

About this error : 

Some package manager is running probably OR you are trying to give the command WITHOUT sudo or not being root.

Close your package managers like synaptic, adept etc then try it again.

DO NOT USE -f (force) option if you dont know what you are doing.

For sun's java : 

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-bin sun-java6-jdk

THEN after this is done : 

duyq@ubuntu:~$ sudo update-java-alternatives -l
java-6-sun 63 /usr/lib/jvm/java-6-sun

You see the output (java-6-sun) then give this command : 

duyq@ubuntu:~$ sudo update-java-alternatives -s java-6-sun

That is all


EDIT : before doing anything, close your package manager and give this command : sudo apt-get update . If something is broken, let us know

---

### Post by 123456789mike on 2008-11-27
I am really sorry, but what is this "package manager?"
I will do sudo aptitude get-update again
Oh, and does it matter if I do apt or aptitude? I will do apt though
Here is the whole thing:
mike@mike-desktop:~$ sudo apt-get update
[sudo] password for mike: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mike@mike-desktop:~$ 

THANKs ;)-Oh and for the character map- if I put an arrow in my myspace (haha I am a child) and my friends are running Vista/XP, will they be able to see the arrow? Or is it something awesome just for us?
*Also! I can't install anything it says something about a software conflict or something. Well, thanks again!
**Also!! After, I hope, I can get this fixed, for installing the recorder, would the command be sudo apt-install gtk-recordmydesktop?

---

### Post by 123456789mike on 2008-11-27
The problem is, when I give the first command: sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-bin sun-java6-jdk
I get this:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Anything I can do?!@!

[edit]Oh, and is there a way just to remove the whole Java thing so I don't need to deal with this ;) Thanks!

---

### Post by bruce89 on 2008-11-27
> **123456789mike said:**
> 3)Lastly, I was wondering about ASCII/Unicode strings-&#9786;&#9787;&#9829;&#9830;&#9827;&#9824;&#8226;&#9688;&#9675;
Is there a way to get these to work on Ubuntu?(I am on Windows, that is how I put those up ;))


Control+Shift+U, then the Unicode hex.

---

### Post by 123456789mike on 2008-11-27
Thanks, but do you think you could help me with this software problem? Is there a way to just overall clear Java? That doesn't seem to be working, I am holding down ontrol/shift/U, then while holding it, pressing in 2328 then releasing all of them,.

---

### Post by CatKiller on 2008-11-28
> **123456789mike said:**
> it took me to a blue page in the terminal and it said 
<ok> at the bottom, and I couldn't click it or hit enter.. it wouldn't do anything, so I closed the terminal... :( any ideas? Thanks!

Then if you haven't restarted your computer, it's probably still sitting there, waiting for you to press OK. ```
ps ax | grep apt
``` should let you find it so that you can kill it.

You can only have one [package manager]("http://en.wikipedia.org/wiki/Package_Manager") successfully running at once, so you won't be able to install anything until you stop that process.

---

### Post by 3rdalbum on 2008-11-28
When you get the curses-based GUIs like the one you describe (the blue screen with the OK button) sometimes you need to press Tab in order to highlight the OK button.

As for your Unicode, I can see the symbols you've put at least!

---

### Post by 123456789mike on 2008-11-28
Yeah, those ones were from XP... but Vista reads a lot more than XP. 
I was talking about these, but I checked and they don't work, is there a way to get Windows XP to read them?:
&#9731; &#9732; &#9733; &#9749; &#9748; &#9742; &#9762; &#9763; &#9764; &#9773; &#9770; &#9767; &#9774; &#9775;(snowman,comet,star,cup of coffee, stormy umbrella,phone,toxic,biohazard,hospital sign thing,russian thing(confused ha)uhm is it Signapore?,Pharmacy sign, peace, yin yang

---

