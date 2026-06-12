---
title: "Need help with Dynex wireless card"
date: 2009-12-22
forum: Hardware
---

### Post by Siruami on 2009-12-22
Hi everybody and specially experts.
I am switching to Ubuntu and inviting friends to do as well, well my neighbor has a very old laptop, Dell inspiron 3800, I suggested him to install Ubuntu to make it more stable and at least make it work, becuase Windows updates have fill  it's 10GB already and after lots of No more virtual memory errors and not working at all he wants to give it a shot to Ubuntu.

We tried first the alternative install Xubuntu, everything went OK but didn't take the Dynex Wireless Enhanced G card he has attached to the PCI port. We tried for several hours but couldn't fix it.
After 1 day of trying I though maybe Xubuntu was the problem so we decide to install the full Ubuntu, which is the Hardy version.
Still the same result, no wireless card even detected.
This is even the first time I have to go to the terminal to try to fix something, so here is some data that I think you will be need to know more about the problem:

 lspci shows:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:03.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
00:08.1 Communication controller: ESS Technology ES1983S Maestro-3i PCI Modem Accelerator (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
02:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

iwconfig shows:

lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I know is detecting it because I have take the card out and run the commands and have different responses or no response at all.
I have tried several things for a couple of hours now without success, the last think I tried was one related to ndiswrapper and install Windows drivers but the result was:
Driver installed, hardware present : NO and obviously the hardware is there.
The drivers actually include a folder for LINUX which has one c file and one h file, but I have no clue how to use.
One more thing, the leds on the card are not even turned on; I guess because it doesn't have something.

If you can advice please help, I will really appreciate all you can do, have great Christmas season.

Siruami

---

### Post by Siruami on 2010-01-27
Believe it or not I solved this. Not very happy with it tough...
I just removed the Dynex card from the computer and put a Dell Wireless card from another computer I temporarily put my hands on, Xubuntu detect it immediately and worked like a charm.
I told about this to the owner, who also had another laptop VAIO, and he decided to switch cards, so to the VAIO I installed Ubuntu Karmic with the Dynex Card and to the Dell the Dell Wireless card and Xubuntu, both computers working as new.
Hope this helps.

---

