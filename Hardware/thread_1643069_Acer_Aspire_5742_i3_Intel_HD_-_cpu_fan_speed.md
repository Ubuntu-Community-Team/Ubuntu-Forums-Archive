---
title: "Acer Aspire 5742 i3 Intel HD - cpu fan speed"
date: 2010-12-11
forum: Hardware
---

### Post by nuspl on 2010-12-11
Hi, I have tried to adjust the cpu fan speed but I could set up only the cpu freqs with cpufreq-set.

Ubuntu 10.10 (maverick) is running on the Acer Aspire 5742 (i3 M370 at 2.4 Ghz) with intel HD graphics.

As I have tried to reduce the frequencies to the lowest value - it has worked. However, the
cpu fan spin-up without anything in every 30 seconds nearly independently. 

With a Compal laptop (actually an Acer) with a power manager running under KDE I could set up an aggressive power saving (centrino cpu) what do just that I would prefer. A cpu fan actually without any noise and with acceptable (nearly zero) system performance reduction only (seemingly nothing). /openSuse/

Actually, I would like to be doing in silent and write a tex document generally but without anything similar like this fan which is going up and down.

Could you suggest me anything what should work? ... or a place where I could find some details info about this gudget.

Hope, somebody can understand my curiosity with these noises :)

---

### Post by Kenda on 2011-02-23
I have exactly the same issue on the same model. Did you find a solution?

---

### Post by Kenda on 2011-02-26
I have now updated the BIOS to 1.12 and this seems to have helped a lot!

---

### Post by intuited on 2011-02-26
Hi Kenda,

That sounds like good news; could you be more specific?  Also, please let us know if there seem to be any side effects from the upgrade.

I'm also wondering if you had to do the firmware upgrade from windows, or if it's possible to do it from ubuntu?

---

### Post by Kenda on 2011-02-27
Hi yes the old version of the Bios was 1.05 and  I downloaded an update from the Acer site.

Although there do seem to be guides to flashing the BIOS in Linux using Unetbootin and a free DOS usb  I couldn't really follow them and it didn't work so I updated the BIOS from within Windows to version 1.12 (in fact I had to swap back in the windows HDD which I had replaced on day one by a dedicated Ubunut 10.10 SSD).

There do not seem to be any issues with the BIOS update and the fan noise does seem to be a lot better but it does occasionally ramp up just not as much as before.

If you do try it I would be very interested if you notice a difference.

---

### Post by intuited on 2011-02-27
I will likely give it a shot.  I'm also curious about why you used version 1.12; the [BIOS tab]("http://support.acer.com/us/en/product/default.aspx?tab=5&modelId=3277") of the downloads section lists version 1.15 as the newest.

Thanks for the tip!

---

### Post by intuited on 2011-02-27
PS I'm also wondering if the BIOS update made temperature sensors available for you?  Control of the fan speed without temperature sensors is a bit dangerous...  Though perhaps you had working temperature sensors before?

---

### Post by Kenda on 2011-02-27
I thought I had downloaded 1.15 in fact I am fairly sure I did but it installed as 1.12 I don't know why.

No sensors working if you know how let me know. I just installed the new BIOS and let it do its own thing! I also use the CPU frequency scaling applet on powersave setting but I'm not sure it makes much of a difference. 

Let me know how you get on and if you notice the difference.

---

### Post by intuited on 2011-02-27
Okay, got it.. I was thinking that the new BIOS firmware made it possible for Linux to control the fan speed.  So it's just doing a better job of doing it itself.

I've written to Acer to see if they have any recommendations in this regard; I'll post a follow-up, perhaps after doing the BIOS flash, once I've heard back from them.

---

### Post by intuited on 2011-02-27
PS I'm guessing that the lack of support for temperature readings and fan control in Linux itself is because of the unsupported HECI and SMBus chips.  When I do ```
$ sudo lshw | grep -A15 UNCLAIMED
``` I see those two controllers listed as unclaimed; I gather that this means that drivers are not available for them.

```


        *-communication UNCLAIMED
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:b4406100-b440610f
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
--
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:b4406000-b44060ff ioport:3000(size=32)
        *-generic
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
--
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define5
       vendor: OEM_Define2
       physical id: 2
       version: OEM_Define6
       serial: OEM_Define3
       capacity: 75mWh
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: vboxnet0
       serial: xx:xx:xx:xx:xx:xx
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

BTW my BIOS firmware version as shipped is 1.07:

```

$ sudo lshw | grep -A10 -- -firmware | xclip
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.07 (09/27/2010)
          size: 1MiB
          capacity: 1472KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-memory
          description: System Memory
          physical id: 1a

```

---

