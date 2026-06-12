---
title: "how can I delete apache2?"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by Shaked on 2009-04-03
hey all, i'm new around.
amm i had a few problems with my apach2 (a few errors that I didnt know how to deal with) so i decided to remove the apache2 and to install it back .. i tried to do this line to remove it,
```
sudo apt-get remove apache2
```
and to install it back but again same errors, but like I can see its not really remove all the files and the folders, I did the line
```
locate apache2 
```
and I see that all the logs and the folders are still there, and that's the problem that stop my solution ;]
there is any way to delete it like it never was installed ?

thanks very much

---

### Post by Meson on 2009-04-03
To completely remove a package, including it's configuration:
```

sudo apt-get purge <packagename>

```

To now remove all packages that were installed because of <packagename>:
```

sudo apt-get --purge autoremove

```

I'm not sure if log files will be purged.  Configuration files will.

---

### Post by snova on 2009-04-03
--purge is what you need, but the configuration files are not in **apache2**, they are in **apache2.2-common**. There might be a few other packages installed as well, so open Synaptic and mark them all for "Complete Removal" (which is the same thing, I believe).

---

### Post by Meson on 2009-04-03
> **snova said:**
> --purge is what you need, but the configuration files are not in **apache2**, they are in **apache2.2-common**. There might be a few other packages installed as well, so open Synaptic and mark them all for "Complete Removal" (which is the same thing, I believe).

Yeah I think the "complete removal" does a purge.  But it doesn't do an autoremove.

---

### Post by Shaked on 2009-04-04
> **Meson said:**
> Yeah I think the "complete removal" does a purge.  But it doesn't do an autoremove.

amm the folders are still there :o
> shaked@DAN:~$ locate apache2                                               
/etc/apache2                                                                   
/etc/apache2/apache2.conf                                                      
/etc/apache2/apache2.conf~                                                     
/etc/apache2/conf.d                                                            
/etc/apache2/envvars                                                           
/etc/apache2/httpd.conf                                                        
/etc/apache2/mods-available                                                    
/etc/apache2/mods-enabled                                                      
/etc/apache2/ports.conf                                                        
/etc/apache2/sites-available                                                   
/etc/apache2/sites-enabled                                                     
/etc/apache2/conf.d/charset                                                    
/etc/apache2/conf.d/security                                                   
/etc/apache2/mods-available/actions.conf                                       


and I tried you'r comment 
```
 sudo apt-get purge apache2
```

ammm and if I'll delete all these folders by myself it will be no wrong right ? it will not do me any problems if I will look for install it again in the future ?

thanks !

---

