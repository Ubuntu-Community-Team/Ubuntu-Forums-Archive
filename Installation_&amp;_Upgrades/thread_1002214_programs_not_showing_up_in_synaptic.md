---
title: "programs not showing up in synaptic"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by Rocket Sock on 2008-12-04
I figure this would be the best place to ask, since this really is more of a larger problem.

I'm trying to install pygame from synaptic (And please dont tell me to compile from source, I would like to fix this). Problem is, it's not showing up. I've cross checked my settings with a friend, and the only thing he has different, is that he's downloading from the US main server. When I set my OS up, I for some reason, selected a Canadian city, and its defaulting me to the Canadian Main Server. I tried to change my location in system>admin>time and date, but no dice. 

Can anyone help me out with swapping servers, or fixing this? I tried to download from one of the US servers on the server list, and still nothing.

---

### Post by taurus on 2008-12-04
System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and pick the Main Server or whatever server on the list.  Don't forget the click the Reload button.

---

### Post by Rocket Sock on 2008-12-04
I tried that. What Im saing is that, by default, you have "Server for United States", or, in my case, "Server for Canada". I can only select from one of the servers in the United States, there is no option for "Server from United States". 

Seems stupid, but I swear, this is the only different between our synaptics. He can see pygame, I cannot.

---

### Post by kostkon on 2008-12-04
> **Rocket Sock said:**
> I tried that. What Im saing is that, by default, you have "Server for United States", or, in my case, "Server for Canada". I can only select from one of the servers in the United States, there is no option for "Server from United States". 

Seems stupid, but I swear, this is the only different between our synaptics. He can see pygame, I cannot.
Check if you have all the necessary repositories enabled in *System &#8594; Administration &#8594; Software Sources* (i.e. main, restricted, universe, multiverse).

---

### Post by Rocket Sock on 2008-12-04
Those are enabled. 
I guess for starters, Is is possible to switch it to where I have "Server for United States" listed? I've got everything else on that screen checked. main, restricted, uni, multi, source.

---

### Post by Rocket Sock on 2008-12-04
Ok. New problem. I found pygame, and discovered the bigger issue. Quick searching doesnt work. At all. I did a quick search for 2vcard (THe first item on the list) and it found nothing. 
Any idea whats wrong?

---

### Post by kostkon on 2008-12-04
> **Rocket Sock said:**
> Ok. New problem. I found pygame, and discovered the bigger issue. Quick searching doesnt work. At all. I did a quick search for 2vcard (THe first item on the list) and it found nothing. 
Any idea whats wrong?
Open a terminal (*Applications &#8594; Accessories &#8594; Terminal*) and do
```
sudo apt-get update
```
it will ask you for a password, give yours.

Post any errors that you may get.

ADDED: close Synaptic or Add/Remove first, before doing the above.

---

### Post by Rocket Sock on 2008-12-04
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_CA        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_CA  
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg             
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_CA  
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Translation-en_CA
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release               
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release               
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release              
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Packages


Still not working on synaptic

---

### Post by jenkinbr on 2008-12-04
> **Rocket Sock said:**
> Ok. New problem. I found pygame, and discovered the bigger issue. Quick searching doesnt work. At all. I did a quick search for 2vcard (THe first item on the list) and it found nothing. 
Any idea whats wrong?
I don't use quicksearch - I've found it to be a joke for that very reason - try using the search tool and see what it does.

---

### Post by sentientd on 2008-12-06
> **jenkinbr said:**
> I don't use quicksearch - I've found it to be a joke for that very reason - try using the search tool and see what it does.

I'm having the same problem and have tried using the search tool, but still find nothing.

All the sources are enabled.

---

