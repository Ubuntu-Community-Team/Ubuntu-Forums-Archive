---
title: "Proprietary Hardware Driver Issues"
date: 2010-06-24
forum: Hardware
---

### Post by Masmidow on 2010-06-24
Dear Ubuntu Community Support,

Hey! I am very new to Ubuntu and have just successfully completed full installation of this OS after extended hard drive partitioning trouble. I am dual booting on a laptop with Windows 7. Upon complete installation of Ubuntu 10.04, I have found that there are no proprietary hardware drivers installed. I also do not have any WiFi connection. I am not a very technical person, but I have heard that Ubuntu is worth a try (because it speeds up your system). 

[B]The Tech. Specs. of my machine are as follows:

Computer: HP Pavilion Laptop dv6-2150us
Processor: Intel(R) Core(TM) i3 CPU    M 330 @2.13GHz  2.13GHZ
RAM: 4.00 GB (3.80 GB usable)

64-bit Operating System
Windows 7 Home Premium
Ubuntu 10.04 LTS[/B]

(See Full Hardware/Software List Below)

Forgive me for being explicit; I am a "noob", so to speak, and am not sure what is necessary to help. The two questions I need answered are:
[FONT=Arial Black]
[I]1.) How to I establish my WiFi connection?

2.) How do I get all of the necessary hardware drivers for my system to work properly?[/I][/FONT]  

Thank you very much in advance!

     Sincerely,

                        Michael S.

P.S. If you have any further questions about my specific hardware and software situation, please do not hesitate to ask. :-)

[SIZE=4]**[COLOR=Red]Complete (Ultra Explicit) Hardware Reference [/COLOR]:D **[/SIZE][B]

Product Name:

[/B]dv6-2150us[B]

Product Number:

[/B]WA779UA#ABA[B]

Microprocessor:

[/B]2.13GHz Intel Core i3-330M  Processor 

[B]Microprocessor Cache:

[/B] 3MB L3 Cache[B]

Memory:

[/B]4GB DDR3 System Memory (2 DIMM)

**Memory  Max**: 8192MB[B]

Video  Graphics:

[/B]Intel  HD Graphics

[B]Video Memory:

[/B]Up to 1696MB

[B]Hard Drive: 

[/B]320GB (7200RPM)[B]

Multimedia  Drive[/B]:

LightScribe  SuperMulti 8X DVD±R/RW with Double Layer Support   [B]

Display:

[/B]15.6" Diagonal High-Definition   LED HP BrightView Display (1366x760)

[B]Network Card:

[/B]Integrated 10/100 Ethernet LAN 

**Wireless  Connectivity:**
[LIST]
[*]802.11b/g/n  WLAN
[*] Bluetooth
[/LIST]
**Sound:**
[LIST]
[*]Altec Lansing with SRS  Premium Sound
[/LIST]
[B]Keyboard:

[/B]101-key compatible with full-size keyboard  with integrated numeric keypad

[B]Pointing Device:

[/B]Touch Pad with On/Off button and  dedicated vertical scroll Up/Down pad

[B]PC Card Slots:

[/B]1 ExpressCard/54 Slot (also  supports ExpressCard/34)

**External Ports:**
[LIST]
[*]5-in-1 integrated Digital  Media Reader for Secure Digital cards, MultiMedia cards, Memory Stick,  Memory Stick Pro, or xD Picture cards
[*]4 Universal Serial Bus  (USB) 2.0, 4th port shared with eSATA
[*] 2 Headphone out
[*] 1  microphone-in
[*]  1 HDMI
[*] 1 VGA (15-pin)
[*] 1 eSATA  + USB 2.0
[*] 1 RJ-11 (modem)
[*] 1 RJ -45 (LAN)
[*] 1  notebook expansion port 3
[*] 1 Consumer IR (Remote Receiver)
[/LIST]
**Other  Devices:**
[LIST]
[*]  HP Webcam with integrated digital microphone
[/LIST]
[B]Dimensions:

[/B] 14.9" (L) x 10.15" (D) x 1.33"  (min H)/1.61" (max H)[B] 

Weight:[/B] 6.34 lbs 

**Security:**
[LIST]
[*]Kensington MicroSaver lock  slot
[*] Power-on password
[*] Accepts 3rd party security  lock devices
[/LIST]
**Power:**
[LIST]
[*]65W AC Adapter
[*]6-Cell  Lithium-Ion Battery
[/LIST]
 
**Software****Operating System:**

Genuine Windows 7 Home Premium 64-bit

 **Security and Support:**

Symantec Norton Internet  Security  2010 60-day Trial

HP  Support Assistant

---

### Post by Yellow Pasque on 2010-06-24
It depends on the wireless chipset. Commands like these might tell you:
```
lspci
sudo lshw -C network
```

---

### Post by Masmidow on 2010-06-24
> **Temüjin said:**
> It depends on the wireless chipset. Commands like these might tell you:
```
lspci
sudo lshw -C network
```


Thank you for such a quick reply. I guess they weren't lying about the community support.

I have the problem solved. Thanks!!!

---

