---
title: "HELP - Blank screen after Resume from Suspend in Edgy"
date: 2006-11-20
forum: Hardware &amp; Laptops
---

### Post by morfyng on 2006-11-20
Hi guys,

I have an Acer Travelmate 8004 Lmi running Ubuntu Edgy/Eft, kernel 2.6.17-generic and Ati MOBILITY RADEON 9700 Generic (8.30.3).

I got my system working fine except suspend does not work, when I want to wake it up, screen stays blank, bluetooth LED blinking and I can't get any tty, answer from ping or anything else. I've to reboot... ](*,) 

I use a swap in /dev/hda2 and my grub system start using:
/vmlinuz-2.6.17-10-generic root=/dev/hda5 resume=/dev/hda2 ro splash locale=it_IT acpi_sleep=s3_bios

I use  Option "VBERestore" "true" in my xorg.conf

any help will be muchly appreciated! Thanks Morfyng

***This is my /etc/default/acpi-suppot file:***

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

***This is my dmesg | grep acpi***
[17179569.184000]  BIOS-e820: 000000007fee0000 - 000000007feec000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000007feec000 - 000000007ff00000 (ACPI NVS)
[17179569.184000] ACPI: RSDP (v000 ACER                                  ) @ 0x000f6020
[17179569.184000] ACPI: RSDT (v001 ACER   TM8000   0x20020131  LTP 0x00000000) @ 0x7fee52ed
[17179569.184000] ACPI: FADT (v001 ACER   TM8000   0x20020131 PTL  0x00000050) @ 0x7feebf2c
[17179569.184000] ACPI: HPET (v001 ACER   TM8000   0x20020131 PTL  0x00000000) @ 0x7feebfa0
[17179569.184000] ACPI: BOOT (v001 ACER   TM8000   0x20020131  LTP 0x00000001) @ 0x7feebfd8
[17179569.184000] ACPI: DSDT (v001 ACER   TM8000   0x20020131 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: HPET id: 0x8086a201 base: 0x0
[17179569.184000] Kernel command line: root=/dev/hda5 resume=/dev/hda2 ro splash locale=it_IT acpi_sleep=s3_bios
[17179570.108000] ACPI: Core revision 20060707
[17179570.108000] ACPI: Looking for DSDT ... not found!
[17179570.112000] ACPI: setting ELCR to 0200 (from 0440)
[17179570.128000] ACPI: bus type pci registered
[17179570.144000] ACPI: Interpreter enabled
[17179570.144000] ACPI: Using PIC for interrupt routing
[17179570.144000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.148000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179570.148000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.152000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179570.152000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179570.152000] ACPI: PCI Interrupt Link [LNKA] (IRQs *6)
[17179570.152000] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[17179570.152000] ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
[17179570.156000] ACPI: PCI Interrupt Link [LNKD] (IRQs *6)
[17179570.156000] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[17179570.156000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
[17179570.156000] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *0, disabled.
[17179570.156000] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[17179570.160000] ACPI: Embedded Controller [EC0] (gpe 29) interrupt mode.
[17179570.176000] ACPI: Power Resource [PFN0] (off)
[17179570.176000] ACPI: Power Resource [PFN1] (off)
[17179570.176000] pnp: PnP ACPI init
[17179570.180000] pnp: PnP ACPI: found 11 devices
[17179570.180000] PnPBIOS: Disabled by ACPI PNP
[17179570.180000] PCI: Using ACPI for IRQ routing
[17179570.188000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 6
[17179570.188000] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKC] -> GSI 6 (level, low) -> IRQ 6
[17179570.188000] ACPI: PCI Interrupt 0000:02:06.1[A] -> Link [LNKC] -> GSI 6 (level, low) -> IRQ 6
[17179570.188000] ACPI: PCI Interrupt 0000:02:06.3[A] -> Link [LNKC] -> GSI 6 (level, low) -> IRQ 6
[17179570.612000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[17179570.612000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179570.616000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[17179570.620000] ACPI: (supports S0 S3 S4 S5)
[17179571.824000] ACPI: Transitioning device [FAN0] to D3
[17179571.824000] ACPI: Transitioning device [FAN0] to D3
[17179571.824000] ACPI: Fan [FAN0] (off)
[17179571.824000] ACPI: Transitioning device [FAN1] to D3
[17179571.824000] ACPI: Transitioning device [FAN1] to D3
[17179571.824000] ACPI: Fan [FAN1] (off)
[17179571.828000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179571.828000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179571.828000] ACPI: Thermal Zone [THRM] (45 C)
[17179572.160000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 6 (level, low) -> IRQ 6
[17179576.732000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 6
[17179576.732000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 6 (level, low) -> IRQ 6
[17179576.836000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
[17179576.836000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
[17179576.940000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 6 (level, low) -> IRQ 6
[17179577.044000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[17179577.044000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[17179577.152000] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179593.228000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179594.052000] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKC] -> GSI 6 (level, low) -> IRQ 6
[17179594.180000] ACPI: PCI Interrupt 0000:02:06.1[A] -> Link [LNKC] -> GSI 6 (level, low) -> IRQ 6
[17179594.308000] ACPI: PCI Interrupt 0000:02:06.3[A] -> Link [LNKC] -> GSI 6 (level, low) -> IRQ 6
[17179594.440000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
[17179594.516000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[17179594.516000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[17179617.476000] ACPI: AC Adapter [ACAD] (on-line)
[17179617.576000] pcc_acpi: loading...
[17179617.588000] ACPI: Power Button (FF) [PWRF]
[17179617.588000] ACPI: Lid Switch [LID]
[17179617.588000] ACPI: Sleep Button (CM) [SLPB]
[17179617.624000] ibm_acpi: ec object not found
[17179617.652000] ACPI: Battery Slot [BAT1] (battery absent)
[17179617.652000] ACPI: Battery Slot [BAT2] (battery absent)
[17179617.664000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179621.116000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 6 (level, low) -> IRQ 6

---

### Post by raul_ on 2006-11-21
Same here...except it's not a blank screen. It sorta looks like static in TV =\

---

### Post by twstokes on 2006-11-23
Same thing here - ATI X300 running 8.31.5 drivers.

I get a blank screen.

---

### Post by twstokes on 2006-11-25
Ok here's what I did to get mine working 100%.

Remove any drivers that you installed before, and then follow [this guide]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-c966b2cb7c82944d6883f27a2896725db3b90a3a").

It took a reboot for my drivers to kick in, but after that it worked flawlessly.

---

### Post by arthur_kalm on 2006-11-27
> **twstokes said:**
> Ok here's what I did to get mine working 100%.

Remove any drivers that you installed before, and then follow [this guide]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-c966b2cb7c82944d6883f27a2896725db3b90a3a").

It took a reboot for my drivers to kick in, but after that it worked flawlessly.

Hmm I followed a similar guide [here]("http://www.ubuntuforums.org/showthread.php?t=291464&highlight=ati+drivers+edgy"), and after editing acpi-support as the HOWTO said, I was able to suspend (before it wouldn't even suspend just sit there with a blank screen). However, even though the suspend turns on correctly, I am not able to wake my laptop up after the suspend. ](*,)

---

### Post by drphilngood on 2006-11-27
[This]("http://www.columbia.edu/~ariel/acpi/acpi_howto.txt") helped me; twas my lvm swap.

---

### Post by morfyng on 2006-11-27
> **twstokes said:**
> Ok here's what I did to get mine working 100%.

Remove any drivers that you installed before, and then follow [this guide]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-c966b2cb7c82944d6883f27a2896725db3b90a3a").

It took a reboot for my drivers to kick in, but after that it worked flawlessly.

I'm sorry, but continuous to having the same problem (blank screen) with Ati drivers repository than Ati drivers proprietary ](*,) 

others suggestion :-k

---

### Post by nmincone on 2006-12-21
Everyone with suspend/hibernation problems, please STF before asking your questions, chances are it has already been addressed.


[Search this thread for clues...]("http://ubuntuforums.org/showthread.php?t=284994")
[Laptop testing team wiki...]("https://wiki.ubuntu.com/LaptopTestingTeam/")
This is a real problem that needs real solutions. Supporting hardware for suspend/hibernation is tricky business and could use some polishing in Linux. There's no magic bullet (at the moment).

---

### Post by karhulitos on 2007-02-14
I'm so happy I need to post now.
Acer Aspire 5040, ATI X200M. Standby mode always started ok but resume produced black screen (like backlight never starts or so..)
[edit] just to make sure I already have fglrx running fine on this box 
From arthur_kalm's link I only took this part:

"FGLRX Suspend and Hibernate
Edit "/etc/default/acpi-support" and change the following lines:
Code:

```
MODULES_WHITELIST="fglrx"
SAVE_VBE_STATE=false
POST_VIDEO=false
DOUBLE_CONSOLE_SWITCH=true

```
"
and voilá, resume worked like a Buick!

Now only problem left is that wlan won't get ip address unless I stop & start ath0. Once I find a workaround for that, I'm happy happy happy.. :)
[edit2] not true, dunno what I did in the first test but ever since 2nd standby, I've had all working in resume I had before entering standby mode.

---

### Post by Lonthong on 2007-02-23
> **karhulitos said:**
> I'm so happy I need to post now.
Acer Aspire 5040, ATI X200M. Standby mode always started ok but resume produced black screen (like backlight never starts or so..)
[edit] just to make sure I already have fglrx running fine on this box 
From arthur_kalm's link I only took this part:

"FGLRX Suspend and Hibernate
Edit "/etc/default/acpi-support" and change the following lines:
Code:

```
MODULES_WHITELIST="fglrx"
SAVE_VBE_STATE=false
POST_VIDEO=false
DOUBLE_CONSOLE_SWITCH=true

```
"
and voilá, resume worked like a Buick!

Now only problem left is that wlan won't ip address unless I stop & start ath0. Once I find a workaround for that, I'm happy happy happy.. :)

Hi karhulitos, can you please paste yr acpi-support here?
I tried on BenQ laptop (Turion X2 + Ati X1100) but still did not work.
Edit: suspend does work but resume not

---

### Post by karhulitos on 2007-02-23
> **Lonthong said:**
> Hi karhulitos, can you please paste yr acpi-support here?


Here you go, hope it's any help to you.

---

### Post by Lonthong on 2007-02-25
It is identical but mine cannot resume. Odd.............

---

### Post by twstokes on 2007-04-07
```
MODULES_WHITELIST="fglrx"
SAVE_VBE_STATE=false
POST_VIDEO=false
DOUBLE_CONSOLE_SWITCH=true
```

In Edgy this worked like a charm for me using 8.34.8 drivers to get resuming working. I have an ATI X300 running on an Inspiron 6000.

---

### Post by lodp on 2007-04-20
> MODULES_WHITELIST="fglrx"
SAVE_VBE_STATE=false
POST_VIDEO=false
DOUBLE_CONSOLE_SWITCH=true

same here! updated /etc/default/acpi-support with these values, and suspend worked again (after having been broken by an update to feisty beta). i' on an acer aspire 1650Z, with an ATI mobility radeon.

---

### Post by odelay on 2007-04-21
Worked great for me too!  Thanks.

---

### Post by garion on 2007-04-21
hmm :(  didn't work for me, don't know why, still stuck with a blank screen on resume.  i've tried it with 8.34 fglrx in repo, 8.35 installed with envy, 8.36 installed manually, same thing.  here is my acpi-support.  everyone here, how is mine different from yours?  do i have to change something in xorg.conf as well?  my laptop is a Dell E1505/6400 with ATI x1300 video, WSXGA+ screen, IPW3945, no bluetooth.



```

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="fglrx"

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
# LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql bluetooth"

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

```

---

### Post by bananasareformonkeys on 2007-04-22
> **arthur_kalm said:**
> Hmm I followed a similar guide [here]("http://www.ubuntuforums.org/showthread.php?t=291464&highlight=ati+drivers+edgy"), and after editing acpi-support as the HOWTO said, I was able to suspend (before it wouldn't even suspend just sit there with a blank screen). However, even though the suspend turns on correctly, I am not able to wake my laptop up after the suspend. ](*,)

my laptop also doesn't seem to wake up, unless i either unplug it or plug it in.  Then it wakes up with the little bubble that says running on AC power

---

### Post by garion on 2007-04-23
even plug in and unplugging power doesn't help me there... my screen is just dead blank on resume, no response with keyboard either... help!



> **bananasareformonkeys said:**
> my laptop also doesn't seem to wake up, unless i either unplug it or plug it in.  Then it wakes up with the little bubble that says running on AC power

---

### Post by spiffytech on 2007-04-24
It's possible that this is a framebuffer issue. In a terminal, "sudo gedit /etc/grub.conf" and change "vga=xxx" to "vga=normal". After you reboot, see if you still have problems. 

This has fixed problems under Slackware for someone else and Sabayon for me. I have an Intel 945GM graphics card on a Dell Inspiron e1405. It might work on your setup as well. Please let me know if it does.

---

### Post by strabes on 2007-04-24
Change "POST_VIDEO=true" to "POST_VIDEO="

reboot and try to suspend.

---

### Post by fastb on 2007-04-24
Editing that file worked!!! Yeeeeyyyyy :guitar:

---

### Post by faust99 on 2007-04-25
Sorry, I'm a total newbie...how do I do "Change "POST_VIDEO=true" to "POST_VIDEO="". I have no idea where to start even...

---

### Post by BoyMike on 2007-05-03
> **faust99 said:**
> Sorry, I'm a total newbie...how do I do "Change "POST_VIDEO=true" to "POST_VIDEO="". I have no idea where to start even...

This is what you have to do:
Open a terminal window.
Enter the following:
```
sudo gedit /etc/default/acpi-support
```
Then you password, and Gedit window with the apci-support file should pop up.
-Mike

---

### Post by faust99 on 2007-05-03
> **BoyMike said:**
> This is what you have to do:
Open a terminal window.
Enter the following:
```
sudo gedit /etc/default/acpi-support
```
Then you password, and Gedit window with the apci-support file should pop up.
-Mike

Thanks Mike! I'd already worked out since then but I appreciate your response.

---

### Post by BVStang1967 on 2007-07-07
> **twstokes said:**
> ```
MODULES_WHITELIST="fglrx"
SAVE_VBE_STATE=false
POST_VIDEO=false
DOUBLE_CONSOLE_SWITCH=true
```

In Edgy this worked like a charm for me using 8.34.8 drivers to get resuming working. I have an ATI X300 running on an Inspiron 6000.

I'm running UbuntuStudio (feistyfawn) on my thinkpad t60p and that fix did the trick!
Thanks so MUCH!

---

