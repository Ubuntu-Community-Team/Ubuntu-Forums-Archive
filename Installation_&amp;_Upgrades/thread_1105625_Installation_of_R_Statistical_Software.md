---
title: "Installation of R Statistical Software"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by PeregrinGo on 2009-03-24
Hi all,

I have tried and tried to install "R" using all of the readmes and tutorials I could, but nothing works because I always end up with the same errors. I thought I should just show you what it all looks like in the terminal to see if that can provide anyone with enough insight to shed some light on the situation. I really want / could use this program, but I just can't seem to get it installed. Please help!

> 
wesley@PeregrinGo:~$ gpg --keyserver subkeys.pgp.net --recv-key E2A11821 
gpg: solicitando clave E2A11821 de hkp servidor subkeys.pgp.net
gpg: clave E2A11821: "Vincent Goulet <vincent.goulet@act.ulaval.ca>" sin cambios
gpg: Cantidad total procesada: 1
gpg:              sin cambios: 1
wesley@PeregrinGo:~$ gpg -a --export E2A11821 | sudo apt-key add -
OK
wesley@PeregrinGo:~$ sudo apt-get update
Des:1 [http://rh-mirror.linux.iastate.edu](http://rh-mirror.linux.iastate.edu) intrepid/ Release.gpg [197B]
Ign [http://rh-mirror.linux.iastate.edu](http://rh-mirror.linux.iastate.edu) intrepid/ Translation-es                
Des:2 [http://rh-mirror.linux.iastate.edu](http://rh-mirror.linux.iastate.edu) intrepid/ Release [1349B]             
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy Release.gpg                         
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy/main Translation-es                 
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Translation-es           
Des:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg [307B]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-es                         
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-es        
Obj [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-es                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-es                
Obj [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-es                  
Ign [http://rh-mirror.linux.iastate.edu](http://rh-mirror.linux.iastate.edu) intrepid/ Packages                      
Obj [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg                          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-es                  
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy/restricted Translation-es           
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy/universe Translation-es             
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy/multiverse Translation-es           
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-updates Release.gpg                 
Ign [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-updates/main Translation-es         
Ign [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-updates/restricted Translation-es   
Ign [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-updates/universe Translation-es     
Ign [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-updates/multiverse Translation-es   
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-backports Release.gpg               
Ign [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-backports/restricted Translation-es 
Obj [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Des:4 [http://rh-mirror.linux.iastate.edu](http://rh-mirror.linux.iastate.edu) intrepid/ Packages [11.3kB]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Translation-es     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Translation-es       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Translation-es     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-es              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-es        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-es          
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release                       
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Des:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg [307B]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-es                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-es                         
Des:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                          
Obj [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Obj [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                              
Ign [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-backports/main Translation-es       
Ign [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-backports/multiverse Translation-es 
Ign [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-backports/universe Translation-es   
Obj [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Packages                 
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Des:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [46.7kB]                          
Des:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Obj [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy Release                             
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-updates Release                     
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-backports Release                   
Obj [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                      
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Packages           
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Packages             
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Packages           
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Sources                  
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Obj [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Obj [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy/main Packages                       
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Sources            
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Sources
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources        
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy/restricted Packages
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy/main Sources
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy/restricted Sources
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy/universe Packages
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy/universe Sources
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages       
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy/multiverse Packages
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy/multiverse Sources
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-updates/main Packages
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-updates/restricted Packages
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-updates/main Sources
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-updates/restricted Sources
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources        
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages       
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages       
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-updates/universe Packages
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-updates/universe Sources
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-updates/multiverse Packages
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-updates/multiverse Sources
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-backports/restricted Packages
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-backports/main Packages
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-backports/multiverse Packages
Obj [http://tezcatl.fciencias.unam.mx](http://tezcatl.fciencias.unam.mx) hardy-backports/universe Packages
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources        
Descargados 13.5kB en 1s (9591B/s)
Leyendo lista de paquetes... Hecho
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 8B9FBE5158B3AFA9
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 60D11217247D1CFF
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas
wesley@PeregrinGo:~$ 


---

### Post by Partyboi2 on 2009-03-25
Open a terminal and add the key by typing
```
gpg --keyserver keyserver.ubuntu.com --recv 8B9FBE5158B3AFA9
gpg --export --armor 8B9FBE5158B3AFA9 | sudo apt-key add -
```
then do the same for the second one
```
gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF
gpg --export --armor 60D11217247D1CFF  | sudo apt-key add -
```

---

### Post by PeregrinGo on 2009-03-25
Thanks so much, this worked like a charm! Now I am installing the JGR interface. Does anyone know if it's possible to open R (via the GUI) with a shortcut instead of the terminal?

---

### Post by Partyboi2 on 2009-03-25
You could try using [[COLOR=Blue]RKWard[/COLOR]]("http://rkward.sourceforge.net/wiki/index.php?title=General_FAQ") as a GUI.

---

### Post by PeregrinGo on 2009-03-25
Thanks, yet again. I'm hoping I can get going with R pretty quickly. The Rkward interface doesn't look too difficult to use, and I already downloaded some user guides. It seems like this is probably closer to SPSS than SAS, is that right? I'm actually pretty new to statistics, but I'm really to happy to have a way to analyze data in Linux!

---

