---
title: "Update PPA keys"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by jlh68 on 2009-03-26
I have a problem when using the Update Manager in that I get a message saying "No Public Key".  Does anyone know how to resolve this problem?

I get this when using my Acer ONE Netbook with Ubuntu 8.10 and Netbook Remix.  I can't remember if the Netbook Remix was down loaded from a PPA site or not.

---

### Post by Partyboi2 on 2009-03-26
You can add the key by opening a terminal and
```
gpg --keyserver keyserver.ubuntu.com --recv *********
gpg --export --armor ********* | sudo apt-key add -
```You will need to replace **** with the correct key. If you still  need help post the output to
```
sudo apt-get update
```

---

### Post by jlh68 on 2009-03-27
Where does the key code come from?  Here is the data requested.  Why do I have some Feisty backports?  I get eror messages about them also.


Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release.gpg
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US    
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                             
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Sources
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Sources
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Sources
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Sources
  404 Not Found [IP: 91.189.88.45 80]
Fetched 309B in 1s (215B/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.45 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
john@john-laptop:~$

---

### Post by jlh68 on 2009-03-27
Is the key this: 60D11217247D1CFF  ?

I used it in the commands in post number two. Below are the reslts.

john@john-laptop:~$ gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF
gpg: requesting key 247D1CFF from hkp server keyserver.ubuntu.com
gpg: key 247D1CFF: public key "Launchpad PPA for OpenOffice.org Scribblers" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
john@john-laptop:~$ gpg --export --armor 60D11217247D1CFF | sudo apt-key add -
OK
john@john-laptop:~$

---

### Post by jlh68 on 2009-03-27
I reviewed the apt-get update and then used 247D1CFF as the key.  I hope I was reading it correct.

comments?

---

### Post by Partyboi2 on 2009-03-27
Yes 60D11217247D1CFF is the correct key.
You will need to remove the feisty repos from your sources.list
```
gksu gedit /etc/apt/sources.list
``` Then remove all the feisty repos  then save and close gedit then back in the terminal update
```
sudo apt-get update
```If you need help removing the fesity repos then post the output to
```
cat /etc/apt/sources.list
```

---

### Post by jlh68 on 2009-03-27
Thanks.  I believe I have the key working correctly.  

Code:
gksu gedit/etc/apt/sources.list

I used this (copy&paste) from your post.  It did not work.  I went back and placed a space between gedit and /etc..... and it worked.  I just commented the fiesty line out using ## and a space, saved, closed and updated and it is all go now.

Again thanks for the help.

---

### Post by Partyboi2 on 2009-03-27
Happy to help, sorry about the missing space. :)

---

### Post by jlh68 on 2009-04-01
I haave three keys that i can't get authorized.  Here are the 3:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3F2A5EE4B796B6FE
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

I tried to use the method used  on my laptop  on this netbook but I got an error:  Invalid operation key

This worked before on the laptop, what is keeping it from working on this netbook?

---

### Post by spike_naples on 2009-04-01
Thanks. I really really needed this. May God bless all the good contributors!

---

### Post by Partyboi2 on 2009-04-01
> **jlh68 said:**
> I haave three keys that i can't get authorized.  Here are the 3:
Open a terminal and do the following for
> W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/") intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3F2A5EE4B796B6FE
```
gpg --keyserver keyserver.ubuntu.com --recv 3F2A5EE4B796B6FE
gpg --export --armor 3F2A5EE4B796B6FE | sudo apt-key add -
```for the next one
> W: GPG error: [http://packages.medibuntu.org]("http://packages.medibuntu.org/") intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```For the final one
> W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/") intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF```
gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF
gpg --export --armor 60D11217247D1CFF | sudo apt-key add -
```
then
```
sudo apt-get update
``` If there are any problems with adding the keys post the output from the terminal.

---

### Post by loomsen on 2009-04-01
```

sudo apt-key adv --recv-keys --keyserver=keyserver.ubuntu.com [color=blue]KeY1 kEy2 Key3 kEY4 key5 ...[/color]
```

```

sudo apt-key adv --recv-keys --keyserver=keyserver.ubuntu.com 3F2A5EE4B796B6FE 2EBC26B60C5A2783 60D11217247D1CFF

```

will fetch all three... Actually I created myself an alias, so far this solved any keyissues I had.

alias keygrab='sudo apt-key adv --recv-keys --keyserver=keyserver.ubuntu.com' 

and after sourcing it, 

keygrab KEY1 KEY2 KEY3

*done*

---

### Post by jlh68 on 2009-04-04
Thanks to both of you for the solutions.  I found that I had keyed in an incorrect command, and that it did not work.  When I was able to go back and copy and paste the earlier code that PARTYBOL2 had given me, I had success.  It goes to show that computers do just what you tell them and if you are not precise in your instructions then the computer either does nothing or produces a lot of garbage or breaks the system.

Again thanks to **Partybol2** and ** Loomsen**.

---

