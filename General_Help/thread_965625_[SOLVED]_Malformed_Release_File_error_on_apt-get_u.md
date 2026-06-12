---
title: "[SOLVED] Malformed Release File error on apt-get update?"
date: 2008-10-31
forum: General Help
---

### Post by JPorter on 2008-10-31
Hi folks, I have a problem.  When attempting to update my package sources, I am getting a strange error.

Here is the output of[FONT="Courier New"] sudo apt-get update[/FONT]:

```
Hit http://security.ubuntu.com intrepid-security Release.gpg                 
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US      
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US 
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US 
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US   
Ign http://security.ubuntu.com intrepid-security/partner Translation-en_US    
Hit http://security.ubuntu.com intrepid-security Release                      
Hit http://security.ubuntu.com intrepid-security/main Packages                
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Packages          
Hit http://security.ubuntu.com intrepid-security/universe Packages            
Get:1 http://us.archive.ubuntu.com intrepid Release.gpg [189B]                
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/partner Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/partner Translation-en_US
Get:2 http://us.archive.ubuntu.com intrepid Release [65.9kB]
Hit http://us.archive.ubuntu.com intrepid-updates Release
Get:3 http://us.archive.ubuntu.com intrepid/main Packages [1256kB]
Get:4 http://us.archive.ubuntu.com intrepid/restricted Packages [8408B]        
Get:5 http://us.archive.ubuntu.com intrepid/multiverse Packages [199kB]        
Get:6 http://us.archive.ubuntu.com intrepid/universe Packages [4542kB]         
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages                
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages          
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages          
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages            
Fetched 6072kB in 2min7s (47.8kB/s)                                            
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Here's my sources.list file:
```
# REPOSITORY SOURCES LIST

# INTREPID
deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted multiverse universe partner
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted multiverse universe partner

# INTREPID-UPDATES
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted multiverse universe partner
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted multiverse universe partner

# INTREPID-BACKPORTS
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

# INTREPID-SECURITY
deb http://security.ubuntu.com/ubuntu/ intrepid-security main restricted multiverse universe partner
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-security main restricted multiverse universe partner

# INTREPID CDROM
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Alpha i386 (20080903.2)]/ intrepid main restricted
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Alpha i386 (20080903.2)]/ intrepid main restricted
```


I've run[FONT="Courier New"] sudo apt-get clean [/FONT]to flush the apt cache, I'm not sure what else to do.  This is on Intrepid, by the way.  I've been running Intrepid for a while, and this behavior seems to have started with the official release yesterday.

Does anyone have any suggestions?


Thanks!

---

### Post by JPorter on 2008-10-31
Nevermind!  I did a stupid thing and somehow I had "partner" on the end of my repo lines when it's supposed to be its own section.

False alarm... no more errors.

Thanks, folks!

---

### Post by age007 on 2009-11-06
I appear to have a similar problem on Jaunty but am a bit of a novice with code.  
My output of[FONT=Courier New] sudo apt-get update[/FONT] is:
```
Hit http://au.archive.ubuntu.com jaunty Release.gpg
Hit http://au.archive.ubuntu.com jaunty/main Translation-en_AU                 
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/main Translation-en_AU          
Hit http://wine.budgetdedicated.com edgy Release.gpg                           
Ign http://wine.budgetdedicated.com edgy/main Translation-en_AU                
Hit http://wine.budgetdedicated.com jaunty Release.gpg                         
Hit http://packages.medibuntu.org jaunty Release.gpg                           
Ign http://packages.medibuntu.org jaunty/free Translation-en_AU                
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_AU    
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_AU      
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_AU    
Hit http://security.ubuntu.com jaunty-security Release                         
Ign http://wine.budgetdedicated.com jaunty/main Translation-en_AU              
Hit http://wine.budgetdedicated.com edgy Release                               
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_AU            
Hit http://packages.medibuntu.org jaunty Release                               
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Hit http://wine.budgetdedicated.com jaunty Release                   
Hit http://packages.medibuntu.org jaunty/free Packages                         
Hit http://security.ubuntu.com jaunty-security/restricted Packages             
Hit http://security.ubuntu.com jaunty-security/main Sources          
Hit http://security.ubuntu.com jaunty-security/restricted Sources    
Hit http://security.ubuntu.com jaunty-security/universe Packages               
Ign http://wine.budgetdedicated.com edgy/main Packages                         
Hit http://packages.medibuntu.org jaunty/non-free Packages                     
Hit http://security.ubuntu.com jaunty-security/universe Sources      
Hit http://security.ubuntu.com jaunty-security/multiverse Packages   
Ign http://wine.budgetdedicated.com jaunty/main Packages             
Hit http://wine.budgetdedicated.com edgy/main Packages
Hit http://wine.budgetdedicated.com jaunty/main Packages
Ign http://au.archive.ubuntu.com jaunty/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com jaunty/universe Translation-en_AU
Ign http://au.archive.ubuntu.com jaunty/multiverse Translation-en_AU
Hit http://au.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://au.archive.ubuntu.com jaunty-updates/main Translation-en_AU
Ign http://au.archive.ubuntu.com jaunty-updates/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com jaunty-updates/universe Translation-en_AU
Ign http://au.archive.ubuntu.com jaunty-updates/multiverse Translation-en_AU
Hit http://au.archive.ubuntu.com jaunty-backports Release.gpg
Ign http://au.archive.ubuntu.com jaunty-backports/main Translation-en_AU
Ign http://au.archive.ubuntu.com jaunty-backports/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com jaunty-backports/universe Translation-en_AU
Ign http://au.archive.ubuntu.com jaunty-backports/multiverse Translation-en_AU
Hit http://au.archive.ubuntu.com jaunty Release            
Hit http://au.archive.ubuntu.com jaunty-updates Release                        
Hit http://au.archive.ubuntu.com jaunty-backports Release                      
Hit http://au.archive.ubuntu.com jaunty/main Packages                          
Hit http://au.archive.ubuntu.com jaunty/restricted Packages
Hit http://au.archive.ubuntu.com jaunty/main Sources       
Hit http://au.archive.ubuntu.com jaunty/restricted Sources 
Hit http://au.archive.ubuntu.com jaunty/universe Packages  
Hit http://au.archive.ubuntu.com jaunty/universe Sources   
Hit http://au.archive.ubuntu.com jaunty/multiverse Packages
Hit http://au.archive.ubuntu.com jaunty/multiverse Sources 
Hit http://au.archive.ubuntu.com jaunty-updates/main Packages
Hit http://au.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://au.archive.ubuntu.com jaunty-updates/main Sources
Hit http://au.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://au.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://au.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://au.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://au.archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://au.archive.ubuntu.com jaunty-backports/main Packages
Hit http://au.archive.ubuntu.com jaunty-backports/restricted Packages
Hit http://au.archive.ubuntu.com jaunty-backports/universe Packages
Hit http://au.archive.ubuntu.com jaunty-backports/multiverse Packages
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release  Unable to find expected entry  multiversedeb/source/Sources in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Don't know the command to find the repo sources.list file or how to remove the 'partner' tag at the end of the repo lines if I find some. 

Just noticed that I must have been downloading the backport packages too. Wonder if that has something to do with it? 

Any other suggestions?

---

### Post by Bad_Andy on 2010-06-01
have a similar error now in 10.04, "malformed release file bla bla bla"

terminal output of sudo apt-get update is thus:

```
Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_US              
Get:2 http://dl.google.com stable Release [2,544B]                             
Hit http://archive.ubuntu.com lucid Release.gpg                                
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US             
Hit http://ppa.launchpad.net lucid Release.gpg                       
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_US
Get:3 http://dl.google.com stable/main Packages [1,082B]             
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US 
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/univers Translation-en_US
Hit http://archive.ubuntu.com lucid-updates Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://ppa.launchpad.net lucid Release     
Hit http://archive.ubuntu.com lucid-security Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://archive.ubuntu.com lucid Release    
Hit http://archive.ubuntu.com lucid-updates Release
Hit http://archive.ubuntu.com lucid-security Release
Hit http://archive.ubuntu.com lucid/main Packages
Hit http://archive.ubuntu.com lucid/restricted Packages
Hit http://archive.ubuntu.com lucid/main Sources
Hit http://archive.ubuntu.com lucid/restricted Sources
Hit http://archive.ubuntu.com lucid/universe Packages
Hit http://archive.ubuntu.com lucid/universe Sources
Hit http://archive.ubuntu.com lucid/multiverse Packages
Hit http://archive.ubuntu.com lucid/multiverse Sources
Hit http://archive.ubuntu.com lucid-updates/main Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Packages
Hit http://archive.ubuntu.com lucid-updates/main Sources
Hit http://archive.ubuntu.com lucid-updates/restricted Sources
Hit http://archive.ubuntu.com lucid-updates/universe Packages
Hit http://archive.ubuntu.com lucid-updates/universe Sources
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://archive.ubuntu.com lucid-security/main Packages
Hit http://archive.ubuntu.com lucid-security/restricted Packages
Hit http://archive.ubuntu.com lucid-security/main Sources
Hit http://archive.ubuntu.com lucid-security/restricted Sources
Hit http://archive.ubuntu.com lucid-security/universe Packages
Hit http://archive.ubuntu.com lucid-security/universe Sources
Hit http://archive.ubuntu.com lucid-security/multiverse Packages
Hit http://archive.ubuntu.com lucid-security/multiverse Sources
Fetched 3,815B in 5s (756B/s)
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid/Release  Unable to find expected entry  univers/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

My update server is set to "main" and apt-get clean also failed to resolve the problem.

---

### Post by ubu-jdc on 2010-06-02
All,

Apologies if this is updating a somewhat older thread, but this was still the first hit I got when investigating a similar problem in Lucid (10.04 LTS).

I am using apt-mirror to create a mirror for some older Karmic Ubuntu servers that are living on an air-gapped network and I kept getting: 

```
'Unable to find expected entry partner/binary-amd64/Packages in Meta-index file (malformed Release file?)'
```

The problem ended up being that I had pretty much used the default set of repositories in my mirror.list (for apt-mirror on my mirroring server) and my sources.list (on the Karmic servers). The trick here was that the sources.list contained a reference to the 'partner' repository, which I hadn't mirrored.

Moral of the story, if you get the error above in a similar situation to mine, check that your sources.list and mirror.list match up and that you're not trying to retrieve something from your mirror that you haven't actually mirrored.

Again, apologies for resurrecting a seemingly old thread, but this still hits #1 on a google search for "apt-get update ubuntu malformed release file?" and it seemed the thread had further un-resolved issues since the original solved case.

Good luck!

---

