---
title: "Can't start systemsettings from kubuntu 9.04"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by mirons on 2009-04-28
That's it other kde apps working fine, just can't start the setting manager of kde. Here's what shell says:

```
[10:42:26  andrea ~ ]$ systemsettings 
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"
systemsettings(24812) MainWindow::readMenu: "" Looking for children in ' "" '                          
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"
systemsettings(24812) MainWindow::readMenu: "  " Looking for children in ' "advanced" '                
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"
systemsettings(24812) MainWindow::readMenu: "    " Looking for children in ' "advanced-user-settings" '
systemsettings(24812) MainWindow::readMenu: "    " found module ' "Avvio automatico" '  "autostart.desktop"
systemsettings(24812) MainWindow::readMenu: "    " filename is  "autostart.desktop"                        
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"    
systemsettings(24812) MainWindow::readMenu: "    " found module ' "CD Audio" '  "audiocd.desktop"          
systemsettings(24812) MainWindow::readMenu: "    " filename is  "audiocd.desktop"                          
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"    
systemsettings(24812) MainWindow::readMenu: "    " found module ' "Gestione della sessione" '  "kcmsmserver.desktop"
systemsettings(24812) MainWindow::readMenu: "    " filename is  "kcmsmserver.desktop"                               
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"             
systemsettings(24812) MainWindow::readMenu: "    " found module ' "Macchina fotografica digitale" '  "kamera.desktop"
systemsettings(24812) MainWindow::readMenu: "    " filename is  "kamera.desktop"                                     
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"              
systemsettings(24812) MainWindow::readMenu: "    " found module ' "Portafogli di KDE" '  "kwalletconfig.desktop"     
systemsettings(24812) MainWindow::readMenu: "    " filename is  "kwalletconfig.desktop"                              
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"              
systemsettings(24812) MainWindow::readMenu: "    " found module ' "Recupero CDDB" '  "libkcddb.desktop"              
systemsettings(24812) MainWindow::readMenu: "    " filename is  "libkcddb.desktop"                                   
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"              
systemsettings(24812) MainWindow::readMenu: "    " found module ' "Service Manager" '  "kcmkded.desktop"             
systemsettings(24812) MainWindow::readMenu: "    " filename is  "kcmkded.desktop"                                    
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"              
systemsettings(24812) MainWindow::readMenu: "    " found module ' "Associazioni file" '  "filetypes.desktop"         
systemsettings(24812) MainWindow::readMenu: "    " filename is  "filetypes.desktop"                                  
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"              
systemsettings(24812) MainWindow::readMenu: "    " found module ' "Hardware" '  "kcm_solid.desktop"                  
systemsettings(24812) MainWindow::readMenu: "    " filename is  "kcm_solid.desktop"                                  
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"              
systemsettings(24812) MainWindow::readMenu: "    " found module ' "Desktop Search" '  "kcm_nepomuk.desktop"          
systemsettings(24812) MainWindow::readMenu: "    " filename is  "kcm_nepomuk.desktop"                                
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"              
systemsettings(24812) MainWindow::readMenu: "    " found module ' "Dettagli del tema desktop" '  "desktopthemedetails.desktop"
systemsettings(24812) MainWindow::readMenu: "    " filename is  "desktopthemedetails.desktop"                                 
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                       
systemsettings(24812) MainWindow::readMenu: "    " found module ' "Risorse di KDE" '  "kresources.desktop"                    
systemsettings(24812) MainWindow::readMenu: "    " filename is  "kresources.desktop"                                          
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                       
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                       
systemsettings(24812) MainWindow::readMenu: "    " Looking for children in ' "system" '                                       
systemsettings(24812) MainWindow::readMenu: "    " found module ' "GRUB Editor" '  "kgrubeditor.desktop"                      
systemsettings(24812) MainWindow::readMenu: "    " filename is  "kgrubeditor.desktop"                                         
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                       
systemsettings(24812) MainWindow::readMenu: "    " found module ' "Gestione degli accessi" '  "kdm.desktop"                   
systemsettings(24812) MainWindow::readMenu: "    " filename is  "kdm.desktop"                                                 
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                       
systemsettings(24812) MainWindow::readMenu: "    " found module ' "Pianificatore di operazioni" '  "kcm_cron.desktop"         
systemsettings(24812) MainWindow::readMenu: "    " filename is  "kcm_cron.desktop"                                            
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                       
systemsettings(24812) MainWindow::readMenu: "    " found module ' "Gestione energetica" '  "powerdevilconfig.desktop"         
systemsettings(24812) MainWindow::readMenu: "    " filename is  "powerdevilconfig.desktop"                                    
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                       
systemsettings(24812) MainWindow::readMenu: "    " found module ' "Samba" '  "kcmsambaconf.desktop"                           
systemsettings(24812) MainWindow::readMenu: "    " filename is  "kcmsambaconf.desktop"                                        
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                       
systemsettings(24812) MainWindow::readMenu: "    " found module ' "Printer Configuration" '  "/usr/share/applications/kde4/kcm-scpk.desktop"                                                                                                                  
systemsettings(24812) MainWindow::readMenu: "    " filename is  "/usr/share/applications/kde4/kcm-scpk.desktop"                
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "  " Looking for children in ' "general" '                                         
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "    " Looking for children in ' "computer-administration" '                       
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " Looking for children in ' "keyboard-and-mouse" '                          
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Tastiera" '  "keyboard.desktop"                           
systemsettings(24812) MainWindow::readMenu: "      " filename is  "keyboard.desktop"                                           
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Scorciatoie globali della tastiera" '  "keys.desktop"     
systemsettings(24812) MainWindow::readMenu: "      " filename is  "keys.desktop"                                               
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Joystick" '  "joystick.desktop"                           
systemsettings(24812) MainWindow::readMenu: "      " filename is  "joystick.desktop"                                           
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Scorciatoie standard della tastiera" '  "standard_actions.desktop"                                                                                                                       
systemsettings(24812) MainWindow::readMenu: "      " filename is  "standard_actions.desktop"                                   
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Mouse" '  "mouse.desktop"                                 
systemsettings(24812) MainWindow::readMenu: "      " filename is  "mouse.desktop"                                              
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " Looking for children in ' "add-and-remove-software" '                     
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Software Updates" '  "kpk_update.desktop"                 
systemsettings(24812) MainWindow::readMenu: "      " filename is  "kpk_update.desktop"                                         
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Software Management" '  "kpk_addrm.desktop"               
systemsettings(24812) MainWindow::readMenu: "      " filename is  "kpk_addrm.desktop"                                          
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Settings" '  "kpk_settings.desktop"                       
systemsettings(24812) MainWindow::readMenu: "      " filename is  "kpk_settings.desktop"                                       
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " Looking for children in ' "input-actions" '                               
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Azioni di immissione" '  "khotkeys.desktop"               
systemsettings(24812) MainWindow::readMenu: "      " filename is  "khotkeys.desktop"                                           
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " Looking for children in ' "display" '                                     
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Controllo energia" '  "energy.desktop"                    
systemsettings(24812) MainWindow::readMenu: "      " filename is  "energy.desktop"                                             
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Dimensione e orientazione" '  "randr.desktop"             
systemsettings(24812) MainWindow::readMenu: "      " filename is  "randr.desktop"                                              
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "    " found module ' "Multimedia" '  "kcm_phonon.desktop"                         
systemsettings(24812) MainWindow::readMenu: "    " filename is  "kcm_phonon.desktop"                                           
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "    " found module ' "Installatore dei caratteri" '  "fontinst.desktop"           
systemsettings(24812) MainWindow::readMenu: "    " filename is  "fontinst.desktop"                                             
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "    " found module ' "Data e ora" '  "clock.desktop"                              
systemsettings(24812) MainWindow::readMenu: "    " filename is  "clock.desktop"                                                
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "    " Looking for children in ' "personal" '                                      
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " Looking for children in ' "accessibility" '                               
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Accessibilità" '  "kcmaccess.desktop"                     
systemsettings(24812) MainWindow::readMenu: "      " filename is  "kcmaccess.desktop"                                          
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " Looking for children in ' "about-me" '                                    
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Percorsi" '  "desktoppath.desktop"                        
systemsettings(24812) MainWindow::readMenu: "      " filename is  "desktoppath.desktop"                                        
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Password e account utente" '  "kcm_useraccount.desktop"   
systemsettings(24812) MainWindow::readMenu: "      " filename is  "kcm_useraccount.desktop"                                    
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " Looking for children in ' "regional-and-language" '                       
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Spell Checker" '  "spellchecking.desktop"                 
systemsettings(24812) MainWindow::readMenu: "      " filename is  "spellchecking.desktop"                                      
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Mappatura della tastiera" '  "keyboard_layout.desktop"    
systemsettings(24812) MainWindow::readMenu: "      " filename is  "keyboard_layout.desktop"                                    
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Country/Region & Language" '  "language.desktop"          
systemsettings(24812) MainWindow::readMenu: "      " filename is  "language.desktop"                                           
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "    " found module ' "Default Applications" '  "componentchooser.desktop"         
systemsettings(24812) MainWindow::readMenu: "    " filename is  "componentchooser.desktop"                                     
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "    " Looking for children in ' "network-and-connectivity" '                      
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " Looking for children in ' "network-settings" '                            
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Preferenze sulle connessioni" '  "netpref.desktop"        
systemsettings(24812) MainWindow::readMenu: "      " filename is  "netpref.desktop"                                            
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Proxy" '  "proxy.desktop"                                 
systemsettings(24812) MainWindow::readMenu: "      " filename is  "proxy.desktop"                                              
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Service Discovery" '  "kcm_kdnssd.desktop"                
systemsettings(24812) MainWindow::readMenu: "      " filename is  "kcm_kdnssd.desktop"                                         
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Impostazioni di rete" '  "kcm_knetworkconfmodule.desktop" 
systemsettings(24812) MainWindow::readMenu: "      " filename is  "kcm_knetworkconfmodule.desktop"                             
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " Looking for children in ' "sharing" '                                     
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Navigazione rete locale" '  "lanbrowser.desktop"          
systemsettings(24812) MainWindow::readMenu: "      " filename is  "lanbrowser.desktop"                                         
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " Looking for children in ' "bluetooth" '                                   
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "    " Looking for children in ' "look-and-feel" '                                 
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " Looking for children in ' "desktop" '                                     
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Effetti del desktop" '  "kwincompositing.desktop"         
systemsettings(24812) MainWindow::readMenu: "      " filename is  "kwincompositing.desktop"                                    
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Segnalazione avvio applicazioni" '  "kcmlaunch.desktop"   
systemsettings(24812) MainWindow::readMenu: "      " filename is  "kcmlaunch.desktop"                                          
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Desktop multipli" '  "desktop.desktop"                    
systemsettings(24812) MainWindow::readMenu: "      " filename is  "desktop.desktop"                                            
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Salvaschermo" '  "screensaver.desktop"                    
systemsettings(24812) MainWindow::readMenu: "      " filename is  "screensaver.desktop"                                        
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " Looking for children in ' "window-behaviour" '                            
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Comportamento delle finestre" '  "kwinoptions.desktop"    
systemsettings(24812) MainWindow::readMenu: "      " filename is  "kwinoptions.desktop"                                        
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Specifiche per la finestra" '  "kwinrules.desktop"        
systemsettings(24812) MainWindow::readMenu: "      " filename is  "kwinrules.desktop"                                          
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " Looking for children in ' "appearance" '                                  
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Stile" '  "style.desktop"                                 
systemsettings(24812) MainWindow::readMenu: "      " filename is  "style.desktop"                                              
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Finestre" '  "kwindecoration.desktop"                     
systemsettings(24812) MainWindow::readMenu: "      " filename is  "kwindecoration.desktop"                                     
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"                        
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Schermata d'avvio" '  "ksplashthememgr.desktop"           
systemsettings(24812) MainWindow::readMenu: "      " filename is  "ksplashthememgr.desktop"                                    
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Tipi di carattere" '  "fonts.desktop"
systemsettings(24812) MainWindow::readMenu: "      " filename is  "fonts.desktop"
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Emoticons" '  "emoticons.desktop"
systemsettings(24812) MainWindow::readMenu: "      " filename is  "emoticons.desktop"
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Icons" '  "icons.desktop"
systemsettings(24812) MainWindow::readMenu: "      " filename is  "icons.desktop"
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"
systemsettings(24812) MainWindow::readMenu: "      " found module ' "GTK Styles and Fonts" '  "kcmgtk4.desktop"
systemsettings(24812) MainWindow::readMenu: "      " filename is  "kcmgtk4.desktop"
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Colori" '  "colors.desktop"
systemsettings(24812) MainWindow::readMenu: "      " filename is  "colors.desktop"
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"
systemsettings(24812) MainWindow::readMenu: "      " Looking for children in ' "notifications" '
systemsettings(24812) MainWindow::readMenu: "      " found module ' "System Notifications" '  "kcmnotify.desktop"
systemsettings(24812) MainWindow::readMenu: "      " filename is  "kcmnotify.desktop"
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"
systemsettings(24812) MainWindow::readMenu: "      " found module ' "Campanella di sistema" '  "bell.desktop"
systemsettings(24812) MainWindow::readMenu: "      " filename is  "bell.desktop"
systemsettings(24812) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"
<unknown program name>(24811)/: Communication problem with  "systemsettings" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" "

```

Thanks for reading.

---

### Post by mirons on 2009-05-05
I reset the application deleting files in
~/.kde/share/apps/systemsettings/  and
~/.kde/share/config/systemsettingsrc
then it worked. I read this is a common solution for dbus problems in kde apps.

---

### Post by thebigob on 2009-05-06
Was trying to work this out for ages!

Thanks so much for this!

---

