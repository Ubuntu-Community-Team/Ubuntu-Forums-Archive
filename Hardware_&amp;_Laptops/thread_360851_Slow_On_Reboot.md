---
title: "Slow On Reboot"
date: 2007-02-13
forum: Hardware &amp; Laptops
---

### Post by omghax on 2007-02-13
**Note:** I'm using Xubuntu right now on my Laptop, but I use Ubuntu on my Desktop.

Every time I install either Ubuntu or Xubuntu on my laptop (I have to use the alternate CD), it runs fine until I have to restart it. It *just* started working semi-ok when I restart, but *only* if I do a cold shutdown. If I'm lucky, it'll randomly work if I regularly shut it down.

If I update it at all, it works x10 slower than if I would of just normally restarted it. I've run the recovery console and used 'top' to see what's eating up the CPU and it said 'kacpid', which doesn't really make sense to be because I used the 'acpi=off' tag in both of the GRUB's loading things.

I then did this in Xubuntu after I restarted, and it was going really slow, it said the same thing.

What is kacpid and why does it eat up my CPU? Why doesn't acpi=off work for me anymore? :'(

---

### Post by tgalati4 on 2007-02-20
How large is your swap partition?
How much RAM do you have? Did it pass memtest?
Could be an interrupt problem.

Go into your BIOS, turn off PnP, serial port, parallel port, infrared and see if that helps.

Post relevant sections of dmesg right after successful boot.

We really need more info to help.

---

### Post by omghax on 2007-02-21
I wasn't really sure what to post, :(

Well, I have 2 'bad' laptops right now that were really cheap, and just recently my girlfriend spilt my Red Bull on one -.-

Every key works, except the 'T' key... but I'm working on it.

On the other laptop, the only key that doesn't work is the F2 key, and I need that to get into Setup. Otherwise it runs fine though, :P


I'll have to check on the swap partition, I usually just let it do it's thing. Should I set it to a certain amount? I have a 10GB hard drive on both of them, never needed more.

I have 2x128MB sticks in them, not much but it seems to work fine for what I need it for (email, web, nothing big).

What's *dmesg*?


-- Thanks for replying, :)

---

### Post by tgalati4 on 2007-02-21
type in a console:  dmesg | more       (q to quit)
It gives you a time-based capture of what the system is doing--especially during bootup.  dmesg | grep pci     (This will show you what is being detected on the pci bus)

For memory 256MB is OK.  A dedicated swap partition of 500MB or 1GB is helpful.  After doing an update, you are running a new kernel.  You need to set the acpi switch for the new kernel.

Of course, if the laptops are beat up, then it could be a hardware problem.  Red Bull may give you wings, but it will cause shorts on the motherboard.

---

### Post by omghax on 2007-02-22
> **tgalati4 said:**
> For memory 256MB is OK. A dedicated swap partition of 500MB or 1GB is helpful. After doing an update, you are running a new kernel. You need to set the acpi switch for the new kernel.
So I need to turn it back on?

> **tgalati4 said:**
> Red Bull may give you wings, but it will cause shorts on the motherboard.
*tear, :(

---

### Post by tgalati4 on 2007-02-22
When booted into the new kernel, examine the output of:

dmesg | grep ACPI

dmesg | grep ACPI > myACPIoutput.txt

Mine looks like this:
[17179569.184000]  BIOS-e820: 000000000fff0000 - 000000000ffffc00 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000ffffc00 - 0000000010000000 (ACPI NVS)
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000f71a0
[17179569.184000] ACPI: RSDT (v001 DELL    I 7500  0x06040000  LTP 0x00000000) @ 0x0fffb971
[17179569.184000] ACPI: FADT (v001 DELL    I 7500  0x06040000 PTL  0x00000001) @ 0x0ffffb65
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x0ffffbd9
[17179569.184000] ACPI: DSDT (v001 DELL    I 7500  0x06040000 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179576.368000] ACPI: Looking for DSDT ... not found!
[17179576.376000] ACPI: setting ELCR to 0200 (from 0820)
[17179576.388000] ACPI: bus type pci registered
[17179576.400000] ACPI: Subsystem revision 20051216
[17179576.408000] ACPI: Interpreter enabled
[17179576.412000] ACPI: Using PIC for interrupt routing
[17179576.412000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179576.424000] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
[17179576.428000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179576.448000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[17179576.448000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
[17179576.448000] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 7) *0, disabled.
[17179576.448000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 14 15)
[17179576.452000] ACPI: Embedded Controller [EC0] (gpe 9) interrupt mode.
[17179576.456000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179576.460000] ACPI: Power Resource [PFAN] (off)
[17179576.460000] pnp: PnP ACPI init
[17179576.472000] pnp: PnP ACPI: found 9 devices
[17179576.472000] PnPBIOS: Disabled by ACPI PNP
[17179576.472000] PCI: Using ACPI for IRQ routing
[17179576.476000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179576.476000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179576.476000] ACPI: PCI Interrupt 0000:00:04.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179576.944000] ACPI wakeup devices:
[17179576.944000] ACPI: (supports S0 S1 S3 S4 S5)
[17179578.464000] ACPI: Fan [FAN] (off)
[17179578.476000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179578.476000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179578.488000] ACPI: Thermal Zone [THRM] (43 C)
[17179583.020000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[17179583.020000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179608.392000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179608.624000] ACPI: PCI Interrupt 0000:00:04.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179610.152000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179634.588000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179646.828000] ACPI: AC Adapter [AC] (on-line)
[17179646.836000] ACPI: Battery Slot [BAT0] (battery present)
[17179646.836000] ACPI: Battery Slot [BAT1] (battery absent)
[17179647.112000] ACPI: Lid Switch [LID]
[17179647.112000] ACPI: Power Button (CM) [PWRB]
[17179647.112000] ACPI: Sleep Button (CM) [SBTN]
[17179665.492000] apm: overridden by ACPI.
[17184920.068000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[17184926.912000] ACPI: PCI interrupt for device 0000:00:08.0 disabled
[17184926.912000] ACPI: PCI interrupt for device 0000:00:07.2 disabled
[17184926.912000] ACPI: PCI interrupt for device 0000:00:04.1 disabled
[17184926.912000] ACPI: PCI interrupt for device 0000:00:04.0 disabled
[17203937.052000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17203937.052000] ACPI: PCI Interrupt 0000:00:04.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17203937.052000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17203937.068000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17203947.704000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17203953.480000] ACPI: Lid Switch [LID]
[17203953.480000] ACPI: Power Button (CM) [PWRB]
[17203953.484000] ACPI: Sleep Button (CM) [SBTN]
[17203954.952000] ACPI: Fan [FAN] (off)
[17203955.044000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17203955.048000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17203955.180000] ACPI: Thermal Zone [THRM] (32 C)
[17203955.664000] ACPI: AC Adapter [AC] (off-line)
[17214072.864000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[17214095.400000] ACPI: PCI interrupt for device 0000:00:08.0 disabled
[17214095.400000] ACPI: PCI interrupt for device 0000:00:07.2 disabled
[17214095.400000] ACPI: PCI interrupt for device 0000:00:04.1 disabled
[17214095.400000] ACPI: PCI interrupt for device 0000:00:04.0 disabled
[17244869.632000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17244869.632000] ACPI: PCI Interrupt 0000:00:04.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17244869.632000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17244869.648000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17244900.452000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17244907.408000] ACPI: Lid Switch [LID]
[17244907.408000] ACPI: Power Button (CM) [PWRB]
[17244907.408000] ACPI: Sleep Button (CM) [SBTN]
[17244908.640000] ACPI: Fan [FAN] (off)
[17244908.736000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17244908.736000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17244908.768000] ACPI: Thermal Zone [THRM] (31 C)
[17244909.124000] ACPI: AC Adapter [AC] (on-line)

A properly working ACPI system will look similar.  A sick ACPI system will have complaints.

If these are pre 2000 laptops then output the following:
dmesg | grep APM

and 

dmesg | grep APM > myAPMoutput.txt

Also realize that after an update, several things happen:

Installed package database gets updated--this can take several minutes.
Locate database gets updated--this can take several minutes.

Shutting the machine down kills these processes, so your machine will run faster.  These processes are not critical but they are important to maintaining an up-to-date system.

On slower machines, you just have to let them run their course, otherwise you get in this never ending cycle of rebooting and restarting the unfinished processes.

Let the machine sit for a while and then capture the process table:

ps -ef > whyismymachinerunningsoslow.txt

Post the process table and then we can see what is really going on.

Enable the system monitor in the top panel bar (right click, panel add) so you can see when the machine is busy.  What are the CPU speeds of these machines.  If less than 500 MHz then expect to wait several minutes for these processes to finish.  That's just a fact of life and why you should only update a working system when you don't have to do anything else.

---

### Post by omghax on 2007-02-22
Thanks a lot, :)

Time to sit back and watch it go! :popcorn:

---

