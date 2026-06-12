---
title: "Serial Console Adapter - Terminal problem"
date: 2018-05-02
forum: Hardware
---

### Post by Gideo000 on 2018-05-02
Hello everyone.

    I've just upgraded my Laptop and installed Ubuntu 18.04 on it. There is a problem with Serial Console adaptors: The OS recognises the device but won't display content from devices it is attached to on a Terminal, from which minicom or other console application is run.

dmesg  excerpt:

[ 4353.581639] usb 2-1: new full-speed USB device number 11 using xhci_hcd
[ 4353.730512] usb 2-1: New USB device found, idVendor=067b, idProduct=2303
[ 4353.730519] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 4353.730524] usb 2-1: Product: USB-Serial Controller
[ 4353.730528] usb 2-1: Manufacturer: Prolific Technology Inc.
[ 4353.731345] pl2303 2-1:1.0: pl2303 converter detected
[ 4353.732079] usb 2-1: pl2303 converter now attached to ttyUSB0

I tried several times to connect to a couple of Cisco switches and would not work.

A -    Serial Device      : /dev/ttyUSB0                              
    | B - Lockfile Location     : /var/lock                                 
    | C -   Callin Program      :                                           
    | D -  Callout Program      :                                           
    | E -    Bps/Par/Bits       : 9600 8N1                                  
    | F - Hardware Flow Control : Yes                                       
    | G - Software Flow Control : No                                        
                                                                      
        


I've tried with other apps too: screen, putty, and picocom. Same problem. Also, the adaptor was replaced by another one. Last test, run on a different laptop which was also upgraded to Ubuntu 18.04. Same issue.

If anybody knows the reason and the fix, well, I'll really appreciate it.

Thank you very much.

Bests!

---

### Post by ilpiero on 2018-05-04
Hello, all that I see looks OK....
When we check serial ports at work we do the following: set flow control to none (you have set hardware now) and with a small peace of metal touch both pins 2 and 3 of the db9 connector.
When you send data with the serial port it will be looped back to you.
Another thing I remember about the serial ports was that the user is supposed to be in the dialout group, otherwise it requires admin privileges. 

Not sure whether this is useful for you.... just my two cents  ;)

Marco

---

### Post by Gideo000 on 2018-05-04
Thanks Marco for helping me. I really appreciate it. Finally, I've got another adapter and another console cable and worked. There was sth faulty with the previous ones. :confused:

Bests!

---

