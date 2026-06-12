---
title: "Del insp 1200, modem problem???"
date: 2009-01-10
forum: Hardware
---

### Post by EmmGeeImage on 2009-01-10
I had many isssues trying to get Ubuntu in this Dell Inspiron 1200! Now even more problems...

I read the literature on "scanmodem.gz" and ran it. It just brought up a list of documents to read. I am not on the net.... 

After reading the site again, i didn't understand "dip pon" with user name and other stuff, because I did not see where to enter any of it.

Am I wrong to ask WHERE you enter this info? I did try to put it into "terminal," after unlocking of course, to get to the internet, for software and updates. No such luck.

Part of the problem, the directions are not specified. The other is that maybe my modem isn't supported by Ubuntu?

Can someone let me know? 

By the way, the modem was built in, not added on.

Someone please let me know, so I can finally get on the net.




*"two and two are twenty two, not four"*

---

### Post by gettinoriginal on 2009-01-10
Try this site to check hardware compatibility: :P

[http://kmuto.jp/debian/hcl/index.cgi](http://kmuto.jp/debian/hcl/index.cgi)

---

### Post by cdtech on 2009-01-10
Which modem do you have? You could post the output of "lshw" (in code blocks) and we could start there. Maybe just post the modem part of the output.

**UPDATE::.**
I run the Sprint USB modem. All of the configuration settings are within the /etc/ppp directory, but you need to know the device ID in order to configure that particular modem.

---

### Post by EmmGeeImage on 2009-01-10
As i mentioned before, where do I get that? Is that something in "termainal?" if so, what do I input to get that?

Talk to me like I'm 1 year old.... all bases need to be covered here. Yes, I have 1 successful machine, but now there's an unsuccessful Ubuntu machine, I'm not thinking right... or analyzing correctly, due to the stress.

So if i seem alittle agitated with not knowing where to get this stuff.... please be patient.



*"Linus lives at the piano"*

---

### Post by cdtech on 2009-01-10
lol, no problem. Just open a terminal under "Accessories" and type in:
```
lshw
```
It's always good practice to copy and paste from the code blocks in order to refrain from miss typed commands. To paste in a terminal use the "ctrl + shift + v"

Don't be too frustrated, it may take a moment or two but we'll get it figured out.......

---

### Post by EmmGeeImage on 2009-01-11
I just got home... a freind of mine told me how to decifer what modem I have....

the "conexant RD02-D110" (All zeros).



Now I hope this helps:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

xxxxx@xxxxxx-pc2:~$ lshw
WARNING: you should run this program as super-user.
mikel-pc2                 
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 247MiB
     *-cpu
          product: Intel(R) Celeron(R) M processor         1.30GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.13.8
          size: 1300MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCI1510 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-network
                description: Ethernet interface
                product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 03
                serial: 00:12:3f:16:84:d2
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@0000:00:1e.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03

---

### Post by EmmGeeImage on 2009-01-11
Now, Another modem issue... I was online for 4 hours, then noticed the modem NOT DIALING. I redid the same exact steps, by hitting the netwrk to see if the connections are there. it showed them as saved. Hoever, no dialing out. Nothing was changed by me. The only thing... 124 pack updates... then cut off. Now i cannot dial, with a phone test for a dial tone. Tone was present. I re-ran the Connexant driver...and did the "lshw" thing again.

Sill nothing.

The system didn't save the  EXACT modem... meaning it being checked, as the location was originally was. It's ALWAYS unchecked, even when I re-save, it UNCHECKS point to point modem. And if  I recheck the TOP-RIGHT green check mark, it will uncheck the modem again, during a save!

How and why would this happen? I would think "make default connection" should keep it in check as the only modem.

I was connected and getting updates, but no such luck now.

please advise.

By the way, same exact login, so that's would not be it. Reboot did not help either. Its also not seeing my cable connection, which is "Automatic," not static, etc.



Thanks

---

