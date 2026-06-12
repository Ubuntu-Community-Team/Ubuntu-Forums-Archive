---
title: "fan doesnt seem to wrok all the time and other things PLEASE HELP!!"
date: 2010-01-03
forum: Hardware
---

### Post by calis1981 on 2010-01-03
ok, i've got Ubuntu NBR 9.10 installed on a medion akoya mini e1210
its basicly a msi wind u100, i even flashed the bios to the msi brand v1.09
the fan does work but only at a low speed, and not very often, but my cpu still get very close to 70C so i have to sit next to my air-con so it starts below 60C, i've tryed a few different applets that are made for eee/netbooks and ive managed to get the fan running at a low speed, but the cpu hits around the 68-69C mark

and i've also got a crazy johns 3G modem, its a U6T9000, first it wouldnt detect it at all, so i installed ndiswrapper, installer the windows driver with that, and now it gets detected, i found a howto here, [http://whirlpool.net.au/wiki/?tag=linux_U6T](http://whirlpool.net.au/wiki/?tag=linux_U6T)
i followed it word for word(the ubuntu part is after the fedora part)
and still no go, it wont list the device in /dev/ttyUSB*, i have no listings in there at all, rite now i have to switch the sim card into my nokia phone to connect to the net, so i have to constantly charge the phone, heres the usb output when useing lsusb while it is mounted as a storage device

shane@shane-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 05c6:f000 Qualcomm, Inc. <-----modem
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 003: ID 5986:0141 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0421:002f Nokia Mobile Phones 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00d2 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
shane@shane-laptop:~$ 


here is output when device is unmounted
shane@shane-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 05c6:9000 Qualcomm, Inc.  <----modem
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 003: ID 5986:0141 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0421:002f Nokia Mobile Phones 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00d2 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
shane@shane-laptop:~$ 

here is the contents of my /dev dir
shane@shane-laptop:/dev$ ls
agpgart fuse mem ram11 rtc0 sndstat tty19 tty33 tty48 tty62 usbmon5  vcsa5
audio            hidraw0  mixer               ram12   sda         stderr   tty2   tty34  tty49  tty63    v4l      vcsa6
binder           hpet     net                 ram13   sda1        stdin    tty20  tty35  tty5   tty7     vcs      vcsa7
block            input    network_latency     ram14   sda2        stdout   tty21  tty36  tty50  tty8     vcs1     vcsa8
bus              kmsg     network_throughput  ram15   sda5        tty      tty22  tty37  tty51  tty9     vcs2     video0
char             log      null                ram2    sdb         tty0     tty23  tty38  tty52  ttyACM0  vcs3     zero
console          loop0    oldmem              ram3    sdc         tty1     tty24  tty39  tty53  ttyS0    vcs4
core             loop1    pktcdvd             ram4    sequencer   tty10    tty25  tty4   tty54  ttyS1    vcs5
cpu_dma_latency  loop2    port                ram5    sequencer2  tty11    tty26  tty40  tty55  ttyS2    vcs6
disk             loop3    ppp                 ram6    serial      tty12    tty27  tty41  tty56  ttyS3    vcs7
dri              loop4    psaux               ram7    sg0         tty13    tty28  tty42  tty57  urandom  vcs8
dsp              loop5    ptmx                ram8    sg1         tty14    tty29  tty43  tty58  usbmon0  vcsa
ecryptfs         loop6    pts                 ram9    sg2         tty15    tty3   tty44  tty59  usbmon1  vcsa1
fb0              loop7    ram0                random  shm         tty16    tty30  tty45  tty6   usbmon2  vcsa2
fd               mapper   ram1                rfkill  snapshot    tty17    tty31  tty46  tty60  usbmon3  vcsa3
full             mcelog   ram10               rtc     snd         tty18    tty32  tty47  tty61  usbmon4  vcsa4
shane@shane-laptop:/dev$ 

the network manager applet doesn't detect it there as well, wvdial doesnt detect it there
and i can install gnomeppp? it says that i need to remove resolvconf
is that important, or can i safly uninstall that without any other programs being effected?
im at a loss on how to correct this
im not quiet a linux noob, but im not an expert, im in the middle somewhere
start useing redhat9 on an old machine years ago, but im more into gaming so ive got a machine with xp for that
my netbook is my linux box, and im hoping to get at least these to problems solved
any help??
or do i need to post more info?

EDIT!!!
ok ive solved the modem problem!! i missed this bit of info here!!

------------------ Method 2
 **Stage One**
 Activate your phone number and pin.
 [https://secure.crazyjohns.com.au/ActiveWeb/activateprepaidservice](https://secure.crazyjohns.com.au/ActiveWeb/activateprepaidservice)
 Log in some time later to verify you have 100 Megs available.
 **Stage Two**
 Download and install wvdial....a dialler for Linux.
 After its installed replace the /etc/wvdial.conf with this one.....using root powers
 -----------------copy and paste between dashes-----------
[Dialer Defaults]
Init 1 = ATZ
Init 2 = ATQ0 V1 E1 +FCLASS=0
Init 3 = AT+CGDCONT=1,"IP","purtona.net"
 Modem Type = Analog Modem
Stupid Mode = 1
Phone =*99***1#
Dial Command = ATDT
ISDN = 0
Username = na
Password = na
Modem = /dev/ttyUSB3
Baud = 460800
 ------------------------------end------------------------
 **Stage Three**
 Create an udev rule for your usb modem
 Using root powers create this file /etc/udev/rules.d/60-persistent-u6t.rules
 ---------------------------------copy and paste between dashes------
 ACTION!="add", GOTO="U6T_End"
 SUBSYSTEMS=="usb", ACTION==”add”, ATTRS{idProduct}=="f000", GOTO="U6T_ZeroCD"
 SUBSYSTEMS=="usb", ACTION==”add”, ATTRS{idProduct}=="9000", GOTO="U6T_Modem"
 LABEL="U6T_ZeroCD"
RUN+="/usr/bin/eject /dev/sr1"
 LABEL="U6T_Modem"
RUN+="/sbin/modprobe usbserial vendor=0x05c6 product=0x9000", RUN+="/sbin/modprobe option", RUN+="/bin/echo "0x05c6 0x9000" > /sys/bus/usb-serial/drivers/option1/new_id"
 LABEL="U6T_End"
 ----------------------------------end---------------------------------------------------
 **Stage Four**
 As a normal user you should be a member of dialout groups. After creating the rule you can test it now by running as root
 sudo udevadm control --reload-rules
 Then insert modem.
 After about 10 seconds running lsusb should show the new product id changing from f000 to No entry to 9000.
Then when you run....ls /dev/ttyU*....you should have ttyUSB0 and 1 and 2 and 3.
 I use a terminal as a local user to issue one command.....wvdial....and dialler starts.
 When you dial and succeed...a new resolve.conf is created at /etc/ppp/ so there should be no need for you to replace any wired ethernet /etc/resolve.conf






from stage 3 down, all i had to do was eject the modem through the file manager and now there is a listing in /dev of ttyUSB0!!!!!


hope that info will help a few others out
still the fan is a problem

---

### Post by derekmbarnes on 2010-01-03
Seems everyone is having fan trouble right now - we're still working on the problem in this thread (hopefully we'll find a solution for everybody): 

[http://ubuntuforums.org/showthread.php?t=1282161](http://ubuntuforums.org/showthread.php?t=1282161)

---

### Post by calis1981 on 2010-01-04
thanks!!! ill check it out!

---

