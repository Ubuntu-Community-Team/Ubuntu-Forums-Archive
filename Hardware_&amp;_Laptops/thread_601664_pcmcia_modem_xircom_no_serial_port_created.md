---
title: "pcmcia modem xircom no serial port created"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by jorgericarte on 2007-11-03
Hi,

I am trying to use a modem Xircom CreditCard 56T (CM56T)  on a Toshiba A7-SP4032. I run ubuntu Gutsy with a kernel  2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12

When I insert the card, dmesg shows:

Nov  3 10:49:02 jrlt kernel: [ 4012.712000] pccard: card ejected from slot 0
Nov  3 10:55:02 jrlt kernel: [ 4372.816000] pccard: PCMCIA card inserted into slot 0
Nov  3 10:55:02 jrlt kernel: [ 4372.816000] pcmcia: registering new device pcmcia0.0

I tried with and without "pci=assign-busses" option to kernel. Same result.

Did I miss something?

tanks

lspcmcia -vvv
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:05:06.0)
        Configuration:  state: on       ready: yes
                        Voltage: 5.0V Vcc: 5.0V Vpp: 0.0V
                        Available IRQs: 3, 4, 6, 7, 10, 11
                        Available ioports:      0x00000100 - 0x000003af
                                                0x000003e0 - 0x000003ff
                                                0x00000408 - 0x000004cf
                                                0x000004d8 - 0x000004ff
                                                0x00000820 - 0x000008ff
                                                0x00000a00 - 0x00000aff
                                                0x00000c00 - 0x00000cf7
                                                0x00006000 - 0x00006fff
                        Available iomem:        0x000c0000 - 0x000fffff
                                                0x60000000 - 0x60ffffff
                                                0xa0000000 - 0xa0ffffff
                                                0xde010000 - 0xde0fffff
Socket 0 Device 0:      [serial_cs]             (bus ID: 0.0)
        Configuration:  state: on
        Product Name:   Xircom CreditCard Modem CM-56T CM-56T 1.00 
        Identification: manf_id: 0x0105 card_id: 0x100a
                        function: 2 (serial)
                        prod_id(1): "Xircom" (0x2e3ee845)
                        prod_id(2): "CreditCard Modem CM-56T" (0xc493287e)
                        prod_id(3): "CM-56T" (0xbc4db03a)
                        prod_id(4): "1.00" (0x83dbf271)

 wvdialconf /etc/wvdial.conf 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

---

