---
title: "IONITX wake from S5 by USB IR remote"
date: 2010-11-03
forum: Hardware
---

### Post by PeterWurmsdobler on 2010-11-03
Hello,


Preamble: when a motherboard is in S5, soft power off, the motherboard is powered from the 5VSB and some circuitry is still alive, such as the Ethernet PHY for WoL, or the USB host, provided the motherboard’s hardware allows for it, and the BIOS permits enabling it. For instance, my Zotac IONITX-B-E has a jumper which can be set such that the USB subsystem remains powered on S5. I am unsure about wake on USB from S5 though.
   
  When my IONITX-B-E is in S5, it appears that my USB IR receiver (CiT Media Centre Remote and receiver from [http://www.cclonline.com]("http://www.cclonline.com/")/) is alive and acknowledges received IR codes by flashing a red LED. Unfortunately, it does not wake (i.e. boot) from S5 when I press the power button on the remote control. Obviously the OS cannot play a role yet at this stage (even though I tried the “echo USB0 > /proc/acpi/wakeup” when it was powered before, but it only is for S3). 
   
  So the questions:

- If the USB subsystem has power from the 5VSB, then a USB IR receiver connected to USB will be powered as well? 
   
  - If the remote control sends a power-on command, say some specific 32 bit value to the IR receiver, the IR could be programmed such that on receipt of this special code it sends a USB message to the host? 
   
  - Now, usually USB devices are polled by the host, so how could a USB device initiate the transmission of a packet of any kind? 
   
  - Further, is there a standardised “wake-up” packet a USB device can send to the USB host controller that encodes a Power-on? 
   
  - Then, what must the USB host controller implement in order to be able to switch on the motherboard? 
 
   - What provisions can the OS (Ubuntu) make to enable the desired behaviou?
    
 - Bottom line: what does the IR USB receiver have to tell the USB host in order to make the USB host tell the motherboard to power on?
   
  - What IR receiver + remote + IONITX combination would allow booting the motherboard from S5?

It all is still a mystery, but I would like to understand how the USB triggered boot works and what hardware I need to see it happen.
   
  I would appreciate any hints that shed a light on this issue.
  Kind regards,
  peter

---

### Post by Gibby13 on 2010-11-29
Any luck on this yet?
How do get to S5?

---

