---
title: "[SOLVED] SunJava 6 plugin crash"
date: 2008-11-26
forum: General Help
---

### Post by uldo on 2008-11-26
I'm using Ubuntu Intrepid 8.10 32bit. The problem is that in firefox while trying to open pages with java applet it just freezes (goes gray), processor usage goes from 40%-60%. I tried to wait some time, while waiting i falled asleep :D . When I woke up (after 4-6h) it was still there. This is not for all pages, just few. Any ideas?

---

### Post by taurus on 2008-11-26
Are you sure it's java plugin, not flash?

---

### Post by uldo on 2008-11-26
Yes, becouse in windows it show SunJava loading screen ( for two of the i'm shore).

---

### Post by taurus on 2008-11-26
How did you install that java plugin?  I assume it is on the list when you type this in the address field.

```
about:plugins
```

---

### Post by uldo on 2008-11-26
I installed it via Synaptic Package Manager. Java(TM) Plug-in 1.6.0_10-b33 and in that list all are "Enabled"... if that is what you wanted to know?! Also when I try to enter Applications --> System Tools --> Sun Java 6 Console --> any of the local processes it says that connection fauiled... is that ok?

---

### Post by taurus on 2008-11-26
What happens if you run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-plugin
```

---

### Post by uldo on 2008-11-26
Everything goes just fine.
Doesnt fix the problem.
```
apt-get update
Hit http://archive.canonical.com intrepid Release.gpg
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://archive.canonical.com intrepid/partner Translation-en_US            
Hit http://archive.ubuntu.com intrepid Release.gpg                             
Ign http://archive.ubuntu.com intrepid/main Translation-en_US                  
Hit http://packages.medibuntu.org intrepid Release.gpg                         
Ign http://archive.ubuntu.com intrepid/restricted Translation-en_US            
Ign http://archive.ubuntu.com intrepid/universe Translation-en_US              
Ign http://archive.ubuntu.com intrepid/multiverse Translation-en_US            
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Hit http://archive.canonical.com intrepid Release                              
Hit http://archive.ubuntu.com intrepid-updates Release.gpg                     
Ign http://archive.ubuntu.com intrepid-updates/main Translation-en_US          
Ign http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US    
Ign http://archive.ubuntu.com intrepid-updates/universe Translation-en_US      
Ign http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_US    
Hit http://archive.ubuntu.com intrepid-security Release.gpg                    
Ign http://archive.ubuntu.com intrepid-security/main Translation-en_US         
Ign http://archive.ubuntu.com intrepid-security/restricted Translation-en_US   
Get:1 http://ppa.launchpad.net intrepid Release [27.6kB]                       
Hit http://archive.canonical.com intrepid/partner Packages                     
Ign http://packages.medibuntu.org intrepid/free Translation-en_US    
Ign http://archive.ubuntu.com intrepid-security/universe Translation-en_US     
Ign http://archive.ubuntu.com intrepid-security/multiverse Translation-en_US   
Hit http://archive.ubuntu.com intrepid Release                                 
Ign http://ppa.launchpad.net intrepid/main Packages                            
Hit http://archive.ubuntu.com intrepid-updates Release                         
Hit http://archive.ubuntu.com intrepid-security Release                        
Ign http://ppa.launchpad.net intrepid/main Sources                  
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US          
Hit http://archive.ubuntu.com intrepid/main Packages                 
Hit http://archive.ubuntu.com intrepid/restricted Packages                     
Hit http://archive.ubuntu.com intrepid/main Sources                            
Hit http://archive.ubuntu.com intrepid/restricted Sources                      
Hit http://archive.ubuntu.com intrepid/universe Packages                       
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://archive.ubuntu.com intrepid/universe Sources                        
Hit http://archive.ubuntu.com intrepid/multiverse Packages                     
Hit http://archive.ubuntu.com intrepid/multiverse Sources
Hit http://archive.ubuntu.com intrepid-updates/main Packages
Hit http://archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://archive.ubuntu.com intrepid-updates/main Sources
Hit http://archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://archive.ubuntu.com intrepid-updates/universe Packages
Hit http://ppa.launchpad.net intrepid/main Sources
Hit http://packages.medibuntu.org intrepid Release
Hit http://archive.ubuntu.com intrepid-updates/universe Sources
Hit http://archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://archive.ubuntu.com intrepid-security/main Packages
Hit http://archive.ubuntu.com intrepid-security/restricted Packages
Hit http://archive.ubuntu.com intrepid-security/main Sources
Hit http://archive.ubuntu.com intrepid-security/restricted Sources
Hit http://archive.ubuntu.com intrepid-security/universe Packages
Hit http://archive.ubuntu.com intrepid-security/universe Sources
Hit http://archive.ubuntu.com intrepid-security/multiverse Packages
Hit http://archive.ubuntu.com intrepid-security/multiverse Sources
Hit http://packages.medibuntu.org intrepid/free Packages
Hit http://packages.medibuntu.org intrepid/non-free Packages
Fetched 1B in 0s (1B/s)
Reading package lists... Done


apt-get install sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 libclucene0ldbl libqt4-opengl ttf-wqy-zenhei librdf0
  kdebase-runtime-data-common ttf-kannada-fonts libevent1 kde-icons-oxygen
  tsocks librasqal0 socat libsoprano4 redland-utils kdelibs5-data
  ttf-telugu-fonts tzdata-java ttf-oriya-fonts libpq5 libraptor1
  ttf-bengali-fonts soprano-daemon kdebase-runtime-data raptor-utils
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

---

### Post by taurus on 2008-11-26
What webpage you are trying to access/view?

---

### Post by uldo on 2008-11-26
the BIG problem is that it doesnt open "What you see is what you get" editor .....  If i dont fix this problem i will have to sit in windows :( ....

p.s. it is mostly used in forums...

---

### Post by uldo on 2008-11-27
anyone?

---

### Post by uldo on 2008-11-27
Just found something interesting at firefox error console! It says:
"Error in parsing value for property 'text-decoration'. Declaration droped."
There are 5 such entries. when I open the link above one of them it opens source with marked line "text-decoration: bold;". this line is marked for all of them!

PLS somebody help..... I need to get this thing working...

---

### Post by Rangi01 on 2008-12-02
How did you solve it.  Please post so that others with the same problem can fix.
Thanks

---

