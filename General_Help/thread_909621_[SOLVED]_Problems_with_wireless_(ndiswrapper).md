---
title: "[SOLVED] Problems with wireless (ndiswrapper)"
date: 2008-09-03
forum: General Help
---

### Post by Titan8990 on 2008-09-03
I just got an Encore ENLWI-G2. There were Linux drivers available on Encore's website but they fail to compile. I have double checked their readme and there is no indication that I need some type of library outside of the norm.

I moved on to trying ndiswrapper because I saw that someone else had got it to work like that. Ndiswrapper shows a successful installation but there is no interface.

Some addition information:

```
jason@iRobot:~$ sudo lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]
02:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
02:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
```

```
jason@iRobot:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:c9:0d:0a  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fec9:d0a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1770 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2339859 (2.2 MB)  TX bytes:183005 (178.7 KB)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:138000 (134.7 KB)  TX bytes:138000 (134.7 KB)

```

```
jason@iRobot:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

```
jason@iRobot:~$ ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

jason@iRobot:~$ ifconfig ath0 up
ath0: ERROR while getting interface flags: No such device

```

```
jason@iRobot:~$ cat /etc/network/interfaces 
auto lo
auto wlan0
iface wlan0 inet dhcp
iface lo inet loopback
```


```
jason@iRobot:~$ ndiswrapper -l
net8185 : driver installed
	device (10EC:8185) present
```


I appreciate any help or support offered.

---

### Post by pytheas22 on 2008-09-03
Most likely it won't work because either 1) the Windows drivers that you installed don't agree with ndiswrapper, and you need to find ones that work better; or 2) you installed a 32-bit Windows driver on 64-bit Ubuntu, or vice-versa.  It's also possible that the ndiswrapper module is simply not loaded.  Please reboot and then post the output of these commands so that we can know for sure:
```

lshw -C Network
lsmod | grep ndis
sudo modprobe ndiswrapper
dmesg | grep -e ndis
uname -m
```

If you want to save time, try following the ndiswrapper-troubleshooting link in my signature, which will hopefully lead you to a solution on your own.  Otherwise I'm happy to help if you post the information requested above.

---

### Post by Titan8990 on 2008-09-03
> 2) you installed a 32-bit Windows driver on 64-bit Ubuntu, or vice-versa.

I completely forgot that I was using 64bit Ubuntu (for whatever reason installation failed using 32bit).

I will try installing the 64bit Windows drivers, reboot and then post the output of the commands given.

Thank you for the reply.

---

### Post by Titan8990 on 2008-09-03
Bad news, that toasted it. It now fails to boot hanging at loading drivers. I was able to get it to drop me a root shell in recovery mode but it will not allow me to alter the /etc/modules file claiming that it is "read-only". I tried to change this via chmod and that failed as well. Going to see if I can dig up my live CD to repair this issue.

---

### Post by pytheas22 on 2008-09-03
> it will not allow me to alter the /etc/modules file claiming that it is "read-only"

You probably forgot to access that file as root.  You should be able to write to it by:
```

sudo chmod +w /etc/modules
sudo nano /etc/modules
```

You could also simply run:
```

sudo rmmod ndiswrapper
```

to unload the ndiswrapper module when it's hanging.

---

### Post by Titan8990 on 2008-09-03
I was root because it was the recovery shell on a computer I have not (and don't plan to) unlock root.

I booted into puppy linux and changed the /etc/modules file, removing the ndiswrapper line. I now seem to be having issues with gdm. After log in it hangs. I tried killing it with CTRL+ALT+Backspace and restarting it with /etc/init.d/gdm restart.

"There was an error starting the GNOME Setting Daemon." 

That is the error message I get. Window looks like XFCE. The close button does nothing and it just hangs there.

Any ideas or is this toast?


Edit/Update: any commands requiring sudo don't work. The system hangs without asking for authentication. I am just going to wipe it since it only takes 45min to reinstall and I'm sure if I were to go about hashing out these issues it would take much longer.

Edit/Update2: Even though I removed the line from /etc/modules ndiswrapper is still there. It shows when I do lsmod | grep ndiswrapper. 

sudo rmod ndiswrapper will not work due to not being able to sudo anything.

---

### Post by pytheas22 on 2008-09-03
> I am just going to wipe it since it only takes 45min to reinstall and I'm sure if I were to go about hashing out these issues it would take much longer.

Yeah, that's what I would do.  I wouldn't want to spend a long time dealing with gdm's flakiness when a reinstall only takes a few minutes.  Once you get reinstalled, try installing the 64-bit driver into ndiswrapper again.  You may want not to add ndiswrapper to /etc/modules for the time being--modprobe it manually instead--so that if it does cause the system to hang, it won't prevent it from booting too.

---

### Post by Titan8990 on 2008-09-03
Alright, I am actually going to give the 32bit a try again because I think that the problems I was having the first time was the need to add acpi=off to the boot. If not I will be installing 64bit again and giving it a go once more.

---

### Post by Titan8990 on 2008-09-03
32bit Ubuntu + ndiswrapper worked perfect. Thanks again for the help.

---

### Post by pytheas22 on 2008-09-04
I'm glad it worked.  And yes, it does seem that if you just want a hassle-free Ubuntu experience, you're best off using 32-bit...64-bit speed is nice but there are issues with flash, more problems with drivers, some packages not compiled for 64-bit, etc.

---

### Post by osdarodi on 2008-09-04
[COLOR="Red"]sorry, i have a problem with ndis..i can not intalling...i am begginer ubuntu, the error 2 is....thank for helpme.....ahhh, i use ubuntu 8.04 64bit for amd turion 64 .[/COLOR]

david@david-laptop:~/Escritorio/ndiswrapper-1.53$ make 
make -C driver 
make[1]: se ingresa al directorio `/home/david/Escritorio/ndiswrapper-1.53/driver' 
make -C /usr/src/linux-headers-2.6.24-16-generic M=/home/david/Escritorio/ndiswrapper-1.53/driver 
make[2]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-16-generic' 
  LD      /home/david/Escritorio/ndiswrapper-1.53/driver/built-in.o 
  MKEXPORT /home/david/Escritorio/ndiswrapper-1.53/driver/crt_exports.h 
  MKEXPORT /home/david/Escritorio/ndiswrapper-1.53/driver/hal_exports.h 
  MKEXPORT /home/david/Escritorio/ndiswrapper-1.53/driver/ndis_exports.h 
  MKEXPORT /home/david/Escritorio/ndiswrapper-1.53/driver/ntoskernel_exports.h 
  MKEXPORT /home/david/Escritorio/ndiswrapper-1.53/driver/ntoskernel_io_exports.h 
  MKEXPORT /home/david/Escritorio/ndiswrapper-1.53/driver/rtl_exports.h 
  MKEXPORT /home/david/Escritorio/ndiswrapper-1.53/driver/usb_exports.h 
  MKSTUBS /home/david/Escritorio/ndiswrapper-1.53/driver/win2lin_stubs.h 
  CC [M]  /home/david/Escritorio/ndiswrapper-1.53/driver/crt.o 
  CC [M]  /home/david/Escritorio/ndiswrapper-1.53/driver/hal.o 
  CC [M]  /home/david/Escritorio/ndiswrapper-1.53/driver/iw_ndis.o 
  CC [M]  /home/david/Escritorio/ndiswrapper-1.53/driver/loader.o 
  CC [M]  /home/david/Escritorio/ndiswrapper-1.53/driver/ndis.o 
  CC [M]  /home/david/Escritorio/ndiswrapper-1.53/driver/ntoskernel.o 
  CC [M]  /home/david/Escritorio/ndiswrapper-1.53/driver/ntoskernel_io.o 
  CC [M]  /home/david/Escritorio/ndiswrapper-1.53/driver/pe_linker.o 
  CC [M]  /home/david/Escritorio/ndiswrapper-1.53/driver/pnp.o 
  CC [M]  /home/david/Escritorio/ndiswrapper-1.53/driver/proc.o 
  CC [M]  /home/david/Escritorio/ndiswrapper-1.53/driver/rtl.o 
  CC [M]  /home/david/Escritorio/ndiswrapper-1.53/driver/wrapmem.o 
  CC [M]  /home/david/Escritorio/ndiswrapper-1.53/driver/wrapndis.o 
  CC [M]  /home/david/Escritorio/ndiswrapper-1.53/driver/wrapper.o 
  CC [M]  /home/david/Escritorio/ndiswrapper-1.53/driver/usb.o 
  AS [M]  /home/david/Escritorio/ndiswrapper-1.53/driver/win2lin_stubs.o 
  LD [M]  /home/david/Escritorio/ndiswrapper-1.53/driver/ndiswrapper.o 
  Building modules, stage 2. 
  MODPOST 1 modules 
  CC      /home/david/Escritorio/ndiswrapper-1.53/driver/ndiswrapper.mod.o 
  LD [M]  /home/david/Escritorio/ndiswrapper-1.53/driver/ndiswrapper.ko 
make[2]: se sale del directorio `/usr/src/linux-headers-2.6.24-16-generic' 
make[1]: se sale del directorio `/home/david/Escritorio/ndiswrapper-1.53/driver' 
make -C utils 
make[1]: se ingresa al directorio `/home/david/Escritorio/ndiswrapper-1.53/utils' 
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c 
loadndisdriver.c:15:20: error: stdlib.h: No existe el fichero ó directorio 
loadndisdriver.c:16:19: error: stdio.h: No existe el fichero ó directorio 
loadndisdriver.c:17:19: error: errno.h: No existe el fichero ó directorio 
loadndisdriver.c:18:20: error: string.h: No existe el fichero ó directorio 
loadndisdriver.c:19:20: error: libgen.h: No existe el fichero ó directorio 
loadndisdriver.c:21:22: error: sys/mman.h: No existe el fichero ó directorio 
loadndisdriver.c:23:23: error: sys/types.h: No existe el fichero ó directorio 
loadndisdriver.c:24:23: error: sys/ioctl.h: No existe el fichero ó directorio 
loadndisdriver.c:25:22: error: sys/stat.h: No existe el fichero ó directorio 
loadndisdriver.c:26:20: error: unistd.h: No existe el fichero ó directorio 
loadndisdriver.c:27:19: error: fcntl.h: No existe el fichero ó directorio 
En el fichero incluído de /usr/lib/gcc/x86_64-linux-gnu/4.2.3/include/syslimits.h:7, 
                 de /usr/lib/gcc/x86_64-linux-gnu/4.2.3/include/limits.h:11, 
                 de loadndisdriver.c:28: 
/usr/lib/gcc/x86_64-linux-gnu/4.2.3/include/limits.h:122:61: error: limits.h: No existe el fichero ó directorio 
loadndisdriver.c:29:19: error: ctype.h: No existe el fichero ó directorio 
loadndisdriver.c:30:20: error: dirent.h: No existe el fichero ó directorio 
loadndisdriver.c:31:20: error: syslog.h: No existe el fichero ó directorio 
loadndisdriver.c:34:25: error: linux/major.h: No existe el fichero ó directorio 
loadndisdriver.c:35:25: error: linux/ioctl.h: No existe el fichero ó directorio 
In file included from loadndisdriver.c:37: 
../driver/loader.h:28: error: expected specifier-qualifier-list before ‘size_t’ 
loadndisdriver.c: En la función ‘load_file’: 
loadndisdriver.c:67: error: ‘size_t’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:67: error: (Cada identificador no declarado solamente se reporta una vez 
loadndisdriver.c:67: error: para cada funcion en la que aparece.) 
loadndisdriver.c:67: error: expected ‘;’ before ‘size’ 
loadndisdriver.c:68: error: ‘NULL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:69: error: no se conoce el tamaño de almacenamiento de ‘statbuf’ 
loadndisdriver.c:71: aviso: declaración implícita de la función ‘basename’ 
loadndisdriver.c:71: aviso: la inicialización crea un puntero desde un entero sin una conversión 
loadndisdriver.c:73: aviso: declaración implícita de la función ‘open’ 
loadndisdriver.c:73: error: ‘O_RDONLY’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:75: aviso: declaración implícita de la función ‘syslog’ 
loadndisdriver.c:75: error: ‘LOG_KERN’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:75: error: ‘LOG_INFO’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:75: aviso: declaración implícita de la función ‘strerror’ 
loadndisdriver.c:75: error: ‘errno’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:76: error: ‘EINVAL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:79: aviso: declaración implícita de la función ‘fstat’ 
loadndisdriver.c:81: aviso: declaración implícita de la función ‘close’ 
loadndisdriver.c:84: error: ‘size’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:86: aviso: declaración implícita de la función ‘mmap’ 
loadndisdriver.c:86: error: ‘PROT_READ’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:86: aviso: la asignación crea un puntero desde un entero sin una conversión 
loadndisdriver.c:87: error: ‘MAP_FAILED’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:93: aviso: declaración implícita de la función ‘strncpy’ 
loadndisdriver.c:93: aviso: declaración implícita incompatible de la función interna ‘strncpy’ 
loadndisdriver.c:95: error: ‘struct load_driver_file’ no tiene un miembro llamado ‘size’ 
loadndisdriver.c:96: error: ‘struct load_driver_file’ no tiene un miembro llamado ‘data’ 
loadndisdriver.c:69: aviso: variable ‘statbuf’ sin usar 
loadndisdriver.c: En la función ‘parse_setting_line’: 
loadndisdriver.c:109: aviso: declaración implícita de la función ‘isspace’ 
loadndisdriver.c:115: aviso: declaración implícita de la función ‘strchr’ 
loadndisdriver.c:115: aviso: declaración implícita incompatible de la función interna ‘strchr’ 
loadndisdriver.c:115: error: ‘NULL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:117: error: ‘LOG_KERN’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:117: error: ‘LOG_INFO’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:118: error: ‘EINVAL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:138: aviso: declaración implícita de la función ‘strlen’ 
loadndisdriver.c:138: aviso: declaración implícita incompatible de la función interna ‘strlen’ 
loadndisdriver.c: En la función ‘read_conf_file’: 
loadndisdriver.c:150: error: no se conoce el tamaño de almacenamiento de ‘statbuf’ 
loadndisdriver.c:151: error: ‘FILE’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:151: error: ‘config’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:157: aviso: declaración implícita de la función ‘lstat’ 
loadndisdriver.c:158: error: ‘LOG_KERN’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:158: error: ‘LOG_INFO’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:158: error: ‘errno’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:160: error: ‘EINVAL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:163: aviso: declaración implícita de la función ‘sscanf’ 
loadndisdriver.c:163: aviso: declaración implícita incompatible de la función interna ‘sscanf’ 
loadndisdriver.c:178: aviso: declaración implícita de la función ‘fopen’ 
loadndisdriver.c:178: error: ‘NULL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:182: aviso: declaración implícita de la función ‘fgets’ 
loadndisdriver.c:194: aviso: declaración implícita incompatible de la función interna ‘strncpy’ 
loadndisdriver.c:205: aviso: declaración implícita de la función ‘fclose’ 
loadndisdriver.c:150: aviso: variable ‘statbuf’ sin usar 
loadndisdriver.c: En la función ‘load_bin_file’: 
loadndisdriver.c:217: error: ‘LOG_KERN’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:217: error: ‘LOG_INFO’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:219: aviso: declaración implícita de la función ‘tolower’ 
loadndisdriver.c:221: aviso: declaración implícita de la función ‘chdir’ 
loadndisdriver.c:222: error: ‘errno’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:224: error: ‘EINVAL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:230: aviso: declaración implícita incompatible de la función interna ‘strncpy’ 
loadndisdriver.c:232: aviso: declaración implícita de la función ‘ioctl’ 
loadndisdriver.c:232: aviso: declaración implícita de la función ‘_IOW’ 
loadndisdriver.c:232: error: expected expression before ‘struct’ 
loadndisdriver.c: En la función ‘load_driver’: 
loadndisdriver.c:249: error: ‘DIR’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:249: error: ‘driver_dir’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:251: error: ‘NULL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:255: error: ‘LOG_KERN’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:255: error: ‘LOG_INFO’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:257: error: ‘errno’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:259: error: ‘EINVAL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:261: aviso: declaración implícita de la función ‘opendir’ 
loadndisdriver.c:267: aviso: declaración implícita de la función ‘malloc’ 
loadndisdriver.c:267: aviso: declaración implícita incompatible de la función interna ‘malloc’ 
loadndisdriver.c:271: aviso: declaración implícita de la función ‘memset’ 
loadndisdriver.c:271: aviso: declaración implícita incompatible de la función interna ‘memset’ 
loadndisdriver.c:272: aviso: declaración implícita incompatible de la función interna ‘strncpy’ 
loadndisdriver.c:280: aviso: declaración implícita de la función ‘readdir’ 
loadndisdriver.c:280: aviso: la asignación crea un puntero desde un entero sin una conversión 
loadndisdriver.c:282: error: no se conoce el tamaño de almacenamiento de ‘statbuf’ 
loadndisdriver.c:284: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:287: aviso: declaración implícita de la función ‘stat’ 
loadndisdriver.c:287: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:288: aviso: declaración implícita de la función ‘S_ISREG’ 
loadndisdriver.c:289: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:294: aviso: declaración implícita incompatible de la función interna ‘strlen’ 
loadndisdriver.c:294: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:296: aviso: declaración implícita de la función ‘strcasecmp’ 
loadndisdriver.c:296: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:299: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:302: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:303: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:305: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:311: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:312: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:313: aviso: declaración implícita de la función ‘strcpy’ 
loadndisdriver.c:313: aviso: declaración implícita incompatible de la función interna ‘strcpy’ 
loadndisdriver.c:314: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:317: error: ‘struct load_driver_file’ no tiene un miembro llamado ‘size’ 
loadndisdriver.c:318: error: ‘struct load_driver_file’ no tiene un miembro llamado ‘data’ 
loadndisdriver.c:321: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:282: aviso: variable ‘statbuf’ sin usar 
loadndisdriver.c:344: error: expected expression before ‘struct’ 
loadndisdriver.c:346: aviso: declaración implícita de la función ‘closedir’ 
loadndisdriver.c:348: aviso: declaración implícita de la función ‘free’ 
loadndisdriver.c:355: aviso: declaración implícita de la función ‘munmap’ 
loadndisdriver.c:355: error: ‘struct load_driver_file’ no tiene un miembro llamado ‘data’ 
loadndisdriver.c:355: error: ‘struct load_driver_file’ no tiene un miembro llamado ‘size’ 
loadndisdriver.c:357: error: ‘struct load_driver_file’ no tiene un miembro llamado ‘data’ 
loadndisdriver.c:357: error: ‘struct load_driver_file’ no tiene un miembro llamado ‘size’ 
loadndisdriver.c: En la función ‘get_device’: 
loadndisdriver.c:367: error: no se conoce el tamaño de almacenamiento de ‘statbuf’ 
loadndisdriver.c:370: error: ‘LOG_KERN’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:370: error: ‘LOG_INFO’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:373: error: ‘errno’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:374: error: ‘EINVAL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:376: aviso: declaración implícita de la función ‘snprintf’ 
loadndisdriver.c:376: aviso: declaración implícita incompatible de la función interna ‘snprintf’ 
loadndisdriver.c:407: aviso: declaración implícita incompatible de la función interna ‘strncpy’ 
loadndisdriver.c:367: aviso: variable ‘statbuf’ sin usar 
loadndisdriver.c: En la función ‘load_device’: 
loadndisdriver.c:419: error: ‘DIR’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:419: error: ‘dir’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:423: error: ‘LOG_KERN’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:423: error: ‘LOG_INFO’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:424: aviso: declaración implícita incompatible de la función interna ‘memset’ 
loadndisdriver.c:426: error: ‘errno’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:427: error: ‘EINVAL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:429: error: ‘NULL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:434: aviso: la asignación crea un puntero desde un entero sin una conversión 
loadndisdriver.c:435: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:436: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:439: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:447: error: expected expression before ‘struct’ 
loadndisdriver.c: En la función ‘get_ioctl_device’: 
loadndisdriver.c:464: error: ‘FILE’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:464: error: ‘proc_misc’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:472: aviso: declaración implícita de la función ‘strstr’ 
loadndisdriver.c:472: aviso: declaración implícita incompatible de la función interna ‘strstr’ 
loadndisdriver.c:473: aviso: declaración implícita de la función ‘strtol’ 
loadndisdriver.c:473: error: ‘NULL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:483: error: ‘LOG_KERN’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:483: error: ‘LOG_INFO’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:488: aviso: declaración implícita de la función ‘unlink’ 
loadndisdriver.c:489: aviso: declaración implícita de la función ‘mknod’ 
loadndisdriver.c:489: error: ‘S_IFCHR’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:489: error: ‘MISC_MAJOR’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:490: error: ‘errno’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:495: error: ‘O_RDONLY’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c: En la función ‘main’: 
loadndisdriver.c:511: aviso: declaración implícita de la función ‘openlog’ 
loadndisdriver.c:511: error: ‘LOG_PERROR’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:511: error: ‘LOG_CONS’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:511: error: ‘LOG_KERN’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:511: error: ‘LOG_DEBUG’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:513: error: ‘LOG_INFO’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:515: aviso: declaración implícita de la función ‘strncmp’ 
loadndisdriver.c:517: aviso: declaración implícita de la función ‘printf’ 
loadndisdriver.c:517: aviso: declaración implícita incompatible de la función interna ‘printf’ 
loadndisdriver.c:527: aviso: declaración implícita de la función ‘atoi’ 
loadndisdriver.c:542: aviso: declaración implícita de la función ‘atof’ 
loadndisdriver.c:549: aviso: declaración implícita de la función ‘strcmp’ 
loadndisdriver.c:556: aviso: declaración implícita incompatible de la función interna ‘sscanf’ 
loadndisdriver.c:590: aviso: declaración implícita de la función ‘closelog’ 
make[1]: *** [loadndisdriver] Error 1 
make[1]: se sale del directorio `/home/david/Escritorio/ndiswrapper-1.53/utils' 
make: *** [all] Error 2 
david@david-laptop:~/Escritorio/ndiswrapper-1.53$ # dmesg 
david@david-laptop:~/Escritorio/ndiswrapper-1.53$ #dmesg 
david@david-laptop:~/Escritorio/ndiswrapper-1.53$

---

### Post by pytheas22 on 2008-09-04
osdarodi,

You tried to compile ndiswrapper from source, which is not necessary in most cases.  If you are currently connected to the Internet in some way, you can easily install ndiswrapper by typing:
```

sudo apt-get install ndiswrapper*
```

If you are not connect to the Internet, you can download the ndiswrapper packages from [http://packages.ubuntu.com](http://packages.ubuntu.com).  You need to find the ndiswrapper-utils and ndiswrapper-common packages.  Then transfer them to Ubuntu via USB drive or something, and double-click to install them.

Please try installing ndiswrapper using one of the methods described above, and let us know.

---

### Post by osdarodi on 2008-09-09
thank you phite, very thank

---

