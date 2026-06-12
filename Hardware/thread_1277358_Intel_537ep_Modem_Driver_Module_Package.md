---
title: "Intel 537ep Modem Driver Module Package"
date: 2009-09-28
forum: Hardware
---

### Post by Steve Francis on 2009-09-28
My p.c. can dual boot into Windows XP and Ubuntu 9.04

In Windows XP, I have an Intel 537EP fax modem installed and operating on COM3.

I am having a frustrating time trying to get the same modem up and running in Ubuntu.

I have run scanModem, which reports

> For candidate card in slot 03:01.0, firmware information and bootup diagnostics are:
 PCI slot    PCI ID        SubsystemID    Name
 ----------    ---------    ---------    --------------
 03:01.0    8086:1080    8086:1000    Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI 

 Modem interrupt assignment and sharing: 
 17:       2974          0   IO-APIC-fasteoi   Intel ICH5, serial
 --- Bootup diagnostics for card in PCI slot 03:01.0 ----
[    0.455494] pci 0000:03:01.0: reg 10 32bit mmio: [0xfeaff000-0xfeafffff]
[    0.455501] pci 0000:03:01.0: reg 14 io port: [0xbc00-0xbcff]
[    0.455536] pci 0000:03:01.0: PME# supported from D0 D3hot D3cold
[    0.455541] pci 0000:03:01.0: PME# disabled
[    1.505776] serial 0000:03:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.505908] 0000:03:01.0: ttyS1 at I/O 0xbc08 (irq = 17) is a 16450
[    1.505989] 0000:03:01.0: ttyS2 at I/O 0xbc10 (irq = 17) is a 8250
[    1.506071] 0000:03:01.0: ttyS3 at I/O 0xbc18 (irq = 17) is a 16450
[    1.506096] Couldn't register serial port 0000:03:01.0: -28

 The PCI slot 03:01.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [EMAIL="discuss@linmodems.org"]discuss@linmodems.org[/EMAIL]
 if help is needed.
 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 03:01.0:
    Modem chipset  detected on
NAME="Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI "
CLASS=0703
PCIDEV=8086:1080
SUBSYS=8086:1000
IRQ=17
IDENT=INTEL537EP

 For candidate modem in:  03:01.0
   0703 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI 
      Primary device ID:  8086:1080
 Support type needed or chipset:    INTEL537EP
 I downloaded the Jaunty driver from
                                 [http://groups.google.com/group/ubuntu-modems/web/modem-driver-downloads-for-537ep](http://groups.google.com/group/ubuntu-modems/web/modem-driver-downloads-for-537ep)


However, when I install this the driver the installation process does not seem to terminate. The following message is visible in terminal:

> FATAL: Module Intel537 not found.
insmod: can't read 'Intel537': No such file or directory
error loading Intel537
ERROR: Module Intel537 does not exist in /proc/modulesHowever, the success.txt file states that the modem driver should be installed correctly.


After installation the following file is present:
/lib/modules/Intel537DriverForJaunty.ko


However, neither GnomePPP nor wvdial report that a modem is present when I test for one.
> Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?
What am I doing wrong?

---

### Post by Steve Francis on 2009-09-28
Some progress...

If I edit my wvdial.conf file as shown below then I _***can***_ get the modem to dial out:

[Dialer Defaults]
Modem = /dev/537
Baud = 9600
Init1 = ATZ
Init2 = AT&F&D2&C1&K3S7=55
Init3 = AT&K3
Phone = 08450792829
Username = Steve    
Password = ********
# New PPPD = yes

Terminal responds with
> $ wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F&D2&C1&K3S7=55
AT&F&D2&C1&K3S7=55
OK
--> Sending: AT&K3
AT&K3
OK
--> Modem initialized.
--> Sending: ATDT08450792829
--> Waiting for carrier.
ATDT08450792829But if I run wvtest, I get
> $ sudo wvdialconf wvtest
Editing `wvtest'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?Also, when I run Gnome PPP the init strings are different from those in wvdial.conf and the modem can't be found.

Very frustrating.

---

### Post by Steve Francis on 2009-09-29
I haven't been able to solve the problem.

It seems that neither wvtest nor Gnome PPP will recognise /dev/537.

I did, however, manage to get Efax-gtk working with the modem by using the following settings:

  	 	 	 	 	 	  IDENTITY
 CSID name and number as necessary

MODEM
 Serial Device: 537
 Lock file: /var/lock
 Capabilities: 1,5,0,2,0,0,0,0
 Rings: 2
 Modem Class: Class 2
 Dial Mode: Tone

PARAMS
Initialisation Params: Z &F&D2&C1&K3S7 &K3
 Reset Params: Z
 Other Params:
 
PRINT
Leave as default
 
VIEW
Leave as default
 
SOCKET
 Leave as default

RECEIVE
Leave as default
 
SEND
Leave as default
 
LOGGING
Log file: /home/steve/efax.log
 
PAGE
 Page Size: A4

---

### Post by GeorgeVita on 2009-09-29
> **Steve Francis said:**
> ...If I edit my wvdial.conf file as shown below then I _***can***_ get the modem to dial out:

[Dialer Defaults]
Modem = **[SIZE="3"]/dev/537[/SIZE]**
Baud = 9600
Init1 = ATZ
Init2 = AT&F&D2&C1&K3S7=55
Init3 = AT&K3
Phone = 08450792829
Username = Steve    
Password = ********
# New PPPD = yes

Hi **Steve Francis**,
your modem for some reason (possibly the driver) assigned as **/dev/537** which is a 'strange' valid name. Usually the 'default' modem for **wvdial** or **gnome-ppp** is /dev/modem or /dev/ttyS0,1,2,3.

Default configuration file for **wvdial** is **wvdial.conf**

In your example you create the configuration file **wvtest** which can be used with: **wvdial wvtest**

To work with your modem connected/named as **/dev/537** you must edit appropriate field into **gnome-ppp** (see attachment) or use 'modem = /dev/537' line into wvdial configuration file (as you did it). A higher baud rate must work (57600, 115200).

**wvdialconf** searches 'typical' serial communication ports to find the modem. An 'alias' between /dev/537 and /dev/modem could work (I do not know how to make it).

Regards,
George

---

### Post by Steve Francis on 2009-10-01
> To work with your modem connected/named as **/dev/537** you must edit appropriate field into **gnome-ppp** (see attachment)Thanks, George. I tried this but unfortunately Gnome-PPP cannot find the modem when I click on 'Detect'

I had the following init strings...
Init2 AT&F1E0Q0V1&C1&D2S0=0 (the Gnome PPP default. I can't delete this)
Init3 ATZ
Init4 AT&F&D2&C1&K3S7
Init5 AT&K3

In Windows, my modem is detected on COM3. I can't understand why there is nothing detected on /dev/ttyS2

---

### Post by GeorgeVita on 2009-10-02
> **Steve Francis said:**
> I tried this but unfortunately Gnome-PPP cannot find the modem when I click on 'Detect'
...
In Windows, my modem is detected on COM3. I can't understand why there is nothing detected on /dev/ttyS2

Hi **Steve Francis**, as I know /dev/ttyS0-3 supposed to be the 'compatible' with h/w com1-4 ports but your driver assigns the /dev/537 for your modem (as shown in your 2nd post). Clicking on 'detect' or running **wvdialconf** this special port name is not scanned.

You must try to enter it by **typing** into specific field (as in my screen capture attached in my previous post) OR use the configuration file that worked (your 2nd post) and continue tries from that point.

Possible new try with **wvdial**: ```
gksudo gedit /etc/wvdial.conf
``` copy paste into gedit window the following configuration: ```
[Dialer Defaults]
Modem = /dev/537
Modem Type = Analog Modem
ISDN = 0
Baud = 48800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Phone = 08450792829
Username = Steve
Password = ********
Auto DNS = yes
Stupid mode = yes
;carrier check = no

```Place appropriate for your provider username & password. Connect with **sudo wvdial**
In any problem post all terminal output (including your 'sudo wvdial' command).

For more info check: [http://ubuntuforums.org/showpost.php?p=7715470&postcount=2](http://ubuntuforums.org/showpost.php?p=7715470&postcount=2)

Regards,
George

---

### Post by Steve Francis on 2009-10-06
Thanks, George.

Since my last post, I had drifted away from our discussion because I can now use the modem successfully with Efax-gtk, which was my initial objective.

I don't necessarily need to use GnomePPP but it would be interesting to know what I could do to get the modem working in PPP.

I'll experiment, and if I have any success I'll report back here.

Thanks again for your suggestions. As a beginner, this forum is invaluable.

---

### Post by Steve Francis on 2009-10-21
If anyone is reading this thread with the same problem, I had some success with the following commands...

GET GNOME-PPP TO DETECT 537EP MODEM: 

Open up Terminal in Ubuntu 9.04 

Type in 
sudo ln -sf /dev/537 /dev/ttyS537 

Type in 
ls -l    /dev/*537* 

Response is 
crw-rw-rw- 1 root dialout 240, 1 2009-10-09 19:16 /dev/537 
crw-rw---- 1 root root    240, 1 2009-10-09 19:01 /dev/5370 
lrwxrwxrwx 1 root root         8 2009-10-09 19:21 /dev/ttyS537 -> /dev/537 

Type in 
sudo gnome-ppp 

Terminal responds with 
WVCONF:    /root/.wvdial.conf 
and the graphical interface for Gnome PPP starts up. 
Click on Setup 
For Device, enter /dev/ttyS537 
(Change Init Strings if desired) 
Click on Detect 
Terminal responds with 
GNOME PPP: STDOUT: Editing `/dev/null'. 
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: Scanning your serial ports for a modem. 
GNOME PPP: STDOUT: 
GNOME PPP: STDERR: ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next  try: 9600 baud 
GNOME PPP: STDERR: ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next  try: 115200 baud 
GNOME PPP: STDERR: ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200,  giving up. 
GNOME PPP: STDERR: ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next  try: 9600 baud 
GNOME PPP: STDERR: ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next  try: 115200 baud 
GNOME PPP: STDERR: ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200,  giving up. 
GNOME PPP: STDERR: ttyS2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next  try: 9600 baud 
GNOME PPP: STDERR: ttyS2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next  try: 115200 baud 
GNOME PPP: STDERR: ttyS2<*1>: ATQ0 V1 E1 -- and failed too at 115200,  giving up. 
GNOME PPP: STDERR: ttyS3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next  try: 9600 baud 
GNOME PPP: STDERR: ttyS3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next  try: 115200 baud 
GNOME PPP: STDERR: ttyS3<*1>: ATQ0 V1 E1 -- and failed too at 115200,  giving up. 
GNOME PPP: STDERR: ttyS537<*1>: ATQ0 V1 E1 -- failed with 2400 baud,  next try: 9600 baud 
GNOME PPP: STDERR: ttyS537<*1>: ATQ0 V1 E1 -- OK 
GNOME PPP: STDERR: ttyS537<*1>: ATQ0 V1 E1 Z -- OK 
GNOME PPP: STDERR: ttyS537<*1>: ATQ0 V1 E1 S0=0 -- OK 
GNOME PPP: STDERR: ttyS537<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK 
GNOME PPP: STDERR: ttyS537<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK 
GNOME PPP: STDERR: ttyS537<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK 
GNOME PPP: STDERR: ttyS537<*1>: Modem Identifier: ATI -- OK 
GNOME PPP: STDERR: ttyS537<*1>: Speed 19200: AT -- OK 
GNOME PPP: STDERR: ttyS537<*1>: Speed 38400: AT -- OK 
GNOME PPP: STDERR: ttyS537<*1>: Speed 57600: AT -- OK 
GNOME PPP: STDERR: ttyS537<*1>: Speed 115200: AT -- OK 
GNOME PPP: STDERR: ttyS537<*1>: Speed 230400: AT -- OK 
GNOME PPP: STDERR: ttyS537<*1>: Speed 460800: AT -- OK 
GNOME PPP: STDERR: ttyS537<*1>: Max speed is 460800; that should be safe. 
GNOME PPP: STDERR: ttyS537<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK 
GNOME PPP: STDOUT: 
GNOME PPP: STDOUT: Found a modem on /dev/ttyS537. 
GNOME PPP: STDERR: ttyS537<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0  &C1 &D2 +FCLASS=0" 
GNOME PPP: STDOUT: Modem configuration written to /dev/null.

Thanks to the guys at [http://linmodems.org/](http://linmodems.org/) for their advice

---

