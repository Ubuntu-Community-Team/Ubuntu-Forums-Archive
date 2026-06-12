---
title: "How do i read input from a gameport?"
date: 2022-08-07
forum: Hardware
---

### Post by pqwoerituytrueiwoq on 2022-08-07
For those who have no idea what i am talking about: [https://en.wikipedia.org/wiki/Game_port](https://en.wikipedia.org/wiki/Game_port)

i want to set the buttons to run commands/scripts

```
chad@niceServer:~$ lsmod | grep game 
gameport               20480  4 cobra,snd_cmipci,emu10k1_gp 
chad@niceServer:~$ ls /dev/input/ 
by-pathevent0event1event10event11event2event3event4event5event6event7event8event9mice
chad@niceServer:~$ sudo lspci -n -v -s 1f:00.1      
1f:00.1 0980: 1102:7003 (rev 04) 
        Subsystem: 1102:0040 
        Flags: bus master, medium devsel, latency 32, IOMMU group 10 
        I/O ports at a040 [size=8] 
        Capabilities: [dc] Power Management version 2 
        Kernel driver in use: Emu10k1_gameport 
        Kernel modules: emu10k1_gp 

chad@niceServer:~$ sudo cat /proc/ioports      
0000-0000 : PCI Bus 0000:00 
  0000-001f : dma1 
  0020-0021 : pic1 
  0040-0043 : timer0 
  0050-0053 : timer1 
  0060-0060 : keyboard 
  0064-0064 : keyboard 
  0080-008f : dma page reg 
  00a0-00a1 : pic2 
  00c0-00df : dma2 
  00f0-00ff : fpu 
0000-0000 : PCI Bus 0000:00 
0000-0cf7 : PCI Bus 0000:00 
  0061-0061 : PNP0800:00 
  0070-0071 : rtc0 
  040b-040b : pnp 00:04 
  04d0-04d1 : pnp 00:04 
  04d6-04d6 : pnp 00:04 
  0800-089f : pnp 00:04 
    0800-0803 : ACPI PM1a_EVT_BLK 
    0804-0805 : ACPI PM1a_CNT_BLK 
    0808-080b : ACPI PM_TMR 
    0810-0815 : ACPI CPU throttle 
    0820-0827 : ACPI GPE0_BLK 
  0900-090f : pnp 00:04 
  0910-091f : pnp 00:04 
  0a00-0a0f : pnp 00:03 
  0a10-0a1f : pnp 00:03 
  0a20-0a2f : pnp 00:03 
    0a25-0a26 : nct6775 
      0a25-0a26 : nct6775 
  0a30-0a3f : pnp 00:03 
  0b00-0b0f : pnp 00:04 
    0b00-0b08 : piix4_smbus 
  0b20-0b3f : pnp 00:04 
    0b20-0b28 : piix4_smbus 
  0c00-0c01 : pnp 00:04 
  0c14-0c14 : pnp 00:04 
  0c50-0c51 : pnp 00:04 
  0c52-0c52 : pnp 00:04 
  0c6c-0c6c : pnp 00:04 
  0c6f-0c6f : pnp 00:04 
  0cd0-0cd1 : pnp 00:04 
  0cd2-0cd3 : pnp 00:04 
  0cd4-0cd5 : pnp 00:04 
  0cd6-0cd7 : pnp 00:04 
  0cd8-0cdf : pnp 00:04 
0cf8-0cff : PCI conf1 
[B]0d00-ffff : PCI Bus 0000:00 
  a000-cfff : PCI Bus 0000:15 
    a000-cfff : PCI Bus 0000:16 
      a000-afff : PCI Bus 0000:1e 
        a000-afff : PCI Bus 0000:1f 
          a000-a03f : 0000:1f:00.0 
          a000-a03f : EMU10K1 
          a040-a047 : 0000:1f:00.1 
          a040-a047 : emu10k1-gp [/B]
      b000-bfff : PCI Bus 0000:1c 
        b000-bfff : PCI Bus 0000:1d 
          b000-b0ff : 0000:1d:04.0 
          b000-b0ff : oxygen 
      c000-cfff : PCI Bus 0000:1b 
        c000-c0ff : 0000:1b:00.0 
  d000-dfff : PCI Bus 0000:38 
    d000-d0ff : 0000:38:00.0 
  e000-efff : PCI Bus 0000:2e 
    e000-e07f : 0000:2e:00.0 
      e000-e07f : ahci 
    e080-e0ff : 0000:2e:00.0 
      e080-e0ff : ahci 
    e100-e17f : 0000:2e:00.0 
      e100-e17f : ahci 
    e180-e1ff : 0000:2e:00.0 
      e180-e1ff : ahci 
    e200-e27f : 0000:2e:00.0 
      e200-e27f : ahci 
  f000-ffff : PCI Bus 0000:10 
    f000-f01f : 0000:10:00.1 
    f020-f03f : 0000:10:00.0

```

long term goal is to make use of this port for a custom DIY control panel

---

### Post by Holger_Gehrke on 2022-08-07
I could be wrong, put if there's something connected to the port which has resistors between 1 and 100 kOhm (those would be potentiometers with a real joystick) connected to the pins for the axis', a kernel module for a joystick should get loaded and you'd get a device /dev/input/js**n** (with n an integer between 0 and some upper limit). You could then read the state of the button with appropriate ioctl calls. Since a game port has only 4 buttons, you probably will want to use the axis' for buttons with some resistors of differing values ...

Holger

---

### Post by pqwoerituytrueiwoq on 2022-08-07
the controller i have just has switches that get pressed by the 'joystick', it has 8 buttons and a joy stick for 12 switches, there are also a couple of membrane buttons, one is labeled autofire/autofire off (prob some kind of macro thing) the joystick is just as functional as the d-pad on a game boy color

but no potentiometers (guess they cost too much so they cheap out and used switches)

---

### Post by Holger_Gehrke on 2022-08-08
8 Buttons ? Then it's probably one of the later examples of game port joysticks. Those usually had some kind of microcontroller onboard and used some proprietary serial protocol to transmit button presses and axis positions, often abusing the midi lines found on the game port on soundcards so they wouldn't work on a game port on a multi-io card. I used to have a Microsoft Sidewinder Gamepad back in the day and the additional buttons only worked either in Windows with a driver or in DOS programs  which had a specific option for this pad; in DOS games which didn't know the pad all but four of the buttons were dead ...

Holger

---

### Post by pqwoerituytrueiwoq on 2022-08-08
if that is the case based on what you said it should show up in the os if i take a 3k resistor (i have a LOT of these) and use it to connect pins 1 (5v) and 3 (x axis) or do i need to make it see a y asis? if so what about pins 11 and 13?

---

### Post by Holger_Gehrke on 2022-08-09
I don't know which axis the kernel module needs to see a resistor on. So my advice is experiment but be careful. Because of the way the axis' get read there's actually a bit of current on that interface and you can damage your card if you make a mistake.

But taking your stated goal of building a custom control panel, I'd probably go with the kind of thing I see on [https://hackaday.com](https://hackaday.com) when I search for 'macropad'; these are usually USB devices that come up as USB-HID devices. A lot of these projects are well documented with Gerber files for the PCB and source code and/or binary dumps for the firmware.

Holger

---

### Post by pqwoerituytrueiwoq on 2022-08-09
this interface uses 5v, with a 3 k resistor it would be between 1.16 and 1.17 mA and the pin out says it says the axis is 0-100k, if lower is left and 100k is right and 50k is center then right is 0 (0k = short) so i should be able use a piece of scrap ethernet/phone/door bell cable/wire

Here is a teardown of the controller i have on hand: [https://imgur.com/a/PWvBAdb](https://imgur.com/a/PWvBAdb)

edit: mod probing analog made the input/js0 appear, that said only 4 buttons and the joystick work with jstest, but that is something, that is enough i can start messing with software

---

