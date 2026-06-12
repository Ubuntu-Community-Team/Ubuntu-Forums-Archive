---
title: "Ubuntu 9.10 Karmic Koala :: Ubuntu Software Center :: No &quot;Install&quot; button."
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by peetbull on 2009-10-29
Just finished Koala's installation.

The very first utility I turned on is "Ubuntu Software Center" (USC).

It sounded very promising, and, it, ultimately, is!

When I initiated the application, I searched through some packages but I couldn't find the "Install" button.

I thought it might be a bug with "Extra Effects Appearance Setting"; actually, my room-mate suggested it; well, it wasn't.

Then I thought to change "Software Sources" (System > Administration > Software Sources) to the following:

[LIST]
[*]    Tab "Ubuntu Software" _checked_:
[LIST]
[*]      Canonical Supported Open Source software (main)
[*]      Community Maintained Open Source software (universe)
[*]      Proprietary drivers for devices (restricted)
[*]     Software restricted by copyright or legal issues (multiverse)
[/LIST]
 
[*]    Tab "Other Software":
[LIST]
[*]      _check_ both repositories
[/LIST]
 
[/LIST]
 
And, then, I opened "Terminal" and executed the following:
  ```

sudo apt-get update
sudo apt-get upgrade

```When I re-opened USC then "Install" button, "magically" appeared.

I still can't figure why this occured, but I am still sharing it, in case anyone meets this issue.

---

### Post by Papajerry on 2009-10-29
Every time I pick a program to load i get, "Not available in the current data" .  How do I get the programs?  All boxes in synaptic are green.

---

### Post by iamthe1 on 2009-10-30
I suggest running the update manager once before running the Ubuntu Software Center just to refresh the software sources. I hope this works for you guys.

---

### Post by Un_loco on 2009-11-22
Thank you for this post.  I was freaking out not able to find the install button for my Audacity! lol I was running around in circles trying to figure it out for 30 minutes.

didnt even think that i had not updated on the fresh install

---

### Post by hougSTAR on 2009-11-22
I have the same issue.

Except when I try to update with Update Manager, it stops at 9 of 28 packages.  I tried to do the terminal, but all that went through was the sudo apt-get upgrade.  

It says for sudo get-apt update:

E: Could not get lock var/lib/atp/lists/lock - open (resource temporarily unavailable)
E: Unable to lock the list directory

---

### Post by Cavalryman on 2009-11-22
This is what I did and it worked (but your results may vary):

I removed Synaptic from the system. It gave me a dire warning, but I did it anyway. I then rebooted the computer just to be sure.

From the terminal, I ran sudo apt-get update and sudo apt-get upgrade

The "Install" button magically appeared.

I then re-installed Synaptic from Ubuntu Software Center and restarted my computer.

I have had no problems since. In fact, this is the **only** issue I have had with Ubuntu 9.10. All my hardware ran flawlessly, although I had to re-install the proprietary driver for my HP CP1215 color laser printer, but I expected that. It may have helped that I had selected all my hardware to "play nice" with Ubuntu 8.04 long ago, but I have had none of the issues that others are complaining about (except the one on this thread). All in all, I consider 9.10 a very nice OS and a step up in functionality.

---

### Post by mahela007 on 2009-12-07
sudo ap-get update worked for me.. I didn't have to do anything else.

---

### Post by djopium on 2009-12-28
> **peetbull said:**
> Just finished Koala's installation.

I still can't figure why this occured, but I am still sharing it, in case anyone meets this issue.

Thanks heaps for sharing that with us. I had the same problem. As soon as I did the update, the USC works fine.

Cheers, OPi

---

### Post by drparin on 2010-02-03
Thank you for posting the solutions.:p

---

### Post by sevenX on 2010-02-20
SOLUTION:

sudo apt-get update
sudo apt-get upgrade

WORKED GREAT! THANKS!

---

### Post by daisyfoofpoof on 2010-02-22
thanks peetbull!  worked great!

---

### Post by Guuthulhu on 2010-02-26
After Vista giving me trouble resulting in a system restore, it was the perfect excuse to go ahead and dual boot Ubuntu again. After ensuring everything was all hunky-dory, I had the same issue - unable to install anything in the Software Center. Thanks to your solution, I can get back to getting myself situated. Cheers!

---

### Post by kliffs on 2010-03-03
> **peetbull said:**
> 


When I re-opened USC then "Install" button, "magically" appeared.


The exact same thing happened to me, i did what you said and voila.

---

### Post by stg1129 on 2010-03-22
Ok this has been rather frustrating. I've done the sudo apt-get update and upgrade. This was the result:


lalvarez@Office:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg                         
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_US              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                 
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release            
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release                 
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages
Reading package lists... Done
sulalvarez@Office:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lalvarez@Office:~$ 


I reopened the Ubuntu Software Center and still get the same message "not available in the current data" Is there any other things I can try?!?!

---

