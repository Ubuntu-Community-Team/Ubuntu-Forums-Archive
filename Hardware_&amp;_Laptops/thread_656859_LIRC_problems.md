---
title: "LIRC problems"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by dummkauf on 2008-01-03
Ok, I have been in the process of building a mythbuntu box over the last couple days, and so far I have everything working except my remote control, which I believe is an issue with LIRC that I can't figure out.  I have been googling this issue for quite a while and have yet to find a working solution, so I am hoping that someone here will have some idea what is going on, or can point me in the right direction.

I am running the latest x64 release of mythbuntu 
kernel: 2.6.22-14-generic

I purchased an nMediaPC case, which so far is great and I am attempting to get the internal IR receiver that came with it working, and from what I've read online so far I believe this hardware is supported by LIRC.  This receiver is connected internally via USB

From my googling I believe that this hardware should be using the lirc_mceusb2 module which is loaded.

> 
$ lsmod | grep lirc
lirc_mceusb2      16900  0 
lirc_dev               18248  1 lirc_mceusb2
usbcore            161584  8 lirc_mceusb2,xpad,usb_storage,usbhid,libusual,ehci_hcd,ohci_hcd


Here is my lircd.conf file(Note: I tried changing "name mceusb" to "name mceusb2" and it made no difference)
> 
$ cat lircd.conf
#
# RC-6 config file
#
# source: [http://home.hccnet.nl/m.majoor/projects__remote_control.htm](http://home.hccnet.nl/m.majoor/projects__remote_control.htm)
#         [http://home.hccnet.nl/m.majoor/pronto.pdf](http://home.hccnet.nl/m.majoor/pronto.pdf)
#
# used by: Philips
#
#########
#
# Philips Media Center Edition remote control
# For use with the USB MCE ir receiver
#
# Dan Conti  dconti|acm.wwu.edu
#
# Updated with codes for MCE 2005 Remote additional buttons
# *, #, Teletext, Red, Green, Yellow & Blue Buttons
# Note: TV power button transmits no code until programmed.
# Updated 12th September 2005
# Graham Auld - mce|graham.auld.me.uk
#
# Radio, Print, RecTV are only available on the HP Media Center remote control
#

begin remote

  name mceusb
  bits           16
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2667   889
  one           444   444
  zero          444   444
  pre_data_bits 21
  pre_data      0x37FF0
  gap          105000
  toggle_bit     22
  rc6_mask     0x100000000


      begin codes

        Blue    0x00007ba1
        Yellow  0x00007ba2
        Green   0x00007ba3
        Red     0x00007ba4
        Teletext        0x00007ba5

# starts at af
        Radio    0x00007baf
        Print    0x00007bb1
        Videos   0x00007bb5
        Pictures 0x00007bb6
        RecTV    0x00007bb7
        Music    0x00007bb8
        TV       0x00007bb9
# no ba - d8

        Guide    0x00007bd9
        LiveTV   0x00007bda
        DVD      0x00007bdb
        Back     0x00007bdc
        OK       0x00007bdd
        Right    0x00007bde
        Left     0x00007bdf
        Down     0x00007be0
        Up       0x00007be1

        Star       0x00007be2
        Hash       0x00007be3

        Replay   0x00007be4
        Skip     0x00007be5
        Stop     0x00007be6
        Pause    0x00007be7
        Record   0x00007be8
        Play     0x00007be9
        Rewind   0x00007bea
        Forward  0x00007beb
        ChanDown 0x00007bec
        ChanUp   0x00007bed
        VolDown  0x00007bee
        VolUp    0x00007bef
        More     0x00007bf0
        Mute     0x00007bf1
        Home     0x00007bf2
        Power    0x00007bf3
        Enter    0x00007bf4
        Clear    0x00007bf5
        Nine     0x00007bf6
        Eight    0x00007bf7
        Seven    0x00007bf8
        Six      0x00007bf9
        Five     0x00007bfa
        Four     0x00007bfb
        Three    0x00007bfc
        Two      0x00007bfd
        One      0x00007bfe
        Zero     0x00007bff
      end codes

end remote


When I look in the /dev directory there is no 'lirc' or 'lirc0' or anything similar listed.  The only thing in the dev folder is 'lircd' which is apparently an LIRC socket.

If I attempt to test the IR receiver with the irw command this is what I get
> 
$ irw
connect: Connection refused


However if I start the lircd daemon it doesn't give me the error when I run 'irw' immediatley afterwards, it just drops to a new line.  However the second time I run 'irw' I get the connection refused error again.  'irw' seems to kill the lircd daemon for some reason
> 
$ sudo /etc/init.d/lirc start
Starting lirc daemon: lircd.
$ irw
$
$irw
connect: Connection refused


here is the relevant output of 'cat /proc/bus/usb/devices'
> 
$ cat /proc/bus/usb/devices

T:  Bus=01 Lev=01 Prnt=01 Port=08 Cnt=03 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=1784 ProdID=0007 Rev= 1.00
S:  Manufacturer=Topseed Technology Corp.
S:  Product=eHome Infrared Transceiver
S:  SerialNumber=TS0000By
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=03(Int.) MxPS=  32 Ivl=32ms
E:  Ad=82(I) Atr=03(Int.) MxPS=  32 Ivl=32ms


here is the output of lsusb
> 
$ lsusb
Bus 002 Device 005: ID 058f:6362 Alcor Micro Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 046d:c714 Logitech, Inc. 
Bus 001 Device 005: ID 046d:c713 Logitech, Inc. 
Bus 001 Device 003: ID 06a3:040c Saitek PLC 
Bus 001 Device 004: ID 1784:0007  
Bus 001 Device 002: ID 046d:0b04 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 


Not sure if this is relevant or not but here's the lspci output
> 
$ lspci
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
04:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)


I've already downloaded the kernel source and header files and am about to try compiling LIRC from source, but I am hoping there is a way to make this work without running custom versions of the application.  I would prefer to use the LIRC package from the Ubuntu repositories.

If anyone has any advice, tips, or even working solution I would greatly appreciate the help.  Also, I have been working on this for the past couple of hours, and I believe I included all the relevant information, however if I missed something let me know and I will get it posted asap

Thanks in advance for your help! :-)

---

### Post by olensan on 2008-01-03
I have the same nmediapc case with IR transceiver.

After digging around for the last couple days, I found out that exact hardware is currently not supported. At least for the hardware ID '0007'

> Bus 001 Device 004: ID 1784:0007 

1784 is Topseed's USB ID, and 0007 is the hardware ID.

Currently, 0001 and 0006 for Topseed are in the lirc_mceusb2.c.
I am not too certain but it could be that 0007 is just the same hardware as 0006, and 0007 being OEM and 0006 retail.

I have not try this yet, but maybe you can try to copy the 0006 line in the lirc_mceusb2.c and change it to 0007 and re-compile the driver, and let us know how it goes. :)

---

### Post by olensan on 2008-01-03
Looks like that id is already in current CVS tree.

> 	{ USB_DEVICE(VENDOR_TOPSEED, 0x0001) },
	/* Topseed HP eHome Infrared Transceiver */
	{ USB_DEVICE(VENDOR_TOPSEED, 0x0006) },
	/* Topseed eHome Infrared Transceiver */
	{ USB_DEVICE(VENDOR_TOPSEED, 0x0007) },
	/* Topseed eHome Infrared Transceiver */
	{ USB_DEVICE(VENDOR_TOPSEED, 0x0008 ) },


---

### Post by anand on 2008-01-16
I recompiled LIRC and added the line to add 0x0007 into lirc_mceusb2.c and the remote works like a charm!

I basically followed the steps from here:
[http://www.mythtv.org/wiki/index.php/Ubuntu_lirc_install](http://www.mythtv.org/wiki/index.php/Ubuntu_lirc_install)

Except after the 1st step of getting lirc-modules-source, I unpacked the tar.gz file, made the change to lirc_mceusb2.c, and then repacked the file ovewriting the original.  I then followed the rest of the process.

---

### Post by dolgue on 2008-01-19
Hello Anand, I was wondering if you could describe exactly how you were able to get your remote to work.  Did you just extract the lirc-modules.tar.gz file located in /usr/src/ and then modify the lirc_mceusb2.c file with the added line for the 0x0007 and then follow the rest of the procedures?  That is what I tried and for some reason it keeps installing the same lirc_mceusb2 module without the 0x0007 support.  

If you could point me in the right direction I would appreciate it.  I would really like to use the nmedia receiver including in my case.  Thanks a bunch.

Sincerely,

Stephen

---

