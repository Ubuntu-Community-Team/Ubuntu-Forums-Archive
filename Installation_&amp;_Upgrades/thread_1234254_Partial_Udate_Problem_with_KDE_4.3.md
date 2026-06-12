---
title: "Partial Udate Problem with KDE 4.3"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by WTaylor on 2009-08-07
Hello all I am new to this Forum and Linux. I tried to install the Beta release of KDE 4.3. It was few days before a production version of 4.3 was released. The long story short is that I now can only do a Partial Update when I run update manager. I had a problem with the public key for KDE. To try to resolve I did the following:

**sudo apt-get update**
                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US           
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                          
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                      
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                         
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                          
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Fetched 616B in 1s (492B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key 
is not available: NO_PUBKEY 2836CB0A8AC93F7A
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key
 is not available: NO_PUBKEY 2836CB0A8AC93F7A
W: You may want to run apt-get update to correct these problems

**gpg --keyserver subkeys.pgp.net --recv 2836CB0A8AC93F7A**

gpg: requesting key 8AC93F7A from hkp server subkeys.pgp.net                    
gpg: key 8AC93F7A: public key "Launchpad Kubuntu Updates" imported              
gpg: no ultimately trusted keys found                                           
gpg: Total number processed: 1                                                  
gpg:               imported: 1  (RSA: 1)  

**gpg --export --armor 2836CB0A8AC93F7A | sudo apt-key add -**

OK   
[B]
sudo apt-get update[/B]

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US           
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                          
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Fetched 616B in 1s (552B/s)
Reading package lists... Done

[B]I run an the "Update Manager" and I still get a partial update response window with the following that can not be updated:
[/B]
akonadi-server
akregator
amarok
amarok-common
ark
dolphin
dragonplayer
gwenview
kaddressbook
kamera
kate
kde-printer-applet
kde-window-manager
kde-zeroconf
kdebase-bin
kdebase-data
kdebase-plasma
kdebase-runtime
kdebase-runtime-bin-kde4
kdebase-runtime-data
kdebase-workspace-bin
kdebase-workspace-data
kdebase-workspace-kgreet-plugins
kdebase-workspace-wallpapers
kdegraphics-strigi-plugins
kdemultimedia-kio-plugins
kdepasswd
kdepim-groupware
kdepim-kresources
kdepim-runtime
kdepim-runtime-data
kdepim-runtime-libs4
kdepim-strigi-plugins
kdepim-wizards
kdepimlibs5
kdeplasma-addons
kdewallpapers
kdm
kfind
khelpcenter4
klipper
kmag
kmail
kmix
kmousetool
knotes
kolf
konqueror
konqueror-nsplugins
konsole
kontact
kopete
korganizer
krdc
krfb
kshisen
ksnapshot
ksysguard
ksystemlog
ktimetracker
kuser
kwalletmanager
libkabcommon4
libkcddb4
libkdcraw7
libkdegames5
libkdepim4
libkleo4
libknotificationitem1
libkonq5
libkonqsidebarplugin4
libkontactinterfaces4
libkopete4
libkorundum4-ruby1.8
libkpgp4
libksieve4
liblancelot0
libmarble4
libmimelib4
libpolkit-qt0
libqt4-ruby1.8
libqt4-scripttools
libqtscriptbindings1
libsmokekde4-2
libsmokeqt4-2
marble-data
okular
okular-extra-backends
plasma-dataengines-addons
plasma-dataengines-workspace
plasma-runners-addons
plasma-scriptengine-javascript
plasma-scriptengine-python
plasma-scriptengine-qedje
plasma-scriptengine-ruby
plasma-scriptengine-webkit
plasma-scriptengines
plasma-wallpapers-addons
plasma-widget-folderview
plasma-widget-lancelot
plasma-widget-network-manager
plasma-widget-networkmanagement
plasma-widgets-addons
plasma-widgets-workspace
printer-applet
python-kde4
python-qt4
python-sip4
systemsettings

:confused: Not sure what to do now. I can not run KDE I have to run GNome.

---

### Post by lykwydchykyn on 2009-08-07
Assuming this is Kpackagekit's update manager, try updating at the console or using the GNOME one.  Kpackagekit is silly about not updating stuff.

Paste the output from: 
```

sudo apt-get upgrade

```

---

### Post by WTaylor on 2009-08-07
Thanks for your response. I do not use  Kpackagekit 

 Well, I guess I should have waited a bit before I posted this problem. Five minutes later I did an update manager and it wanted to do a new distribution. So I did select the install of the new distribution. KDE was then updated to the current version 4.3.0 and all is well and running as designed.

Maybe this thread will help others with same type of problem problem.

Thanks in advance  :biggrin:

---

### Post by Soley on 2009-08-07
I followed the directions here:

[http://webupd8.blogspot.com/2009/08/install-kde-43-in-ubuntu-jaunty-904.html]("http://webupd8.blogspot.com/2009/08/install-kde-43-in-ubuntu-jaunty-904.html")

Then I got an error with libindi0_0.6-0ubuntu1.deb not being able to install. I found a fix for it at:

[http://kubuntuforums.net/forums/index.php?topic=3105561.msg191220#msg191220]("http://kubuntuforums.net/forums/index.php?topic=3105561.msg191220#msg191220")

Oh, I see you got it up & running. Cheers!

---

