---
title: "missing PUBKEY error"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by jimwhitend on 2009-09-20
I added and removed some third party software sources and now Update Manager return this error below. What to do? Thanks.
-JimW

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

---

### Post by drs305 on 2009-09-20
Run the following command, replacing the <key> with the last 8 alphanumeric characters in the error message:
```

gpg --keyserver keyserver.ubuntu.com --recv-keys [COLOR="DarkRed"]<key>[/COLOR] && gpg --export --armor [COLOR="DarkRed"]<key>[/COLOR] | sudo apt-key add - 

```

In your messages, since the keys are the same, you can run this:
```

gpg --keyserver keyserver.ubuntu.com --recv-keys 437D05B5  && gpg --export --armor 437D05B5 | sudo apt-key add - 

```



*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by sisco311 on 2009-09-20
open a terminal and type:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 437D05B5
sudo apt-get update
```

---

### Post by jimwhitend on 2009-09-25
I've got network problems that I don't have a clue how to solve. The above commands yield this:
jim@jim-ubuntu:~$ gpg --keyserver keyserver.ubuntu.com --recv-keys 437D05B5  && gpg --export --armor 437D05B5 | sudo apt-key add -
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
jim@jim-ubuntu:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 437D05B5
[sudo] password for jim: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
jim@jim-ubuntu:~$ 

Can you point me to a method to troubleshoot, or a forum that might be helpful? Thanks.
-JimW

---

### Post by drs305 on 2009-09-25
jimwhitend,

I tried importing the key but it appears the server isn't working. I was able to successfully import it via this one, although it took about a minute to complete.
```
gpg --keyserver subkeys.pgp.net --recv-keys 437D05B5
```

---

### Post by junke1990 on 2009-09-25
had the same problems a few days ago server seems down????

---

### Post by Partyboi2 on 2009-09-25
> **junke1990 said:**
> had the same problems a few days ago server seems down????
Looks like it.

---

### Post by beloved88 on 2009-12-18
ok, so i've had this problem once before on my netbook, and i was able to fix it using the info on this forum.  Now i've installed the same distribution (easy peasy 1.5) on a VM on my desktop, so i can try out some major changes before i commit, and I
m running across the same issues, but this time I've hit all wall, these are some of the errors I get:

on ```
$ sudo aptitude update
```everythings normal until:

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release 

and at the end

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>



and when i run some of the commands given in in this thread, i get weird things

$ sudo apt-key adv --recv-keys --keyserver subkeys.pgp.net 437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver subkeys.pgp.net 437D05B5
gpg: requesting key 437D05B5 from hkp server subkeys.pgp.net
gpg: key 437D05B5: public key "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
[COLOR=Red]gpg: no ultimately trusted keys found[/COLOR]
gpg: Total number processed: 1
gpg:               imported: 1

---

### Post by drs305 on 2009-12-19
beloved88,

I just tried adding the key with the command from post 3. It took about a minute but it was imported successfully.

Try opening synaptic and go to Settings, Repositories, Authentication tab. If you have a 437D0... key delete it and run the command again.

---

### Post by beloved88 on 2009-12-19
ok, it doesn't work, and I got mad and closed the terminal before posting the results, but it was the same.  Did I mention this was a VM clone of my netbook on my desktop?  Could i copy the repositories list and keys from my netbook to the VM?

---

### Post by beloved88 on 2009-12-20
AAAHHH!!!  ok, so it's not that dramatic, i found my sources.list, and such copied the one from my netbook to my VM, and everything seemed ok-ish until i ran apt-get update:

user@Skipper:~/Desktop$ sudo cp sources.list /etc/apt/sources.list
user@Skipper:~/Desktop$ cd
user@Skipper:~$ sudo apt-get udpate
E: Invalid operation udpate
user@Skipper:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                     
Ign [http://archive.geteasypeasy.com](http://archive.geteasypeasy.com) jaunty Release.gpg                         
Ign [http://archive.geteasypeasy.com](http://archive.geteasypeasy.com) jaunty/main Translation-en_US              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                               
Get:3 [http://archive.geteasypeasy.com](http://archive.geteasypeasy.com) jaunty Release [1245B]                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Get:4 [http://dl.google.com](http://dl.google.com) testing Release.gpg [189B]                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US   
Ign [http://dl.google.com](http://dl.google.com) testing/non-free Translation-en_US                    
Hit [http://archive.geteasypeasy.com](http://archive.geteasypeasy.com) jaunty/main Packages                       
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Get:6 [http://dl.google.com](http://dl.google.com) stable Release [2540B]                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                                   
Get:7 [http://dl.google.com](http://dl.google.com) testing Release [2513B]                             
Ign [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Ign [http://dl.google.com](http://dl.google.com) testing Release                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US           
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                       
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources [555kB]                   
Get:11 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [1010B]                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages                  
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Get:12 [http://dl.google.com](http://dl.google.com) stable/main Packages [867B]                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Get:13 [http://dl.google.com](http://dl.google.com) testing/non-free Packages [793B]                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources                   
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources               
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources    
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages [2902B]
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources [1046B]                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages      
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages [490B]
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources [351B]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources [3156B]
Fetched 693kB in 5s (137kB/s)                            
Reading package lists... Done
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://dl.google.com](http://dl.google.com) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 90345E8D2FEF0CE2
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6B15AB91951DC1E2
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


so obviousely their were a few other things i didn't transfer over.  Um, linux question!!!  From what i understand about the file system, aren't there just a few directories i would need to copy over to create a complete clone of my other machine, like sbin, var, etc, opt, and usr? how whould I go about doing that?

---

### Post by beloved88 on 2009-12-20
found out how to open nautilus as root, and i moved a couple directories over, it cleared up all the new problems, but i still got issues with the old problems...

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


Anyone know where the keys are located within the filesystem!? I found key rings, and moved those over, but to no avail, since aren't those just lists of trusted keys, not actual keys themselves?

---

### Post by slakkie on 2009-12-20
Have a look at this post:
[http://ubuntuforums.org/showthread.php?p=8521190#post8521190](http://ubuntuforums.org/showthread.php?p=8521190#post8521190)

---

### Post by buddy007 on 2011-09-16
i tried gpg --keyserver subkeys.pgp.net --recv-keys 7362E5D0
but it is showing
gpg: requesting key 7362E5D0 from hkp server subkeys.pgp.net
gpgkeys: key 7362E5D0 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

---

### Post by oldos2er on 2011-09-16
Closed for necromancy. If you're having a problem please start a new thread and give full details.

---

