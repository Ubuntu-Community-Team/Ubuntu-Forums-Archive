---
title: "Help Please!! My whole system is horrible!"
date: 2008-07-14
forum: General Help
---

### Post by Kaleb816 on 2008-07-14
Hello, I am very new to Ubuntu and I honestly would prefer not to have it. But, it is installed on my work laptop which is a Toshiba and it probably has all of the problems in the world. First off, once I received it..I noticed that the sound didn't work. So I did some research on these forums to try and fix it. But as I did every step possible. The systems would come up with "Line" errors and things like that. So, I tried to do a program update and had horrible results because THAT would even give me an error that would kick me out before even selecting a update. Then I tried to do the Synaptic route and the system has a error for that program as well. Can anyone help me!!!

---

### Post by Rainstride on 2008-07-14
what model toshiba? it should say on the back.

---

### Post by Elfy on 2008-07-14
Well we might be able to - lets start with the synaptic error - open a terminal from the accessories menu - paste this command in and enter your password when it asks, you won't see your password being entered but it is there.

When you've entered the password - if there is an error message - paste it all here so we can see what it says.

```
sudo apt-get update
```

---

### Post by Kaleb816 on 2008-07-14
Okay, It doesn't say what model on the back. But I did the update code and got this...(( E: Type '‘deb' is not known on line 58 in source list /etc/apt/sources.list ))

---

### Post by Elfy on 2008-07-14
Ok in the terminal run this and paste it all 

```
cat /etc/apt/sources.list
```

---

### Post by Kaleb816 on 2008-07-14
Okay, the model of Toshiba I think is the (Satellite)  Does that sound correct?

---

### Post by Kaleb816 on 2008-07-14
Here are my results from that 



# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse #Added by software-properties
#AUTOMATIX REPOS END
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe #Added by software-properties
‘deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted’

---

### Post by Rainstride on 2008-07-14
on the back there should be a code something like l45-s2416 or something of the sort. i had to fix a toshiba yesterday and found they all have sound problems, depending on the model, i can tell you how to fix it.

---

### Post by coffeecat on 2008-07-14
The line that is causing the problem is the very last one - it starts with a tick. I'll let more knowledgeable people tell you how to deal with, but in the meantime I noticed this:

> #AUTOMATIX REPOSYou have been hit by the Automatix bug. You do not have a vanilla install of Ubuntu so you are not getting a genuine  experience of Ubuntu. Your Ubuntu is contaminated and how you uncontaminate it I do not know.

[Interesting reading]("http://en.wikipedia.org/wiki/Automatix_%28software%29").

---

### Post by knutschr on 2008-07-14
```
sudo gedit /etc/apt/sources.list
```

Remove the tick in front and end of your last line and save the file.

Do
```
sudo apt-get update
``` again and tell the result.

---

### Post by Kaleb816 on 2008-07-14
The model # is A135-S4727..

What exactly do you guys mean by the Ticks? bc I don't want to erase something I shouldn't. Thanks

---

### Post by Kaleb816 on 2008-07-14
Well, I deleted those lines and then tried the update.. Here are the results

E: Type '‘deb' is not known on line 58 in source list /etc/apt/sources.list

---

### Post by knutschr on 2008-07-14
In the beginning and end of your last line is a ' sign.
These must be removed to get the line understandable for the system.

---

### Post by Taxman415a on 2008-07-14
If this is a work laptop, why not ask your support people at work or at least the people that installed it? Ideally ask if you can do a fresh install without the automatix stuff.

---

### Post by Kaleb816 on 2008-07-14
okay..sorry I misunderstood last time...Here are the true results

Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US                  
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                 
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                           
Err [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                           
  404 Not Found
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [189B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [189B]   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_US           
Get:3 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]          
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release [58.5kB]     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US     
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [189B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US       
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US      
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [189B]      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg [189B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_US      
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release.gpg [189B]        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US               
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release [44.0kB]              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Translation-en_US 
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed Release.gpg [189B]          
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/universe Translation-en_US     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release [58.5kB]             
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release [58.5kB]                
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release [44.6kB]          
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages [103kB]         
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release [58.5kB]           
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed Release [51.5kB]            
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release [65.9kB]                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages                     
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages [273kB]        
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages [32.6kB]        
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages [14B]     
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages [103kB]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages [16.9kB]  
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Sources [9660B]          
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Sources [14B]      
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Sources [25.0kB]     
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages [5280B]   
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources [944B]     
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources [19.6kB]         
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources [812B]     
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources [11.5kB]     
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages [75.1kB]    
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Sources [3659B]    
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages [100kB]       
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages [10.8kB]    
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources [16.9kB]       
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources [1881B]      
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages [103kB]          
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages [5280B]    
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages [75.1kB]     
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages [5774B]    
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Sources [19.6kB]          
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Sources [944B]      
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Sources [11.5kB]      
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Sources [812B]      
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages [5764B]  
Get:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages [1075kB]                  
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources [74.2kB]        
Get:50 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages [5774B]   
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources [944B]    
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Packages [32.4kB]
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Packages [14B] 
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Packages [51.9kB]
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Packages [4849B]
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Sources [8289B]      
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Sources [14B]  
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Sources [16.7kB]
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Sources [1393B]
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/restricted Packages [14B]   
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main Packages [35.8kB]      
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Packages [1326B] 
Get:63 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/universe Packages [2813B]   
Get:64 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/restricted Sources [14B]    
Get:65 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main Sources [20.5kB]       
Get:66 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages [7664B]             
Get:67 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Sources [619B]
Get:68 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/universe Sources [655B]
Fetched 2820kB in 5s (508kB/s)                                         
Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Kaleb816 on 2008-07-14
> **Taxman415a said:**
> If this is a work laptop, why not ask your support people at work or at least the people that installed it? Ideally ask if you can do a fresh install without the automatix stuff.

Well, I did ask them and they have no support whatsoever. We are a small growing company and my people have little time to fix these issues.

---

### Post by knutschr on 2008-07-14
> **Taxman415a said:**
> If this is a work laptop, why not ask your support people at work or at least the people that installed it? Ideally ask if you can do a fresh install without the automatix stuff.

Agree.
It seems like the system has been badly treated before he got it :-(

---

### Post by issih on 2008-07-14
Ok looks like sources.list is ok now, as those results are proof it is connecting to the different repositories defined in the list.

So, with a bit of luck you should now be able to use update manager and synaptic, which should allow you to start installing new packages.

In essence that list tells the computer where on the internet to look for packages and updates. If the list contains invalid data it can't be parsed and then none of the update and package management facilities can run. Now it has been corrected things should be smoother.

As for the sound issue, hopefully having access to synaptic will let you fix it, let us know how it goes

---

### Post by avtolle on 2008-07-14
Go into the /etc/apt/sources.list file and comment out the last line you posted which refers to automatix by placing a # before it. Then, from the thermial ```
sudo apt-get update
``` which should update your sources, and if there are still error messages, post them here.

---

### Post by Kaleb816 on 2008-07-14
I think I erased the automatix lines..Where it said Beginning and End Automatix lines.

---

### Post by Rainstride on 2008-07-14
try runnig 

sudo gedit /etc/modprobe.d/alsa-base

it will open a text file, go to the bottom, in a new line paste this:

options snd-hda-intel model=3stack

when you reboot your sound should work if not try changing "3stack" to "6stack"
depending on your hardware that part will change. its how i fixed my friends toshiba.

---

### Post by Kaleb816 on 2008-07-14
Hey Rainstride...It wouldn't let me save that file..It said that it was restricted. =((

---

### Post by issih on 2008-07-14
Thats fine, those lines were comments (comments start with a # sign in that file, and many linux ones) deleting them will have had no effect whatsoever.

As has been mentioned, at some point someone installed Automatix on your pc. This program was intended to enable various popular add ons to ubuntu, mostly multimedia related. Unfortunately, it dodn't do a very good job, and has been superseded by much better methods. If you are lucky things will be ok, but automatix is known to have caused problems to do with update manager and various other things (have a look at the link posted earlier)

For now, I'd ignore that and just see if you can get your pc working, just be aware that the issue is there.

---

### Post by Rainstride on 2008-07-14
did it ask for your password when you ran sudo gedit /etc/modprobe.d/alsa-base?

---

### Post by issih on 2008-07-14
you need to be the root user to edit the file.
launch the text editor from a terminal (or from alt f2) using the command:

"gksudo gedit"

Enter your login password when prompted, then edit the file, you should now be able to save the changes.

sudo temporarily grants you the power of the root user.

---

### Post by coffeecat on 2008-07-14
> **Kaleb816 said:**
> I think I erased the automatix lines..Where it said Beginning and End Automatix lines.

That wasn't really what I meant. The problem line was the last one that started with a tick. It wasn't an Automatix line. Someone else told you what to do with that. The automatix lines pointed to various repositories used by automatix. They are not a problem in themselves. What worried me was what automatix might have done to your system already. Someone earlier in the thread said:

> It seems like the system has been badly treated before he got it :sad:Most of the problems you list in your first post seem to stem from this mucked-about sources.list. You can solve those problems but there may still be others lurking in your system because of the use of automatix. **Please** do not judge Ubuntu on the basis of this.

Food for thought from the link I gave earlier:

> On August 4, 2007, Automatix was reviewed by Matthew Garrett, a member of the core Ubuntu development team. In his words, &#8220;Automatix is, in itself, a poor quality package which fails to conform to Debian or Ubuntu policy.&#8221;

---

### Post by Kaleb816 on 2008-07-14
> **Rainstride said:**
> did it ask for your password when you ran sudo gedit /etc/modprobe.d/alsa-base?

Yes, and here are my results

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

---

### Post by koenn on 2008-07-14
> **Kaleb816 said:**
> Hello, I am very new to Ubuntu and I honestly would prefer not to have it. But, it is installed on **my work laptop** ... 
contact the helpdesk / IT department of the place where you work

---

### Post by Rainstride on 2008-07-14
yeah, at the very bottom in a new line add:

options snd-hda-intel model=3stack

---

### Post by Rainstride on 2008-07-14
it should say.

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
# Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
# non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=3stack

---

