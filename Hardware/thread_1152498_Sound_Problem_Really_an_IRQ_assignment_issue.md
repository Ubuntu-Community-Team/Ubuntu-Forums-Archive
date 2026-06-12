---
title: "Sound Problem? Really an IRQ assignment issue"
date: 2009-05-07
forum: Hardware
---

### Post by gorean on 2009-05-07
My issue is with a Tascam US-122l.

I need some help.  Even though I have been a member here for a long time this is the first time I have had to ask.  I have always been able to glean the answers I need from someone else's question.

The symptom is there is no sound. Currently none at all.  If I remove the .asoundrc file I have sound but it comes from the on board sound card.

First I would like to get this away from being a sound card issue.

I believe right now that the question is "how can I assign an IRQ to this card?".

Ubuntu 9.04
2.6.28-12-generic
alsa-1.0.20

To be thorough, a list of hardware:
Gigabyte MB GA-81865GME-775RH
Celeron 2.6 ghz processor
Award BIOS (not updated)
ATI 9800 pro video
1 IDE drive, 1 SATA drive, 1 DVD-RW
1 USB printer 
Keyboard and mouse are PS/2.
Tascam US-122L (the item in question)

Let me state categorically that the system recognizes the unit.  The modules and drivers are loaded. It shows up in /proc/asound/cards (but not with and IRQ) and if you plug a mike into it sound comes out the speakers.  The issue (I believe)is that ALSA only recognizes cards that have an IRQ.  Thusly even though my .asoundrc sets it up properly and all the modules (drivers, etc.) get loaded and even hwdinfo lists and all it's functionality correctly it is not available for use by any of the sound server/applications save jack and it only lists the midi ports.

Still aplay -l will list only the on board sound device and not the Tascam even though it immediately shows up in proc.
Per ALSA.org website "only real sound cards have IRQ's".  So I am assuming that this is the reason it is not available in ALSA/aplay.

I have tried all the HOWTO'S I can find, upgraded from source ALSA and all the rest of the related software.
I looked at compiling the kernel but could find nothing to change that seemed like it would make a difference.
I have moved the plugs and removed and replaced everything possible.
I have tried adding acpi=off irqpoll as kernel options in menu.lst.
I have tried adding noapic pci=irqroute pci=noacpi acpi=off irqpoll as kernel options in menu.lst.
Note that even though I cannot find documentation on these I believe they have been deprecated.  At least irqpoll gives an error message as an unknown command.
I have analyzed ad nauseum the results of all of the commands such as lspci, lsmod|grep '^snd',modinfo snd_usb_us122l, modinfo snd_usb_lib, modinfo snd_hwdep, cat /var/log/syslog | grep snd, cat /etc/modprobe.d/alsa-base.conf, hwinfo and more.  All give the results expected from a working situation.

Following is information that I think points to issue.

Error exert from dmesg during boot.  Finally the boot continues and but does not register the hardware.

[   18.208021] usb 1-5: device descriptor read/64, error -110
[   33.424020] usb 1-5: device descriptor read/64, error -110
[   33.640018] usb 1-5: new high speed USB device using ehci_hcd and address 4
[   48.752021] usb 1-5: device descriptor read/64, error -110
[   63.968022] usb 1-5: device descriptor read/64, error -110
[   64.184018] usb 1-5: new high speed USB device using ehci_hcd and address 5
[   74.592014] usb 1-5: device not accepting address 5, error -110
[   74.704023] usb 1-5: new high speed USB device using ehci_hcd and address 6
[   85.112015] usb 1-5: device not accepting address 6, error -110
[   85.112094] hub 1-0:1.0: unable to enumerate USB device on port 5
[   85.376016] usb 4-1: new full speed USB device using uhci_hcd and address 2
[  100.488018] usb 4-1: device descriptor read/64, error -110
[  115.704024] usb 4-1: device descriptor read/64, error -110
[  115.920016] usb 4-1: new full speed USB device using uhci_hcd and address 3
[  131.032019] usb 4-1: device descriptor read/64, error -110
[  146.248017] usb 4-1: device descriptor read/64, error -110
[  146.464017] usb 4-1: new full speed USB device using uhci_hcd and address 4
[  156.872023] usb 4-1: device not accepting address 4, error -110
[  156.984020] usb 4-1: new full speed USB device using uhci_hcd and address 5
[  167.392017] usb 4-1: device not accepting address 5, error -110
[  167.392090] hub 4-0:1.0: unable to enumerate USB device on port 1

When I plug it in after boot dmesg says:

[  490.680041] usb 1-5: new high speed USB device using ehci_hcd and address 7
[  490.812507] usb 1-5: config 1 interface 1 altsetting 1 bulk endpoint 0x83 has invalid maxpacket 9
[  490.849106] usb 1-5: configuration #1 chosen from 1 choice
[  492.384591] usbcore: registered new interface driver snd-usb-us122l


Following are the results from procinfo.  This may offer a picture worth examination.

procinfo
Memory:        Total        Used        Free     Buffers                       
RAM:         1026552      750436      276116       35800                       
Swap:        1646620           0     1646620                                   

Bootup: Thu May  7 13:44:11 2009   Load average: 0.06 0.08 0.02 2/201 7947     

user  :   00:07:53.75   4.6%  page in :           320998                       
nice  :   00:01:28.07   0.9%  page out:           291916                       
system:   00:03:26.86   2.0%  page act:            72046                       
IOwait:   00:01:06.73   0.6%  page dea:                0                       
hw irq:   00:00:08.10   0.1%  page flt:          2811335                       
sw irq:   00:00:01.56   0.0%  swap in :                0                       
idle  :   02:38:02.65  91.8%  swap out:                0                       
uptime:   02:52:07.21         context :          5557213                       

irq   0:        194  timer               irq  16:      77948  uhci_hcd:usb2, uh
irq   1:       5055  i8042               irq  17:     156749  Intel ICH5       
irq   8:          1  rtc0                irq  18:        175  ata_piix, uhci_hc
irq   9:          0  acpi                irq  19:          0  uhci_hcd:usb3    
irq  12:     257017  i8042               irq  20:      28945  eth0             
irq  14:      30855  ata_piix            irq  23:    1694355  ehci_hcd:usb1    
irq  15:      40253  ata_piix                                                  

sda            19695r           11153w   sdb1              28r               0w
sda1           19632r           11153w   sdb2              27r               0w
sda2               3r               0w   sdb3              30r               0w
sda5              39r               0w   sdb4               3r               0w
sdb              138r               0w   sdb5              28r               0w

lo          TX 1.98KiB       RX 1.98KiB       pan0        TX 0.00B         RX 0.00B        
eth0        TX 877.89KiB     RX 19.59MiB 

cat .asoundrc
# The usb_stream plugin configuration

pcm.!usb_stream {
	@args [ CARD ]
	@args.CARD {
		type string
		default "1"
	}

	type usb_stream

	card $CARD
}
Source for info on the .asoundrc comes from Fredrico at briata.org. It reflects the card correctly and like mentioned earlier with a mike sound comes out of the speakers.

---

