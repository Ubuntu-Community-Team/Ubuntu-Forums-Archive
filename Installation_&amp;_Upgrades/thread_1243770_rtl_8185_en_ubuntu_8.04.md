---
title: "rtl 8185 en ubuntu 8.04"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by hgracia on 2009-08-18
Estimados:
 
 
Seguí las instrucciones para configurar mi tarjeta inalambrica y tuve éxito.
Cuando instalé las actualizaciones disponibles (397 aprox.) dejó de funcionar.
Intenté instalarla nuevamente pero al probar sudo ./wlan0up me dio un error.
A continuación van los pasos que seguí:
 
[COLOR=red]1. Asegurarse de tener las herraminetas de desarrollo necesarias para compilar:[/COLOR]
 
[COLOR=red]sudo aptitude install build-essential[/COLOR]
 
[COLOR=red]2. Descargar las fuentes del controlador:[/COLOR]
 
[COLOR=red]wget [/COLOR][[COLOR=red]http://willdaniels.co.uk/attachments/rtl8185.zip[/COLOR]]("http://willdaniels.co.uk/attachments/rtl8185.zip")
 
[COLOR=red]3. Extraer los archivos y entrar en el directorio extraído:[/COLOR]
 
[COLOR=red]unzip rtl8185.zip[/COLOR]
[COLOR=red]cd rtl8185[/COLOR]
 
[COLOR=red]4. Compilar el controlador (no preocuparse por mensajes de warning, en tanto no haya ningún “fatal error” todo bien):[/COLOR]
 
[COLOR=red]./makedrv[/COLOR]
 
[COLOR=red]5. Probar que el módulo cargue sin problemas:[/COLOR]
 
[COLOR=red]sudo ./wlan0up[/COLOR]
 
[COLOR=red]6. Si todo está funcionando, copiar los módulos compilados a una ubicación más conveniente:[/COLOR]
 
[COLOR=red]sudo cp rtl8185/*.ko /lib/modules/`uname -r`/kernel/net/wireless[/COLOR]
[COLOR=red]sudo cp ieee80211/*.ko /lib/modules/`uname -r`/kernel/net/wireless[/COLOR]
 
[COLOR=red]7. Actualizar las dependencias de los módulos:[/COLOR]
 
[COLOR=red]sudo depmod -a[/COLOR]
 
[COLOR=red]Hay un paso final, para asegurarse que el módulo se cargue al momento del boot.[/COLOR]
 
[COLOR=red]sudo -i[/COLOR]
[COLOR=red]echo ieee80211_crypt_rtl >> /etc/modules[/COLOR]
[COLOR=red]echo ieee80211_crypt_wep_rtl >> /etc/modules[/COLOR]
[COLOR=red]echo ieee80211_crypt_tkip_rtl >> /etc/modules[/COLOR]
[COLOR=red]echo ieee80211_crypt_ccmp_rtl >> /etc/modules[/COLOR]
[COLOR=red]echo ieee80211_rtl >> /etc/modules[/COLOR]
[COLOR=red]echo r8180 >> /etc/modules[/COLOR]
[COLOR=red]exit[/COLOR]
 
Y aqui pego el error que me dió:
 
[FONT=Times New Roman][SIZE=3][COLOR=red]hernan@hernan:~/rtl8185$ sudo ./wlan0up[/COLOR][/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][COLOR=red]insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 File exists[/COLOR][/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][COLOR=red]insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 File exists[/COLOR][/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][COLOR=red]insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 File exists[/COLOR][/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][COLOR=red]insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 File exists[/COLOR][/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][COLOR=red]insmod: error inserting 'ieee80211-rtl.ko': -1 File exists[/COLOR][/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][COLOR=red]insmod: error inserting 'r8180.ko': -1 Unknown symbol in module[/COLOR][/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][COLOR=red]wlan0: ERROR mientras se obtenían las banderas de interfaz: No existe el dispositivo[/COLOR][/SIZE][/FONT]
 
[FONT=Nimbus Roman No9 L][FONT=Times New Roman][COLOR=red]hernan@hernan:~/rtl8185$ [/COLOR][/FONT][/FONT]
 
[FONT=Nimbus Roman No9 L][FONT=Times New Roman]Se agradece cualquier ayuda.[/FONT][/FONT]
[FONT=Nimbus Roman No9 L][FONT=Times New Roman]Gracias[/FONT][/FONT]

---

