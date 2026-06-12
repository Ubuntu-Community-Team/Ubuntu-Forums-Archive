---
title: "Problems with serial port drivers"
date: 2009-10-13
forum: Hardware
---

### Post by jarmok on 2009-10-13
Hi, I'm trying to install drivers for a Moxa CA-108 serial multiport board, and when executing "make" i get the following errors:


```

/home/molinos/mxpcdrv/driver/mxpcdrv.c:474: aviso: inicialización desde un tipo de puntero incompatible
/home/molinos/mxpcdrv/driver/mxpcdrv.c: En la función &#8216;mxpcdrv_initbrd&#8217;:
/home/molinos/mxpcdrv/driver/mxpcdrv.c:662: error: &#8216;SA_SHIRQ&#8217; no se declaró aquí (primer uso en esta función)
/home/molinos/mxpcdrv/driver/mxpcdrv.c:662: error: (Cada identificador no declarado solamente se reporta una vez
/home/molinos/mxpcdrv/driver/mxpcdrv.c:662: error: para cada funcion en la que aparece.)
/home/molinos/mxpcdrv/driver/mxpcdrv.c:662: error: &#8216;SA_INTERRUPT&#8217; no se declaró aquí (primer uso en esta función)
/home/molinos/mxpcdrv/driver/mxpcdrv.c: En la función &#8216;mxpcdrv_init&#8217;:
/home/molinos/mxpcdrv/driver/mxpcdrv.c:717: error: &#8216;struct tty_driver&#8217; no tiene un miembro llamado &#8216;open&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c:718: error: &#8216;struct tty_driver&#8217; no tiene un miembro llamado &#8216;close&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c:719: error: &#8216;struct tty_driver&#8217; no tiene un miembro llammake[2]: se sale del directorio `/usr/src/linux-headers-2.6.28-11-server'
make[1]: se sale del directorio `/home/molinos/mxpcdrv/driver'
me/molinos/mxpcdrv/driver/mxpcdrv.c:721: error: &#8216;struct tty_driver&#8217; no tiene un miembro llamado &#8216;flush_chars&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c:722: error: &#8216;struct tty_driver&#8217; no tiene un miembro llamado &#8216;write_room&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c:723: error: &#8216;struct tty_driver&#8217; no tiene un miembro llamado &#8216;chars_in_buffer&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c:724: error: &#8216;struct tty_driver&#8217; no tiene un miembro llamado &#8216;flush_buffer&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c:725: error: &#8216;struct tty_driver&#8217; no tiene un miembro llamado &#8216;ioctl&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c:726: error: &#8216;struct tty_driver&#8217; no tiene un miembro llamado &#8216;throttle&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c:727: error: &#8216;struct tty_driver&#8217; no tiene un miembro llamado &#8216;unthrottle&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c:728: error: &#8216;struct tty_driver&#8217; no tiene un miembro llamado &#8216;set_termios&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c:729: error: &#8216;struct tty_driver&#8217; no tiene un miembro llamado &#8216;stop&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c:730: error: &#8216;struct tty_driver&#8217; no tiene un miembro llamado &#8216;start&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c:731: error: &#8216;struct tty_driver&#8217; no tiene un miembro llamado &#8216;hangup&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c:734: error: &#8216;struct tty_driver&#8217; no tiene un miembro llamado &#8216;wait_until_sent&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c: En la función &#8216;mxpcdrv_open&#8217;:
/home/molinos/mxpcdrv/driver/mxpcdrv.c:977: error: declaración implícita de la función &#8216;process_session&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c:978: error: declaración implícita de la función &#8216;process_group&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c: En la función &#8216;mxpcdrv_close&#8217;:
/home/molinos/mxpcdrv/driver/mxpcdrv.c:1107: error: &#8216;struct tty_driver&#8217; no tiene un miembro llamado &#8216;flush_buffer&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c:1108: error: &#8216;struct tty_driver&#8217; no tiene un miembro llamado &#8216;flush_buffer&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c:1116: error: &#8216;struct tty_ldisc&#8217; no tiene un miembro llamado &#8216;flush_buffer&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c:1117: error: &#8216;struct tty_ldisc&#8217; no tiene un miembro llamado &#8216;flush_buffer&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c: En la función &#8216;mxpcdrv_flush_buffer&#8217;:
/home/molinos/mxpcdrv/driver/mxpcdrv.c:1297: error: &#8216;struct tty_ldisc&#8217; no tiene un miembro llamado &#8216;write_wakeup&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c:1298: error: &#8216;struct tty_ldisc&#8217; no tiene un miembro llamado &#8216;write_wakeup&#8217;
/home/molinos/mxpcdrv/driver/mxpcdrv.c: En la función &#8216;mxpcdrv_receive_chars&#8217;:
/home/molinos/mxpcdrv/driver/mxpcdrv.c:1988: error: &#8216;TTY_FLIPBUF_SIZE&#8217; no se declaró aquí (primer uso en esta función)
make[3]: *** [/home/molinos/mxpcdrv/driver/mxpcdrv.o] Error 1
make[2]: *** [_module_/home/molinos/mxpcdrv/driver] Error 2
make[1]: *** [module] Error 2
make: *** [mxser] Error 2


```

Any idea about what's going on?
I use kernel 2.6.28-11-server.

---

