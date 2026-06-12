---
title: "consulta kubuntu 9.10 - RLT8185"
date: 2009-12-07
forum: Hardware
---

### Post by cristiaan3003 on 2009-12-07
Hola, quiesiera saber si alguien pudo instalar y que funcione correctamente  uan placa encore enlwi-g2 (RTL8185) .
Yo estoy intentando instalar y no funciona, la primera ves  cuando recien instale la detectaba  usaba los driver que trae por defencto RTL8180, pero tenia señal muy baja que en relidad no servia para nada.
baje los driver de la pagina de realtek para linux,  bueno  cuando los compilo "make" tira 2 errores y cdo hago "make install" tmb, ose no anda no puedo instalar de esa forma. Prove ndiswrapper-1.55, (use los driver para XP ) lo intale junto con todas la dependencias nesesartias ( el tools y winfi utils o algo asi tmb tng intalados), bueno la cuention es  que cuando hago "ndiswrapper -l" me dice que los driver estan instalados, pero cuando quiero cagar el modulo con "modprobe ndiswrapper" dice "FATAL: Module ndiswrapper not found",y si no carga el modulo nunca me a a funcionas.

Ya puse la rtl 8180 y otra cosas mas en la blacklist como se puede encotrar en  google, es lo que tira primero en la busqueda.

en definitiva hice de todo pero la placa wifi no la encuentra de ninguna de las 2 formas, quiera saber como  hacer anda el driver de linux o como solucionar el error para subir el modulo

---

### Post by luks911 on 2009-12-07
Pasá el link desde donde descargaste el driver para Linux y pegá también cuál es el error exacto que te da al compilar. Capaz que te falta alguna dependencia nomás.

---

### Post by cristiaan3003 on 2009-12-08
Hola bueno, el link de donde baje es, desde ahi baje los de linux y xp

[http://www.encore-usa.com/product_download.php?region=us&bid=3&pgid=81_4&pid=285](http://www.encore-usa.com/product_download.php?region=us&bid=3&pgid=81_4&pid=285)

los pasos que  hice para instalar los driver de linux son los que vienen descriptos dentro del archivo  explicativo que  esta dentro de la carpeta que contiene los drivers, los pasos para ndiswrapper los saque desde distintas paginas y leyendo  alguna explicaciones que encontre.

aca te que es lo que fui realizando en orden, y adjunto una cuanta imagenes para que veas:

1.[http://img51.imageshack.us/img51/3043/1carpetas.jpg](http://img51.imageshack.us/img51/3043/1carpetas.jpg)
2.[http://img37.imageshack.us/img37/7508/2pasosdeintalacion.jpg](http://img37.imageshack.us/img37/7508/2pasosdeintalacion.jpg)
3. LA SALIDA DE LA CONSOLA ( la pego el final, es un poco larga por eso)
4.[http://img19.imageshack.us/img19/6002/4comandosifconfigiwconf.jpg](http://img19.imageshack.us/img19/6002/4comandosifconfigiwconf.jpg)
NO funciono asi que  intente usar ndiswrapper , abajo esta lo que fui haciendo
5.[http://img205.imageshack.us/img205/2420/6comandoslspci.jpg](http://img205.imageshack.us/img205/2420/6comandoslspci.jpg)
6.[http://img13.imageshack.us/img13/6117/7driverxpcarpetas.jpg](http://img13.imageshack.us/img13/6117/7driverxpcarpetas.jpg)
7.[http://img509.imageshack.us/img509/7096/75salidadelcomandondisw.jpg](http://img509.imageshack.us/img509/7096/75salidadelcomandondisw.jpg)
8.[http://img691.imageshack.us/img691/1972/8ndiswrapercomandol.jpg](http://img691.imageshack.us/img691/1972/8ndiswrapercomandol.jpg)
9.[http://img13.imageshack.us/img13/8537/9ndiswrapercomandomosea.jpg](http://img13.imageshack.us/img13/8537/9ndiswrapercomandomosea.jpg)
10.[http://img13.imageshack.us/img13/2237/10paquetesndiswrapperin.jpg](http://img13.imageshack.us/img13/2237/10paquetesndiswrapperin.jpg)
11.[http://img691.imageshack.us/img691/6861/11paqueteswirelessintal.jpg](http://img691.imageshack.us/img691/6861/11paqueteswirelessintal.jpg)
12.[http://img691.imageshack.us/img691/9391/12cabecerasdemikernel.jpg](http://img691.imageshack.us/img691/9391/12cabecerasdemikernel.jpg)
13.[http://img691.imageshack.us/img691/2639/13bkacklistconfigparaqu.jpg](http://img691.imageshack.us/img691/2639/13bkacklistconfigparaqu.jpg)
14.[http://img51.imageshack.us/img51/9414/14archivomodules.jpg](http://img51.imageshack.us/img51/9414/14archivomodules.jpg)
15.[http://img51.imageshack.us/img51/3468/16comandomodprobenoloca.jpg](http://img51.imageshack.us/img51/3468/16comandomodprobenoloca.jpg)


ESTA ES LA SALIDA DE LA CONSOLA (3) DESPUES DE HACER ./MAKEDRV

kubuntu@desktop:~/Escritorio/sss/rtl8185_linux_26.1010.0531.2006$** sudo ./makedrv**
[sudo] password for kubuntu:                                                    
ieee80211/                                                                      
ieee80211/ieee80211_tx.c                                                        
ieee80211/Modules.symvers                                                       
ieee80211/ieee80211_softmac_wx.c                                                
ieee80211/LICENSE                                                               
ieee80211/ieee80211_rx.c                                                        
ieee80211/ieee80211_crypt_tkip.c                                                
ieee80211/ieee80211_crypt.h                                                     
ieee80211/ieee80211_crypt_ccmp.c                                                
ieee80211/ieee80211_module.c                                                    
ieee80211/Makefile                                                              
ieee80211/.tmp_versions/                                                        
ieee80211/.tmp_versions/ieee80211_crypt-rtl.mod                                 
ieee80211/.tmp_versions/ieee80211_crypt_wep-rtl.mod                             
ieee80211/.tmp_versions/ieee80211_crypt_tkip-rtl.mod                            
ieee80211/.tmp_versions/ieee80211_crypt_ccmp-rtl.mod                            
ieee80211/.tmp_versions/ieee80211-rtl.mod                                       
ieee80211/ieee80211.h                                                           
ieee80211/ieee80211_softmac.c                                                   
ieee80211/README                                                                
ieee80211/ieee80211_wx.c                                                        
ieee80211/ieee80211_crypt_wep.c                                                 
ieee80211/ieee80211_crypt.c                                                     
rtl818x-0.1/                                                                    
rtl818x-0.1/r8180_wx.h                                                          
rtl818x-0.1/r8180_wx.c                                                          
rtl818x-0.1/r8180_rtl8225.h                                                     
rtl818x-0.1/r8180_rtl8255.h                                                     
rtl818x-0.1/AUTHORS                                                             
rtl818x-0.1/r8180_max2820.c                                                     
rtl818x-0.1/r8180.h                                                             
rtl818x-0.1/r8180_max2820.h                                                     
rtl818x-0.1/tags                                                                
rtl818x-0.1/r8180_sa2400.h                                                      
rtl818x-0.1/r8180_93cx6.c                                                       
rtl818x-0.1/ieee80211.h                                                         
rtl818x-0.1/r8180_gct.c                                                         
rtl818x-0.1/r8180_gct.h                                                         
rtl818x-0.1/.r8180_core.o.d                                                     
rtl818x-0.1/r8180_rtl8225.c.old                                                 
rtl818x-0.1/Modules.symvers                                                     
rtl818x-0.1/CHANGES                                                             
rtl818x-0.1/LICENSE                                                             
rtl818x-0.1/r8180_93cx6.h                                                       
rtl818x-0.1/README.master                                                       
rtl818x-0.1/r8180_hw.h                                                          
rtl818x-0.1/README                                                              
rtl818x-0.1/r8180_pm.c                                                          
rtl818x-0.1/r8180_sa2400.c                                                      
rtl818x-0.1/COPYING                                                             
rtl818x-0.1/README.adhoc                                                        
rtl818x-0.1/r8180_rtl8225.c                                                     
rtl818x-0.1/.tmp_versions/                                                      
rtl818x-0.1/.tmp_versions/r8180.mod                                             
rtl818x-0.1/INSTALL                                                             
rtl818x-0.1/r8180_rtl8255.c                                                     
rtl818x-0.1/r8180_core.c                                                        
rtl818x-0.1/r8180_pm.h                                                          
rtl818x-0.1/Makefile                                                            
rtl818x-0.1/ieee80211_crypt.h                                                   
rm -f *.mod.c *.mod *.o .*.cmd *.ko                                             
rm -rf /home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/tmp
make -C /lib/modules/2.6.31-14-generic/build M=/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211 CC=gcc modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.31-14-generic'                                                        
  CC [M]  /home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.o                                
In file included from /home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:17:                
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211.h: In function â€˜ieee80211_privâ€™:                   
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211.h:1159: warning: â€˜netdev_privâ€™ is static but used in inline function â€˜ieee80211_privâ€™ which is not static                                                                                                                                                                                        
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function â€˜ieee80211_softmac_scan_wqâ€™:                                                     
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:391: warning: ISO C90 forbids mixed declarations and code                                     
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:412: warning: passing argument 2 of â€˜queue_delayed_workâ€™ from incompatible pointer type       
include/linux/workqueue.h:203: note: expected â€˜struct delayed_work *â€™ but argument is of type â€˜struct work_struct *â€™                                                                     
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function â€˜ieee80211_softmac_stop_scanâ€™:                                                   
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:486: warning: passing argument 1 of â€˜cancel_delayed_workâ€™ from incompatible pointer type      
include/linux/workqueue.h:233: note: expected â€˜struct delayed_work *â€™ but argument is of type â€˜struct work_struct *â€™                                                                     
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function â€˜ieee80211_associate_abortâ€™:                                                     
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:885: warning: passing argument 2 of â€˜queue_delayed_workâ€™ from incompatible pointer type       
include/linux/workqueue.h:203: note: expected â€˜struct delayed_work *â€™ but argument is of type â€˜struct work_struct *â€™                                                                     
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1359:4: warning: #warning CHECK_LOCK_HERE                                                     
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1399:2: warning: #warning CHECK_LOCK_HERE                                                     
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function â€˜ieee80211_rx_frame_softmacâ€™:                                                    
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1470: warning: ISO C90 forbids mixed declarations and code                                    
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function â€˜ieee80211_stop_protocolâ€™:                                                       
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2059: warning: passing argument 1 of â€˜cancel_delayed_workâ€™ from incompatible pointer type     
include/linux/workqueue.h:233: note: expected â€˜struct delayed_work *â€™ but argument is of type â€˜struct work_struct *â€™                                                                     
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2167:78: error: macro "INIT_WORK" passed 3 arguments, but takes just 2                        
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function â€˜ieee80211_softmac_initâ€™:                                                        
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2167: error: â€˜INIT_WORKâ€™ undeclared (first use in this function)                              
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2167: error: (Each undeclared identifier is reported only once                                
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2167: error: for each function it appears in.)                                                
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2168:88: error: macro "INIT_WORK" passed 3 arguments, but takes just 2                        
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2169:94: error: macro "INIT_WORK" passed 3 arguments, but takes just 2                        
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2170:96: error: macro "INIT_WORK" passed 3 arguments, but takes just 2                        
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2171:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2                        
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2172:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2                        
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function â€˜ieee80211_softmac_freeâ€™:                                                        
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2191: warning: passing argument 1 of â€˜cancel_delayed_workâ€™ from incompatible pointer type     
include/linux/workqueue.h:233: note: expected â€˜struct delayed_work *â€™ but argument is of type â€˜struct work_struct *â€™                                                                     
[COLOR=Red]make[2]: *** [/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.o] Error 1  [/COLOR]                                                                      
[COLOR=Red]make[1]: *** [_module_/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/ieee80211] Error 2   [/COLOR]                                                                                 
[COLOR=Red]make[1]: se sale del directorio `/usr/src/linux-headers-2.6.31-14-generic'                                                                                                               
make: *** [modules] Error 2 [/COLOR]                                                                                                                                                             
rm -f *.mod.c *.mod *.o .*.cmd *.ko                                                                                                                                                      
rm -rf /home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/tmp                                                                                                      
make -C /lib/modules/2.6.31-14-generic/build M=/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1 CC=gcc modules                                                   
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.31-14-generic'                                                                                                             
  CC [M]  /home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.o
In file included from /home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:61:
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.h:29:26: error: linux/config.h: No existe el fichero Ã³ directorio
In file included from /home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.h:44,
                 from /home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:61:
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/ieee80211.h: In function â€˜ieee80211_privâ€™:
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/ieee80211.h:1158: warning: â€˜netdev_privâ€™ is static but used in inline function â€˜ieee80211_privâ€™ which is not static
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.h:46:27: error: asm/semaphore.h: No existe el fichero Ã³ directorio
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function â€˜rtl8180_proc_module_initâ€™:
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:541: error: â€˜proc_netâ€™ undeclared (first use in this function)
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:541: error: (Each undeclared identifier is reported only once
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:541: error: for each function it appears in.)
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function â€˜rtl8180_proc_module_removeâ€™:
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:547: error: â€˜proc_netâ€™ undeclared (first use in this function)
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function â€˜rtl8180_rxâ€™:
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2080: error: implicit declaration of function â€˜rdtscâ€™
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2953:67: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function â€˜rtl8180_initâ€™:
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2953: error: â€˜INIT_WORKâ€™ undeclared (first use in this function)
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:3041: error: â€˜struct net_deviceâ€™ has no member named â€˜get_statsâ€™
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:3276: error: â€˜SA_SHIRQâ€™ undeclared (first use in this function)
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:3276: warning: passing argument 2 of â€˜request_irqâ€™ from incompatible pointer type
include/linux/interrupt.h:116: note: expected â€˜irq_handler_tâ€™ but argument is of type â€˜enum irqreturn_t (*)(int,  void *, struct pt_regs *)â€™
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function â€˜rtl8180_pci_probeâ€™:
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:3960: [COLOR=Green]_*error: implicit declaration of function *_[/COLOR]â€˜SET_MODULE_OWNERâ€™
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:4023: error: â€˜struct net_deviceâ€™ has no member named â€˜openâ€™
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:4024: error: â€˜struct net_deviceâ€™ has no member named â€˜stopâ€™
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:4026: error: â€˜struct net_deviceâ€™ has no member named â€˜tx_timeoutâ€™
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:4028: error: â€˜struct net_deviceâ€™ has no member named â€˜do_ioctlâ€™
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:4029: error: â€˜struct net_deviceâ€™ has no member named â€˜set_multicast_listâ€™
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:4030: error: â€˜struct net_deviceâ€™ has no member named â€˜set_mac_addressâ€™
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:4031: error: â€˜struct net_deviceâ€™ has no member named â€˜get_wireless_statsâ€™
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function â€˜rtl8180_pci_module_initâ€™:
/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:4156: error: implicit declaration of function â€˜pci_module_initâ€™
[COLOR=Red]make[2]: *** [/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.o] Error 1[/COLOR]
[COLOR=Red]make[1]: *** [_module_/home/kubuntu/Escritorio/sss/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1] Error 2[/COLOR]
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.31-14-generic'
[COLOR=Red]**make: *** [modules] Error 2**[/COLOR]
kubuntu@desktop:~/Escritorio/sss/rtl8185_linux_26.1010.0531.2006$

---

### Post by luks911 on 2009-12-08
Tengo una mala noticia y una buena. 
La mala es que el driver que estás usando no se lleva bien con la versión del kernel que viene en Karmic, nisiquiera la última versión del driver funciona. Hay un problema por el cual no se compila y devuelve un error.
La buena es que esto es software libre, así que alguien que sabe metió mano, hizo las modificaciones necesarias y parece que funciona.
Lo que tenés que hacer es el paso por paso de más abajo. Todo en una terminal. Podés copiar y pegar así es más fácil. Ah, si tocaste algo en los archivos para poner en blacklist algún driver (creo haber visto algo en las imágenes que pasaste), volvelo a como estaba por si las dudas, es decir, editá los archivos que tocaste y borrá lo que pusiste. Ah, también sa&#263;a el ndiswrapper que pusiste en modules (también me pareció ver eso). 
Luego sí, lo siguiente:

1) Bajás el driver modificado
```

wget http://blog.ivangadea.com/wp-content/uploads/rtl8185_linux_26.1030.0625.2009.release.mod.tar.gz
```

2) Por si no lo tenías instalás todo lo necesario para compilar
```
sudo aptitude install linux-headers-$(uname -r) build-essential
```

3) Descomprimís el driver que se habrá descargado en el directorio desde el que estás trabajando, seguramente tu home
```
tar -zvxf rtl8185_linux_26.1030.0625.2009.release.mod.tar.gz
```

4) Te movés al directorio que se creó al descomprimir
```
cd rtl8185_linux_26.1030.0625.2009.release.mod
```

5) Compilás
```
make
```

6) Instalás el driver
```
sudo make install
```

7) Reiniciás y el wifi debería estar funcionando

Avisá por cualquier error o duda. Y agradecé al administrador de este blog[0], encargado de modificar el driver ;-)

[0] [http://blog.ivangadea.com/2009/11/11/driver-realtek-pci-wireless-rtl8185-para-ubuntu-karmic/](http://blog.ivangadea.com/2009/11/11/driver-realtek-pci-wireless-rtl8185-para-ubuntu-karmic/)

---

### Post by cristiaan3003 on 2009-12-09
Hola, bueno andubo, solo que el para intalar cambie la linea
 sudo make install 
por 2 pasos
sudo su
make install
 
de la otra manera parece que perdia privilegios por ahi adentro y tiraba error o nose pero asi intalo bien, agarra poca señal 16 %, el principio pense que era eso por lo que anba lenta  la conexion , con 16 % decia 1Mbts ( igual no tendria que haber sido lenta pero bueno ponele), la cuestion es que  agarro la red de mi vecino que la tiene para todos sin seguridad y ahi tmb con la misma señal anda perfecto. bueno  asi que agarre y prove yo con mi router y paso lo mismo, la configuracion de seguridad que tng en el router es 
Security Type: WPA-PSK / WPA2-PSK
Security Option:WPA2-PSK
 FOTO-->[http://img689.imageshack.us/img689/7817/dibujowcy.jpg](http://img689.imageshack.us/img689/7817/dibujowcy.jpg)
 
que cuernos me esta pasando en la configuracion para que me ande lento con la clave y sin clave ande bien
 
saludos

---

### Post by luks911 on 2009-12-09
Me alegro de que funcione. Es raro que no instalara con sudo, porque en teoría es lo mismo, pero bueh.
Con respecto a la señal, lo único que se me ocurre es atribuírselo al driver. No obstante, no sé cuán confiable es el dato de la señal (no sólo en este caso). Si no se te corta la conexión, no me preocuparía.

---

### Post by alfplayer on 2009-12-09
> **luks911 said:**
> Me alegro de que funcione. Es raro que no instalara con sudo, porque en teoría es lo mismo, pero bueh.
Con respecto a la señal, lo único que se me ocurre es atribuírselo al driver. No obstante, no sé cuán confiable es el dato de la señal (no sólo en este caso). Si no se te corta la conexión, no me preocuparía.

No es lo mismo. Por ejemplo las variables de entorno son diferentes.

---

### Post by luks911 on 2009-12-09
> **alfplayer said:**
> No es lo mismo. Por ejemplo las variables de entorno son diferentes.

Claro, una cosa es el usuario con privilegios y otra es el root, ¿no? 
Tu aclaración confirma mi falta de conocimientos teóricos :-P

---

### Post by alfplayer on 2009-12-09
> **luks911 said:**
> Claro, una cosa es el usuario con privilegios y otra es el root, ¿no?

Los privilegios de sudo son los de root. Pero el entorno no es el mismo que ejecutando su.

---

