---
title: "HP nw8440 bluetooth hciconfig empty"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by Strelock on 2007-03-17
Hi all!

I'm totally stuck with bluetooth on my laptop. It's HP Compaq nw8440. So the problem is:
hciconfig -a returns nothing.

Some more info:
dmesg | grep Blue
[17179616.804000] Bluetooth: Core ver 2.8
[17179616.804000] Bluetooth: HCI device and connection manager initialized
[17179616.804000] Bluetooth: HCI socket layer initialized
[17179616.816000] Bluetooth: L2CAP ver 2.8
[17179616.816000] Bluetooth: L2CAP socket layer initialized
[17179616.824000] Bluetooth: RFCOMM socket layer initialized
[17179616.824000] Bluetooth: RFCOMM TTY layer initialized
[17179616.824000] Bluetooth: RFCOMM ver 1.7
[17184661.708000] Bluetooth: HCI USB driver ver 2.9
lsmod | grep hci
hci_usb                18068  0 
bluetooth              53476  5 hci_usb,rfcomm,l2cap
sdhci                  20108  0 
mmc_core               32136  1 sdhci
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  5 hci_usb,usbhid,ehci_hcd,uhci_hcd
ahci                   20356  4 
libata                 74892  1 ahci
scsi_mod              144648  5 sbp2,sg,sd_mod,ahci,libata

I've search the web but pretty much nobody describes what to do when hciconfig -a returns nothing... any ideas anybody?

---

### Post by Strelock on 2007-03-18
Bump?

Is there a way to power up the bluetooth?

---

### Post by RaZer0r on 2007-03-30
got the same problem but with an acer aspire 5612WLMi i have a on off switch at the front of my laptop but it doesn't seem to do anything if i switch it... the wireless has the same switch (next to the bt switch) and that one works flawlessy...

---

### Post by zabbaskeema on 2007-11-24
Bump!
Same here, NW8440, Kubuntu Gutsy Latest.
Zabba

---

### Post by krychek on 2008-03-18
Another bump.
I have nw8440 and ubuntu hardy. There is no switch on button for the bluetooth..
Is this bug reported? It should be..

---

### Post by jever321 on 2008-04-01
Hi, 
I have as well a HP nw8440. The Bluetooth works fine with gutsy and hardy:

xxx@yyy:~$ hciconfig -a
hci0:   Type: USB
        BD Address: 00:1E:37:04:F1:86 ACL MTU: 1017:8 SCO MTU: 64:8
        UP RUNNING
        RX bytes:1235 acl:0 sco:0 events:30 errors:0
        TX bytes:617 acl:0 sco:0 commands:30 errors:0
        Features: 0xff 0xff 0x8f 0xfe 0x9b 0xf9 0x00 0x80
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3
        Link policy: RSWITCH HOLD SNIFF PARK
        Link mode: SLAVE ACCEPT
        Name: 'yyyy-0'
        Class: 0x18010c
        Service Classes: Capturing, Object Transfer
        Device Class: Computer, Laptop
        HCI Ver: 2.0 (0x3) HCI Rev: 0x2129 LMP Ver: 2.0 (0x3) LMP Subver: 0x41cf
        Manufacturer: Broadcom Corporation (15)

Maybe you did not activate the Bluetooth (layer 0 problem?):

the bluetooth switch is the same as for the wlan!

cheers

---

### Post by krychek on 2008-04-01
Your bluetooth just works out of the box? Mine doesn't. Nothing happens when I press the wlan button and "hciconfig -a" has no output at all. Are you sure you haven't done some trick to make it work?

Btw what about the wlan? Does it work out of the box are needs some windows driver and ndiswrapper? (I can't test it I don't have wlan network here.)

---

### Post by jever321 on 2008-04-02
hi,

the bluetooth and the wlan is working out of the box. 
I have for the wlan the ip3945 module must be available, I installed it with apt-get, for gutsy I installed: linux-ubuntu-modules-2.6.22-14-generic
For the bluetooth I choosed the kdebluetooth from kubuntu and the tools.

from my /etc/modules (for gutsy):

loop 
lp
sbp2 
fuse 
vfat 
smbfs 
bcm203x 
hci_usb 
hci_vhci 
msdos 
ntfs 
irda 
irnet 
ircomm  
irlan  
ieee80211_crypt_ccmp  
ieee80211_crypt_tkip  
ieee80211_crypt_wep  
ieee80211 
ieee80211softmac  
avm_cs  
ati-agp  
usb-storage  
usbserial 
coretemp  
snd  
aes  
wlan  
wlan_tkip  
wlan_ccmp  
wlan_acl 
wlan_scan_ap  
wlan_xauth 
kvm-intel
ipw3945 

cheers
tim

---

### Post by krychek on 2008-04-02
It doesn't work out of the box if you had to install extra packages. :)

So you installed "linux-ubuntu-modules-2.6.22-14-generic" and wlan started to work?

---

### Post by jever321 on 2008-04-02
yes,

for the wlan you need the ipw3945 modules (for hardy it is iwl3945) else you will not get wlan up.
You can get a hint for the configuration/installation:
[http://ubuntuforums.org/showthread.php?t=636177](http://ubuntuforums.org/showthread.php?t=636177)

for the bluetooth you need modules loaded:
bluetooth,rfcomm,l2cap,hci_vhci,hci_usb

the best and easy way to load these modules: install modconf (apt-get install modconf), there you can select the modules.

cheers
tim

---

### Post by krychek on 2008-04-02
I edited the blacklist and the modules file so now I have all the required modules loaded but still nothing has changed. Shouldn't I install some driver with ndiswrapper?

Still no wlan, no bluetooth :(

---

### Post by jever321 on 2008-04-02
Hi,

iwconfig does not show anything? After having the modules loaded, what are the entries in dmesg?
When I first loaded the modules I get iwconfig and iwlist wlan0_rename scanning giving me output...

For the bluetooth/wlan you should get something like:
[   42.805129] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driv
er for Linux, 1.2.0
[   42.805132] iwl3945: Copyright(c) 2003-2007 Intel Corporation
...
[   42.904048] Bluetooth: Core ver 2.11
[   42.923611] ACPI: PCI Interrupt 0000:10:00.0[A] -> GSI 17 (level, low) -> IRQ
 17
[   42.923626] PCI: Setting latency timer of device 0000:10:00.0 to 64
[   42.923644] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   42.970745] NET: Registered protocol family 31
[   42.970748] Bluetooth: HCI device and connection manager initialized
[   42.970751] Bluetooth: HCI socket layer initialized
...
[   43.172573] Bluetooth: HCI USB driver ver 2.9
...
[   75.170828] Bluetooth: Broadcom Blutonium firmware driver ver 1.0
[   75.170858] usbcore: registered new interface driver bcm203x
[   75.193497] Bluetooth: Virtual HCI driver ver 1.2
...
[   95.142845] Bluetooth: L2CAP ver 2.9
[   95.142852] Bluetooth: L2CAP socket layer initialized
[   95.289942] Bluetooth: RFCOMM socket layer initialized
[   95.289957] Bluetooth: RFCOMM TTY layer initialized
[   95.289960] Bluetooth: RFCOMM ver 1.8

what is your lsusb and lspci, the iwconfig output?
Maybe your laptop looks like having wlan installed, but there is no card in there (check with the screwdriver!).

What I changed from the default(?) in the BIOS is the powersaving feature, which disables the wlan chipset while the ethernet connection is used. After disabling (!) this feature wlan is always switched on.

cheers
tim

---

### Post by krychek on 2008-04-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/199634](https://bugs.launchpad.net/ubuntu/+bug/199634) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have a wlan card, cuz it works in windows :)
I was able to make it work with ndiswrapper and NETw4x32.inf windows driver but it takes almost 5 minutes to boot.. so I'm still not happy.
I attached two dmesg outputs, one is with the ndiswrapper driver when wlan works the other one is without ndiswrapper.

I have this in my blacklist: 

blacklist ipw3945

blacklist ieee80211

blacklist ieee80211_crypt

And this in my etc/modules:

iwlwifi_mac80211

iwl3945

---

### Post by jever321 on 2008-04-04
Hi,

strange stuff is: you have loaded in both cases the replacement for the ipw3945 driver: the iwl3945 driver!

And even in the "unsuccessful" case you have the driver fully loaded:

[   42.068421] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   42.201310] iwl3945: Radio Frequency Kill Switch is On:
[   42.201312] Kill switch must be turned off for wireless networking to work.
[   42.206525] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   42.216546] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   42.236489] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   42.263905] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   42.286079] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels

I assume that the iwl3945 OR the ipw3945 can be choosen but NOT both.

In the ubuntuforums you can see that there is a bug in hardy (for example) where the light is not triggered for wlan enabled and therefor the ipw3945 was kicked out of the ubuntu modules-restricted package. The ipl3945 still works with me on hardy with nw8440.
Try to only set up with modconf the minimum required driver sets, so that you have either ipw3945 OR ipw3945. Remove the entries from the blacklist, load the modules.

My current lsmod with working everything (only the Fingertip switch not tested) is attached.
My blacklist is currently only holding one entry for the fglrx driver.

cheers
tim

---

### Post by krychek on 2008-04-05
I have a feeling that it's not gonna work until a fresh reinstall.. :/
Could you upload you /etc/modules too? Thanks.

When wlan works why does it take about 3 minutes to load the "loop" module? What is its function anyway?

---

### Post by krychek on 2008-04-05
[   45.295547] iwl3945: Radio Frequency Kill Switch is On:
[   45.295549] Kill switch must be turned off for wireless networking to work.

Maybe it's just turned off? Nothing happens when I press the wlan button. Do you have to press it? Does the little blue light turn on too?

Wlan works when I boot from the Live cd.. so something must be really wrong. :(

Edit: seems like wlan only works when I get this "Radio Frequency Kill Switch is On" message. I don't get it normally.

---

### Post by krychek on 2008-04-05
Ok, I've made some discovery. I turned wifi on in windows and booted back to Ubuntu and it worked! But it only works when there is no cable plugged in the NIC. I didn't know this either :) Then I booted back to windows again, wlan was turned off by default. Then I came back to Ubuntu and there was no wlan anymore.. I think windows is able to turn wlan on and off but Ubuntu can't. :(
Maybe this is a bug and should be reported?

---

### Post by jever321 on 2008-04-07
Hi,

this is what i wrote earlier: in the BIOS you have to disable (!) a feature which by default disables the WLAN chipset if a cable based network connection is established. This is a power saving feature. In the BIOS just disable it and wlan will be switched on always.(its a feature, not a bug :-) )

cheers
tim

---

### Post by krychek on 2008-04-07
I've found two possible options: LAN power saving (disabled bye default) and LAN/WLAN switching (enabled by default). So I disabled the second one but still no good. Wlan only works if I turn it on in windows, I think Ubuntu just can't turn it on. Could you tell exactly where is that option in the bios? 

And I've tried all the 4 methods here: [https://wiki.ubuntu.com/LaptopTestingTeam/HotkeyResearch](https://wiki.ubuntu.com/LaptopTestingTeam/HotkeyResearch) . Pressing wlan button has absolutely no effect.


Edit: I don't know what's going on anymore but I've put back those 3 modules to the blacklist (ipw3945, ieee80211, ieee80211_crypt) and now it's working no matter if the lan cable is plugged in or not. I hope it'll continue working. Thanks for your help! :)

---

### Post by JKoltner on 2008-07-17
Just in case you're still reading this, I have pretty much the same experience on my nw8440: To get wireless to work at all, I have to boot into Windows first and then re-boot into Ubuntu (8.04, using the iwl driver).  At that point, from network manage I can enable and disable wireless.  I can have Ethernet connected when I start this process, though, and it's not a problem.  However, if I ever press the hardware switch on the laptop to turn off wireless, it's gone for good! -- Ubuntu can't switch it back on, and rebooting into Windows is required.

For me this is annoying but livable.

---

