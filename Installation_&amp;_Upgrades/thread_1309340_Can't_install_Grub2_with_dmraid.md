---
title: "Can't install Grub2 with dmraid"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by dancantong on 2009-11-01
Hi!
I have upgraded from Jaunty to Karmik Koala and I would like to convert my root ext3 filesystem to ext4. I know I also have to upgrade Grub to Grub2 because Grub does not work with ext4.

My hard disk is configured as RAID0 (with dmraid) and when I try to install Grub2 as a chainloader of Grub I get this error:

```
Configurando grub-pc (1.97~beta4-1ubuntu3) ...
Generating core.img
grub-probe: error: no mapping exists for `isw_cfbaihebid_ARRAY6'
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
dpkg: error al procesar grub-pc (--configure):
 el subproceso script post-installation instalado devolvió el código de salida de error 1
dpkg: problemas de dependencias impiden la configuración de grub2:
 grub2 depende de grub-pc; sin embargo:
 El paquete `grub-pc' no está configurado todavía.
dpkg: error al procesar grub2 (--configure):
 problemas de dependencias - se deja sin configurar
No se ha escrito ningún informe de Apport porque el mensaje de error indica que es un error proveniente de un fallo anterior.
                                             Se encontraron errores al procesar:
 grub-pc
 grub2
```

It seems Grub2 does not handle correctly dmraid.

Is there any way to get it working?

Thank you in advance.

Daniel.

---

### Post by mambazo on 2009-11-01
I'm in the EXACT same situation. Based on some googling, it seems that Grub2 currently does not support dmraid partitions, so we may have to stick to Legacy Grub for now.

However, you are mistaken in thinking that Legacy Grub doesn't not support ext4. It does. I used ext4 and grub1 when installing Jaunty, and it's still working fine on upgrading to Karmic.

---

