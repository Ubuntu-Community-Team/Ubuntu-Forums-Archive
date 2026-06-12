---
title: "update manager error"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by Muskegman on 2009-05-03
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

This is the error message i get when using update manager any ideas how to proceed? I recently upgraded from Intrepid 8.10 to Jaunty 9.04

---

### Post by Partyboi2 on 2009-05-04
Hi, open a terminal (Applications>Accessories>Terminal) and add the key 
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by Muskegman on 2009-05-09
Hello again I am still having trouble getting third party software re enabled :

I type the following in terminal and this is the result: 


mark@mark-desktop:~$ gksu gedit /etc/apt/sources.list
mark@mark-desktop:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_CA                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_CA              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_CA                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_CA              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_CA  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports Release.gpg      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/main Translation-en_CA
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_CA           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_CA 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports Release          
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/main Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/restricted Packages        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Sources
Fetched 308B in 2s (103B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2836CB0A8AC93F7A
W: You may want to run apt-get update to correct these problems
mark@mark-desktop:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_CA                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_CA   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports Release.gpg      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/restricted Translation-en_CA
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_CA           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_CA      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_CA  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports Release          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_CA 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_CA
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/main Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) intrepid-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Sources
Fetched 308B in 2s (107B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2836CB0A8AC93F7A
W: You may want to run apt-get update to correct these problems
mark@mark-desktop:~$ 

After typing  "apt-get update" I keep getting the same message

Anyone have any ideas it just keeps sending me in this same loop:(

---

### Post by Partyboi2 on 2009-05-09
You need to add the key for the 3rd party ppa.
```
gpg --keyserver keyserver.ubuntu.com --recv 2836CB0A8AC93F7A
gpg --export --armor 2836CB0A8AC93F7A  | sudo apt-key add -
```
then
```
sudo apt-get update
```

---

### Post by Muskegman on 2009-05-09
Thanks for your help partyboi2 i will give it a try
:)

---

### Post by Muskegman on 2009-05-09
Hi it took me 2 attempts but all seems to have downloaded and worked, again Thankyou very much for all your help partyboi2 very much appreciated.:)

Cheers

Muskegman

---

### Post by hoghunter82d on 2009-05-16
Thanks Partyboi2! This solved my problem.

---

### Post by carljung on 2009-06-11
I followed the terminal instructions but then I get the message : 

gpg: "gpg" not a key ID: skipping
gpg: "--export" not a key ID: skipping
gpg: "--armor" not a key ID: skipping
gpg: requesting key 8AC93F7A from hkp server keyserver.ubuntu.com
gpg: requesting key 8AC93F7A from hkp server keyserver.ubuntu.com
gpg: key 8AC93F7A: "Launchpad Kubuntu Updates" not changed
gpg: key 8AC93F7A: "Launchpad Kubuntu Updates" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2
gpg: no valid OpenPGP data found.

I'm completely incompetent when it comes to terminal, so any help on thsi would be greatly appreciated. :confused:

---

### Post by Partyboi2 on 2009-06-11
> **carljung said:**
> I followed the terminal instructions but then I get the message : 

gpg: "gpg" not a key ID: skipping
gpg: "--export" not a key ID: skipping
gpg: "--armor" not a key ID: skipping
gpg: requesting key 8AC93F7A from hkp server keyserver.ubuntu.com
gpg: requesting key 8AC93F7A from hkp server keyserver.ubuntu.com
gpg: key 8AC93F7A: "Launchpad Kubuntu Updates" not changed
gpg: key 8AC93F7A: "Launchpad Kubuntu Updates" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2
gpg: no valid OpenPGP data found.

I'm completely incompetent when it comes to terminal, so any help on thsi would be greatly appreciated. :confused:
Hi, looks like you might have entered both terminal commands as one. There are 2 commands that you need to enter, so the first needs to run first before you can run the 2nd. So in the terminal run the first one[FONT=monospace]
[/FONT]```
gpg --keyserver keyserver.ubuntu.com --recv 2836CB0A8AC93F7A
```when it has finished and returns you to the prompt (eg karl@karl-desktop) enter the 2nd one
```
gpg --export --armor 2836CB0A8AC93F7A  | sudo apt-key add -
```then
```
sudo apt-get update
```

---

### Post by jonnybal@googlemail.com on 2009-10-01
Thanks to Partyboi2 for this information. I have now edited [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) to include these vital commands to add the key. I guess someone left that bit out on the original post. Hopefully now people wont have the problem.

---

### Post by JonathanEllis on 2009-10-01
Thanks to Partyboi2 for this information. I have now edited [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) to include these vital commands to add the key. I guess someone left that bit out on the original post. Hopefully now people wont have the problem.

---

### Post by udippel on 2010-01-20
Alas, I do still have that problem.

Here the BADSIG key is 2EBC26B60C5A2783, but I tried both; and both additions worked ("requesting key ... not changed ... gpg: unchanged :1"), followed by the export/key-add which ends with 'OK'.

Still, I get the error for the medibuntu, and only for the medibuntu.

What can I do next?

Uwe

---

### Post by ramashema on 2010-06-16
thanx

---

