---
title: "Help a Gentoo convert with LIRC"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by mitchd123 on 2009-05-02
Ok, long time Gentoo user attempting to switch to Ubuntu 9.04 desktop.  Things went better than expected until I tried setting up lirc.  I've tried to remove it and rety.

Lirc was working fine with Gentoo, so I know this is not a hardware problem.  If I boot into Gentoo it works fine.

I'm using a homebrew serial adapter.

lircd starts fine and irw loads fine and mode2 also works.  However I get absolutely nothing when I push a remote key with either mode2 or irw.   It's like the serial port is not working correctly.  I am using an add-in serial card which uses IRQ 19.  I found out when I originally set this up under Gentoo that the IRQ 19 and the io address are challenging, and the module options needs to be specified correctly.

How do I check the serial port is being correctly identified by Ubuntu?  Setserial seems to work fine.

root@virtual:/# /bin/setserial -v /dev/ttyS0 irq 19 port 0x00ac uart none
/dev/ttyS0, UART: unknown, Port: 0x00ac, IRQ: 19

I think this is typical for serial ports
root@virtual:/# cat /dev/ttyS0
cat: /dev/ttyS0: Input/output error

Here's some log info:

root@virtual:/# setserial -a /dev/ttyS0
/dev/ttyS0, Line 0, UART: unknown, Port: 0x00ac, IRQ: 19
    Baud_base: 115200, close_delay: 50, divisor: 0
    closing_wait: 3000
    Flags: spd_normal

Modules load correctly:
root@virtual:/# modprobe -a -v lirc_serial
insmod /lib/modules/2.6.28-11-generic/updates/dkms/lirc_dev.ko 
insmod /lib/modules/2.6.28-11-generic/updates/dkms/lirc_serial.ko irq=19 io=0x00ac

Address matchs lspci -v 

05:00.0 Serial controller: NetMos Technology PCI 9835 Multi-I/O Controller (rev 01) (prog-if 02)
    Subsystem: LSI Logic / Symbios Logic Device 0002
    Flags: medium devsel, IRQ 19
    I/O ports at ac00 [size=8]
    I/O ports at a800 [size=8]
    I/O ports at a400 [size=8]
    I/O ports at a000 [size=8]
    I/O ports at 9c00 [size=8]
    I/O ports at 9800 [size=16]
    Kernel driver in use: serial
    Kernel modules: parport_serial


Lircd starts correctly:

root@virtual:/# pkill lircd
root@virtual:/# lircd -n 
lircd: lircd(default) ready

After I type irw in another terminal it adds the client
lircd: accepted new client on /dev/lircd

And when I kill irw, the cllient is correctly removed
lircd: removed client

Everything is working as I think it should be, and dmesg provides:

root@virtual:/# dmesg
[ 8389.003562] lirc_dev: IR Remote Control driver registered, major 61 
[ 8389.504532] lirc_serial: auto-detected active low receiver
[ 8389.504536] lirc_dev: lirc_register_plugin: sample_rate: 0

Here are my config files:

root@virtual:/# cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Home-brew (16x50 UART compatible serial port)"
REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

I'm using the same remote file that I used with Gentoo

root@virtual:/# cat /etc/lircd.conf

begin remote

  name  my.test
  bits           24
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100

  header       4196  3770
  one           716  1773
  zero          716   777
  ptrail        715
  gap          64246
  min_repeat      1
  toggle_bit      0


      begin codes
          menu                     0xE081F7
          guide                    0xE1A1E5
          info                     0xE3C1C3
          exit                     0xE061F9
          up                       0xE591A6
          left                     0xE561A9
          select                   0xEF410B
          right                    0xE571A8
          down                     0xE581A7
          channel+                 0xE2D1D2
          channel-                 0xE2C1D3
          stop                     0xE1F1E0
          play                     0xE151EA
          pause                    0xE191E6
          rewind                   0xE1D1E2
          forward                  0xE1C1E3
          record                   0xE171E8
          eject                    0xE101EF
          1                        0xE311CE
          2                        0xE321CD
          3                        0xE331CC
          4                        0xE341CB
          5                        0xE351CA
          6                        0xE361C9
          7                        0xE371C8
          8                        0xE381C7
          9                        0xE391C6
          enter                    0xE531AC
          0                        0xE301CF
          tv/video                 0xE051FA
      end codes

end remote


root@virtual:/# cat /etc/modprobe.d/lirc-serial.conf 
#COM1 equivalent, /dev/ttyS0
options lirc_serial irq=19 io=0x00ac

I've also tried the softcarrier setting, but that made no different


 In Gentoo I have the serial port enable in the kernel, but in Ubuntu the module is loading.  
I've tried it with the module loaded and with the serial module unloaded.  


What can I try next?    Ideas anyone?

---

### Post by mitchd123 on 2009-05-04
I had incorrectly specified the ioport on the serial adapter.  I specified 0x00ac instead of 0xac00

The devil is in the details. 

This is now set correctly in /etc/modprobe.d/lirc.conf  and /etc/serial.conf, and everything is working as expected.

---

### Post by RockDr on 2009-06-24
Hi! I realise that this posting doesn't have anything to do with this forum, but I think that you may be able to help me!

It was by chance that I came across your
posts relating to the Wyse 3630LE, and you managing to locate a 3235
primer.

I have bought four of the 3630LE's off eBay, all for peanuts, and like
you, I plan to distribute them around the house for the children to
use.

Unfortunately I haven't had much luck with Wyse support in terms of
getting hold of the primer.

Would you be able to send me the various files you compiled for the
upgrade, and a summary of the steps that you took?

Are you still using the terminals over RDP with the XP box, or have
you played around with Linux as well?

Anyway, I look forward to hearing from you soon.
[COLOR=#888888]
James[/COLOR]

---

