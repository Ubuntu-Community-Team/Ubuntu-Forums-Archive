---
title: "Linux GPIB Agilent 82357B help!!"
date: 2012-03-15
forum: Hardware
---

### Post by bohu2008 on 2012-03-15
Hello All,
I am try to control my GPIB devcie from fedora Linux.  I get error when I run gpib_config after I load the Agilent 82357B firmware.

Let me descibe the problem

Linux system version; 2.6.34.7-56.fc13.i686.

I followed the flowing steps
1. install the linux-gpib from source, according to the install guide, I down load my kernel source and 'make oldconfig' -> 'make vmlinux' -> 'make modules'  using my current .config 

file(although I don't know what's this for), then .configure -> make -> make install. Then give root access to the computer's gpib group.

2. install the firmware for usb devices (/usr/share/usb/agilent_8237a/measat_releaseX1.8.hex
    sudo fxload -t fx2 -D /proc/bus/usb/001/002 -I /usr/share/usb/agilent_8237a/measat_releaseX1.8.hex
    sudo fxload -t fx2 -D /proc/bus/usb/001/003 -I /usr/share/usb/agilent_8237a/measat_releaseX1.8.hex
    
3.    edit /etc/gpib.conf   as following.

interface {
        minor = 0       /* board index, minor = 0 uses /dev/gpib0, minor = 1 uses /dev/gpib1, etc. */
        board_type = "agilent_82357a"   /* type of interface board being used */
        name = "agilent_82357a"
        master = yes    /*interface board is system controller*/
        pad = 0 /* primary address of interface             */
        sad = 0 /* secondary address of interface           */
        timeout = T3s   /* timeout for commands */
}

device {
        minor = 0
        name = "ATTN"
        pad = 0
        sad = 0
}
        

4.  execute "sudo gpib_config"
        Right now the ready light should now be on


After step 2 all three lights on Agilent 82357B is on. after step 4 only ready light is on. looks good. However dmesg shows as following at this time.

########################################################################################
usb 1-7: new high speed USB device using ehci_hcd and address 23
usb 1-7: New USB device found, idVendor=0957, idProduct=0518
usb 1-7: New USB device strings: Mfr=0, Product=0, SerialNumber=0
usb 1-7: USB disconnect, address 23
usb 1-7: new high speed USB device using ehci_hcd and address 24
usb 1-7: New USB device found, idVendor=0957, idProduct=0518
usb 1-7: New USB device strings: Mfr=0, Product=0, SerialNumber=0
usb 1-7: USB disconnect, address 24
usb 1-7: new high speed USB device using ehci_hcd and address 25
usb 1-7: New USB device found, idVendor=0957, idProduct=0718
usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=5
usb 1-7: Product: 82357B ()
usb 1-7: Manufacturer: Agilent Technologies, Inc.
usb 1-7: SerialNumber: MY48200870
probe succeeded for path: usb-0000:00:1d.7-7
gpib0: exiting autospoll thread
agilent_82357a_detach: detached
attached to bus interface 0, address 0xe045e800
agilent_82357a_attach: attached
/home/btwireless/Desktop/linux-gpib-3.2.16/drivers/gpib/agilent_82357a/agilent_82357a.c: agilent_82357a_update_status: agilent_82357a_read_registers() returned error
/home/btwireless/Desktop/linux-gpib-3.2.16/drivers/gpib/agilent_82357a/agilent_82357a.c: agilent_82357a_update_status: agilent_82357a_read_registers() returned error
/home/btwireless/Desktop/linux-gpib-3.2.16/drivers/gpib/agilent_82357a/agilent_82357a.c: 
########################################################################################

Looks like the firmware loading to Agilent 82357B is fine. However there's problem for the library config.



Then I trying to use the problem "ibtest" provided by the Linux-gpib package. the problem always stunck after I command to send out string. Please see following. I need Ctrl +C to end 

the program.

#############################################################################################################################
[root@root etc]# /usr/local/bin/ibtest 
Do you wish to open a (d)evice or an interface (b)oard?
    (you probably want to open a device): b
enter name of interface board (or device) you wish to open: agilent_82357a
trying to open board named 'agilent_82357a'
You can:
    w(a)it for an event
    write (c)ommand bytes to bus (system controller only)
    send (d)evice clear (device only)
    change remote (e)nable line (system controller only)
    (g)o to standby (release ATN line, system controller only)
    send (i)nterface clear (system controller only)
    ta(k)e control (assert ATN line, system controller only)
    get bus (l)ine status (board only)
    go to local (m)ode
    change end (o)f transmission configuration
    (q)uit
    (r)ead string
    perform (s)erial poll (device only)
    change (t)imeout on io operations
    request ser(v)ice (board only)
    (w)rite data string
: w
enter a string to send to your device: *IDN?
sending string: *IDN?
################################################################################################################################

Now dmesg is as following

########################################################################################
/home/btwireless/Desktop/linux-gpib-3.2.16/drivers/gpib/agilent_82357a/agilent_82357a.c: agilent_82357a_update_status: agilent_82357a_read_registers() returned error
/home/btwireless/Desktop/linux-gpib-3.2.16/drivers/gpib/agilent_82357a/agilent_82357a.c: agilent_82357a_update_status: agilent_82357a_read_registers() returned error
/home/btwireless/Desktop/linux-gpib-3.2.16/drivers/gpib/agilent_82357a/agilent_82357a.c: 
########################################################################################


I have tried different gpib_conf file settings I think may be right. But still the same problem.


Anybody have idear what's wrong with it?  Thanks in advance. Really need help.


Regards
Bo

---

### Post by sevoku on 2012-05-02
hi,

I had same problems. The bug seems to be fixed in svn. You may try my packages from [https://launchpad.net/~v-kukol/+archive/gpib-testing](https://launchpad.net/~v-kukol/+archive/gpib-testing). Using them since one week on some test machines without issues.

---

