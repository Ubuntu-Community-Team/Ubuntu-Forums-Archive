---
title: "Hal, udev, etc..."
date: 2005-04-07
forum: Hardware &amp; Laptops
---

### Post by tasca on 2005-04-07
somebody can help me with this.

tasca@ubuntu:~$ sudo dpkg --configure -a
Instalando udev (0.050-3ubuntu7) ...
Populating the new /dev filesystem temporarily mounted on /tmp/dir.oMKqNm/...
mount: mount point /.dev does not exist
dpkg: erro processando udev (--configure):
 subprocesso post-installation script retornou código de saída de error 32
dpkg: problemas de dependência impedem configuração de hal:
 hal depende de udev; porém:
  Pacote udev não está configurado ainda.
dpkg: erro processando hal (--configure):
 problemas de dependência - deixando desconfigurado
dpkg: problemas de dependência impedem configuração de hwdb-client:
 hwdb-client depende de hal; porém:
  Pacote hal não está configurado ainda.
dpkg: erro processando hwdb-client (--configure):
 problemas de dependência - deixando desconfigurado
dpkg: problemas de dependência impedem configuração de hal-device-manager:
 hal-device-manager depende de hal; porém:
  Pacote hal não está configurado ainda.
dpkg: erro processando hal-device-manager (--configure):
 problemas de dependência - deixando desconfigurado
Erros foram encontrados durante processamento de:
 udev
 hal
 hwdb-client
 hal-device-manager
tasca@ubuntu:~$


  
Gnome 2.10 from hoary
Xorg  from hoary
Kernel 2.6.11-kanotix-6 from kanotix
 
 
FORCE AND ILLUMINATION FOR ALL
 
tasca

---

### Post by Nis on 2005-04-07
[QUOTE=tasca]somebody can help me with this.

tasca@ubuntu:~$ sudo dpkg --configure -a
Instalando udev (0.050-3ubuntu7) ...
Populating the new /dev filesystem temporarily mounted on /tmp/dir.oMKqNm/...
mount: mount point /.dev does not exist
dpkg: erro processando udev (--configure):
 subprocesso post-installation script retornou código de saída de error 32
dpkg: problemas de dependência impedem configuração de hal:
 hal depende de udev; porém:
  Pacote udev não está configurado ainda.
dpkg: erro processando hal (--configure):
 problemas de dependência - deixando desconfigurado
dpkg: problemas de dependência impedem configuração de hwdb-client:
 hwdb-client depende de hal; porém:
  Pacote hal não está configurado ainda.
dpkg: erro processando hwdb-client (--configure):
 problemas de dependência - deixando desconfigurado
dpkg: problemas de dependência impedem configuração de hal-device-manager:
 hal-device-manager depende de hal; porém:
  Pacote hal não está configurado ainda.
dpkg: erro processando hal-device-manager (--configure):
 problemas de dependência - deixando desconfigurado
Erros foram encontrados durante processamento de:
 udev
 hal
 hwdb-client
 hal-device-manager
tasca@ubuntu:~$


  
Gnome 2.10 from hoary
Xorg  from hoary
Kernel 2.6.11-kanotix-6 from kanotix
 
 
FORCE AND ILLUMINATION FOR ALL
 
tasca[/QUOTE]
 Try:
```

sudo mkdir /.dev

```
and then reboot.

---

### Post by tasca on 2005-04-08
Hi Nis

 thanks, thanks, thanks...

 tasca

---

### Post by davidhanney on 2005-06-23
i got the same thing

it might be a general warty to hoary upgrade issue

---

