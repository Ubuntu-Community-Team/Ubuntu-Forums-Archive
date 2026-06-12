---
title: "Can't install qutim!"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by hello_from_russia! on 2009-03-16
Hello!
Sorry, but I just start to use Linux and may be I do something wrong. I use ubuntu 8.10 but I can't install qutim. I added the url to /etc/apt/sources.list than I updated by "sudo apt-get update" and try to install qutim by "sudo apt-get install qutim". So my terminal displayed me that my package can't be installed because there are some problems with dependences.
qutim depends from  libqt4-core (>= 4.3.4) and libqt4-gui (>= 4.3.4) but they will be not installed... Packages are broken. Please, help me... :(

---

### Post by Partyboi2 on 2009-03-16
What 'url' did you add to your sources.list?

---

### Post by hello_from_russia! on 2009-03-16
> **Partyboi2 said:**
> What 'url' did you add to your sources.list?

I tryed to add these repositories:
deb [http://ppa.launchpad.net/smakc/ubuntu](http://ppa.launchpad.net/smakc/ubuntu) hardy main
deb [http://qutim.org/debian/](http://qutim.org/debian/) unstable main
May be I mistake?

---

### Post by taurus on 2009-03-16
If you are running intrepid, how come you added a repo from hardy?

---

### Post by Partyboi2 on 2009-03-16
Remove those from your sources.list. Then make sure you have "multiverse" enabled in your sources.list.  (System>Admin>Software Sources>1st tab) then either search synaptic for 'qutim' and install or you can install it from the terminal (Applications>Accessories>Terminal)
```
sudo apt-get install qutim
```

---

### Post by hello_from_russia! on 2009-03-16
> **Partyboi2 said:**
> Remove those from your sources.list. Then make sure you have "multiverse" enabled in your sources.list.  (System>Admin>Software Sources>1st tab) then either search synaptic for 'qutim' and install or you can install it from the terminal (Applications>Accessories>Terminal)
```
sudo apt-get install qutim
```

I have "multiverse" enabled in my sources.list. I searched synaptic for 'qutim' and tryed to install but message window appeared, there written that: 
'Could not mark all packages for installation or upgrade
The following packages have unresolvable dependencies.
Make sure that all required repositories are added and enabled in the preferences.
qutim:
 depend: libqt4-core but it is not going to be installed
 depend: libqt4-gui but it is not going to be installed
 &#1056;&#1077;&#1082;&#1086;&#1084;&#1077;&#1085;&#1076;&#1091;&#1077;&#1090;: qutim-emoticons but it is not going to be installed'

---

### Post by taurus on 2009-03-16
Did you remember to run sudo apt-get update first?

```
sudo apt-get update
sudo apt-get install qutim
```

---

### Post by hello_from_russia! on 2009-03-16
> **taurus said:**
> Did you remember to run sudo apt-get update first?

```
sudo apt-get update
sudo apt-get install qutim
```

yes, I always update when I change my sources.list

---

### Post by taurus on 2009-03-16
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by hello_from_russia! on 2009-03-17
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ru.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://ru.archive.ubuntu.com/ubuntu/ intrepid main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb http://ru.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://ru.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ru.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://ru.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://ru.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://ru.archive.ubuntu.com/ubuntu/ intrepid-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ru.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://ru.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://ru.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://ru.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb http://rusxmms.sourceforge.net/ubuntu/rusxmms dapper main
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner
deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://ppa.launchpad.net/tualatrix/ubuntu hardy main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu hardy main
deb http://rusxmms.sourceforge.net/ubuntu/rusxmms dapper main
deb http://wine.budgetdedicated.com/apt intrepid main

deb http://ppa.launchpad.net/qgis/ubuntu hardy main
deb http://ru.archive.ubuntu.com/ubuntu/ intrepid-backports restricted main multiverse universe
deb http://ru.archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe

```

---

### Post by Partyboi2 on 2009-03-17
Try disabling all the non intrepid repos in your sources.list. Open a terminal and
```
gksu gedit /etc/apt/sources.list
```then add a # infront of all the non intrepid repos.
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) intrepid main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) intrepid-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse[COLOR=Red]
#deb [http://rusxmms.sourceforge.net/ubuntu/rusxmms](http://rusxmms.sourceforge.net/ubuntu/rusxmms) dapper main[/COLOR]
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
[COLOR=Red]#deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main
#deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main
#deb [http://rusxmms.sourceforge.net/ubuntu/rusxmms](http://rusxmms.sourceforge.net/ubuntu/rusxmms) dapper main[/COLOR]
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main
[COLOR=Red]#deb [http://ppa.launchpad.net/qgis/ubuntu](http://ppa.launchpad.net/qgis/ubuntu) hardy main[/COLOR]
deb [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) intrepid-backports restricted main multiverse universe
deb [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe
```Then save close gedit, then 
```
sudo apt-get update && sudo apt-get install qutim
```

---

### Post by hello_from_russia! on 2009-03-17
Thanks for your advice, I've done it but situation doesn't change :(

---

### Post by taurus on 2009-03-17
What is the whole output of command?

```
sudo apt-get update
```

---

### Post by hello_from_russia! on 2009-03-17
The whole output is:
```
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid Release.gpg
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid/main Translation-ru               
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid/restricted Translation-ru         
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid/universe Translation-ru           
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid/multiverse Translation-ru         
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-updates Release.gpg               
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-updates/main Translation-ru       
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-updates/restricted Translation-ru 
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.canonical.com intrepid Release.gpg                       
&#1048;&#1075;&#1085; http://archive.canonical.com intrepid/partner Translation-ru               
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-updates/universe Translation-ru   
&#1048;&#1075;&#1085; http://ppa.launchpad.net hardy Release.gpg                                 
&#1048;&#1075;&#1085; http://ppa.launchpad.net hardy/main Translation-ru                         
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-updates/multiverse Translation-ru 
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-backports Release.gpg             
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com intrepid-backports/restricted Translation-ru  
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com intrepid-backports/main Translation-ru        
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com intrepid-backports/multiverse Translation-ru  
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com intrepid-backports/universe Translation-ru    
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.canonical.com intrepid Release                           
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-proposed Release.gpg              
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-proposed/restricted Translation-ru
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:1 http://ppa.launchpad.net hardy Release [27,6kB]                     
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-proposed/main Translation-ru      
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-proposed/multiverse Translation-ru
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-proposed/universe Translation-ru  
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid Release                           
&#1048;&#1075;&#1085; http://ppa.launchpad.net hardy/main Packages                               
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.canonical.com intrepid/partner Packages                  
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-updates Release                   
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-backports Release                 
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-proposed Release                  
&#1042; &#1082;&#1077;&#1096;&#1077; http://ppa.launchpad.net hardy/main Packages                            
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid/main Packages                     
&#1042; &#1082;&#1077;&#1096;&#1077; http://archive.canonical.com intrepid/partner Sources                   
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid/restricted Packages               
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid/main Sources                      
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid/restricted Sources                
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid/universe Packages                 
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid/universe Sources                  
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid/multiverse Packages               
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid/multiverse Sources                
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-updates/main Packages             
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-updates/restricted Packages       
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-updates/main Sources              
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-updates/restricted Sources        
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-updates/universe Packages         
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-updates/universe Sources          
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-updates/multiverse Packages       
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-updates/multiverse Sources        
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-backports/restricted Packages     
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-backports/main Packages           
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-backports/multiverse Packages     
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-backports/universe Packages       
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-proposed/restricted Packages      
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-proposed/main Packages            
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-proposed/multiverse Packages      
&#1042; &#1082;&#1077;&#1096;&#1077; http://ru.archive.ubuntu.com intrepid-proposed/universe Packages        
&#1042; &#1082;&#1077;&#1096;&#1077; http://security.ubuntu.com intrepid-security Release.gpg                
&#1048;&#1075;&#1085; http://security.ubuntu.com intrepid-security/main Translation-ru           
&#1048;&#1075;&#1085; http://security.ubuntu.com intrepid-security/restricted Translation-ru     
&#1048;&#1075;&#1085; http://security.ubuntu.com intrepid-security/universe Translation-ru       
&#1048;&#1075;&#1085; http://security.ubuntu.com intrepid-security/multiverse Translation-ru     
&#1042; &#1082;&#1077;&#1096;&#1077; http://security.ubuntu.com intrepid-security Release                    
&#1042; &#1082;&#1077;&#1096;&#1077; http://security.ubuntu.com intrepid-security/main Packages              
&#1042; &#1082;&#1077;&#1096;&#1077; http://security.ubuntu.com intrepid-security/restricted Packages
&#1042; &#1082;&#1077;&#1096;&#1077; http://security.ubuntu.com intrepid-security/main Sources               
&#1042; &#1082;&#1077;&#1096;&#1077; http://wine.budgetdedicated.com intrepid Release.gpg                    
&#1048;&#1075;&#1085; http://wine.budgetdedicated.com intrepid/main Translation-ru               
&#1042; &#1082;&#1077;&#1096;&#1077; http://wine.budgetdedicated.com intrepid Release                        
&#1048;&#1075;&#1085; http://wine.budgetdedicated.com intrepid/main Packages     
&#1042; &#1082;&#1077;&#1096;&#1077; http://wine.budgetdedicated.com intrepid/main Packages
&#1042; &#1082;&#1077;&#1096;&#1077; http://security.ubuntu.com intrepid-security/restricted Sources         
&#1042; &#1082;&#1077;&#1096;&#1077; http://security.ubuntu.com intrepid-security/universe Packages
&#1042; &#1082;&#1077;&#1096;&#1077; http://security.ubuntu.com intrepid-security/universe Sources
&#1042; &#1082;&#1077;&#1096;&#1077; http://security.ubuntu.com intrepid-security/multiverse Packages
&#1042; &#1082;&#1077;&#1096;&#1077; http://security.ubuntu.com intrepid-security/multiverse Sources
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086; 1&#1041; &#1079;&#1072; 15s (0&#1041;/c)                  
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;

```

---

