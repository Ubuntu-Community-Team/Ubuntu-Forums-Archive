---
title: "Can't sudo apt-get ANYTHING"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by anotherdrumdude on 2009-03-12
I am unable to sudo apt-get anything. I was trying to find a way to upgrade to the new Open Office 3.0.1 and I did something to create this, but now I can't sudo ANYTHING!!!

Plus... I still haven't been able to upgrade my Open Office.

Help!

---

### Post by anotherdrumdude on 2009-03-12
E: Type 'http://74.125.113.132/search?q=cache:FOc-JwWlCyUJ:news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml+ubuntu+open+office+3&hl=en&ct=clnk&cd=1&gl=us&client=firefox-adeb' is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.

---

### Post by cantormath on 2009-03-12
> **anotherdrumdude said:**
> E: Type 'http://74.125.113.132/search?q=cache:FOc-JwWlCyUJ:news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml+ubuntu+open+office+3&hl=en&ct=clnk&cd=1&gl=us&client=firefox-adeb' is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.

Not sure what your situation is, but what happens when you 
:~$ sudo apt-get update
:~$ sudo apt-get upgrade
?

Did you add something to your /etc/apt/sources.list file? if so what?

---

### Post by anotherdrumdude on 2009-03-12
:~$ sudo apt-get update
E: Type 'http://74.125.113.132/search?q=cache:FOc-JwWlCyUJ:news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml+ubuntu+open+office+3&hl=en&ct=clnk&cd=1&gl=us&client=firefox-adeb' is not known on line 54 in source list /etc/apt/sources.list

~$ sudo apt-get upgrade
E: Type 'http://74.125.113.132/search?q=cache:FOc-JwWlCyUJ:news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml+ubuntu+open+office+3&hl=en&ct=clnk&cd=1&gl=us&client=firefox-adeb' is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.

I think I tried adding the http:// address above to the repository listing in /etc/apt/sources.list in order to get updates for Open Office like one of the forums suggested. Problem is that it didn't work.

---

### Post by Partyboi2 on 2009-03-12
Looks like you have an incorrect entry in your sources.list. Could you please post your sources.list
```
cat /etc/apt/sources.list
```

---

### Post by anotherdrumdude on 2009-03-12
:~$ cat /etc/apt/sources.list
# deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1)]/ intrepid main restricted                                                          
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to    
# newer versions of the distribution.                                        

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any  
## review or updates from the Ubuntu security team.                        
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe                 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe             
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe         
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe     

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in      
## multiverse WILL NOT receive any review or updates from the Ubuntu        
## security team.                                                           
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse                
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse            
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse        
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse    

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
[http://74.125.113.132/search?q=cache:FOc-JwWlCyUJ:news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml+ubuntu+open+office+3&hl=en&ct=clnk&cd=1&gl=us&client=firefox-adeb](http://74.125.113.132/search?q=cache:FOc-JwWlCyUJ:news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml+ubuntu+open+office+3&hl=en&ct=clnk&cd=1&gl=us&client=firefox-adeb) [http://74.125.113.132/search?q=cache:FOc-JwWlCyUJ:news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml+ubuntu+open+office+3&hl=en&ct=clnk&cd=1&gl=us&client=firefox-adeb](http://74.125.113.132/search?q=cache:FOc-JwWlCyUJ:news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml+ubuntu+open+office+3&hl=en&ct=clnk&cd=1&gl=us&client=firefox-adeb) [http://74.125.113.132/search?q=cache:FOc-JwWlCyUJ:news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml+ubuntu+open+office+3&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a](http://74.125.113.132/search?q=cache:FOc-JwWlCyUJ:news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml+ubuntu+open+office+3&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a) openoffice

---

### Post by sahabcse on 2009-03-12
Comment out the following entry in /etc/apt/sources.list

[http://74.125.113.132/search?q=cache...t=firefox-adeb](http://74.125.113.132/search?q=cache...t=firefox-adeb) [http://74.125.113.132/search?q=cache...t=firefox-adeb](http://74.125.113.132/search?q=cache...t=firefox-adeb) [http://74.125.113.132/search?q=cache...ient=firefox-a](http://74.125.113.132/search?q=cache...ient=firefox-a) openoffice 

Then try apt-get update

---

### Post by sisco311 on 2009-03-12
never mind, i'm slow

---

### Post by Partyboi2 on 2009-03-12
You need to remove the bad entry from your sources.list 
> [http://74.125.113.132/search?q=cache...t=firefox-adeb]("http://74.125.113.132/search?q=cache:FOc-JwWlCyUJ:news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml+ubuntu+open+office+3&hl=en&ct=clnk&cd=1&gl=us&client=firefox-adeb") [http://74.125.113.132/search?q=cache...t=firefox-adeb]("http://74.125.113.132/search?q=cache:FOc-JwWlCyUJ:news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml+ubuntu+open+office+3&hl=en&ct=clnk&cd=1&gl=us&client=firefox-adeb") [http://74.125.113.132/search?q=cache...ient=firefox-a]("http://74.125.113.132/search?q=cache:FOc-JwWlCyUJ:news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml+ubuntu+open+office+3&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a") openofficeTo do this 
```
gksu gedit /etc/apt/sources.list
```then remove ```
[http://74.125.113.132/search?q=cache...t=firefox-adeb]("http://74.125.113.132/search?q=cache:FOc-JwWlCyUJ:news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml+ubuntu+open+office+3&hl=en&ct=clnk&cd=1&gl=us&client=firefox-adeb") [http://74.125.113.132/search?q=cache...t=firefox-adeb]("http://74.125.113.132/search?q=cache:FOc-JwWlCyUJ:news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml+ubuntu+open+office+3&hl=en&ct=clnk&cd=1&gl=us&client=firefox-adeb") [http://74.125.113.132/search?q=cache...ient=firefox-a]("http://74.125.113.132/search?q=cache:FOc-JwWlCyUJ:news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml+ubuntu+open+office+3&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a") openoffice
```  from the bottom of your sources.list and save and close gedit. Then back in the terminal
```
sudo apt-get update
```

---

### Post by anotherdrumdude on 2009-03-12
:~$ gksu gedit /etc/apt/sources.list

(gksu:29147): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(gksu:29147): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(gksu:29147): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(gksu:29147): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(gksu:29147): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(gksu:29147): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(gksu:29147): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(gksu:29147): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

:~$ gksu gedit /etc/apt/sources.list
:~$ gksu gedit /etc/apt/sources.list
:~$

Doesn't seem to do anything. I'm running the new version of Kubuntu if that helps? I'm kinda new to Linux.

---

### Post by Partyboi2 on 2009-03-12
Then don't use gedit, gedit is for ubuntu, for Kubuntu you need to replace gedit with kate so try
```
kdesu kate /etc/apt/sources.list
```

---

### Post by anotherdrumdude on 2009-03-12
:~$ kdesu kate /etc/apt/sources.list
bash: kdesu: command not found

******* A...

---

### Post by thesavager on 2009-03-12
its:

```
ksudo kate /etc/apt/sources.list
```

cheers ...

---

### Post by sahabcse on 2009-03-12
Try

Vim /etc/apt/sources.list

Otherwise install apt-get install kdesu kate and try

kdesu kate /etc/apt/sources.list

---

### Post by anotherdrumdude on 2009-03-12
michael@Mikes-Laptop:~$ kdesu kate /etc/apt/sources.list
bash: kdesu: command not found
michael@Mikes-Laptop:~$ ksudo kate /etc/apt/sources.list
bash: ksudo: command not found
michael@Mikes-Laptop:~$ Vim /etc/apt/sources.list
bash: Vim: command not found
michael@Mikes-Laptop:~$ install apt-get install kdesu kate
install: target `kate' is not a directory

Still no luck. I think my computer has it in for me... I knew I should have bought it that new CD drive it wanted lol.

---

### Post by sahabcse on 2009-03-12
Hi

Open the synaptic manager in system>>administration and there click setting>>repositories and remove the entry 

[http://74.125.113.132/search?q=cache...t=firefox-adeb](http://74.125.113.132/search?q=cache...t=firefox-adeb) [http://74.125.113.132/search?q=cache...t=firefox-adeb](http://74.125.113.132/search?q=cache...t=firefox-adeb) [http://74.125.113.132/search?q=cache...ient=firefox-a](http://74.125.113.132/search?q=cache...ient=firefox-a) openoffice 

in third party software tap. And click reload

---

### Post by Kevbert on 2009-03-12
Try ```
sudo nano -w /etc/apt/sources.list
```
Go to the offending line and put ## at the start of the line.
To save, select Ctrl+O (as in orange), Yes to save and Ctrl+X to exit.

---

### Post by anotherdrumdude on 2009-03-12
> **Kevbert said:**
> Try ```
sudo nano -w /etc/apt/sources.list
```
Go to the offending line and put ## at the start of the line.
To save, select Ctrl+O (as in orange), Yes to save and Ctrl+X to exit.

That worked, it's removed! ok, great!

Now would anyone know the CORRECT way to update OpenOffice 3.0 to 3.0.1?
And maybe possibly get to it continually do this?

---

### Post by Partyboi2 on 2009-03-12
You should be able to add
```
 deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
``` as a 3rd party repo and upgrade to 3.0.1

---

### Post by anotherdrumdude on 2009-03-12
It says I am missing a public key. Any idea where I could find one?

---

### Post by sisco311 on 2009-03-12
> **anotherdrumdude said:**
> it says i am missing a public key. Any idea where i could find one?

[thread]1056099[/thread]

---

### Post by Partyboi2 on 2009-03-12
Open a terminal and add the key

```
gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF
gpg --export --armor 60D11217247D1CFF | sudo apt-key add -
```
then
```
sudo apt-get update
```

---

### Post by anotherdrumdude on 2009-03-12
Thanks guys! Works like a charm!

You rock! :P

---

### Post by nelskurian on 2009-03-12
Do you have the root privileges.may be its due to some graphical drawing error.So if you familiar with terminal pls try

#sudo vim /etc/apt/sources.list

press 'i'
remove the above referred lines and then press 'ESC' then ":wq' to save and quit.
Then do the one below 

#sudo apt-get update
Check-it-out

---

