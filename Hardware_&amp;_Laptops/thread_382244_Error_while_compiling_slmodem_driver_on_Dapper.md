---
title: "Error while compiling slmodem driver on Dapper"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by rizal on 2007-03-11
hello, 

just finish install ubuntu dapper including its build-essential package. i tried to compile the slmodem driver (Smart Link) from the modem vendor's CD for my PCI internal modem, but got the following error while run 'make': 

rizal@loki:~/modem-driver$ uname -r
2.6.15-23-386
rizal@loki:~/modem-driver$ gzip -dc slmodem-2.9.11.tar.gz | tar xf -
rizal@loki:~/modem-driver$ cd  slmodem-2.9.11-01Jun2005 
rizal@loki:~/modem-driver/slmodem-2.9.11-01Jun2005$ ls
Changes  COPYING  drivers  Makefile  modem  patches  README  scripts

rizal@loki:~/modem-driver/slmodem-2.9.11-01Jun2005**$ sudo make**
Password:
make -C modem all
make[1]: Entering directory `/home/goku/modem-driver/slmodem-2.9.11-01Jun2005/modem'
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem.o -c modem.c
modem.c: In function ‘modem_reset’:
modem.c:1701: error: invalid storage class for function ‘sregs_init’
modem.c:1713: warning: implicit declaration of function ‘sregs_init’
modem.c: At top level:
modem.c:1727: error: static declaration of ‘sregs_init’ follows non-static declaration
modem.c:1713: error: previous implicit declaration of ‘sregs_init’ was here
make[1]: *** [modem.o] Error 1
make[1]: Leaving directory `/home/goku/modem-driver/slmodem-2.9.11-01Jun2005/modem'
make: *** [modem] Error 2
rizal@loki~/modem-driver/slmodem-2.9.11-01Jun2005$


the kernel_dir in the Makefile is leaved unchanged as KERNEL_DIR:=/lib/modules/$(shell uname -r)/build 
i do have directory /lib/modules/2.6.15-23-386 like here: 

rizal@loki:/lib/modules/2.6.15-23-386$ ls
[COLOR="Blue"]initrd[/COLOR]      	   
[COLOR="Blue"]kernel[/COLOR]            
[COLOR="Blue"]madwifi[/COLOR]     	 
[COLOR="Blue"]madwifi-ng[/COLOR]              
[COLOR="Blue"]volatile[/COLOR]
modules.alias                   
modules.inputmap   	
modules.seriomap
modules.ccwmap       	    
modules.isapnpmap  	 
modules.symbols
modules.dep          	      
modules.ofmap          
modules.usbmap
modules.ieee1394map     
modules.pcimap
rizal@loki:/lib/modules/2.6.15-23-386$

Any clue guys? 
Thanks.

---

### Post by vespo on 2007-03-23
Hi

why would you compile it from scratch when sl-modem-daemon comes precompiled from debian repositories?

---

