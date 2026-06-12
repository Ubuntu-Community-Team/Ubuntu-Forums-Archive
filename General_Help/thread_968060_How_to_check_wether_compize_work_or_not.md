---
title: "How to check wether compize work or not"
date: 2008-11-02
forum: General Help
---

### Post by mihir786 on 2008-11-02
i dnt knw how to chek on my desktop dat compize fusion work on my pc or not

please help me out for this i wnt to install the compize fusion 

please thanx in advance :|

---

### Post by Kevbert on 2008-11-02
First thing is to find out what video card you have. Go to Applications-Accessories-Terminal and enter
```
lspci
```
The last line will indicate what make and model display adapter you have (please post this information here). If its Intel, Nvidia or ATI then there's a goog chance it will work with compiz.  What version of Ubuntu, Kubuntu, or Xubuntu are you using ?

---

### Post by mihir786 on 2008-11-02
> **Kevbert said:**
> First thing is to find out what video card you have. Go to Applications-Accessories-Terminal and enter
```
lspci
```
The last line will indicate what make and model display adapter you have (please post this information here). If its Intel, Nvidia or ATI then there's a goog chance it will work with compiz.  What version of Ubuntu, Kubuntu, or Xubuntu are you using ?



```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0b.0 Communication controller: Agere Systems Unknown device 0620
00:0b.1 Communication controller: Agere Systems Unknown device 0620
00:0b.2 Communication controller: Agere Systems Unknown device 0620
00:0b.3 Communication controller: Agere Systems Unknown device 0620
00:0b.4 Communication controller: Agere Systems Unknown device 0620
00:0b.5 Communication controller: Agere Systems Unknown device 0620
00:0b.6 Communication controller: Agere Systems Unknown device 0620
00:0b.7 Communication controller: Agere Systems Unknown device 0620
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter


```

I got this output buddy :|

---

### Post by mihir786 on 2008-11-02
And i m using ubuntu 8.04.1 desktop edition :-"

---

### Post by mihir786 on 2008-11-02
Please reply me can i use compize ??

---

### Post by loomsen on 2008-11-03
Not 2 much info from your lspci...

Use compiz check to get some more info:
```

wget http://blogage.de/files/4359/download -O compiz-check && chmod +x compiz-check && ./compiz-check
```

---

### Post by mihir786 on 2008-11-03
But wht can i do with this ?

---

### Post by mihir786 on 2008-11-03
```

--10:56:57--  http://blogage.de/files/4359/download
           => `compiz-check'
Resolving blogage.de... 78.46.34.206
Connecting to blogage.de|78.46.34.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 27,814 (27K) [application/octet-stream]

100%[====================================>] 27,814        37.26K/s             

10:56:58 (37.23 KB/s) - `compiz-check' saved [27814/27814]


Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
 Driver in use:         sis
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]




```

This is my output tell me please nw

---

### Post by loomsen on 2008-11-03
Well, looks good, seems like you should be able to run compiz.. in general. 

But I can't really help you as I have a nvidia card. ATI usually is a little behind with open source support. 

To install all run this, if you have gnome...
```

sudo apt-get update && sudo apt-get install ccsm emerald-themes compizconfig-backend-gconf fusion-icon-gtk emerald compiz-fusion compiz-fusion-gnome libcompizconfig compiz-gnome compiz-bcop compiz compizconfig-python compiz-fusion-extras compiz-fusion-extras-gnome
```

When done, type 
fusion-icon

and pray ^^ You should see an icon in your systemtray now. Rightclick, and find out :)

---

### Post by mihir786 on 2008-11-03
```

Ign http://ppa.launchpad.net hardy Release.gpg                       
Ign http://ppa.launchpad.net hardy/main Translation-en_IN            
Hit http://security.ubuntu.com hardy-security Release.gpg            
Ign http://security.ubuntu.com hardy-security/main Translation-en_IN 
Hit http://in.archive.ubuntu.com hardy Release.gpg                   
Ign http://in.archive.ubuntu.com hardy/main Translation-en_IN        
Ign http://ppa.launchpad.net intrepid Release.gpg                    
Ign http://ppa.launchpad.net intrepid/main Translation-en_IN         
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_IN
Ign http://security.ubuntu.com hardy-security/universe Translation-en_IN
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_IN
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]                
Ign http://in.archive.ubuntu.com hardy/restricted Translation-en_IN  
Ign http://in.archive.ubuntu.com hardy/universe Translation-en_IN    
Ign http://in.archive.ubuntu.com hardy/multiverse Translation-en_IN  
Hit http://in.archive.ubuntu.com hardy-updates Release.gpg           
Ign http://in.archive.ubuntu.com hardy-updates/main Translation-en_IN
Ign http://in.archive.ubuntu.com hardy-updates/restricted Translation-en_IN
Get:2 http://ppa.launchpad.net intrepid Release [27.6kB]             
Hit http://security.ubuntu.com hardy-security Release                
Ign http://in.archive.ubuntu.com hardy-updates/universe Translation-en_IN
Ign http://in.archive.ubuntu.com hardy-updates/multiverse Translation-en_IN
Hit http://in.archive.ubuntu.com hardy Release 
Hit http://in.archive.ubuntu.com hardy-updates Release              
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://ppa.launchpad.net hardy/main Sources                      
Hit http://security.ubuntu.com hardy-security/main Packages          
Hit http://in.archive.ubuntu.com hardy/main Packages                 
Ign http://ppa.launchpad.net intrepid/main Packages
Ign http://ppa.launchpad.net intrepid/main Sources                   
Hit http://security.ubuntu.com hardy-security/restricted Packages    
Hit http://security.ubuntu.com hardy-security/main Sources           
Hit http://security.ubuntu.com hardy-security/restricted Sources     
Hit http://in.archive.ubuntu.com hardy/restricted Packages           
Hit http://in.archive.ubuntu.com hardy/main Sources                  
Hit http://in.archive.ubuntu.com hardy/restricted Sources            
Hit http://ppa.launchpad.net hardy/main Packages                     
Hit http://security.ubuntu.com hardy-security/universe Packages      
Hit http://security.ubuntu.com hardy-security/universe Sources       
Hit http://security.ubuntu.com hardy-security/multiverse Packages    
Hit http://security.ubuntu.com hardy-security/multiverse Sources     
Hit http://in.archive.ubuntu.com hardy/universe Packages             
Hit http://in.archive.ubuntu.com hardy/universe Sources
Hit http://in.archive.ubuntu.com hardy/multiverse Packages
Hit http://in.archive.ubuntu.com hardy/multiverse Sources
Hit http://in.archive.ubuntu.com hardy-updates/main Packages
Hit http://in.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://in.archive.ubuntu.com hardy-updates/main Sources
Hit http://ppa.launchpad.net hardy/main Sources
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://in.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://in.archive.ubuntu.com hardy-updates/universe Packages
Hit http://in.archive.ubuntu.com hardy-updates/universe Sources
Hit http://in.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://in.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://ppa.launchpad.net intrepid/main Sources
Fetched 2B in 2s (1B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ccsm



```

hey i cant install this coz

the error is coming above i display tell me wht to do :((

---

### Post by loomsen on 2008-11-03
The same again and leave ccsm out.....
Maybe it's called compiz-config-settings-manager or such in the meanwhile.

---

### Post by Kevbert on 2008-11-03
Unfortunately you have a card that isn't supported by compiz-fusion. I'm surprised that compiz-check works.

---

### Post by mihir786 on 2008-11-03
Now tell me can i use compiz or nt???

---

### Post by mihir786 on 2008-11-03
> **loomsen said:**
> The same again and leave ccsm out.....
Maybe it's called compiz-config-settings-manager or such in the meanwhile.
I tried but not working :(

---

### Post by Kevbert on 2008-11-03
No. As far as I know it's not possible to use compiz with SiS graphics cards. I've mailed the originator of compiz-check and will let you know of any outcome. There was a project to try to get it running (Unichrome) but that has ceased.  So sorry you're out of luck.

---

### Post by mihir786 on 2008-11-03
Okie no pro :) 

so i cant run compize :((

---

### Post by Forlong on 2008-11-04
OK first of all, the inevitable disclaimer:
> **loomsen said:**
> Use compiz check to get some more info:
```

wget http://blogage.de/files/****/download -O compiz-check && chmod +x compiz-check && ./compiz-check
```
**DO NOT JUST COPY AND PASTE THIS** ([find out why]("http://forlong.blogage.de/entries/pages/To-everyone-who-want-to-share-my-projects"))
Please just link to the [project's page]("http://forlong.blogage.de/article/pages/Compiz-Check"). Thank you.
Oh, and by the way: it's nice you want to help but posting cryptically shell commands without explaining what they do is NOT helping. 


Now that we have that out of the way...
> **Kevbert said:**
> No. As far as I know it's not possible to use compiz with SiS graphics cards.
I already met people online claiming they could -- that's why I changed Compiz-Check so that it doens't FAIL in this case anymore -- but that's the first time I actually see an output of Compiz-Check confirming it.
I'm surprised to see it didn't prompt you that your card is blacklisted... I guess you already worked around that.

Could you please post the output of ```
compiz
``` in a terminal?

---

### Post by loomsen on 2008-11-04
I'm sorry and going to mind that in future posts.:oops:

---

### Post by Forlong on 2008-11-06
**mihir786**, maybe I didn't make myself clear enough as I quoted Kevbert. not you:

Please run ```
compiz
``` in a terminal and post the output here. This will help us finding out what the problem is.


@loomsen: sorry, I may have been a little too harsh on you. Thanks for taking the time and helping out. And thank you for understanding.

---

### Post by mihir786 on 2008-11-07
This is the otuput of the compize commnad :) so please tell me nw :)
```

noob@nobody-is-here:~/Desktop$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


```


so please tell me nw and thanx  for ur postive reply :)

---

### Post by Forlong on 2008-11-07
Well, I just searched around a bit and still can't seem to find anything positive for SiS chips regarding Compiz.

I don't know why exactly it doesn't work (as you can see, it surpasses any test I know) but it's obviously still not enough.

The output above basically says the same thing. The chip is blacklisted but you chose to ignore that. Then it goes on to check certain things and everything *seems* to be OK. But then it actually launches Compiz and it fails (the error message is not very informative, though).

So I'm, afraid it is in fact not possible (for now?) to run Compiz on that hardware.

---

### Post by mihir786 on 2008-11-07
Okie thanx for ur support and help 

but if there is any solution then please reply me here :)

---

