---
title: "Ubuntu 7.10 on Sony Vaio: Wireless problem"
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by farazhussain on 2007-11-23
Hi All,

I'm just got a Sony Vaio VGN NR110E laptop. I tried to get rid of Vista straight away. 

First, there was a problem with the installation since it won't recognize my display card. Using google I  found that I can just use the OEM install option. 

That's worked just fine.

Everything seems to be working great except for the wireless.

Anyone has the same problem?

I tried to look around but can't  find anything useful. I already have ndiswrapper installed.

Thanks,

Regards,

Faraz.

---

### Post by opteek on 2007-11-23
399 at BB, right? I just got installed ubuntu on the same machine a few minutes ago. Same   problem with the integrated atheros 54g. 

I get this line from dmesg, I think it's related:

wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)

---

### Post by farazhussain on 2007-11-23
> **opteek said:**
> 399 at BB, right? I just got installed ubuntu on the same machine a few minutes ago. Same   problem with the integrated atheros 54g. 

I get this line from dmesg, I think it's related:

wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)

Yes, just got it from BB.

And I'm getting exactly the same message as you on running 'dmesg'.

I heard there would be some problems with the sound and display -- but all that seems to be fine so far, except for the display problem I had during installation.

---

### Post by chalewa on 2007-11-24
same problem...

its an atheros ar5006eg which is in a few toshiba models as well, so i guess i will try to go the ndiswrapper route. kinda annoying that the atheros driver isn't supporting it.

---

### Post by EricMattessich on 2007-11-24
I just picked up a vgn-nr110e at the BB sale and i'd like to ditch the vista for ubuntu... do you think the Atheros AR5BXB63 driver from the asus eee pc would work? I mean ubuntu and xandros (which is what the eee pc uses) are both Debian-based so the driver should run.... just wonder if it would run the hardware....i dunno if i figure anything out ill post.

---

### Post by chalewa on 2007-11-24
well the first battle is going to be getting the wireless card to actually 'turn on'

---

### Post by chalewa on 2007-11-24
well spent the majority of the day trying to get the wireless card to power on, doesn't seem to want to work. 

i don't know what else to do at this point

---

### Post by karnage1 on 2007-11-24
this i posted 4 hours ago
"ubuntu didnt work on the video side on a cd run
i figured the help file and used the sample help line on the cd and it worked
live vga=771 noapic nolapic

but what does it mean? is my onboard video suported? i want to cross over but i would like to know for sure that the laptop is going to work media readers cd dvd dual layer burner usb audio vga out modem and eth0 will work? does ubuntu and the gnu apps take advantage of dual core?

please if anyone has this laptop and knows that everything is peachy let me know."

with no response, but now i see ty for the info.

pls i used that comand to start the video but were can i get the video drivers?

---

### Post by chalewa on 2007-11-25
> **karnage1 said:**
> this i posted 4 hours ago
"ubuntu didnt work on the video side on a cd run
i figured the help file and used the sample help line on the cd and it worked
live vga=771 noapic nolapic

but what does it mean? is my onboard video suported? i want to cross over but i would like to know for sure that the laptop is going to work media readers cd dvd dual layer burner usb audio vga out modem and eth0 will work? does ubuntu and the gnu apps take advantage of dual core?

please if anyone has this laptop and knows that everything is peachy let me know."

with no response, but now i see ty for the info.

pls i used that comand to start the video but were can i get the video drivers?

i installed xubuntu rather than ubuntu and had no video or sound issues...

maybe try that, and then install gnome on top of it.

---

### Post by ruchirbhai on 2007-11-25
hi Coulhelp me in installing ubuntu on Sony Vaio NR110E also how to user the OEM installation

Thanks in advance

Ruchir

---

### Post by chalewa on 2007-11-25
when you put the install disc in, there should be an option to install ubuntu, and then a couple more options down, there is an OEM install option. That is the one that you want.

---

### Post by farazhussain on 2007-11-25
Did anyone get the wireless working?

---

### Post by chalewa on 2007-11-25
no. there is supposedly a way to make the wireless lan card turn on, which is the first battle, but i have not been able to get it to work.

---

### Post by ejw2076 on 2007-11-25
How the hell do we get power to it?

---

### Post by chalewa on 2007-11-25
> **ejw2076 said:**
> How the hell do we get power to it?



haha your guess is as good as mine, after doing some more reading, there was a sonypi driver that supposedly helped to turn the card on, but there was no mention of this model number, and the driver has now turned into a driver known as sony-laptop.

---

### Post by ejw2076 on 2007-11-25
```
wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)

```
```

           *-network UNCLAIMED
                description: Ethernet controller
                product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0

```
```

06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: Foxconn International, Inc. Unknown device e000
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at fa000000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>
```

So we are obviously dealing with the **ar5006eg**.  [This]("http://madwifi.org/ticket/1206") page is working on the ar5005g.

[This]("http://www.jonhuxley.com/linux-laptops/") page says to get it to work we need the windows drivers from our windows backup partition.

---

### Post by ejw2076 on 2007-11-25
> **chalewa said:**
> haha your guess is as good as mine, after doing some more reading, there was a sonypi driver that supposedly helped to turn the card on, but there was no mention of this model number, and the driver has now turned into a driver known as sony-laptop.

Well, the computer is obviously seeing it, thats why dmesg spits out a model number, this seems to be the same problem that other laptops are having with this and the ar5005g.

---

### Post by chalewa on 2007-11-25
yea i tried to use ndiswrapper to get it working, but it kept complaining that the driver i was trying to install was invalid....

---

### Post by ejw2076 on 2007-11-25
[http://www.atheros.cz/](http://www.atheros.cz/)

---

### Post by chalewa on 2007-11-25
> **ejw2076 said:**
> Well, the computer is obviously seeing it, thats why dmesg spits out a model number, this seems to be the same problem that other laptops are having with this and the ar5005g.


good point, hadn't thought about that. the reason i thought that it was not getting 'turned on' was because the led light on the front was not lit when the switch was moved to on.

---

### Post by ejw2076 on 2007-11-25
all the ar5006eg drivers come with a .inf file that reads for 5001

---

### Post by ejw2076 on 2007-11-25
> **chalewa said:**
> good point, hadn't thought about that. the reason i thought that it was not getting 'turned on' was because the led light on the front was not lit when the switch was moved to on.

I don't think there is a light for wifi.  Or at least I didn't notice one when I booted into vista, just a light on the vista desktop that went on and off with the switch.

---

### Post by chalewa on 2007-11-25
> **ejw2076 said:**
> I don't think there is a light for wifi.  Or at least I didn't notice one when I booted into vista, just a light on the vista desktop that went on and off with the switch.

if you look at the front of the computer, where the sd card slot is, there is a switch on the far right for wireless lan

---

### Post by ejw2076 on 2007-11-25
> **chalewa said:**
> if you look at the front of the computer, where the sd card slot is, there is a switch on the far right for wireless lan

I see the switch, but unlike my other laptop I don't think there is an led light that is on when the wireless is on.  I'm still trying to get my ndiswrapper configured.

---

### Post by chalewa on 2007-11-25
ok let me know if you can get the driver installation part.

---

### Post by ejw2076 on 2007-11-25
> **chalewa said:**
> ok let me know if you can get the driver installation part.

```

eric@vaio:~$ tail /var/log/messages
Nov 25 20:39:46 vaio kernel: [  145.948000] PCI: Enabling device 0000:06:00.0 (0000 -> 0002)
Nov 25 20:39:46 vaio kernel: [  145.948000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Nov 25 20:39:46 vaio kernel: [  145.948000] ndiswrapper (ZwClose:2227): closing handle 0xe41d7828 not implemented
Nov 25 20:39:46 vaio kernel: [  145.948000] ndiswrapper (mp_init:216): couldn't initialize device: C000009A
Nov 25 20:39:46 vaio kernel: [  145.948000] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
Nov 25 20:39:46 vaio kernel: [  145.948000] ndiswrapper (mp_halt:259): device e2634500 is not initialized - not halting
Nov 25 20:39:46 vaio kernel: [  145.948000] ndiswrapper: device eth%%d removed
Nov 25 20:39:46 vaio kernel: [  145.948000] ACPI: PCI interrupt for device 0000:06:00.0 disabled
Nov 25 20:39:46 vaio kernel: [  145.948000] ndiswrapper: probe of 0000:06:00.0 failed with error -22
Nov 25 20:39:46 vaio kernel: [  145.948000] usbcore: registered new interface driver ndiswrapper

```

So the 5001 driver isn't working at all.  We need the original driver that comes with vista.

---

### Post by ejw2076 on 2007-11-25
[http://www.mail-archive.com/madwifi-tickets@lists.sourceforge.net/msg06396.html](http://www.mail-archive.com/madwifi-tickets@lists.sourceforge.net/msg06396.html)


are we sure that we have this card?

---

### Post by ejw2076 on 2007-11-25
I guess we could try [this]("http://ubuntuforums.org/showthread.php?t=512828") tut.  Seems as though it could work.

---

### Post by ejw2076 on 2007-11-25
```
eric@vaio:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Alright... Now for configuration.
I removed the net5221.inf using the gui, then selected the net5211.inf downloaded from [here]("http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz").

---

### Post by chalewa on 2007-11-25
> **ejw2076 said:**
> ```
eric@vaio:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Alright... Now for configuration.
I removed the net5221.inf using the gui, then selected the net5211.inf downloaded from [here]("http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz").

same place as you



edit: ok got it. used wicd to manage the wireless network. for some reason, network manager was not working right...


it wouldn't auto find the network, so i had to type in the ssid, but after that no problems.,,,

i wonder why lspci gives the wrong info

---

### Post by farazhussain on 2007-11-25
My Iwconfig only gives this:

faraz@hussain-computer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

'dmesg' gives this:

faraz@hussain-computer:~$  dmesg | grep wifi
[   14.860000] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)

---

### Post by farazhussain on 2007-11-25
[QUOTE=ejw2076;3839060]
```

           *-network UNCLAIMED
                description: Ethernet controller
                product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0

```
```

06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: Foxconn International, Inc. Unknown device e000
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at fa000000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>
```


How did you get those two outputs? Which command to I have to run to see that.

I don't think my dmesg throws out either of those.

faraz@hussain-computer:~$ dmesg | grep Ethernet
faraz@hussain-computer:~$ dmesg | grep network
faraz@hussain-computer:~$

---

### Post by ejw2076 on 2007-11-25
> **farazhussain said:**
> [QUOTE=ejw2076;3839060]
```

           *-network UNCLAIMED
                description: Ethernet controller
                product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0

```
```

06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: Foxconn International, Inc. Unknown device e000
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at fa000000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>
```


How did you get those two outputs? Which command to I have to run to see that.

I don't think my dmesg throws out either of those.

faraz@hussain-computer:~$ dmesg | grep Ethernet
faraz@hussain-computer:~$ dmesg | grep network
faraz@hussain-computer:~$

lshw

lspci -vv


I had it working, but very slowly.  So I know the driver works, but I'm not sure if the driver was slow, or the network manager I was using.  I'm going to try to get it to work with knetworkmanager.

---

### Post by farazhussain on 2007-11-26
> **ejw2076 said:**
> [QUOTE=farazhussain;3839685]

lshw

lspci -vv


I had it working, but very slowly.  So I know the driver works, but I'm not sure if the driver was slow, or the network manager I was using.  I'm going to try to get it to work with knetworkmanager.

Here's what i get:

faraz@hussain-computer:~$  lspci | grep Ethernet
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)


Then on doing 'lspci -vv':

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
        Subsystem: Sony Corporation Unknown device 902d
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at f6000000 (64-bit, non-prefetchable) [size=16K]
        Region 2: I/O ports at 2000 [size=256]
        Capabilities: <access denied>

06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: Foxconn International, Inc. Unknown device e000
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at fa000000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>


'

---

### Post by farazhussain on 2007-11-26
Okay, I'm getting the same message as you now on doing lshw:

faraz@hussain-computer:~$ lshw | grep network -A 5
WARNING: you should run this program as super-user.
           *-network      
                description: Ethernet interface
                product: 88E8039 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
--
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
f

---

### Post by ejw2076 on 2007-11-26
I have no idea what to do now.  I have to get the KNetworkManager to see the WiFI card and give me the Wireless Icon in the System tray (right now I just get the wired icon.)  If anyone has any idea how to do this please share.

Summary:
I believe that it is the ar5006eg wifi card, but I can't be sure.  The windows driver that is suggested for it under xp, reads "for 5001" in the .inf file, as do the rest of the drivers for the 500x series.


The switch does work in linux, if you boot the nr110e with the switch off, the wifi card will not be detected, but switching it on while running wont allow it to be visible in the KNeworkManager configuation.

followed: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) to install ndiswrapper (I used aptitude.)

got the ar5211.inf driver for the card, I was able to get it to work for a short while under wicd, but it was painfully slow.

So the problem now seems to get KNetworkManager to realize that there is a wifi card and to display the wireless icon in the system tray (rather than just the wired icon.)


Helpful links:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

If you get  "FATAL: Module ndiswrapper not found" - [http://hansengel.wordpress.com/2007/07/24/ubuntu-710-wireless-adapter-problems/](http://hansengel.wordpress.com/2007/07/24/ubuntu-710-wireless-adapter-problems/)

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)


we could still try madwifi and there was another one out there that I heard about but didn't look up (came across it while I was busy.)


Someone else's turn...

---

### Post by farazhussain on 2007-11-26
I tried madwifi, sort of half heartedly and couldn't get it to work. There's just too many opinions of how to actually do that.

And becuase of madwifi runs so many scripts, its turned on and off certain things and I don't know how to restore it to its original state.

---

### Post by ejw2076 on 2007-11-26
> **farazhussain said:**
> I tried madwifi, sort of half heartedly and couldn't get it to work. There's just too many opinions of how to actually do that.

And becuase of madwifi runs so many scripts, its turned on and off certain things and I don't know how to restore it to its original state.

In that case I don't think I'm going to give that a run.  I really don't know a whole lot about linux, I just learn as I go along.  I was able to see wireless networks using the settings I had, I guess a "iwlist scan" might tell us a bit more.

---

### Post by ejw2076 on 2007-11-27
I have a intel 4965AGN wifi card on the way (yeah, I caved.)  This card will fit in our computers (I dissasembled just to make sure,) but am unsure yet whether or not the bios will let it run.  It does have an intel support [page]("http://support.intel.com/support/notebook/sb/CS-006408.htm") and linux drivers.

---

### Post by farazhussain on 2007-11-28
> **ejw2076 said:**
> I have a intel 4965AGN wifi card on the way (yeah, I caved.)  This card will fit in our computers (I dissasembled just to make sure,) but am unsure yet whether or not the bios will let it run.  It does have an intel support [page]("http://support.intel.com/support/notebook/sb/CS-006408.htm") and linux drivers.

How difficult is it to disassemble VGN- NR110E?

---

### Post by chandler on 2007-11-28
Not trying to hijack this thread but I think this driver may help your problems
[http://members.driverguide.com/driver/detail.php?driverid=983575](http://members.driverguide.com/driver/detail.php?driverid=983575)

I used it with openSUSE 10.3 and it worked.  Trying to get it to work for Ubuntu 7.10 now but geting a -22 error when modprobing

Edit:
And the light didn't work when I had it installed on openSUSE

Edit (again):
This is my error output...> Nov 28 18:05:34 tux kernel: [ 2464.016000] ndiswrapper version 1.45 loaded (smp=yes)
Nov 28 18:05:34 tux kernel: [ 2464.032000] ndiswrapper: driver net5211 (,06/29/2006,5.0.0.107) loaded
Nov 28 18:05:34 tux kernel: [ 2464.032000] PCI: Enabling device 0000:06:00.0 (0000 -> 0002)
Nov 28 18:05:34 tux kernel: [ 2464.032000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Nov 28 18:05:34 tux kernel: [ 2464.032000] ndiswrapper (mp_init:263): couldn't initialize device: C000009A
Nov 28 18:05:34 tux kernel: [ 2464.032000] ndiswrapper (pnp_start_device:440): Windows driver couldn't initialize the device (C0000001)
Nov 28 18:05:34 tux kernel: [ 2464.032000] ndiswrapper (mp_halt:305): device dfb08500 is not initialized - not halting
Nov 28 18:05:34 tux kernel: [ 2464.032000] ndiswrapper: device eth%%d removed
Nov 28 18:05:34 tux kernel: [ 2464.032000] ACPI: PCI interrupt for device 0000:06:00.0 disabled
Nov 28 18:05:34 tux kernel: [ 2464.032000] ndiswrapper: probe of 0000:06:00.0 failed with error -22
Nov 28 18:05:34 tux kernel: [ 2464.032000] usbcore: registered new interface driver ndiswrapper


---

### Post by ejw2076 on 2007-11-29
> **farazhussain said:**
> How difficult is it to disassemble VGN- NR110E?

It isn't hard at all.  Just remove the screws on the bottom of the laptop and you have access to the wifi card.

---

### Post by ejw2076 on 2007-11-29
> **chandler said:**
> Not trying to hijack this thread but I think this driver may help your problems
[http://members.driverguide.com/driver/detail.php?driverid=983575](http://members.driverguide.com/driver/detail.php?driverid=983575)

I used it with openSUSE 10.3 and it worked.  Trying to get it to work for Ubuntu 7.10 now but geting a -22 error when modprobing

Edit:
And the light didn't work when I had it installed on openSUSE

Edit (again):
This is my error output...

That is the driver I was able to get it working with slowly.

---

### Post by chandler on 2007-11-30
Didn't realize there were so many pages to this, but I got mine up and running now too.  I had to use version 1.49 and I still can't even connect to my WPA'd connection...

As you mentioned prior it may be the driver.  The more detailed name for our card is "LAN-Express AS IEEE 802.11g PCI-E Adapter Driver", there's 4 more drivers listed on driverguide but they're all the same net5211.inf

I tried madwifi on openSUSE but it didn't work.  On their site I think it deliberately states that this one won't work...

---

### Post by ove overgaard on 2007-11-30
Dear Farazhussain

I had the same problem on a Dell computer. I used ndiswrapper and windows98 driver for netgear hardware (xp98 driver did not work). You can google ndiswrapper and get a lot of help there. I hope this will help.

Kind regards Ove

---

### Post by chandler on 2007-11-30
Okay I had some problems with the drivers mentioned so I looked at the vista install a little more in depth..  I found 2 drivers that were identical one called oem5.inf and a netathr.inf in the C:/Windows/Drivers/Wireless... folder so I copied them over and installed them and they seem to work like a champ.  I've uploaded the .zip file of the whole folder.  Hope this helps.  If there were problems before.

---

### Post by ktru on 2007-11-30
Hey everyone, I'm really new to Ubuntu and the whole Linux thing and I'm having the same issues you guys are having. I recently got a sony vaio vgn nr140e, and couldn't bare all the vista junk. 

Can someone explain how I would go about installing these drivers so that my wireless internet can start working?

---

### Post by chalewa on 2007-11-30
Ok, here is my howto to get this thing working...

basically i followed some tutorials for other cards and systems, and tried to remember what i could about ndiswrapper from when i used it many moons ago.


but this is what i did.

first i disabled the restricted drivers that ubuntu installs... system > restricted driver managers, then just uncheck the atheros driver and disable it. 

then i installed ndiswrapper, (get it from synaptic or command line if you choose) then i installed ndisgtk to install the windows driver which i got from here...

[http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz)


to install the driver simply load up ndisgtk from the command line and hit install driver, and browse to the location of the inf file you extracted from above. 

after you have done this, verify that you have in fact installed the driver, and it is being recognized:

```
 ndiswrapper -l 
```

if it is installed correctly, it should look something like this:

```
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

```


then, make sure that you have the restricted driver that ubuntu installs by default blacklisted 

```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```

then to make sure ndiswrapper starts

```
sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules
```

then restart your computer. 


i personally use wicd to manage my networks, but you can use whatever you like. 


now, i have been having some trouble getting the card to power up when i restart the computer. I am still working out the exact steps that need to happen everytime that one turns on and off their computer, but it seems to have something to do with toggling the wireless lan switch on and off. What i have done thus far is boot the system with the switch in the off positions, obviously ifconfig is not going to list the wlan0. then, i restart again, and flick the switch to on. for some reason, this seems to get it back on again. 



with all this said, i assume that this is what most of you have been doing to get this card working in this laptop. I know that there was talk earlier of slower speeds with the net5211.inf driver, i never experienced any of this. 



if this doesn't work, make sure that ndiswrapper isn't giving you any errors, and post what iwconfig outputs. maybe we will also be able to figure out how to keep this card on all the time.

---

### Post by farazhussain on 2007-11-30
> **chalewa said:**
> Ok, here is my howto to get this thing working...

basically i followed some tutorials for other cards and systems, and tried to remember what i could about ndiswrapper from when i used it many moons ago.


but this is what i did.

.
.
.


Chalewa, thanks a ton for that post. 

I followed exactly what you said and it works perfectly (not slow at all).

At the end of your instructions you told to restart and that's what I did. So far, I haven't had any problems with trying to get the card to "power up". I just restarted  once and it was working straight away.

Btw, here's my 'iwconfig' output:

```

faraz@hussain-machine:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"IASTATE"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0E:38:D4:35:30   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```


Thanks again,

Regards.

Faraz.

---

### Post by farazhussain on 2007-11-30
> **ktru said:**
> Hey everyone, I'm really new to Ubuntu and the whole Linux thing and I'm having the same issues you guys are having. I recently got a sony vaio vgn nr140e, and couldn't bare all the vista junk. 

Can someone explain how I would go about installing these drivers so that my wireless internet can start working?

Mine is a  VGN-NR110E and I just followed the instructions in chalewa's last post, and its working fine for me. My card is: Atheros AR5006 EG.

I'd definitely recommend trying out what Chalewa wrote.

---

### Post by farazhussain on 2007-11-30
> **ejw2076 said:**
> It isn't hard at all.  Just remove the screws on the bottom of the laptop and you have access to the wifi card.

Hmm thanks. I asked because I had a problem with my earlier HP Pavilion laptop. My fan was making a lot of noise so I was thinking of changing it myself. But I learned that  I would have to take apart almost all the parts to be able to detach the fan.

That's why I was skeptical about this. Anyway, its working great now, so  can't complain.

---

### Post by farazhussain on 2007-11-30
> **ove overgaard said:**
> Dear Farazhussain

I had the same problem on a Dell computer. I used ndiswrapper and windows98 driver for netgear hardware (xp98 driver did not work). You can google ndiswrapper and get a lot of help there. I hope this will help.

Kind regards Ove

Thanks. I did use ndiswrapper and the driver link that Chalewa gave in his post. Its working fine so far !

Thanks again,

Regards.

---

### Post by karnage1 on 2007-11-30
for more info i found this site it might be helful to ppl
[ubuntu-fs]("http://ubuntufs.wordpress.com")

---

### Post by amdma2003 on 2007-11-30
I found out that the OEM installation didn't work. I don't know how other people got it to work. But what I did was I selected the F-key to select VGA and change it to 1024x768 and the F-key for other options. 

Then I just moved the up-down arrows to different selection, and lastly I entered on the Normal boot.

I don't know why it worked, but it worked.

---

### Post by jcabrera on 2007-11-30
just installed 7.10 yesterday and encountered the same issue as described above about the atheros wireless card on sony vaio vgn-nr110e. I watched this play out today and am pleased to say chalewa's solution worked for me. took his process less than 5 minutes to execute and i got wireless up and running, even though the light on the front of the laptop for wlan isn't lighting up, the device and driver still works perfectly. also the connection isn't slow as some have encountered.

thanks chalewa

---

### Post by ktru on 2007-12-01
> Mine is a VGN-NR110E and I just followed the instructions in chalewa's last post, and its working fine for me. My card is: Atheros AR5006 EG.

I'd definitely recommend trying out what Chalewa wrote.

I'm having a few problems following Chlaewa's instructions. At first everything seems to be going smoothly   until i run into this code line

> sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules

the terminal didn't spit anything back at me so I figured it must have just done it's job and restarted. Then I tried testing to see if the wireless internet was running. It didn't seem to work so I went on a quest to instal Wicd since worked for Chalewa. Little did I know when I installed Wicd it removed my network manager now I have no internet access at all =/.

Any help?:(

---

### Post by nappyjay on 2007-12-01
I followed Chalewa's tutorial and had one problem: when I check to see if ndiswrapper is working

sudo modprobe ndiswrapper

I get 

FATAL: Module Ndiswrapper is not found.

Any suggestions?

Thanks

---

### Post by chalewa on 2007-12-01
> **ktru said:**
> I'm having a few problems following Chlaewa's instructions. At first everything seems to be going smoothly   until i run into this code line



the terminal didn't spit anything back at me so I figured it must have just done it's job and restarted. Then I tried testing to see if the wireless internet was running. It didn't seem to work so I went on a quest to instal Wicd since worked for Chalewa. Little did I know when I installed Wicd it removed my network manager now I have no internet access at all =/.

Any help?:(



you can always get network manager back, just search for it in the repositories. however, you should still be able to connect to the wired connection through wicd. 


and yes, when you ran those two commands, you shouldn't get anyhting back at you, just another terminal entry line. 

when you type in iwconfig does it list wlan0?

---

### Post by chalewa on 2007-12-01
> **nappyjay said:**
> I followed Chalewa's tutorial and had one problem: when I check to see if ndiswrapper is working

sudo modprobe ndiswrapper

I get 

FATAL: Module Ndiswrapper is not found.

Any suggestions?

Thanks


you are sure that you actually have ndiswrapper installed? 

when you type in 

```
 ndiswrapper -l
```

what do you get out?

---

### Post by farazhussain on 2007-12-01
> **ktru said:**
> I'm having a few problems following Chlaewa's instructions. At first everything seems to be going smoothly   until i run into this code line



the terminal didn't spit anything back at me so I figured it must have just done it's job and restarted. Then I tried testing to see if the wireless internet was running. It didn't seem to work so I went on a quest to instal Wicd since worked for Chalewa. Little did I know when I installed Wicd it removed my network manager now I have no internet access at all =/.

Any help?:(

Did you restart the computer after that command? That's what I did, just as per the instructions.

Also, I didn't install wicd. After restarting,  I just used the default nm-applet which was on my panel on the top-right.

---

### Post by ktru on 2007-12-02
> **chalewa said:**
> you can always get network manager back, just search for it in the repositories. however, you should still be able to connect to the wired connection through wicd. 


and yes, when you ran those two commands, you shouldn't get anyhting back at you, just another terminal entry line. 

when you type in iwconfig does it list wlan0?

Wicd doesn't seem to working for me :( and since it's not working I'm going to try to reinstall ubuntu and try this out again. I'll let you know how it turns out, thanks for all the help so far though!

---

### Post by chalewa on 2007-12-02
> **ktru said:**
> Wicd doesn't seem to working for me :( and since it's not working I'm going to try to reinstall ubuntu and try this out again. I'll let you know how it turns out, thanks for all the help so far though!



ah you shouldn't have to reinstall all of ubuntu unless you really want to have a clean install...

sudo apt-get install network-manager-gnome will get you the network manager back

---

### Post by ktru on 2007-12-02
> **chalewa said:**
> ah you shouldn't have to reinstall all of ubuntu unless you really want to have a clean install...

sudo apt-get install network-manager-gnome will get you the network manager back

will that work even without internet access?

nvm I just tried it, the code won't work unless i have internet access =/

---

### Post by farazhussain on 2007-12-02
> **ktru said:**
> will that work even without internet access?

nvm I just tried it, the code won't work unless i have internet access =/

Try searching for  it in Synaptic Package Manager and install it using the Ubuntu CD.

---

### Post by nappyjay on 2007-12-02
Chalewa,

When I typed in 

ndiswrapper -l

I got exactly what your original post said that I should get. I typed iwconfig to see what was happening and it did not recognize the wireless card at all.

<getting ready to sell this Sony and get an HP>

---

### Post by ktru on 2007-12-02
After I reinstalled Ubuntu and followed the directions again it worked flawlessly! You rock chalewa!!! Works like a charm!!

---

### Post by klintron on 2008-01-30
chalewa's directions worked great, except for one problem. Sometimes I completely lose my network connection.  The network manager still reports being connected to my wireless network with a full signal, but it's clear that nothing's happening. If I try to reconnect, I just get prompted over and over again for my WEP key, no matter how many times I correctly enter it. I can fix the problem reliably by completely powering down the laptop and powering back up again. Restarting Gnome or even the whole system doesn't work, it has to be a power down.

Any ideas?

---

### Post by chandler on 2008-02-06
run lspci when it goes down next time.  Look at the device then it's revision.  Mine always changes to "ff"...  My connection usually goes out when it needs a new IP lease.  I think it's faulty hardware as my girlfriend's laptop (same one) doesn't have any problems.

---

### Post by klintron on 2008-02-08
OK, after losing connection it's "06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev ff)"

It's rev 01 right now.

What do you mean by faulty hardware? I don't run into this problem on the same laptop while running Vista (I dual boot). Also, it happens on any wireless network.

---

### Post by chandler on 2008-02-09
That's the same exact thing I've noticed but I have no idea on whre to go after that.  Probably just a bad implementation of ndiswrapper and our driver...  Might have to wait for ath5k to come out from the makers of madwifi.  Supposed to work for all atheros chipsets when it does.

---

### Post by klintron on 2008-02-23
Anyone have any luck swapping out the Atheros card for something more supported?

---

### Post by kayel_justice on 2008-03-29
> **chalewa said:**
> Ok, here is my howto to get this thing working...

basically i followed some tutorials for other cards and systems, and tried to remember what i could about ndiswrapper from when i used it many moons ago.


but this is what i did.

first i disabled the restricted drivers that ubuntu installs... system > restricted driver managers, then just uncheck the atheros driver and disable it. 

then i installed ndiswrapper, (get it from synaptic or command line if you choose) then i installed ndisgtk to install the windows driver which i got from here...

[http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz)


to install the driver simply load up ndisgtk from the command line and hit install driver, and browse to the location of the inf file you extracted from above. 

after you have done this, verify that you have in fact installed the driver, and it is being recognized:

```
 ndiswrapper -l 
```

if it is installed correctly, it should look something like this:

```
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

```


then, make sure that you have the restricted driver that ubuntu installs by default blacklisted 

```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```

then to make sure ndiswrapper starts

```
sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules
```

then restart your computer. 


i personally use wicd to manage my networks, but you can use whatever you like. 


now, i have been having some trouble getting the card to power up when i restart the computer. I am still working out the exact steps that need to happen everytime that one turns on and off their computer, but it seems to have something to do with toggling the wireless lan switch on and off. What i have done thus far is boot the system with the switch in the off positions, obviously ifconfig is not going to list the wlan0. then, i restart again, and flick the switch to on. for some reason, this seems to get it back on again. 



with all this said, i assume that this is what most of you have been doing to get this card working in this laptop. I know that there was talk earlier of slower speeds with the net5211.inf driver, i never experienced any of this. 



if this doesn't work, make sure that ndiswrapper isn't giving you any errors, and post what iwconfig outputs. maybe we will also be able to figure out how to keep this card on all the time.

-----------------------------------------------------------------------------------------------------------
I'm SOrry, I got to this part[

to install the driver simply load up ndisgtk from the command line and hit install driver, and browse to the location of the inf file you extracted from above. 
]

I think I looked everywhere, sheesh, but I managed to extract it on my desktop but now what commands do I use to load it? It should be from the terminal right?

Thanks

---

### Post by kayel_justice on 2008-03-29
OK I found it..man I was getting frustrated...ok, I'm off to finish the tut.....btw, thatnks for posting these

---

### Post by kayel_justice on 2008-03-29
oh well, I installed it from synaptic, it's still not working...back to my original question. extracted it on my desktop(ndisg - whatever), how to I get it to load from there? The folder says ar5007eg-32-0.2, and inside it is a ar5211.sys file and a net5211.inf?
Please help

---

### Post by kayel_justice on 2008-03-29
OK......FIGURED IT OUT, SORRY....I'm going to shut up now, until my next problem...lol

---

### Post by harmeet on 2008-04-04
Chalewa

I tried to follow your instructions and get this error when I run ndisgtk -

```

** (ndisgtk:6114): CRITICAL **: Error opening file: No such file or directory

** (ndisgtk:6114): CRITICAL **: Error opening file: No such file or directory

```

But I went ahead and follow the rest of the procedure and I have my wireless working as well!

\\:D/

Thanks

---

### Post by chalewa on 2008-04-07
> **harmeet said:**
> Chalewa

I tried to follow your instructions and get this error when I run ndisgtk -

```

** (ndisgtk:6114): CRITICAL **: Error opening file: No such file or directory

** (ndisgtk:6114): CRITICAL **: Error opening file: No such file or directory

```

But I went ahead and follow the rest of the procedure and I have my wireless working as well!

\\:D/

Thanks



great glad I could be of help. as far as ndisgtk goes, it is just a graphical frontend for loading the inf file into ndiswrapper, this can be done via the command line if necessary, i just thought that it might be easier to include something graphical in the tutorial. 


In addition, I am really hoping that this card works out of the box with hardy, but i guess we are goin to have to wait a couple more weeks to figure that out.

---

### Post by chalewa on 2008-04-07
> **klintron said:**
> chalewa's directions worked great, except for one problem. Sometimes I completely lose my network connection.  The network manager still reports being connected to my wireless network with a full signal, but it's clear that nothing's happening. If I try to reconnect, I just get prompted over and over again for my WEP key, no matter how many times I correctly enter it. I can fix the problem reliably by completely powering down the laptop and powering back up again. Restarting Gnome or even the whole system doesn't work, it has to be a power down.

Any ideas?

> **chandler said:**
> run lspci when it goes down next time.  Look at the device then it's revision.  Mine always changes to "ff"...  My connection usually goes out when it needs a new IP lease.  I think it's faulty hardware as my girlfriend's laptop (same one) doesn't have any problems.

> **klintron said:**
> OK, after losing connection it's "06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev ff)"

It's rev 01 right now.

What do you mean by faulty hardware? I don't run into this problem on the same laptop while running Vista (I dual boot). Also, it happens on any wireless network.

> **chandler said:**
> That's the same exact thing I've noticed but I have no idea on whre to go after that.  Probably just a bad implementation of ndiswrapper and our driver...  Might have to wait for ath5k to come out from the makers of madwifi.  Supposed to work for all atheros chipsets when it does.


yea, i think that i have been experiencing this problem all along. essentially what happens is that occassionally if i shut down my computer and power back up, its like my card doesn't 'turn on'. i will simply have to keep on restarting till the card is recognized by the system again. 


no idea why this happens. hope this is fixed in hardy or with ath5k

---

### Post by pablotorres2 on 2008-05-24
I have a Sony Vaio VGN-NR120E, got Hardy Heron and installed it, and wireless didn't work with Atheros driver that came with it. So, I searched over internet, and found this topic. 

I've installed ndiswrapper, followed the procedures listed in this topic, and had the same problems noticed here, after reboot no wifi network is detected.

So I decided to try again with madwifi driver, and after searching some foruns, found some solutions for similar cards from other vendors. 
After some experiments, I've finally get my card working with madwifi, but the reboot problem still. 
The problem seems to be the identification of the card, after reboot the driver doesn't recognize it. 

I can't reboot the machine if I want wireless, need to shutdown and turn on to get wifi working.

At least, now I don't need windows drivers anymore.


How to get it working with madwifi (assuming that your kernel version is 2.6.24-16):

1. Download madwifi patched for Atheros AR5007 - [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz) 

2. If you don't have installed ndiswrapper, go to step 3. If you do:
   a) remove it from /etc/modules
   b) remove the line "blacklist ath_pci" from /etc/modprobe.d/blacklist
   c) run ```
sudo apt-get remove ndiswrapper
``` or find it in Synaptics and mark it for full removal

3. If you're running the madwifi drivers that came with ubuntu, stop them in Restricted Drivers menu in gnome, or run in command line:
```
ifconfig ath0 down
ifconfig wifi0 down
sudo modprobe -r ath_pci
sudo modprobe -r wlan_scan_sta
sudo modprobe -r wlan_wep

```

4. Install the packages needed to compile the new driver:
```
sudo apt-get install build-essential linux-headers-2.6.24-16-generic
```

5. Remove old madwifi driver packed with ubuntu
   In Synaptics, mark for removal the package "linux-restricted-modules-2.6.24-16-generic" or in command-line:
```
sudo apt-get remove linux-restricted-modules-2.6.24-16-generic
```

6. In a terminal, extract the driver downloaded in step 1
```
tar -xvzf madwifi-nr-r3366+ar5007.tar.gz
```

7. Enter the folder "madwifi-nr-r3366+ar5007" where you unpacked it in last step

8. Compile the new driver and install it
```
sudo make
sudo make install

```

Restart your system, and voilá!

---

### Post by harmeet on 2008-05-26
> **pablotorres2 said:**
> I have a Sony Vaio VGN-NR120E, got Hardy Heron and installed it, and wireless didn't work with Atheros driver that came with it. So, I searched over internet, and found this topic. 

I've installed ndiswrapper, followed the procedures listed in this topic, and had the same problems noticed here, after reboot no wifi network is detected.

So I decided to try again with madwifi driver, and after searching some foruns, found some solutions for similar cards from other vendors. 
After some experiments, I've finally get my card working with madwifi, but the reboot problem still. 
The problem seems to be the identification of the card, after reboot the driver doesn't recognize it. 

I can't reboot the machine if I want wireless, need to shutdown and turn on to get wifi working.

At least, now I don't need windows drivers anymore.


How to get it working with madwifi (assuming that your kernel version is 2.6.24-16):

1. Download madwifi patched for Atheros AR5007 - [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz) 

2. If you don't have installed ndiswrapper, go to step 3. If you do:
   a) remove it from /etc/modules
   b) remove the line "blacklist ath_pci" from /etc/modprobe.d/blacklist
   c) run ```
sudo apt-get remove ndiswrapper
``` or find it in Synaptics and mark it for full removal

3. If you're running the madwifi drivers that came with ubuntu, stop them in Restricted Drivers menu in gnome, or run in command line:
```
ifconfig ath0 down
ifconfig wifi0 down
sudo modprobe -r ath_pci
sudo modprobe -r wlan_scan_sta
sudo modprobe -r wlan_wep

```

4. Install the packages needed to compile the new driver:
```
sudo apt-get install build-essential linux-headers-2.6.24-16-generic
```

5. Remove old madwifi driver packed with ubuntu
   In Synaptics, mark for removal the package "linux-restricted-modules-2.6.24-16-generic" or in command-line:
```
sudo apt-get remove linux-restricted-modules-2.6.24-16-generic
```

6. In a terminal, extract the driver downloaded in step 1
```
tar -xvzf madwifi-nr-r3366+ar5007.tar.gz
```

7. Enter the folder "madwifi-nr-r3366+ar5007" where you unpacked it in last step

8. Compile the new driver and install it
```
sudo make
sudo make install

```

Restart your system, and voilá!

pablotorres2

This works for me too! I am using VGN-NR115E.

I also have the wireless not working on reboot. I have to shutdown and then turn on. Please post here if you find a fix for this.

One more thing, every time I turn on the system, I have to run -

```
sudo modprobe ath_pci
```

How to make the system automaticallyload it?

Thanks

---

### Post by pablotorres2 on 2008-05-26
harmeet: just add the line
```
ath_pci
```
to the end of the file /etc/modules

You must edit this file as root.

About the restart problem, I've been testing it more exhaustively. 
I have read some people saying that it may be a hardware problem, but I don't think so. 
On my machine I dual boot with vista. If I boot in ubuntu, then restart in vista, the card isn't recognized too!!!
But, if I first boot in vista after turning on, then restart in vista or ubuntu, the problem doesn't occur. 

I'll investigate more and post more info.

[]s

---

### Post by Ripfox on 2008-06-28
> **pablotorres2 said:**
> I have a Sony Vaio VGN-NR120E, got Hardy Heron and installed it, and wireless didn't work with Atheros driver that came with it. So, I searched over internet, and found this topic. 

I've installed ndiswrapper, followed the procedures listed in this topic, and had the same problems noticed here, after reboot no wifi network is detected.

So I decided to try again with madwifi driver, and after searching some foruns, found some solutions for similar cards from other vendors. 
After some experiments, I've finally get my card working with madwifi, but the reboot problem still. 
The problem seems to be the identification of the card, after reboot the driver doesn't recognize it. 

I can't reboot the machine if I want wireless, need to shutdown and turn on to get wifi working.

At least, now I don't need windows drivers anymore.


How to get it working with madwifi (assuming that your kernel version is 2.6.24-16):

1. Download madwifi patched for Atheros AR5007 - [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz) 

2. If you don't have installed ndiswrapper, go to step 3. If you do:
   a) remove it from /etc/modules
   b) remove the line "blacklist ath_pci" from /etc/modprobe.d/blacklist
   c) run ```
sudo apt-get remove ndiswrapper
``` or find it in Synaptics and mark it for full removal

3. If you're running the madwifi drivers that came with ubuntu, stop them in Restricted Drivers menu in gnome, or run in command line:
```
ifconfig ath0 down
ifconfig wifi0 down
sudo modprobe -r ath_pci
sudo modprobe -r wlan_scan_sta
sudo modprobe -r wlan_wep

```

4. Install the packages needed to compile the new driver:
```
sudo apt-get install build-essential linux-headers-2.6.24-16-generic
```

5. Remove old madwifi driver packed with ubuntu
   In Synaptics, mark for removal the package "linux-restricted-modules-2.6.24-16-generic" or in command-line:
```
sudo apt-get remove linux-restricted-modules-2.6.24-16-generic
```

6. In a terminal, extract the driver downloaded in step 1
```
tar -xvzf madwifi-nr-r3366+ar5007.tar.gz
```

7. Enter the folder "madwifi-nr-r3366+ar5007" where you unpacked it in last step

8. Compile the new driver and install it
```
sudo make
sudo make install

```

Restart your system, and voilá!

Dude you are a lifesaver. Mine is a Vaio nr360e and after this, YES it even works after reboot! Had to add the module as per the last post to make it permanent. You rock!

---

### Post by cameronh4050 on 2008-07-19
Thanks alot for that post chalewa!
Worked perfectly =]

---

