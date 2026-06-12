---
title: "Error to compiling Via video card driver"
date: 2008-11-27
forum: Hardware
---

### Post by rodrigocorsi on 2008-11-27
Hello for All!
My laptop has a  CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] video card.
	
With the Ubuntu 8.04 I could use the compiz with the driver [http://linux.via.com.tw/support/beginDownload.action?eleid=8&fid=169]("http://linux.via.com.tw/support/beginDownload.action?eleid=8&fid=169")

When I try to compile this drive in Ubuntu 8.10 I receive a error:

```

sudo make
[sudo] password for rodrigo: 
make  all-recursive
make[1]: Entrando no diretório `/home/rodrigo/Desktop/xf86-video-via-83.1.0/X11R7'
Making all in src
make[2]: Entrando no diretório `/home/rodrigo/Desktop/xf86-video-via-83.1.0/X11R7/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -I/usr/include/xorg -I/usr/include/pixman-1   -DIN_MODULE -DXFree86Module -DXFree86LOADER  -DXFree86Server -I/usr/include/drm -I/usr/include/X11/dri   -I/usr/include/X11  -I/usr/include/X11/extensions -I.. -I.  -g -O2 -MT hw.lo -MD -MP -MF .deps/hw.Tpo -c -o hw.lo hw.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -I/usr/include/xorg -I/usr/include/pixman-1 -DIN_MODULE -DXFree86Module -DXFree86LOADER -DXFree86Server -I/usr/include/drm -I/usr/include/X11/dri -I/usr/include/X11 -I/usr/include/X11/extensions -I.. -I. -g -O2 -MT hw.lo -MD -MP -MF .deps/hw.Tpo -c hw.c  -fPIC -DPIC -o .libs/hw.o
In file included from hw.c:32:
via_driver.h:46:24: error: xf86_ansic.h: Arquivo ou diretório inexistente
In file included from via_driver.h:72,
                 from hw.c:32:
drm.h:425:1: warning: "DRM_IOCTL_VIA_FREEMEM" redefined
In file included from drm.h:104,
                 from via_driver.h:72,
                 from hw.c:32:
via_drm.h:186:1: warning: this is the location of the previous definition
In file included from hw.c:32:
via_driver.h:323: error: expected specifier-qualifier-list before ‘pciVideoPtr’
make[2]: ** [hw.lo] Erro 1
make[2]: Saindo do diretório `/home/rodrigo/Desktop/xf86-video-via-83.1.0/X11R7/src'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretório `/home/rodrigo/Desktop/xf86-video-via-83.1.0/X11R7'
make: ** [all] Erro 2


```

"via_driver.h: 46:24: error: xf86_ansic.h: File or directory does not exist"

	
There is no file /usr/include/xorg/xf86_ansic.h

how do I get this dependency?

---

