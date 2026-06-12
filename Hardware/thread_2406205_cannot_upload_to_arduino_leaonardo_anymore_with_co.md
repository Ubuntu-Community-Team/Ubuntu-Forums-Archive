---
title: "cannot upload to arduino leaonardo anymore with cosmic"
date: 2018-11-17
forum: Hardware
---

### Post by eallaud-gmail on 2018-11-17
Hi all,
odd issue and I would like to know if I am the only one with  this. I have been uploading sketches with arduino 1.8.6 on my linux box  (ubuntu 16.xx,17.xx and 18.04) with no problem (uno, mega and leonardo).
Now since I upgraded to ubuntu 18.10 no joy for leonardo anymore! I am still able to upload to Uno and Mega though.
I did not change the arduino toolchain at all, only the rest ;-) was upgraded. I suspect a problem with the new CDC driver.
In any case this is the log:

avrdude: Version 6.3-20171130
         Copyright (c) 2000-2005 Brian Dean, [http://www.bdmicro.com/](http://www.bdmicro.com/)
         Copyright (c) 2007-2014 Joerg Wunsch

          System wide configuration file is  "/home/emmanuel/.arduino15/packages/arduino/tools/avrdude/6.3.0-arduino14/etc/avrdude.conf"
         User configuration file is "/home/emmanuel/.avrduderc"
         User configuration file does not exist or is not a regular file, skipping

         Using Port                    : /dev/ttyACM1
         Using Programmer              : avr109
         Overriding Baud Rate          : 57600
         AVR Part                      : ATmega32U4
         Chip Erase delay              : 9000 us
         PAGEL                         : PD7
         BS2                           : PA0
         RESET disposition             : dedicated
         RETRY pulse                   : SCK
         serial program mode           : yes
         parallel program mode         : yes
         Timeout                       : 200
         StabDelay                     : 100
         CmdexeDelay                   : 25
         SyncLoops                     : 32
         ByteDelay                     : 0
         PollIndex                     : 3
         PollValue                     : 0x53
         Memory Detail                 :

                                  Block Poll               Page                       Polled
           Memory Type Mode Delay Size  Indx Paged  Size   Size #Pages MinW  MaxW   ReadBack
           ----------- ---- ----- ----- ---- ------ ------ ---- ------ ----- ----- ---------
           eeprom        65    20     4    0 no       1024    4      0  9000  9000 0x00 0x00
           flash         65     6   128    0 yes     32768  128    256  4500  4500 0x00 0x00
           lfuse          0     0     0    0 no          1    0      0  9000  9000 0x00 0x00
           hfuse          0     0     0    0 no          1    0      0  9000  9000 0x00 0x00
           efuse          0     0     0    0 no          1    0      0  9000  9000 0x00 0x00
           lock           0     0     0    0 no          1    0      0  9000  9000 0x00 0x00
           calibration    0     0     0    0 no          1    0      0     0     0 0x00 0x00
           signature      0     0     0    0 no          3    0      0     0     0 0x00 0x00

         Programmer Type : butterfly
         Description     : Atmel AppNote AVR109 Boot Loader

Connecting to programmer: .
Found programmer: Id = "CATERIN"; type = S
    Software Version = 1.0; No Hardware Version given.
Programmer supports auto addr increment.
Programmer supports buffered memory access with buffersize=128 bytes.

Programmer supports the following devices:
    Device code: 0x44

avrdude: devcode selected: 0x44
avrdude: AVR device initialized and ready to accept instructions

Reading | ################################################## | 100% 0.00s

avrdude: Device signature = 0x1e9587 (probably m32u4)
avrdude: reading input file "/tmp/arduino_build_164818/RR-duino.ino.hex"
avrdude: writing flash (18572 bytes):

Writing | avrdude: butterfly_recv(): programmer is not responding
avrdude: error: programmer did not respond to command: write block
 ***failed;  
 ***failed;

repeated a lot and then several:

avrdude: Error: butterfly programmer uses avr_write_page() but does not
provide a cmd() method.
 *** page 127 (addresses 0x0000 - 0x007f) failed to write

with different page numbers

BTW  I can still upload sketches to my leonardo on another linux box, but  first I have to reflash the bootloader (that I can do on the problematic  linux box via a tinyUSB !!)
Anyone could help pls?
TIA
Manu

---

### Post by mvalenti on 2018-12-19
I'm watching this one. I went from beaver to cosmic and neither one worked especially well. My application is trying to update firmware on my 3d printer with a mega board... Took me a bit just to get printer working, usb permissions....

---

