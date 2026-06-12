---
title: "RFID Reader from"
date: 2009-11-20
forum: Hardware
---

### Post by FMaz008 on 2009-11-20
Hi there !

I just received this unit from CNCGeeker, and maybe it might interest some of you... and maybe also myself :p :
[http://www.cncgeeker.com/index.php?main_page=product_info&cPath=10&products_id=31](http://www.cncgeeker.com/index.php?main_page=product_info&cPath=10&products_id=31)

At first I was pretty entousiast, I simply plugged a USB Cable, then I looked at the info to see if the device was plugged & recognized correctly:

```

laptop:~$ dmesg | tail -n 5
[12610.096136] usb 5-1: new full speed USB device using uhci_hcd and address 5
[12610.258343] usb 5-1: configuration #1 chosen from 1 choice
[12610.264375] cp210x 5-1:1.0: cp210x converter detected
[12610.376107] usb 5-1: reset full speed USB device using uhci_hcd and address 5
[12610.524332] usb 5-1: cp210x converter now attached to ttyUSB0
laptop:~$
laptop:~$ lsusb | grep 210x
Bus 005 Device 005: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x Composite Device
laptop:~$ 


```

So everything seemed ok, now time to test:
```

laptop:~$ cat /dev/ttyUSB0 | xxd
0000000: 3031 4e30 314e 3031 4e30 314e 3031 4e38  01N01N01N01N01N8
0000010: 3054 3031 4e30 314e 3031 4e30 314e 3031  0T01N01N01N01N01
0000020: 4e30 314e 3031 4e30 314e 3031 4e30 314e  N01N01N01N01N01N
0000030: 3031 4e30 314e 3031 4e30 314e 3031 4e30  01N01N01N01N01N0
0000040: 314e 3830 5438 3054 3031 4e38 3054 3031  1N80T80T01N80T01
0000050: 4e38 3054 3031 4e38 3054 3031 4e38 3054  N80T01N80T01N80T
0000060: 3031 4e38 3054 3031 4e38 3054 3031 4e38  01N80T01N80T01N8
0000070: 3054 3031 4e38 3054 3031 4e38 3054 3031  0T01N80T01N80T01
0000080: 4e38 3054 3031 4e38 3054 3031 4e38 3054  N80T01N80T01N80T
0000090: 3031 4e38 3054 3031 4e38 3054 3031 4e38  01N80T01N80T01N8
00000a0: 3054 3031 4e38 3054 3031 4e30 314e 3031  0T01N80T01N01N01
00000b0: 4e30 314e 3031 4e30 314e 3031 4e30 314e  N01N01N01N01N01N
00000c0: 3031 4e30 314e 3031 4e30 314e 3031 4e30  01N01N01N01N01N0
00000d0: 314e 3031 4e30 314e 3830 5430 314e 3031  1N01N01N80T01N01
^C
laptop:~$

```

Note that I'm reading nothing for the moment. the device seem to output a bunch of data (maybe it's scaning to find any tags ?)

Anyway, with this amount of data, I can't extract any data as easilly as it should. All the data you seem have been collected in less than 0.5 sec.

I've tried the GUI RFdump, but the software doesn't support this specific circuit, even if I put in the correct settings:
(They are:
Baudrate: 115200 bit/s
Data bits: 8
Parity: None
Stop bits: 1
)

I also contact Adam, from RFIDIOt, and he replied:
> 
Hi,

It looks like it's a serial device using it's own protocol. To get it to work with RFIDIOt, we'd need to know the API/protocol definitions as it's not sending data that looks like anything I've already implemented.

cheers,
Adam


So I don't really know what to do to be able to display only what the reader really read. (the tags content)

Any hint would be greatly appreciated !

---

