---
title: "Canon Pixma ip1700 driver for Ubuntu 11.04(64 bit)"
date: 2012-04-10
forum: Hardware
---

### Post by nipunshakya on 2012-04-10
Hello guys and gurus. I have been spending whole day googling and searching driver for my printer canon pixma ip1700 for ubuntu but unfortunately, none has worked. 
[https://wiki.ubuntu.com/HardwareSupportComponentsPrintersCanon](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersCanon)
Was the link i used...and other ones were similar to the step suggested. Im totally out of clues now to make my printer work. I know this issue has been out there, but it seems like nothing is going to work out for this machine... Any help would be appreciated. :(

I ran the following:
```

winuxuser@MagicBox:~$ sudo gedit /etc/apt/sources.list
[sudo] password for winuxuser: 

(gedit:21248): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.97HSCW': No such file or directory

(gedit:21248): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
                                                       
(gedit:21248): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.K9TECW': No such file or directory

(gedit:21248): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:21248): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.HKHRCW': No such file or directory

(gedit:21248): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
winuxuser@MagicBox:~$ sudo apt-get uodate
E: Invalid operation uodate
winuxuser@MagicBox:~$ sudo apt-get update
Ign http://extras.ubuntu.com natty InRelease
Ign http://mambo.kuhp.kyoto-u.ac.jp ./ InRelease                               
Hit http://extras.ubuntu.com natty Release.gpg                                 
Ign http://mambo.kuhp.kyoto-u.ac.jp ./ Release.gpg                             
Hit http://extras.ubuntu.com natty Release                                     
Ign http://mambo.kuhp.kyoto-u.ac.jp ./ Release                                 
Hit http://extras.ubuntu.com natty/main Sources                                
Ign http://mambo.kuhp.kyoto-u.ac.jp ./ Packages/DiffIndex                      
Hit http://extras.ubuntu.com natty/main amd64 Packages               
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Ign http://archive.ubuntu.com natty InRelease                                  
Ign http://archive.ubuntu.com natty-updates InRelease                
Ign http://archive.ubuntu.com natty-backports InRelease              
Ign http://archive.canonical.com natty InRelease                     
Ign http://archive.ubuntu.com natty-security InRelease                         
Ign http://archive.ubuntu.com natty-proposed InRelease                         
Get:1 http://archive.ubuntu.com natty Release.gpg [198 B]                      
Hit http://archive.canonical.com natty Release.gpg                             
Get:2 http://archive.ubuntu.com natty-updates Release.gpg [198 B]              
Get:3 http://archive.ubuntu.com natty-backports Release.gpg [198 B]            
Get:4 http://archive.ubuntu.com natty-security Release.gpg [198 B]             
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Hit http://archive.canonical.com natty Release                                 
Ign http://extras.ubuntu.com natty/main Translation-en                         
Get:5 http://archive.ubuntu.com natty-proposed Release.gpg [198 B]   
Hit http://mambo.kuhp.kyoto-u.ac.jp ./ Packages                                
Hit http://archive.canonical.com natty/partner amd64 Packages        
Ign http://mambo.kuhp.kyoto-u.ac.jp ./ Translation-en_US             
Ign http://mambo.kuhp.kyoto-u.ac.jp ./ Translation-en
Get:6 http://archive.ubuntu.com natty Release [39.8 kB]
Ign http://archive.canonical.com natty/partner TranslationIndex
Get:7 http://archive.ubuntu.com natty-updates Release [39.8 kB]                
Get:8 http://archive.ubuntu.com natty-backports Release [39.8 kB]              
Get:9 http://archive.ubuntu.com natty-security Release [39.8 kB]               
Get:10 http://archive.ubuntu.com natty-proposed Release [39.8 kB]              
Ign http://archive.canonical.com natty/partner Translation-en_US               
Get:11 http://archive.ubuntu.com natty/main Sources [862 kB]                   
Ign http://archive.canonical.com natty/partner Translation-en                  
Get:12 http://archive.ubuntu.com natty/restricted Sources [4,104 B]            
Get:13 http://archive.ubuntu.com natty/universe Sources [4,380 kB]             
Get:14 http://archive.ubuntu.com natty/multiverse Sources [155 kB]             
Get:15 http://archive.ubuntu.com natty/main amd64 Packages [1,550 kB]          
Get:16 http://archive.ubuntu.com natty/restricted amd64 Packages [9,001 B]     
Get:17 http://archive.ubuntu.com natty/universe amd64 Packages [6,004 kB]      
Get:18 http://archive.ubuntu.com natty/multiverse amd64 Packages [181 kB]      
Ign http://archive.ubuntu.com natty/main TranslationIndex                      
Ign http://archive.ubuntu.com natty/multiverse TranslationIndex                
Ign http://archive.ubuntu.com natty/restricted TranslationIndex                
Ign http://archive.ubuntu.com natty/universe TranslationIndex                  
Get:19 http://archive.ubuntu.com natty-updates/main Sources [157 kB]           
Get:20 http://archive.ubuntu.com natty-updates/restricted Sources [753 B]      
Get:21 http://archive.ubuntu.com natty-updates/universe Sources [42.6 kB]      
Get:22 http://archive.ubuntu.com natty-updates/multiverse Sources [3,116 B]    
Get:23 http://archive.ubuntu.com natty-updates/main amd64 Packages [440 kB]    
Get:24 http://archive.ubuntu.com natty-updates/restricted amd64 Packages [838 B]
Get:25 http://archive.ubuntu.com natty-updates/universe amd64 Packages [140 kB]
Get:26 http://archive.ubuntu.com natty-updates/multiverse amd64 Packages [6,350 B]
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex              
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex        
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex        
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex          
Get:27 http://archive.ubuntu.com natty-backports/main amd64 Packages [5,742 B] 
Get:28 http://archive.ubuntu.com natty-backports/restricted amd64 Packages [14 B]
Get:29 http://archive.ubuntu.com natty-backports/universe amd64 Packages [25.3 kB]
Get:30 http://archive.ubuntu.com natty-backports/multiverse amd64 Packages [1,473 B]
Ign http://archive.ubuntu.com natty-backports/main TranslationIndex            
Ign http://archive.ubuntu.com natty-backports/multiverse TranslationIndex      
Ign http://archive.ubuntu.com natty-backports/restricted TranslationIndex      
Ign http://archive.ubuntu.com natty-backports/universe TranslationIndex        
Get:31 http://archive.ubuntu.com natty-security/main Sources [93.8 kB]         
Get:32 http://archive.ubuntu.com natty-security/restricted Sources [14 B]      
Get:33 http://archive.ubuntu.com natty-security/universe Sources [22.6 kB]     
Get:34 http://archive.ubuntu.com natty-security/multiverse Sources [1,640 B]   
Get:35 http://archive.ubuntu.com natty-security/main amd64 Packages [284 kB]   
Get:36 http://archive.ubuntu.com natty-security/restricted amd64 Packages [14 B]
Get:37 http://archive.ubuntu.com natty-security/universe amd64 Packages [78.1 kB]
Get:38 http://archive.ubuntu.com natty-security/multiverse amd64 Packages [3,546 B]
Ign http://archive.ubuntu.com natty-security/main TranslationIndex             
Ign http://archive.ubuntu.com natty-security/multiverse TranslationIndex       
Ign http://archive.ubuntu.com natty-security/restricted TranslationIndex       
Ign http://archive.ubuntu.com natty-security/universe TranslationIndex         
Get:39 http://archive.ubuntu.com natty-proposed/restricted amd64 Packages [2,476 B]
Get:40 http://archive.ubuntu.com natty-proposed/main amd64 Packages [116 kB]   
Get:41 http://archive.ubuntu.com natty-proposed/multiverse amd64 Packages [1,300 B]
Get:42 http://archive.ubuntu.com natty-proposed/universe amd64 Packages [28.4 kB]
Ign http://archive.ubuntu.com natty-proposed/main TranslationIndex             
Ign http://archive.ubuntu.com natty-proposed/multiverse TranslationIndex       
Ign http://archive.ubuntu.com natty-proposed/restricted TranslationIndex       
Ign http://archive.ubuntu.com natty-proposed/universe TranslationIndex         
Ign http://archive.ubuntu.com natty/main Translation-en_US                     
Ign http://archive.ubuntu.com natty/main Translation-en
Ign http://archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty/multiverse Translation-en
Ign http://archive.ubuntu.com natty/restricted Translation-en_US
Ign http://archive.ubuntu.com natty/restricted Translation-en
Ign http://archive.ubuntu.com natty/universe Translation-en_US
Ign http://archive.ubuntu.com natty/universe Translation-en
Ign http://archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://archive.ubuntu.com natty-updates/main Translation-en
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com natty-updates/universe Translation-en
Ign http://archive.ubuntu.com natty-backports/main Translation-en_US
Ign http://archive.ubuntu.com natty-backports/main Translation-en
Ign http://archive.ubuntu.com natty-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-backports/multiverse Translation-en
Ign http://archive.ubuntu.com natty-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-backports/restricted Translation-en
Ign http://archive.ubuntu.com natty-backports/universe Translation-en_US
Ign http://archive.ubuntu.com natty-backports/universe Translation-en
Ign http://archive.ubuntu.com natty-security/main Translation-en_US
Ign http://archive.ubuntu.com natty-security/main Translation-en
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en
Ign http://archive.ubuntu.com natty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-security/restricted Translation-en
Ign http://archive.ubuntu.com natty-security/universe Translation-en_US
Ign http://archive.ubuntu.com natty-security/universe Translation-en
Ign http://archive.ubuntu.com natty-proposed/main Translation-en_US
Ign http://archive.ubuntu.com natty-proposed/main Translation-en
Ign http://archive.ubuntu.com natty-proposed/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-proposed/multiverse Translation-en
Ign http://archive.ubuntu.com natty-proposed/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-proposed/restricted Translation-en
Ign http://archive.ubuntu.com natty-proposed/universe Translation-en_US
Ign http://archive.ubuntu.com natty-proposed/universe Translation-en
Fetched 14.8 MB in 12min 42s (19.4 kB/s)
Reading package lists... Done
winuxuser@MagicBox:~$ sudo apt-get install libcnbj-2.6 bjfilter-2.6 pstocanonbj
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libcnbj-2.6
E: Couldn't find any package by regex 'libcnbj-2.6'
E: Unable to locate package bjfilter-2.6
E: Couldn't find any package by regex 'bjfilter-2.6'
E: Unable to locate package pstocanonbj
winuxuser@MagicBox:~$ 


```Regards,WinuxUser

---

