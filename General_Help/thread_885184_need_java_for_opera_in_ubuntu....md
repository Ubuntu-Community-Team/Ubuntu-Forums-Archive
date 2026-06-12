---
title: "need java for opera in ubuntu..."
date: 2008-08-09
forum: General Help
---

### Post by PsychedelicWonders on 2008-08-09
How do I get java for opera in ubuntu?

I tried the widget search but only came up with javascript cheat sheet.

---

### Post by Diabolis on 2008-08-09
Java Runtime Environment
```
sudo apt-get install sun-java6-jre
```

Java plug in
```
sudo apt-get install sun-java6-plugin
```

---

### Post by PsychedelicWonders on 2008-08-09
i do both of those i take it?

---

### Post by Diabolis on 2008-08-09
Probably you need only the plug in.

---

### Post by PsychedelicWonders on 2008-08-09
what happens if i try to install the other one and I already ahve it?

nothing?

---

### Post by Diabolis on 2008-08-09
Yes, nothing, it will tell you that you already have it. And if you have an old version it will tell you too, so you can upgrade it.

---

### Post by PsychedelicWonders on 2008-08-09
i got this message....

psychedelicwonders@JohnnyScience:~$ sudo apt-get install sun-java6-jre
[sudo] password for psychedelicwonders: 
E: Type '&#8220;deb' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
psychedelicwonders@JohnnyScience:~$ 


whats wrong?

---

### Post by Diabolis on 2008-08-09
You have a typo in your sources.list file. Open it:
```
sudo gedit /etc/apt/sources.list
```

Give a look to line 56 as the error message says. Seems like you have an unneeded quote character.

---

### Post by PsychedelicWonders on 2008-08-09
> **Diabolis said:**
> You have a typo in your sources.list file. Open it:
```
sudo gedit /etc/apt/sources.list
```

Give a look to line 56 as the error message says. Seems like you have an unneeded quote character.

where ever line 56 is, i have no idea.

what program is it in and how do i find it so I can copy and paste it for you guys?

what would have put an extra character in there to give me this error message?

---

### Post by Diabolis on 2008-08-09
It could happen if you edited the file by hand, but probably that didn't happen. I really can't tell why it happened.

Just type the command that I gave you and post the content of the file here, so I can see it.

---

### Post by PsychedelicWonders on 2008-08-09
could this be the reason my MAC OS theme wasnt going any further?

#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
&#8220;deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221;
&#8220;deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221;
&#8220;deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221;
&#8220;deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221;
&#8220;deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main&#8221;

---

### Post by Diabolis on 2008-08-09
> “deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main”
“deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main”
“deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main”
“deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main”
“deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main”

Thats the problem. Delete the quotes, so it will look like this:
```

deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main

```

---

### Post by PsychedelicWonders on 2008-08-09
alright that seemed to work now because I am downloading java enviroment now.

what would put those quotations in there like that?

---

### Post by Diabolis on 2008-08-09
Probably you did it, but not by editing the file directly. Those lines are the repositories for avant-window-navigator which you might have added through synaptic. Synaptic writes to that file.

---

### Post by PsychedelicWonders on 2008-08-09
i was messing with the synatic, there must have been a bug in some of the files I was downloading to convert to a MAC OS look.

Alright I installed java enviroment and then the terminal turned different colors, listed all kinds of user agreements...

&#9472;&#9508; Configuring sun-java6-bin &#9500;&#9472;

that was the "title"

at the bottom is says "ok"

should I just close out, or do I have to do anything else here?

---

### Post by Diabolis on 2008-08-09
Follow the screens, it will ask you to accept and agreement or somehting like that. It won't take more than 5 minutes.

---

### Post by PsychedelicWonders on 2008-08-09
alright i did that and it seemed to bring me back to my prompt...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
psychedelicwonders@JohnnyScience:~$ 


so when it brings me back home to my prompt, does that mean the file and everything is finished?

---

### Post by Diabolis on 2008-08-09
Yes, its done installing the package. You can check if Java was installed successfully by typing this:
```
java -version
```

It will return something like this:
> java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)


---

### Post by PsychedelicWonders on 2008-08-09
tried to install the plugin and got this in my terminal...

[sudo] password for psychedelicwonders: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
psychedelicwonders@JohnnyScience:~$

---

### Post by PsychedelicWonders on 2008-08-09
yeah that checked out.  thanks.

now just gotta figure out the plugin problem

---

### Post by Diabolis on 2008-08-09
Are you on a AMD 64? because seems like the plug in for that architecture is missing.

[https://bugs.launchpad.net/sun-java/+bug/104512](https://bugs.launchpad.net/sun-java/+bug/104512)

However, the plug in is not a requisite for opera. Its required by some sites tho.

---

### Post by PsychedelicWonders on 2008-08-09
no intel quad core.

what should I do?

tha link basically said to install 32 until 64 is more advanced?

or install iced tea java but then others say that sucks?

---

### Post by Diabolis on 2008-08-09
Ah, ok. In synaptic **settings / repositories** and enable the other repositories (universe, multiverse, restricted).

Differences between the repositories: [http://www.ubuntu.com/community/ubuntustory/components](http://www.ubuntu.com/community/ubuntustory/components)

---

### Post by PsychedelicWonders on 2008-08-09
they were already enabled?

---

### Post by Diabolis on 2008-08-09
Have you updated recently?
```
sudo apt-get update
```

---

### Post by PsychedelicWonders on 2008-08-09
i typed that and got this...

psychedelicwonders@JohnnyScience:~$ sudo apt-get update
[sudo] password for psychedelicwonders: 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources                    
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages [4001B]                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages             
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources [1291B]                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources               
Fetched 32.9kB in 9s (3323B/s)                                                 
Reading package lists... Done
W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_hardy_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_hardy_main_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
psychedelicwonders@JohnnyScience:~$ 

is that good or bad?

---

### Post by Diabolis on 2008-08-09
No big deal, you have 2 entries duplicated in your sources.list file. You already know how to edit it. Just delete the duplicates and update again.

It is even telling you which are the duplicates:
> W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_hardy_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_hardy_main_binary-amd64_Packages)

You can highlight them in gedit, press <Ctrl>f and enter the text that you want to highlight. So you can point them out quickly.

---

### Post by PsychedelicWonders on 2008-08-09
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main

Seems I have 3 of the same here and 2 of the same... should I delete all duplicates?

---

### Post by Diabolis on 2008-08-09
Yes, you only need 2 of those.

---

### Post by PsychedelicWonders on 2008-08-10
why are there so many duplicates?

what about all these, should i clean these up too/

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by Diabolis on 2008-08-10
> **PsychedelicWonders said:**
> why are there so many duplicates?

what about all these, should i clean these up too/

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

If you look very carefully to those entries, you'll notice that none of them are duplicates ;)

---

### Post by PsychedelicWonders on 2008-08-10
alright, dups have been deleted, update has been run.

now what?

am I just SOL for getting a java plugin for 64?

---

### Post by Diabolis on 2008-08-10
Try to install the plug in again. It should work now.
```
sudo apt-get install sun-java6-plugin
```

---

### Post by PsychedelicWonders on 2008-08-10
still no dice...

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Fetched 1B in 1s (1B/s)  
Reading package lists... Done
psychedelicwonders@JohnnyScience:~$ sudo apt-get install sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
psychedelicwonders@JohnnyScience:~$

---

### Post by Diabolis on 2008-08-10
Can you post your sources.list file please.

---

### Post by PsychedelicWonders on 2008-08-10
#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main

---

### Post by Diabolis on 2008-08-10
This is the reason why is not working:
> #deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted

---

### Post by PsychedelicWonders on 2008-08-10
> **Diabolis said:**
> This is the reason why is not working:

so what does taht mean and what do i do to fix it so I can install java?

---

### Post by Diabolis on 2008-08-10
It is saying that you are in a 64 bit architecture and that you are in trouble: [https://bugs.launchpad.net/sun-java/+bug/104512](https://bugs.launchpad.net/sun-java/+bug/104512)

Java is already installed, the plug in is only for web content.

You said you weren't, so you either copied the sources.list file from another pc or you really are using a 64 bit cpu.

---

### Post by PsychedelicWonders on 2008-08-10
> **Diabolis said:**
> It is saying that you are in a 64 bit architecture and that you are in trouble: [https://bugs.launchpad.net/sun-java/+bug/104512](https://bugs.launchpad.net/sun-java/+bug/104512)

Java is already installed, the plug in is only for web content.

You said you weren't, so you either copied the sources.list file from another pc or you really are using a 64 bit cpu.

Hmm this is the only comp im using, so it must be 64 then.

It was the web I was trying to get java for, so im SOL?

---

### Post by Diabolis on 2008-08-10
You might want to follow the suggestions offered in the link I posted and keep an eye on that bug report. Hopefully the proper java plug in for the 64 bit architecture will be available in the near future.

---

### Post by PsychedelicWonders on 2008-08-10
everyone in the link said its basically impossible or not worth it though?

what is so difficult with 64 that things just "dont work" in this day and age?

---

### Post by PsychedelicWonders on 2008-08-14
I really want to be able to run java in opera, so much I am considering going from 64 to 32.

If i were to do so, is there any way to save all of the changes and settings I've done so far in 64 to make the flip that much easier and desirable?

---

### Post by Diabolis on 2008-08-14
Probably yes. Almost every application has a configuration folder in your home folder. You can see them by pressing **<Ctrl>h**. Maybe the 32 bit version will use your previous configuration folder and your changes will be kept.

---

