---
title: "How to send data  serial port"
date: 2008-10-25
forum: General Help
---

### Post by InvisibleMind on 2008-10-25
I have ubuntu 7.10 and have a machine that communcate with serial port (not a modem).
I want to send some data to serial port for test a machine 
Could you please help me? to send a data
I'm try to using with C language 

#include<stdio.h>
main()
{
 FILE *fp;
 fp = fopen("/dev/ttys0","wb");
   fprintf(fp,"T");
 fclose(fp);
 
}

and not work

---

### Post by The Cog on 2008-10-25
You may have to configure the port for the right speed/parity etc.
**stty -F /dev/ttyS0 -a**
will show the current settings.

Oh, and it's probably a capital S, ttyS0 not ttys0.

---

