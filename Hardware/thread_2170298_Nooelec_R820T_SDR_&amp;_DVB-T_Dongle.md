---
title: "Nooelec R820T SDR &amp; DVB-T Dongle"
date: 2013-08-25
forum: Hardware
---

### Post by bcavotta on 2013-08-25
I've been trying for several weeks to get a Nooelec R820T SDR & DVB-T Dongle working with UBUNTU. Let me give some info first.

ACER Aspire 5100
Ram- 3 GB
Processor- AMD Turion 64x2 Mobile Technology TL-56 x2
OS- UBUNTU 13.04  32 bit
H.D. 150 GB
Dongle- NooElec R280T SDR & DVB-T
My problem is two fold. One issue is driver related, and the second is software related. Issue #1- The dongle I'm using is designed for reception of European T.V. transmissions, but can be used with several Software Defined Radio programs to receive HF/VHF/UHF radio transmissions. The program I'm currently working with is HDSDR which runs well in UBUNTU. The problem is that it doesn't see the dongle. There are multitudes of "fixes" on the web, but so far none have worked. I'm a newbie and have only been using linux for a few months. I've tried the "lsusb" command and the result has been " Buss 001 Device 005: obda:2838 Realtek Semiconductor Corp. RTL2838 DVB-T" so I think the system sees the dongle. I've also used the "dmseg" and I get this result  :
[  371.400303] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  371.400312] usb 1-7: Product: RTL2838UHIDIR
[  371.400319] usb 1-7: Manufacturer: Realtek
[  371.400326] usb 1-7: SerialNumber: 00000001
[  371.640050] usb 1-7: dvb_usb_v2: found a 'Realtek RTL2832U reference design' in warm state
[  371.640211] usbcore: registered new interface driver dvb_usb_rtl28xxu
[  371.707661] usb 1-7: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[  371.707746] DVB: registering new adapter (Realtek RTL2832U reference design)
[  371.711788] usb 1-7: dvb_usb_rtl28xxu: unknown tuner=NONE
[  371.724722] usb 1-7: dvb_usb_v2: 'Realtek RTL2832U reference design' error while loading driver (-19)
[  371.725503] usb 1-7: dvb_usb_v2: 'Realtek RTL2832U reference design' successfully deinitialized and disconnected
[  456.404228] r8712u: [r8712_got_addbareq_event_callback] mac = 00:1d:d1:4b:9f:b0, seq = 4800, tid = 0
[  564.890468] r8712u: [r8712_got_addbareq_event_callback] mac = 00:1d:d1:4b:9f:b0, seq = 6256, tid = 0
[ 1171.088484] r8712u: [r8712_got_addbareq_event_callback] mac = 00:1d:d1:4b:9f:b0, seq = 24080, tid = 0
[ 2077.782729] r8712u: [r8712_got_addbareq_event_callback] mac = 00:1d:d1:4b:9f:b0, seq = 31040, tid = 0
[ 2137.733844] r8712u: [r8712_got_addbareq_event_callback] mac = 00:1d:d1:4b:9f:b0, seq = 35264, tid = 0
[ 2148.494293] r8712u: [r8712_got_addbareq_event_callback] mac = 00:1d:d1:4b:9f:b0, seq = 37296, tid = 0
[ 2367.215142] r8712u: [r8712_got_addbareq_event_callback] mac = 00:1d:d1:4b:9f:b0, seq = 45216, tid = 0
[ 2432.525313] r8712u: [r8712_got_addbareq_event_callback] mac = 00:1d:d1:4b:9f:b0, seq = 47648, tid = 0
[ 2572.166317] r8712u: [r8712_got_addbareq_event_callback] mac = 00:1d:d1:4b:9f:b0, seq = 52752, tid = 0
[ 2703.069815] usb 1-7: USB disconnect, device number 4
[ 2715.029264] r8712u: [r8712_got_addbareq_event_callback] mac = 00:1d:d1:4b:9f:b0, seq = 54448, tid = 0
[ 2842.061090] r8712u: [r8712_got_addbareq_event_callback] mac = 00:1d:d1:4b:9f:b0, seq = 55872, tid = 0
[ 2859.502992] systemd-hostnamed[2800]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 3442.375690] r8712u: [r8712_got_addbareq_event_callback] mac = 00:1d:d1:4b:9f:b0, seq = 62640, tid = 0
[ 4075.092622] r8712u: [r8712_got_addbareq_event_callback] mac = 00:1d:d1:4b:9f:b0, seq = 3712, tid = 0
[ 4326.963864] r8712u: [r8712_got_addbareq_event_callback] mac = 00:1d:d1:4b:9f:b0, seq = 6784, tid = 0
[ 4373.636137] usb 1-7: new high-speed USB device number 5 using ehci-pci
[ 4373.780288] usb 1-7: New USB device found, idVendor=0bda, idProduct=2838
[ 4373.780303] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 4373.780312] usb 1-7: Product: RTL2838UHIDIR
[ 4373.780320] usb 1-7: Manufacturer: Realtek
[ 4373.780326] usb 1-7: SerialNumber: 00000001
[ 4373.786239] usb 1-7: dvb_usb_v2: found a 'Realtek RTL2832U reference design' in warm state
[ 4373.853090] usb 1-7: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[ 4373.853178] DVB: registering new adapter (Realtek RTL2832U reference design)
[ 4373.853962] usb 1-7: dvb_usb_rtl28xxu: unknown tuner=NONE
[ 4373.867020] usb 1-7: dvb_usb_v2: 'Realtek RTL2832U reference design' error while loading driver (-19)
[ 4373.867942] usb 1-7: dvb_usb_v2: 'Realtek RTL2832U reference design' successfully deinitialized and disconnected
[ 4617.579270] r8712u: [r8712_got_addbareq_event_callback] mac = 00:1d:d1:4b:9f:b0, seq = 9472, tid = 0
[ 4761.639870] r8712u: [r8712_got_addbareq_event_callback] mac = 00:1d:d1:4b:9f:b0, seq = 11136, tid = 0

This looks like it can't load the driver.  At first I thought that the dongle may be bad, but I installed the same software on a Windows 7 machine and it works as it should. I run the program on UBUNTU using Wine and it seems to operate as it should except not seeing the dongle. I've installed the same driver in both systems.

Let me appologize in advance if I've posted this in the wrong section and any assistance would be greatly appreciated

---

### Post by joblacker on 2013-12-01
I haven't found a good way for HDSDR to "talk" with the dongle, yet.  I've gone around in circles several times.  There's a program called BorIP which is supposed to act as a "go-between" the dongle and HDSDR, but I've not had any success with it.  I've tried using the rtl package and the Winrad 1.6.1 software, but it's not too user friendly and I've abandoned using it.  I did have some limited success with a package called SDRSharp.  You install it, you install the rtl "helpers" software and then you disable the kernel module dvb_usb_rtl28xxu so that rtl_tcp will work.  The program rtl_tcp seems to act as a go between and SDRSharp does the displaying.  SDRSharp is pretty good in my mind...since I've gotten it to work, it's infinitely better than HDSDR.  I'll help any way I can and if someone can explain a better way to make this stuff come together, I'm all ears>

---

