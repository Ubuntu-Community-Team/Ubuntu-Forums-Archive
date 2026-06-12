---
title: "7600 GT causing problems"
date: 2008-06-01
forum: Hardware
---

### Post by 00zer0 on 2008-06-01
Hi there. I'll start by pointing out im new to Ubuntu/linux.
I might also be posting in the wrong place, perhap I could just be pointed in the right direction.

My question:
Is my videocard faulty?


A few weeks ago I replaced windows with Ubuntu on my desktop machine.
I decided yesturday to install ubuntu on my old computer to be a media server for my PS3. Anpluged my Desktop.
After I finished with the server s ive only got one screen/mouse/keyboard etc I u(for now) I plugged my desktop back in.
It powered up fine. But once I was logged in the screen was what I can only describe as flickering. Thinking I had not pluged it back in fully I checked the back of the pc. it was ok. After about 5minutes the screen went black.
The screen was still on. It had NOT turned off because no input.

I turned the computer off. The screen picked up the lack of input and turned off as well. When I turned it back on, the screen turned on but stayed black..

I unpluged the desktop and pluged in the server in to see if it was the screen or something else that was causing the problem. The screen worked fine.

The 7600 GT has 2 DVI plugs on it, so I tryed the other one.
When I power the computer back on. after about 15seconds the screen finaly turns on and it starts to post.
It doesnt just delay the screen turning on but the whole system startup.
Basically it takes about 18second or so to get to the 'press F2 to enter setup'. Which used to be about 2/3seconds (straight after video test)
However after this delay it does boot. I see all the post (be it delayed) then the Ubuntu loading screen. But when the gdm login is due to pop up, i get the 'no input detected' and the screen turns off.
If I press Ctrl + Alt + F1, the screen does turn back on at the command promt. Im sure this is because gdm is configured to use the DVI1 output, not the DVI2 that its now pluged into. Ill make another post asking how to change that.

I have opened the case and reseated the card. It wasnt loose at all. Ive also had a go at blowing the plugs to make sure something hadnt floated in there when I was moving the monitor cable over and back.
I unplugged my hdd's and dvd rom. (I have no pci cards or anything else) and tryed rebooting. same problem.

Is my card faulty or what?
Im guessing the powersupply or motherboard cant be to blame?
No hardware errors come up anywhere.
I dont know of any tests I can do to test the card.
The card is PCI-E and I dont have another to take it out and test.


I dont fully understand all this, but ive done a 'sudo lshw -short' to try and show some of my hardware spec.
If there is another command that shows this better, please just let me know and ill run it.


H/W path             Device     Class       Description
=======================================================
                                system      PROD00000000
/0                              bus         965P-S3
/0/0                            memory      128KiB BIOS
/0/4                            processor   Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
/0/4/a                          memory      20KiB L1 cache
/0/4/b                          memory      L2 cache
/0/4/1.1                        processor   Logical CPU
/0/4/1.2                        processor   Logical CPU
/0/1b                           memory      1GiB System Memory
/0/1b/0                         memory      512MiB DIMM 66 MHz (15.2 ns)
/0/1b/1                         memory      DIMM 41486 MHz (0.0 ns) [empty]
/0/1b/2                         memory      512MiB DIMM 66 MHz (15.2 ns)
/0/1b/3                         memory      DIMM 42510 MHz (0.0 ns) [empty]
/0/1                            processor
/0/1/1.1                        processor   Logical CPU
/0/1/1.2                        processor   Logical CPU
/0/100                          bridge      82P965/G965 Memory Controller Hub
/0/100/1                        bridge      82P965/G965 PCI Express Root Port
/0/100/1/0                      display     G70 [GeForce 7600 GT]
/0/100/1a                       bus         82801H (ICH8 Family) USB UHCI Controller #4
/0/100/1a.1                     bus         82801H (ICH8 Family) USB UHCI Controller #5
/0/100/1a.7                     bus         82801H (ICH8 Family) USB2 EHCI Controller #2
/0/100/1b                       multimedia  82801H (ICH8 Family) HD Audio Controller
/0/100/1c                       bridge      82801H (ICH8 Family) PCI Express Port 1
/0/100/1c.3                     bridge      82801H (ICH8 Family) PCI Express Port 4
/0/100/1c.3/0                   storage     JMicron 20360/20363 AHCI Controller
/0/100/1c.3/0.1                 storage     JMicron 20360/20363 AHCI Controller
/0/100/1c.4                     bridge      82801H (ICH8 Family) PCI Express Port 5
/0/100/1c.4/0        eth0       network     88E8056 PCI-E Gigabit Ethernet Controller
/0/100/1d                       bus         82801H (ICH8 Family) USB UHCI Controller #1
/0/100/1d.1                     bus         82801H (ICH8 Family) USB UHCI Controller #2
/0/100/1d.2                     bus         82801H (ICH8 Family) USB UHCI Controller #3
/0/100/1d.7                     bus         82801H (ICH8 Family) USB2 EHCI Controller #1
/0/100/1e                       bridge      82801 PCI Bridge
/0/100/1f                       bridge      82801HB/HR (ICH8/R) LPC Interface Controller
/0/100/1f.2          scsi5      storage     82801H (ICH8 Family) 4 port SATA IDE Controller
/0/100/1f.2/0.0.0    /dev/sda   disk        80GB ST380811AS
/0/100/1f.2/0.0.0/1  /dev/sda1  volume      1953MiB Linux swap volume
/0/100/1f.2/0.0.0/2  /dev/sda2  volume      18GiB EXT3 volume
/0/100/1f.2/0.0.0/3  /dev/sda3  volume      53GiB EXT3 volume
/0/100/1f.3                     bus         82801H (ICH8 Family) SMBus Controller
/0/100/1f.5                     storage     82801H (ICH8 Family) 2 port SATA IDE Controller

---

