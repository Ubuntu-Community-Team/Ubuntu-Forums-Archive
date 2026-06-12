---
title: "ASUS A6000 keyboard behaving strangely"
date: 2009-11-17
forum: Hardware
---

### Post by urs_kemmann on 2009-11-17
[SIZE=2]Hi all,[/SIZE]
 

 [SIZE=2]to be honest I would be suprised if anyone can help me with this, but I would definitely be very, very thankful. I want to apologize in advance as the descriction of the problem is a bit lenghty.[/SIZE]
 

 [SIZE=2]It all started when I still had Windows XP installed on my ASUS A6000 laptop. Suddenly the start menu kept opening and closing, as if the windows key was stuck.  I removed and checked the keyboard, attached an external keyboard, and reinstalled Windows - but the problem persisted.[/SIZE]
 

 [SIZE=2]I tryed to be a smart *** and installed Ubuntu 9.10 in order to circumvent problems related to the windows key. Everything went very well and I was quite happy having finally switched to Linux with my own laptop - until the following problem occured (and I'm not sure this is related to what I described in the second paragraph):[/SIZE]
 

 [SIZE=2]Sometimes my keyboard stops working in certain contexts. For example, right now it has happend. I can still type perfectly in OpenOffice Writer and copy the result into the text area of this porsting. But if I change to Firefox or any Ubuntu dialogue box I cannot type text into any of the input fields. But, as I said, this is only present in certain contexts. For example, the shell and OpenOffice Writer   always working fine, I can type whatever I want. After a restart the problem is gone. For some time.[/SIZE]
 

 [SIZE=2]lshw gives me the following:
[/SIZE]```
urs-laptop
    description: Notebook
    product: A6Km
    vendor: ASUSTeK Computer Inc.
    version: 1.0
    serial: SSN12345678901234567
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=notebook uuid=FD000000-1500-0080-BF5A-5FFEFFFCFBBD
  *-core
       description: Motherboard
       product: A6Km
       vendor: ASUSTeK Computer Inc.
       physical id: 0
       version: 1.0
       serial: BSN12345678901234567
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 209 (03/20/2006)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu

```[SIZE=2]
[/SIZE]
[SIZE=2]The only idea I have is a BIOS update. But I have never done that before and I'm a bit worried this might mess up the existing configurations (it took me a while to get my Broadcom WLAN adapter to work).[/SIZE]
 

 [SIZE=2]Thanks in advance for any input or ideas,[/SIZE]
 

 [SIZE=2]Urs[/SIZE]

---

