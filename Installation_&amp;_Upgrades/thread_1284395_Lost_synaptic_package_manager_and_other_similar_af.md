---
title: "Lost synaptic package manager and other similar after automatic update"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by obinan on 2009-10-06
I am very new to Ubuntu and have not used it much but read quiet a lot about it and would like to use it as my main O/S. I have it on dual boot at present with Win98SE. It seemed to be working well on 9.04 but yesterday I accepted an automatic update and now have no software listed in Synaptic Package Manager. The following error message is shown if I try to open it:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

I do not know enough to do anything about it and do not even know how or to whom I should report it.

Can someone offer advice please.

---

### Post by arrange on 2009-10-06
Simply remove the file and run an update, the file will recreate itself.```
sudo mv /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages.old
sudo apt-get update
```

---

### Post by obinan on 2009-10-06
Thank you for your help. So far I have only tested Ubuntu and looked around it. I have no knowledge about inputting the code you suggest into the O/S. Can you help me over that hurdle? Thanks Obinan.

---

### Post by arrange on 2009-10-06
You can do it via GUI. Press Alt+F2 and type ```
gksudo nautilus
```Then navigate to */var/lib/apt/lists* folder and find the **gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages** file there. Rename it as you please. 

Then try Synaptic and see if it works now. But first run **Edit &#8594; Reload Package information** to check if we've managed to overcome the problem.

---

### Post by obinan on 2009-10-06
I did as you suggested. I checked SPM and the same error message came up. I tried alt  F2 route and arrived at root\desktop but discovered the following error message in terminal when I was searching around, not sure what to do:

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

What should I do next please? Obinan.

---

### Post by arrange on 2009-10-06
Have you renamed the file or not? If you ignore the Nautilus error, are you able to use the file browser?

You can also try using ```
gksudo nautilus /var/lib/apt/lists
```(this should open the appropriate folder automatically) instead of

```
gksudo nautilus
```

---

### Post by obinan on 2009-10-07
Thanks for new code suggestion, Arrange. It worked and I was able to find and rename the file you suggested. Should I now take the next step:

Edit &#8594; Reload Package information

I look forward to hearing from you again - last night I lost my DSL so was unable to tell you about this until it returned today.

---

### Post by obinan on 2009-10-07
I checked synaptic and Edit is still greyed out and giving the same error message as far as I remember.

---

### Post by arrange on 2009-10-07
Now you WILL have to go to the command line I guess :)

Please open the [Terminal](https://help.ubuntu.com/community/GnomeTerminal) and [copy](https://help.ubuntu.com/community/UsingTheTerminal#Pasting%20in%20commands) these commands (one by one) into it and hit Enter after each```
ls -al /var/lib/apt/lists
sudo apt-get update
```It will give some output which you should copy back here. It will look like this```
arrange@lean:/etc/rc2.d$ ls -al /var/lib/apt/lists
total 44844
drwxr-xr-x 3 root root     4096 2009-10-06 22:24 .
drwxr-xr-x 6 root root     4096 2009-10-04 21:52 ..
-rw-r--r-- 1 root root     8372 2009-08-05 02:04 archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages
-rw-r--r-- 1 root root     3885 2009-08-05 02:04 archive.canonical.com_ubuntu_dists_jaunty_partner_source_Sources
-rw-r--r-- 1 root root    10490 2009-08-05 02:04 archive.canonical.com_ubuntu_dists_jaunty_Release
-rw-r--r-- 1 root root      189 2009-08-05 02:51 archive.canonical.com_ubuntu_dists_jaunty_Release.gpg
-rw-r--r-- 1 root root  7703897 2009-04-22 23:27 cz.archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages
-rw-r--r-- 1 root root   934978 2009-04-22 23:28 cz.archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root   463463 2009-04-22 23:35 cz.archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_source_Sources
-rw-r--r-- 1 root root    74637 2009-04-22 23:35 cz.archive.ubuntu.com_ubuntu_dists_jaunty_Release
-rw-r--r-- 1 root root      189 2009-04-22 23:35 cz.archive.ubuntu.com_ubuntu_dists_jaunty_Release.gpg
-rw-r--r-- 1 root root    48998 2009-04-22 23:27 cz.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages
-rw-r--r-- 1 root root    11046 2009-04-22 23:33 cz.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_source_Sources
-rw-r--r-- 1 root root 22962013 2009-04-22 23:28 cz.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages
-rw-r--r-- 1 root root 10671074 2009-04-22 23:35 cz.archive.ubuntu.com_ubuntu_dists_jaunty_universe_source_Sources
-rw-r--r-- 1 root root  1197249 2009-10-06 20:19 cz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_main_binary-i386_Packages
-rw-r--r-- 1 root root    35536 2009-10-06 20:19 cz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root     6473 2009-10-06 20:31 cz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_multiverse_source_Sources
-rw-r--r-- 1 root root    57884 2009-10-06 20:31 cz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_Release
-rw-r--r-- 1 root root      189 2009-10-06 20:31 cz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_Release.gpg
-rw-r--r-- 1 root root    12515 2009-10-06 20:19 cz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages
-rw-r--r-- 1 root root     1152 2009-10-06 20:31 cz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_source_Sources
-rw-r--r-- 1 root root   350838 2009-10-06 20:19 cz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_universe_binary-i386_Packages
-rw-r--r-- 1 root root    60227 2009-10-06 20:31 cz.archive.ubuntu.com_ubuntu_dists_jaunty-updates_universe_source_Sources
-rw-r----- 1 root root        0 2009-04-26 20:32 lock
-rw-r--r-- 1 root root     8022 2009-09-27 11:19 packages.medibuntu.org_dists_jaunty_free_binary-i386_Packages
-rw-r--r-- 1 root root    32912 2009-09-27 11:19 packages.medibuntu.org_dists_jaunty_non-free_binary-i386_Packages
-rw-r--r-- 1 root root    11709 2009-09-27 11:19 packages.medibuntu.org_dists_jaunty_Release
-rw-r--r-- 1 root root      197 2009-09-27 11:19 packages.medibuntu.org_dists_jaunty_Release.gpg
drwxr-xr-x 2 root root     4096 2009-10-06 22:24 partial
-rw-r--r-- 1 root root   708270 2009-10-06 19:08 security.ubuntu.com_ubuntu_dists_jaunty-security_main_binary-i386_Packages
-rw-r--r-- 1 root root     3409 2009-10-06 19:08 security.ubuntu.com_ubuntu_dists_jaunty-security_multiverse_binary-i386_Packages
-rw-r--r-- 1 root root      921 2009-10-06 19:10 security.ubuntu.com_ubuntu_dists_jaunty-security_multiverse_source_Sources
-rw-r--r-- 1 root root    57886 2009-10-06 19:10 security.ubuntu.com_ubuntu_dists_jaunty-security_Release
-rw-r--r-- 1 root root      189 2009-10-06 19:10 security.ubuntu.com_ubuntu_dists_jaunty-security_Release.gpg
-rw-r--r-- 1 root root    12515 2009-10-06 19:08 security.ubuntu.com_ubuntu_dists_jaunty-security_restricted_binary-i386_Packages
-rw-r--r-- 1 root root     1152 2009-10-06 19:10 security.ubuntu.com_ubuntu_dists_jaunty-security_restricted_source_Sources
-rw-r--r-- 1 root root   247797 2009-10-06 19:08 security.ubuntu.com_ubuntu_dists_jaunty-security_universe_binary-i386_Packages
-rw-r--r-- 1 root root    25424 2009-10-06 19:10 security.ubuntu.com_ubuntu_dists_jaunty-security_universe_source_Sources

arrange@lean:/etc/rc2.d$ sudo apt-get update
[sudo] password for arrange: 
Get:1 http://security.ubuntu.com jaunty-security Release.gpg [189B]
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Hit http://packages.medibuntu.org jaunty Release.gpg                                                                       
Ign http://packages.medibuntu.org jaunty/free Translation-en_US                                                            
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US                                                        
Hit http://packages.medibuntu.org jaunty Release                                                                           
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US                                                               
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US                                                           
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US                                                         
Get:2 http://security.ubuntu.com jaunty-security Release [57.9kB]                                                                   
Hit http://cz.archive.ubuntu.com jaunty Release.gpg                                           
Ign http://cz.archive.ubuntu.com jaunty/restricted Translation-en_US                          
Hit http://archive.canonical.com jaunty Release.gpg                                           
Ign http://archive.canonical.com jaunty/partner Translation-en_US                             
Ign http://cz.archive.ubuntu.com jaunty/main Translation-en_US                                
Ign http://cz.archive.ubuntu.com jaunty/universe Translation-en_US         
Ign http://cz.archive.ubuntu.com jaunty/multiverse Translation-en_US       
Get:3 http://cz.archive.ubuntu.com jaunty-updates Release.gpg [189B]       
Ign http://cz.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://cz.archive.ubuntu.com jaunty-updates/main Translation-en_US     
Ign http://cz.archive.ubuntu.com jaunty-updates/universe Translation-en_US 
Ign http://cz.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://archive.canonical.com jaunty Release                                                  
Hit http://packages.medibuntu.org jaunty/free Packages                                           
Hit http://cz.archive.ubuntu.com jaunty Release                                                 
Get:4 http://cz.archive.ubuntu.com jaunty-updates Release [57.9kB]                               
Hit http://packages.medibuntu.org jaunty/non-free Packages                  
Hit http://archive.canonical.com jaunty/partner Packages                                                
Hit http://archive.canonical.com jaunty/partner Sources                                            
Hit http://cz.archive.ubuntu.com jaunty/restricted Packages                                        
Hit http://cz.archive.ubuntu.com jaunty/main Packages 
Hit http://cz.archive.ubuntu.com jaunty/restricted Sources
Hit http://cz.archive.ubuntu.com jaunty/universe Packages
Hit http://cz.archive.ubuntu.com jaunty/universe Sources
Hit http://cz.archive.ubuntu.com jaunty/multiverse Packages
Hit http://cz.archive.ubuntu.com jaunty/multiverse Sources
Get:5 http://cz.archive.ubuntu.com jaunty-updates/restricted Packages [2589B]
Get:6 http://cz.archive.ubuntu.com jaunty-updates/main Packages [190kB]
Get:7 http://security.ubuntu.com jaunty-security/restricted Packages [2589B]
Get:8 http://security.ubuntu.com jaunty-security/main Packages [113kB]     
Get:9 http://cz.archive.ubuntu.com jaunty-updates/restricted Sources [623B]
Get:10 http://cz.archive.ubuntu.com jaunty-updates/universe Packages [74.2kB]
Get:11 http://cz.archive.ubuntu.com jaunty-updates/universe Sources [21.0kB]      
Get:12 http://cz.archive.ubuntu.com jaunty-updates/multiverse Packages [8128B]         
Get:13 http://security.ubuntu.com jaunty-security/restricted Sources [623B]            
Get:14 http://security.ubuntu.com jaunty-security/universe Packages [53.1kB]
Get:15 http://cz.archive.ubuntu.com jaunty-updates/multiverse Sources [2505B]    
Get:16 http://security.ubuntu.com jaunty-security/universe Sources [12.4kB]              
Get:17 http://security.ubuntu.com jaunty-security/multiverse Packages [1662B]
Get:18 http://security.ubuntu.com jaunty-security/multiverse Sources [588B]
Fetched 599kB in 2s (250kB/s)                           
Reading package lists... Done
```

---

### Post by obinan on 2009-10-08
Thanks Arrange for the additional help but yesterday evening I managed to get a package manager update and synaptic package manager is now working again. I think that solves my problem so thank you for your help. Should I now mark my thread as solved?

---

### Post by arrange on 2009-10-08
I guess so... :)

---

### Post by sfgiantsfan916 on 2010-10-15
Hey thanks a lot for the nautilus code. That helped me out a lot. I am new to linux distribution as well. The apt-get update couldn't update because the file in /var/lib/etc.. was locked. Appreciate the code.

---

