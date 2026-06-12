---
title: "Samsung printer ML1860 instalation"
date: 2011-08-16
forum: Hardware
---

### Post by etsah57 on 2011-08-16
I have just purchased a new Samsung ML1860 printer and I can't get it to work. Samsung provide a driver at their web site, UnifiedLinuxDriver 0.95.tar.gz
I downloaded this file onto my harddrive, but I can't seem to get it to install.
Instructions received said to open a terminal and type: $ sudo cdroot/autorun
This did not work.
etsah57@etsah57-KZ208AA-ABG-m9385a:~$ $ sudo cdroot/autorun
$: command not found

 I then tried to add the appropriate steps to where the file is on my harddrive
etsah57@etsah57-KZ208AA-ABG-m9385a:~$ $ sudo Colin/08.downloads/Samsung/cdroot/autorun
$: command not found
This didn't work either.

I tried to make the address a bit more complete, no success.
etsah57@etsah57-KZ208AA-ABG-m9385a:~$ $ sudo media/Colin/08.Downloads/Samsung/cdroot/autorun
$: command not found

I then found this instruction "[FONT=Arial][FONT=Arial][COLOR=black]Download and extract the driver[/COLOR][/FONT][/FONT][LEFT][LEFT][FONT=Arial][FONT=Arial][COLOR=black]   [root@localhost root]#tar xzf [Downloaded File Name(XXXX.tar.gz)]"[/COLOR][/FONT][/FONT][/LEFT][/LEFT]
etsah57@etsah57-KZ208AA-ABG-m9385a:~$ [root@localhost root]#tar xzf unifiedLinuxDriver_0.95.tar.gz
[root@localhost: command not found
This hasn't worked either. What do I do? I am a novice and this doesn't make a lot of sense to me
Please help

---

### Post by Azdour on 2011-08-16
Hi,

Whenever I need to install a Samsung printer I use these instructions that have been kindly written by tweedledee:

[http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)

---

### Post by etsah57 on 2011-08-16
So I opened the file: /etc/apt/sources.list and edited it so it has these 2 lines at the end;
deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra
deb-src [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra
Now it wants me to Install the GPG key: 
single step in the terminal (as root or using sudo): 
[LIST]
[*]wget -O - [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg) | sudo apt-key add -
[/LIST]
Did that in terminal, seems to be ok. Last instruction:
Refresh your repository listings
How do I do that?

---

### Post by Azdour on 2011-08-16
Hi,

It says in the instructions to use:

```
sudo apt-get update
```

Once you've installed the packages you are looking for the Samsung Unified Driver Configurator. On my machine thats under Applications | System Tools. I use the Configurator to add the Printer.

---

### Post by etsah57 on 2011-08-16
Did that, and this hapened.
etsah57@etsah57-KZ208AA-ABG-m9385a:~$ sudo apt-get update
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty InRelease
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates InRelease                       
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security InRelease                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty Release.gpg                             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates Release.gpg                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security Release.gpg                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty Release                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates Release                         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security Release                        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/main Sources                            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/universe Sources                        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/main i386 Packages                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/multiverse Sources              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/main i386 Packages              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/restricted i386 Packages        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/universe i386 Packages          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/multiverse i386 Packages        
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security/restricted Sources             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security/main Sources                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security/multiverse Sources             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security/universe Sources               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security/main i386 Packages             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security/restricted i386 Packages       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security/universe i386 Packages         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security/multiverse i386 Packages       
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security/main TranslationIndex          
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security/multiverse TranslationIndex    
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security/restricted TranslationIndex    
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security/universe TranslationIndex      
Ign [http://www.bchemnet.com](http://www.bchemnet.com) debian InRelease                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/main Translation-en_US                  
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/main Translation-en           
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/multiverse Translation-en_US  
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/multiverse Translation-en     
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/restricted Translation-en_US  
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/restricted Translation-en     
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/universe Translation-en_US              
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/main Translation-en_US          
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/main Translation-en             
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/multiverse Translation-en_US    
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security/main Translation-en_US         
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security/main Translation-en            
Get:1 [http://www.bchemnet.com](http://www.bchemnet.com) debian Release.gpg [198 B]                       
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security/multiverse Translation-en_US   
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security/multiverse Translation-en      
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security/restricted Translation-en_US   
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security/restricted Translation-en
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) natty-security/universe Translation-en        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                   
Get:2 [http://www.bchemnet.com](http://www.bchemnet.com) debian Release [3,757 B]
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                        
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                
Hit [http://www.bchemnet.com](http://www.bchemnet.com) debian/extra Sources                      
Hit [http://www.bchemnet.com](http://www.bchemnet.com) debian/extra i386 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release     
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages          
Ign [http://www.bchemnet.com](http://www.bchemnet.com) debian/extra TranslationIndex
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex             
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US     
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en        
Ign [http://www.bchemnet.com](http://www.bchemnet.com) debian/extra Translation-en_US
Ign [http://www.bchemnet.com](http://www.bchemnet.com) debian/extra Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Fetched 271 B in 6s (39 B/s)                                                   
Reading package lists... Done

But it still doesn't print

---

### Post by Azdour on 2011-08-16
Hi,

> Just installing the samsungmfp-driver and samsungmfp-data packages should enable full printing support;

Once you've installed the packages you are looking for the Samsung Unified Driver Configurator application. On my machine that's under Applications | System Tools. I used the Configurator to add the Printer. I then go to System | Administration| Printing to see that the printer is there and to print a test page to check it's all working.

---

### Post by etsah57 on 2011-08-16
The printer is there under applications, but does not print. Either telling it to print a test sheet or trying to print a document.
It lists the printer as a ML-1860
But, in the properties it lists make and model as: Samsung ML-1750 - CUPS+Gutenprint v5.2.6 simplified.
It does give an option to change, so, in the spirit of Adventure, it gives me a further 8 choices. ML-1750, 2.0.0 [en] does actually print a page which says:
Internal error - please use the proper driver
Position: 0x0 (0)
System: h6fw_5.49/xl_op
Lines: 180
Version: SPL 5.49 10-20-2010

---

### Post by Azdour on 2011-08-16
Hi,

So you launched the Samsung Unified Driver Configurator under the Applications menu and you added the printer. Or was the printer already there? In which case can you remove it and add it back using the Samsung Unified Driver Configurator?

If that does not help I can only suggest you asking on HOWTO Install Samsung Unified Printer Driver thread:

[http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)

Or wait to see if anyone else can answer you on this thread, sorry I cannot be of more help. I alway use the Configurator and I've never has a problem with any of our Samsung printers.

---

### Post by etsah57 on 2011-08-16
[QUOTE=Azdour;11157045]Hi,

So you launched the Samsung Unified Driver Configurator under the Applications menu and you added the printer. Or was the printer already there? In which case can you remove it and add it back using the Samsung Unified Driver Configurator?

I don't have, in the Applications,  Samsung Unified Driver Configurator. I only have a printer option. And it lists the ML1860

I have used Samsung ML1640's in the past with no problems, it died and I couldn't get another one. I tried to install a Canon LBP6000 without success. So I picked up this Samsung ML1860, but just can't get it to work and there are no drivers that match up to it, except on the Samsung site and I can't seem to install the driver they provide

Frustrated

---

### Post by Azdour on 2011-08-16
Hi,

Have you installed the following packages:

samsungmfp-driver and samsungmfp-data

---

### Post by etsah57 on 2011-08-16
> **Azdour said:**
> Hi,

Have you installed the following packages:

samsungmfp-driver and samsungmfp-data

Not deliberately or purposefully. If they installed automatically, they are installed. Otherwise, where do I find these 2 files and how do I install them?

---

### Post by Azdour on 2011-08-17
Hi,

Since you have updated you repositories you should be able to find them in the Synaptic Package Manager.

---

### Post by etsah57 on 2011-08-17
It worked!!! Thank you very much for your help:p

---

### Post by Azdour on 2011-08-18
Hi,

Glad to hear it's all working. Any chance you can mark this thread as solved?

---

### Post by etsah57 on 2011-10-15
Aaaaaahhhhhhh!
Updated to the latest version of Ubuntu and the printer has stopped working.
Tried to follow the same patten as before, but the system is different and I can't follow it exactly. 
In the Synaptic package manage there is the file: samsungmfp-driver, but it is not ticked. I can't tick it, but when I right click on the name I have the option to mark for installation, or mark for deletion. 
When I click on Mark for installation I get this message:
Package samsungmfp-driver has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list
The other file: samsungmfp-data is not there at all
When I go into the dashboard, system, printing. The printer is there. It has both a green tick on it and a red exclamation mark.
When I right click properties, under Printer State: it says: Idle - File "/usr/lib/cups/filter/rastertosamsungsplc" not available: No such file or directory

What do I do?
Please

---

### Post by Azdour on 2011-10-17
Hi,

I think you should re-post your question on the thread:

[http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)

Hopefully someone there may be able to give you the answer.

---

