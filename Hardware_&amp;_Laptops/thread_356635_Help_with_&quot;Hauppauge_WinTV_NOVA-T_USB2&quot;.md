---
title: "Help with &quot;Hauppauge WinTV NOVA-T USB2&quot;"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by emil.s on 2007-02-08
Hello!

Now i think i have tried everything. But i can't get it work... :(

Some info:
/var/log/messages:
```
Feb  8 20:09:32 Megaleif kernel: [ 2974.927170] usb 5-2: new high speed USB device using ehci_hcd and address 4
Feb  8 20:09:32 Megaleif kernel: [ 2975.059869] usb 5-2: configuration #1 chosen from 1 choice
Feb  8 20:09:32 Megaleif kernel: [ 2975.206359] dib0700: loaded with support for 2 different device-types
Feb  8 20:09:32 Megaleif kernel: [ 2975.210430] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
Feb  8 20:09:32 Megaleif kernel: [ 2975.238963] usbcore: registered new interface driver dvb_usb_dib0700
```

But:
```
emil@Megaleif:~$ sudo xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-6-386)
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available
```

```
emil@Megaleif:~$ sudo lsmod | grep dvb
dvb_usb_nova_t_usb2     6020  0 
dvb_usb_dibusb_common     9988  1 dvb_usb_nova_t_usb2
dvb_usb_dib0700        12808  0 
dib7000m               15108  1 dvb_usb_dib0700
dib7000p               13444  1 dvb_usb_dib0700
dvb_usb                20748  3 dvb_usb_nova_t_usb2,dvb_usb_dibusb_common,dvb_usb_dib0700
dvb_core               78760  1 dvb_usb
dvb_pll                14468  2 dvb_usb_dibusb_common,dvb_usb
dib3000mc              12548  2 dvb_usb_dibusb_common,dvb_usb_dib0700
i2c_core               21776  7 dib7000m,dib7000p,dvb_usb,dvb_pll,dib3000mc,dibx000_common,i2c_ec
usbcore               131352  10 dvb_usb_nova_t_usb2,dvb_usb_dib0700,dvb_usb,pl2303,usbserial,usbhid,ohci_hcd,ehci_hcd,uhci_hcd
```

 dmesg:
```
[ 2974.927170] usb 5-2: new high speed USB device using ehci_hcd and address 4
[ 2975.059869] usb 5-2: configuration #1 chosen from 1 choice
[ 2975.206359] dib0700: loaded with support for 2 different device-types
[ 2975.210430] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[ 2975.238573] dvb-usb: did not find the firmware file. (dvb-usb-dib0700-01.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
[ 2975.238963] usbcore: registered new interface driver dvb_usb_dib0700
[ 3791.069653] usbcore: registered new interface driver dvb_usb_nova_t_usb2
```

More info:
[http://www.linuxtv.org/wiki/index.php/DVB_USB#Hauppauge_WinTV-NOVA-T_usb2](http://www.linuxtv.org/wiki/index.php/DVB_USB#Hauppauge_WinTV-NOVA-T_usb2)
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_USB2](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_USB2)

In linux/Documentation/dvb i found this:
```
emil@Megaleif:~/Desktop/linux-2.6.20/Documentation/dvb$ ./get_dvb_firmware dibusb
Firmware dvb-dibusb-5.0.0.11.fw extracted successfully.
Now copy it to either /usr/lib/hotplug/firmware or /lib/firmware
(depending on configuration of firmware hotplug).
```

But in /lib/firmware i already get all these files:
```
emil@Megaleif:~/Desktop/linux-2.6.20/Documentation/dvb$ ls /lib/firmware/
2.6.20-5-386/           2.6.20-6-386/           2.6.20-6-generic/       dvb-dibusb-5.0.0.11.fw  
emil@Megaleif:~/Desktop/linux-2.6.20/Documentation/dvb$ ls /lib/firmware/2.6.20-6-386/
acx                                 atmel_at76c504.bin            dvb-usb-vp702x-01.fw  ql2200_fw.bin
atmel_at76c502_3com.bin             atmel_at76c504c-wpa.bin       dvb-usb-vp7045-01.fw  ql2300_fw.bin
atmel_at76c502_3com-wpa.bin         atmel_at76c505a-rfmd2958.bin  dvb-usb-wt220u-01.fw  ql2322_fw.bin
atmel_at76c502.bin                  atmel_at76c505-rfmd2958.bin   ipw2100-1.3.fw        ql2400_fw.bin
atmel_at76c502d.bin                 atmel_at76c505-rfmd.bin       ipw2100-1.3-i.fw      rt2561.bin
atmel_at76c502d-wpa.bin             atmel_at76c506.bin            ipw2100-1.3-p.fw      rt2561s.bin
atmel_at76c502e.bin                 atmel_at76c506-wpa.bin        ipw2200-bss.fw        rt2661.bin
atmel_at76c502e-wpa.bin             dvb-fe-or51132-qam.fw         ipw2200-ibss.fw       rt73.bin
atmel_at76c502-wpa.bin              dvb-fe-or51132-vsb.fw         ipw2200-sniffer.fw    v4l-cx2341x-dec.fw
atmel_at76c503-i3861.bin            dvb-fe-or51211.fw             ipw3945.ucode         v4l-cx2341x-enc.fw
atmel_at76c503-i3863.bin            dvb-ttpci-01.fw               isl3877               v4l-cx2341x-init.mpg
atmel_at76c503-rfmd-0.90.2-140.bin  dvb-usb-avertv-a800-02.fw     isl3886               v4l-cx25840.fw
atmel_at76c503-rfmd-acc.bin         dvb-usb-dibusb-5.0.0.11.fw    isl3887usb_bare       v4l-pvrusb2-24xxx-01.fw
atmel_at76c503-rfmd.bin             dvb-usb-dibusb-6.0.0.8.fw     isl3890               v4l-pvrusb2-29xxx-01.fw
atmel_at76c504_2958-wpa.bin         dvb-usb-dtt200u-01.fw         isl3890usb            zd1211
atmel_at76c504a_2958-wpa.bin        dvb-usb-umt-010-02.fw         ql2100_fw.bin
```

And now i have tried with compiling my own kernel. With this patch:
[http://www.linuxtv.org/downloads/patches_to_2.6.20/v4l_dvb_hg_4819_dib0700_add_support_for_new_revision_of_nova_t_stick.patch](http://www.linuxtv.org/downloads/patches_to_2.6.20/v4l_dvb_hg_4819_dib0700_add_support_for_new_revision_of_nova_t_stick.patch)
But it does not work... :(

Help me! [-o<

EDIT:
More about the card:
```
root@Megaleif:~# lsusb 
Bus 006 Device 005: ID 2040:7060 Hauppauge

lshw...  
            *-usb UNCLAIMED
                   description: Generic USB device
                   product: Nova-T Stick
                   vendor: Hauppauge
                   physical id: 2
                   bus info: usb@6:2
                   version: 1.00
                   serial: 4027804485
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=480.0MB/s

```

---

### Post by CarloMagno on 2007-02-14
I had exactly the same problems, but today I got it working. I only had to place the firmware files: **dvb-usb-nova-t-usb2-02.fw** and **dvb-usb-nova-t-usb2-01.fw** in /lib/firmware and in /lib/firmware/"somefolderwithversionofyourkernel"/

As I did't know which of them worked I used both, it seems that the one loaded is the one which ends in "-01" but I have read in other threads that you could use the newer firmware ("-02") if you rename it as dvb-usb-nova-t-usb2-**01**.fw. Note that I have also placeand the *.fw files in /lib/firmware and in its sub-folder, just to make sure it was loaded. I am new to linux world so I can imagine there is a better way to do things that trying everything, but It took me a lot of reading to get it loaded.

I downloaded the firmware files following a link posted in this thread: [http://www.ubuntuforums.org/showthread.php?t=348707&highlight=hauppauge+nova+usb](http://www.ubuntuforums.org/showthread.php?t=348707&highlight=hauppauge+nova+usb)

the link is (many thanks to the user that posted it).
[http://www.easy-it.co.uk/Temp/nova-t/](http://www.easy-it.co.uk/Temp/nova-t/)

It seems that you can also extract these fw files from several "rpm" packages for other distros, but you also have to install "rpm" package (with synaptic or apt-get) in ubuntu to extract the files from it.

After you had placed the firmware files in /lib/firmware unplug and plug again your usb hauppauge and in calling dmesg in a terminal window you will see some messages afther the line  "...found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware", and a new /dev/dvb/ folder will be created. If that doesn't happen something has gone wrong.

I will try this afternoon to configure scan and tzap to watch some TV, hope it works :-)

My system is:
Laptop Pentium M 1,8Ghz - 1 GB ram, ATI mobility Radeon 9700, Ubuntu EDGY, Hauppauge WinTV Nova USB2

---

### Post by emil.s on 2007-02-17
I think i have located the problem...

My cards name is "WinTV NOVA-T-***_STICK_*** USB2"
Not only "WinTV NOVA-T USB2". So it's two different cards. :cool: 

So now i think i can solve this by myself. :)

---

### Post by anaconda on 2007-02-20
This guy got wintv nova-t stick usb2 to work:

[http://www.ubuntuforums.org/showthread.php?t=327487&highlight=wintv+stick](http://www.ubuntuforums.org/showthread.php?t=327487&highlight=wintv+stick)

---

