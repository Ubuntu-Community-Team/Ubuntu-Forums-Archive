---
title: "installation of acroread and mozilla-acroread packages"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by groundnut on 2009-04-28
I have installed Medibuntu. Though that is not reflected in Synaptic.
I have been able to install skype (with the terminal) from Medibuntu.

However I am not able to install the acroread and mozilla-acroread packages.
I get the message that the packages could not be found.

What is the problem here?

---

### Post by ajgreeny on 2009-04-28
They are not in the medibuntu repos, but rather in the archive.canonical.main.  Go to System>Administration>Software Sources and make sure they are enabled, then sudo apt-get update and acroread should be found, not sure about mozilla-acroread.

---

### Post by oldos2er on 2009-04-28
In Jaunty, acroread and mozilla-acroread are both in Medibuntu. Try running this in a terminal:
```
sudo apt-get update && sudo apt-get install acroread mozilla-acroread
```

---

### Post by groundnut on 2009-04-29
Still the same problem.
At the end it says could not find package acroread.

Somewhere in the middle it says (genegeerd=ignored):
Genegeerd [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-nl
Genegeerd [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-nl

 

tony@xp:~$ sudo apt-get update && sudo apt-get install acroread mozilla-acroreadGeraakt [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Genegeerd [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-nl       
Genegeerd [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-nl 
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty Release.gpg                        
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/main Translation-nl                
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/restricted Translation-nl          
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/universe Translation-nl            
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/multiverse Translation-nl          
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates Release.gpg                
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/main Translation-nl      
Genegeerd [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-nl   
Genegeerd [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-nl 
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                     
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/restricted Translation-nl
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/universe Translation-nl
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/multiverse Translation-nl
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty Release        
Geraakt [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg   
Genegeerd [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-nl
Genegeerd [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-nl
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates Release                    
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages               
Geraakt [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                           
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/main Packages                      
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages         
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/restricted Packages                
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/main Sources                       
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/restricted Sources                 
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/universe Packages                  
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/universe Sources                   
Geraakt [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                     
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources            
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/multiverse Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/multiverse Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/main Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/restricted Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/main Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/restricted Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/universe Packages
Geraakt [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/universe Sources
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/multiverse Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/multiverse Sources
Pakketlijsten worden ingelezen... Klaar
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
E: Kon pakket acroread niet vinden
tony@xp:~$

---

### Post by ajgreeny on 2009-04-29
> **oldos2er said:**
> In Jaunty, acroread and mozilla-acroread are both in Medibuntu. Try running this in a terminal:
```
sudo apt-get update && sudo apt-get install acroread mozilla-acroread
```
Sorry, but I think you'll find that acroread is in the archive.canonical.main repos as I said in post #2.  Mozilla-acroread does not seem to be available, however.  So to get teh acroread package add the following line to your /etc/apt/sources.list file ```
deb http://archive.canonical.com/ubuntu jaunty partner
```then ```
sudo apt-get update
``` and try again.

---

### Post by groundnut on 2009-04-29
Thank you very much ajgreeny!

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner was already there in third parties software sources but unchecked. So I only had to check it.

Then installing acroread was no problem.
Mozilla-acroread was not available as you mentioned. After installation of acroread it was also possible to view pdf files in Firefox. No need for mozilla-acroread anymore.

---

### Post by oldos2er on 2009-04-29
It really is in Medibuntu: [http://packages.medibuntu.org/pool/non-free/a/acroread/acroread_8.1.3-0medibuntu0.8.10.2_amd64.deb](http://packages.medibuntu.org/pool/non-free/a/acroread/acroread_8.1.3-0medibuntu0.8.10.2_amd64.deb) and 
[http://packages.medibuntu.org/pool/non-free/a/acroread/mozilla-acroread_8.1.3-0medibuntu0.8.10.2_amd64.deb](http://packages.medibuntu.org/pool/non-free/a/acroread/mozilla-acroread_8.1.3-0medibuntu0.8.10.2_amd64.deb)

 Maybe the 64-bit repos are different.

---

### Post by coffeecat on 2009-04-29
There's something odd going on with Medibuntu and Acroread. I used Medibuntu to install both acroread and mozilla-acroread in Hardy and Intrepid. Then, just after the Beta was released I managed to get acroread installed in Jaunty. But since then it's disappeared from Synaptic just as the OP says (this is with 32-bit). But it's still being listed in their package list. See here:

[http://packages.medibuntu.org/jaunty/index.html](http://packages.medibuntu.org/jaunty/index.html)

**groundnut**, I know you've got acroread installed now, but if by chance you want to try a different pdf viewer, have a look at Okular. It's in the repositories and is excellent, although being a KDE app will bring in a load of KDE libraries and dependencies.

---

### Post by groundnut on 2009-04-30
thanks coffeecat,

I have installed Okolar. It's a nice program.
I have one problem with it though.

I also use it to read the newspaper online. Each article is a pdf file.
Every time I click on an article (=PDF file) a new instance of Okular is started.
Adobe Reader loads the new PDF in the current instance. Is that also possible with Okular?

---

### Post by coffeecat on 2009-04-30
I don't know. I must admit, I haven't tried using it through a web browser yet, although I'm not quite sure what you mean by "in the current instance".

If you have pdf files on your local system, acroread and okular both behave in the same way, opening second and subsequent files in new windows.

If you mean opening in new windows or new tabs in firefox, perhaps this is a firefox setting. If I have time, I'll do some experimenting later.

---

### Post by groundnut on 2009-04-30
hello coffeecat,

By instance I mean a window.
So when you want to read ten articles you end up with ten Okular windows.
Adobe reader just reuses the first window (instance).

---

### Post by coffeecat on 2009-04-30
OK, I understand. Yes, I can see that's a nuisance.

---

### Post by pbubenik on 2009-05-03
Does anyone know where to find the mozilla-acroread and/or acroread-plugins packages for ubuntu 9.04 jaunty jackalope in the 32 bit repositories? They do not seem to be available.

---

### Post by coffeecat on 2009-05-04
> **pbubenik said:**
> Does anyone know where to find the mozilla-acroread and/or acroread-plugins packages for ubuntu 9.04 jaunty jackalope in the 32 bit repositories? They do not seem to be available.

I'm not surprised you've found the foregoing confusing, because I've done some experimenting and the results are - um - interesting. :wink:

**For a 32-bit system**: seemingly not available from the Medibuntu repository. Go to System > Administration > Software Sources > Third Party Software Tab. Tick the archive.canonical.com line. (You don't need the Source Code line.) Reload the repository information and install via Synaptic. During installation you are prompted for whether you want Acroread to be your default pdf reader. If you click on yes, it will become the pdf reader in Firefox. This gave me Adobe Reader version 9.1.0.

**For a 64-bit system**: available in medibuntu (with Synaptic or apt-get) if you have the medibuntu repo enabled, but you have to select both the acroread and mozilla-acroread packages, and these bring in a few other dependencies. But the version of Adobe Reader is 8.1.3.

The fact that I was able to install acroread for a 32-bit system from Medibuntu during the Jaunty Beta stage but cannot now, and that the version of Acroread now available from Medibuntu for a 64-bit system is an older one suggests that acroread is being withdrawn from Medibuntu. I don't know.

I like that archive.canonical gives you everything in just one package, so I'll try uninstalling all the Medibuntu stuff from my 64-bit system and try archive.canonical instead.

**Edit:** curiouser and curiouser. Acroread is **not** available from archive.canonical for a 64-bit system. Or, at least, at the moment. I should imagine this is a watch this space situation.

So, as of 4th May 2009 for Adobe Reader: 32-bit - use archive.canonical. 64-bit - use Medibuntu and put up with an older version.

---

### Post by celem on 2009-05-04
I couldn't get acroread to work, so I simply pointed the PDF application to /usr/bin/evince and that works fine.

---

