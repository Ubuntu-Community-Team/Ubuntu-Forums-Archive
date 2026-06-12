---
title: "Trouble compiling DAHDI drivers on 10.04"
date: 2010-10-31
forum: Hardware
---

### Post by elperepat on 2010-10-31
Hi!

I own a [Yeastar TDM1600]("http://www.yeastar.com/Products/TDM1600.asp") card (16 ports telephony card). It was working properly on 8.04, but I decided to upgrade my ubuntu version to 10.04. Back then, on 8.04, I had to compile the zaptel driver, patched to make the tdm1600 work properly.

I tried to follow the same steps, but compile failed because Digium changed the drivers name back in 2008 to dahdi (Digium Asterisk Hardware Device Interface) and stopped the support of zaptel.

On the manufacturer website, there this [document]("http://www.yeastar.com/download/TDM_DriverInstall_dahdi.pdf") which I followed to compile the new dahdi drivers. All the compilation procedure is fine, but the driver is not loaded. I get the following error:

```
FATAL: Error inserting ystdm16xx (/lib/modules/2.6.32-25-generic/dahdi/ystdm16xx.ko): Invalid module format
```

From what I understand, this means the driver was compiled for a different kernel version or architecture. I did compile it on my computer. I also removed the old kernel version to make sure the compilation was not using it. So now, I only have one linux-headers, 2.6.32-25-generic

If I modinfo my newly complied driver, I get:

```
filename:       /lib/modules/2.6.32-25-generic/dahdi/ystdm16xx.ko
license:        GPL v2
alias:          ystdm16xx
author:         yeastar <support@yeastar.com>
description:    YSTDM16xx Yeastar Driver
srcversion:     4E2EA5181F58940CCA57608
alias:          pci:v0000E159d00000001sv00006151sd*bc*sc*i*
depends:        dahdi
vermagic:       2.6.32-25-generic SMP mod_unload modversions 586 

```

uname -a returns:
```
Linux hawkeye 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686 GNU/Linux

```


Why do I get the invalid module format error? I don't know if it's revelant, but from my search, I've seen many threads mentionning this error. Can it be ubuntu related? More certainly, I'm doing something wrong, but what?

Anybody can help?


Thanks

Patrick

---

### Post by BotonInicio on 2010-11-17
Hola:

  Siento no escribir en ingles, pero es que no sé hacerlo bien y me resisto a utilizar los traductores automáticos.
  
  Quizá llego tarde a darte una posible solución pero a mí me funcionado y quizá otro la pueda aprovechar.

  Intenté poner el parametro -f en /etc/init.d/dahdi en las líneas donde pone "modprobe dahdi" y "modprobe dahdi_dummy" para que quedaran "modprobe -f dahdi" y "modprobe -f dahdi_dummy" y no me funcionó (hay a quien sí). Lo que sí me funcionó fue ejecutar esto "/var/lib/dpkg/info/dahdi-dkms.postinst configure", espero que a alguien le pueda servír.

Saludos.

---

### Post by netpro25 on 2010-12-01
This happens when you upgrade the kernel as it does not automatically recompile the dahdi modules. As the previous user stated running

```
/var/lib/dpkg/info/dahdi-dkms.postinst configure
```

fixes this problem as it recompiles the dahdi modules.

---

### Post by elperepat on 2010-12-02
I was not clear, but I did a fresh reinstall of 10.04 and did not installed 10.04 over 8.04.

So I installed a clean 10.04 version and then tried to compile the dahdi driver. This is what failed.

I will try that command anyway, but I doubt it'll work.

Thanks

Patrick

---

### Post by davemc on 2011-03-03
This solution worked for me on Lucid, thanks netpro25.  

Was a fully working Lucid system, did a routine upgrade to land on 2.6.32-28 and struck the above problem.

Takes a while to run through, with plenty of output.

At the end, this now works, no errors.
```

/etc/init.d/dahdi restart

lsmod | grep dah

```
is happy with all modules loaded.

DaveMc

---

### Post by wstephan on 2011-05-15
Thank's for this post, it saved me hours...

---

