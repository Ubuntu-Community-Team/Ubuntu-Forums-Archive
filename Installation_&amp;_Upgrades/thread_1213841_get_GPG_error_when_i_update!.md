---
title: "get GPG error when i update!"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by hyperyoda on 2009-07-15
Any clue how to fix this? Running Jaunty

root@hyperyoda:~#  update-manager  
/var/lib/python-support/python2.6/dbus/connection.py:242: DeprecationWarning: object.__init__() takes no parameters
  super(Connection, self).__init__(*args, **kwargs)
root@hyperyoda:~#  update-manager  
root@hyperyoda:~# apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [191B]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                    
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                                                                                
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1308B]                                                                                         
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                                                                                       
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US                                                                      
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                                                                             
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US                                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                                                                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US                                                                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_US                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                                                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                                                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US                                                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                                                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                                                                             
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                                                                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                                                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US                                                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US                                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                                                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                                                                                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US                                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg                                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US                                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US                                                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US                                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release.gpg                                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                                                                               
Get:6 [http://dl.google.com](http://dl.google.com) stable/main Packages [615B]                                                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Translation-en_US                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Translation-en_US                                   
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [52.9kB]                                                                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages                                                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Translation-en_US                                     
Get:8 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [954B]                                                       
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                                                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Translation-en_US                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Sources                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Sources
Fetched 3684B in 1s (3093B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 015A66E603E02400
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A7E13D78E4A4F4F4
W: You may want to run apt-get update to correct these problems

---

### Post by raymondh on 2009-07-15
In terminal, type (or copy and paste into) ... I have already added the pubkeys in the commands:

```
gpg --keyserver subkeys.pgp.net --recv 015A66E603E02400
gpg --export --armor 015A66E603E02400 | sudo apt-key add -
```

```
gpg --keyserver subkeys.pgp.net --recv A7E13D78E4A4F4F4
gpg --export --armor A7E13D78E4A4F4F4 | sudo apt-key add -
```

What you are doing is looking for, exporting and adding the pubkey. 

Then re-run you update/upgrade command.

Post back if you encounter further errors.

---

### Post by hyperyoda on 2009-07-16
> **raymondhenson said:**
> In terminal, type (or copy and paste into) ... I have already added the pubkeys in the commands:

```
gpg --keyserver subkeys.pgp.net --recv 015A66E603E02400
gpg --export --armor 015A66E603E02400 | sudo apt-key add -
```

```
gpg --keyserver subkeys.pgp.net --recv A7E13D78E4A4F4F4
gpg --export --armor A7E13D78E4A4F4F4 | sudo apt-key add -
```

What you are doing is looking for, exporting and adding the pubkey. 

Then re-run you update/upgrade command.

Post back if you encounter further errors.

Thanks Raymond, that worked :D

---

### Post by raymondh on 2009-07-16
> **hyperyoda said:**
> Thanks Raymond, that worked :D

De nada (you're welcome) hyperyoda :)

Keep the code handy, you will be adding more pubkeys in the future.

happy Ubuntuing.

---

### Post by Vermind on 2009-08-05
Hi, I have created a script to 
[ automatically add PPAs and their associated pubkeys]("http://ubuntuforums.org/showthread.php?p=7737482#post7737482"). I hope it helps.

---

