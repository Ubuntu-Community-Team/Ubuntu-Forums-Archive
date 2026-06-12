---
title: "Printing: Lexmark x5150"
date: 2006-01-01
forum: Hardware &amp; Laptops
---

### Post by awalsh on 2006-01-01
Hi,

Im pretty new to ubuntu but not to linux (Had fedora, redhat, mandrake etc in the past). Ive got a Lexmark x5150 under the desk and its not been used since i converted to linux, as i heard there is no way to get it working. Its been a while since i found that (about a year or so) so does anyone know of a way to get this working?

Bit of a waste of printer using it as a foot rest....


Thanks for any help

Andrew

---

### Post by Sef on 2006-01-03
This gentoo-wiki tells how to get your printer working:  [http://gentoo-wiki.com/HOWTO_Lexmark_Printers]("http://gentoo-wiki.com/HOWTO_Lexmark_Printers")

---

### Post by _aeon on 2006-05-18
Lexmark X5150 works under Linux (with Z55 driver). Here's how:

1.- Download Lexmark Z55 linux driver [here]("http://www.downloaddelivery.com/srfilecache/CJLZ55LE-CUPS-1.0-1.TAR.GZ")

2.- Follow [these]("http://www.ubuntuforums.org/archive/index.php/t-83456.html") instructions.

Note:
1.- Instructions are for Z600LE but it works the same with Z55.
2.- Scanner doesn't work (yet). Only printer.

---

### Post by SwedishHatFaction on 2007-03-25
I installed the Z55 driver for my X5150 but when I printed the test page, the lines and color did not completely match up (perhaps the print heads are out of alignment?). Is there any software utility to correct this? Thanks.

---

### Post by netreg on 2007-06-08
Just followed the instructions on Feisty and it worked :D 

oh Happy Days !!!!! :popcorn:

---

### Post by boodasmurph_uk on 2008-01-01
Just got it to work on Gutsy.  Yeah!!

---

### Post by cesium62 on 2008-01-04
I have a Dell Inspiron 530 and am trying to get my Dell A940 (lexmark 5150) printer up and running with the lexmark z55 driver.   I'm using Fiesty Fawn.  I'm currently having 2 problems.

1)  When I run /usr/lib/cups/backend/z55, I get no output.  I used strace on the binary and see tht it does:

[INDENT]> open("/dev/usb/lp0", O_WRONLY)          = -1 ENOENT (No such file or directory)
open("/dev/usb/usblp0", O_WRONLY)       = -1 ENOENT (No such file or directory)
open("/dev/usblp0", O_WRONLY)           = 3
close(3)                                = 0
brk(0)                                  = 0x804d000
brk(0x806e000)                          = 0x806e000
open("/proc/bus/usb/devices", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f1f000
read(3, "\nT:  Bus=08 Lev=00 Prnt=00 Port="..., 4096) = 4096
read(3, "2 Lev=01 Prnt=01 Port=01 Cnt=01 "..., 4096) = 1265
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb7f1f000, 4096)                = 0
exit_group(0)     [/INDENT]

And, if we just cat /proc/bus/usb/devices, we find the printer:

> T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=413c ProdID=5103 Rev= 0.01
S:  Manufacturer=Dell
S:  Product=Dell A940
S:  SerialNumber=17K045000897597
C:* #Ifs= 3 Cfg#= 1 Atr=c0 MxPwr= 16mA
I:  If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=87(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=07(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=07(print) Sub=01 Prot=02 Driver=usblp
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:  If#= 2 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=83(I) Atr=03(Int.) MxPS=   8 Ivl=100ms

Is the 'z55' binary looking for a printer labeled as a Lexmark z55 instead of a Dell A940 and that's why I don't get any output?  Or is there a real problem here that I need to fix?

I've read through various threads, and getting no ouptut from /usr/lib/cups/backend/* seems fairly common, so if we could document additional reasons why there is sometimes no output, that might help.


2)  At one point in time, I was able to get a test page to print.  However, when I went to the browser (firefox) and printed a page, I got no output.  I've enabled debugging in cups.conf and have looked through /var/log/cups/error_log, and it looks like all of the processes are running successfully to completion.

> I [03/Jan/2008:21:16:44 -0800] Started filter /usr/lib/cups/filter/pstops (PID 9525) for job 14.
I [03/Jan/2008:21:16:44 -0800] Started filter /usr/lib/cups/filter/pstoraster (PID 9526) for job 14.
I [03/Jan/2008:21:16:44 -0800] Started filter /usr/lib/cups/filter/rastertoz55 (PID 9527) for job 14.
I [03/Jan/2008:21:16:44 -0800] Started backend /usr/lib/cups/backend/usb (PID 9528) for job 14.
...
D [03/Jan/2008:21:16:44 -0800] PID 9525 (/usr/lib/cups/filter/pstops) exited with no errors.
...
D [03/Jan/2008:21:16:48 -0800] PID 9526 (/usr/lib/cups/filter/pstoraster) exited with no errors.
...
D [03/Jan/2008:21:16:48 -0800] PID 9527 (/usr/lib/cups/filter/rastertoz55) exited with no errors.
...
D [03/Jan/2008:21:16:48 -0800] PID 9528 (/usr/lib/cups/backend/usb) exited with no errors.


So, it looks to me like the printer output is being generated and written down the usb bus and the printer is just tossing it?

I just power cycled the printer and restarted the cupsys daemon.  The test page currently prints.  I then asked firefox to print out this page and it currently prints.

Are there well documented reasons why the lexmark 5150 would hang?

Anyway... Maybe this post will provide extra diagnostic hints or ideas to others who are having problems.

---

### Post by z-vap on 2008-02-02
I have this lexmark printer connected to my network, but through a windows PC.  When the pc is on, I can print to it, but only if I am booted into windows.  If I am in Linux, the job just sits there, in my Printer queue.

anyone else come across this?

---

### Post by Woe_is_me on 2008-03-06
> **z-vap said:**
> I have this lexmark printer connected to my network, but through a windows PC.  When the pc is on, I can print to it, but only if I am booted into windows.  If I am in Linux, the job just sits there, in my Printer queue.

anyone else come across this?

I have this same problem as well. I have tried following the instructions above as well. But it doesn't work for me. :(

---

### Post by z-vap on 2008-03-07
Actually I just recently got it working again. I have the driver installed.  What the issue was (I believe) is DHCP.  I added to hosts file the PC that was hosting the printer (MACHINE_NAME and IP_ADDRESS), and suddenly the thing works.  


I don't know if the trouble is my router or my Linux network setup.  But currently I am good to go, until the printer host's ip address changes :)

---

### Post by therawski on 2008-07-23
I'm new to linux (that's why I'm using ubuntu), please bear with me, I am trying to set up my Lexmark X5150 to print but when I get stuck in the instructions here:

therawski@ubuntu9:/etc/rc2.d$ ls
README                       S12dbus           S20rsync       S89cron
S01policykit                 S18avahi-daemon   S24dhcdbd      S98usplash
S05vbesave                   S20apmd           S24hal         S99acpi-support
S10acpid                     S20apport         S25bluetooth   S99laptop-mode
S10powernowd.early           S20cupsys         S25pulseaudio  S99rc.local
S10sysklogd                  S20hotkey-setup   S30gdm         S99rmnologin
S10xserver-xorg-input-wacom  S20nvidia-kernel  S89anacron     S99stop-readahead
S11klogd                     S20powernowd      S89atd
therawski@ubuntu9:/etc/rc2.d$ sudo S20cupsys restart
sudo: S20cupsys: command not found

SEE!?! can anyone help? I'm obviously using the Z55 driver for this 

> **_aeon said:**
> Lexmark X5150 works under Linux (with Z55 driver). Here's how:

1.- Download Lexmark Z55 linux driver [here]("http://www.downloaddelivery.com/srfilecache/CJLZ55LE-CUPS-1.0-1.TAR.GZ")

2.- Follow [these]("http://www.ubuntuforums.org/archive/index.php/t-83456.html") instructions.

Note:
1.- Instructions are for Z600LE but it works the same with Z55.
2.- Scanner doesn't work (yet). Only printer.

---

