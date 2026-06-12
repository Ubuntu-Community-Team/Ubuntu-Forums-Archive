---
title: "USR802981-OEM dial-up modem not detected in Ubuntu 10.04"
date: 2010-05-27
forum: Hardware
---

### Post by craigmc35 on 2010-05-27
Hello All,  Please can someone advise what steps  are necessary to get
the USR802981-OEM modem working. I have two of these which I plan on
using with Hylafax if they ever work.  At the moment the serial port
does not appear to have been created although the device is listed
when I run lspci.  I'm assuming they are compatible with Linux in some
way as this is what it says on USR website:-


 [http://www.usr.com/support/product-template.asp?prod=oem#2980](http://www.usr.com/support/product-template.asp?prod=oem#2980).


 Here is the lspci output:-
 root@swreuk-fax-gw-dt:/home/localadmin# lspci -vvv -s  04:00.0
04:00.0 Serial controller: U.S. Robotics Device 0152 (rev 02) (prog-if  02)
 Subsystem: Exar Corp. Device 0129
 Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr-  Stepping- SERR+ FastB2B- DisINTx-
 Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort-  <TAbort- <MAbort- >SERR- <PERR- INTx-
 Interrupt: pin A routed to IRQ 16
 Region 0: Memory at fe5ffc00 (32-bit, non-prefetchable) [size=1K]
 root@swreuk-fax-gw-dt:/home/localadmin#


 Here is the serserial output:-


 root@swreuk-fax-gw-dt:/home/localadmin# setserial -g  /dev/ttyS*
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3


 wvdialconfig does not detect the modem either:-


 root@swreuk-fax-gw-dt:/home/localadmin# wvdialconf
Editing `/etc/wvdial.conf'.
 Scanning your serial ports for a modem.
 ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600  baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200  baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3
 Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?
 Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)
 If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
root@swreuk-fax-gw-dt:/home/localadmin#


 Any help greatly appreciated.

---

### Post by dino99 on 2010-05-27
are modemmanager and pppoe pppoeconf hwinfo installed ?

---

### Post by craigmc35 on 2010-05-28
yes they are installed.

---

### Post by pwinkeler on 2011-03-11
You need to download the xr17c15x driver sources from the USR site and build the kernel module and load it into the runtime kernel (modprobe).  Note that you will also have to re-build your running kernel with the built-in EXAR support disabled as this enhanced module would otherwise conflict.

---

