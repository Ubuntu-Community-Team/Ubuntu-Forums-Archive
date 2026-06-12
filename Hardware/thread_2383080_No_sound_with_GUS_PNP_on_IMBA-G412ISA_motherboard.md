---
title: "No sound with GUS PNP on IMBA-G412ISA motherboard"
date: 2018-01-20
forum: Hardware
---

### Post by danieldeme on 2018-01-20
To whom it may concern,
I have been trying to start my old GUS PNP on Ubuntu 32 bit 14.04. without success.
I have loaded snd_interwave. I have checked with alsamixer (unmuted).
No interruption conflicts.
On aplay: *pcm_write*:*1939*: *write error*: *Input*/*output error*.
During testing, there are no parameters: */proc/asound/card2/pcm0p/sub0/hw_params* - followed by nothing, but returns to $. See below the terminal report.
Is anybody have a suggestion for this problem?
Thank you in advance!
Daniel

$ cat /proc/interrupts
           CPU0       CPU1       CPU2       CPU3       
  0:      11049      11168      10273       9303   IO-APIC   2-edge      timer
  1:          0          1          0          1   IO-APIC   1-edge      i8042
  8:          0          1          0          0   IO-APIC   8-edge      rtc0
  9:          0          2          0          1   IO-APIC   9-fasteoi   acpi
 11:          0          0          0          0   IO-APIC  11-edge      InterWave
 12:          2          0          1          1   IO-APIC  12-edge      i8042
 14:        142        196        188        139   IO-APIC  14-edge      ata_piix
 15:          0          0          0          0   IO-APIC  15-edge      ata_piix
 16:          0          0          0          0   IO-APIC  16-fasteoi   uhci_hcd:usb5
 18:          0          0          0          0   IO-APIC  18-fasteoi   uhci_hcd:usb4
 19:       3433       2509       3967       2483   IO-APIC  19-fasteoi   ata_piix, uhci_hcd:usb3
 23:       2820       2326         77         33   IO-APIC  23-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
 24:          0          0          0          0   PCI-MSI 458752-edge      PCIe PME, pciehp
 25:          0          0          0          0   PCI-MSI 460800-edge      PCIe PME, pciehp
 26:          0          0          0          0   PCI-MSI 524288-edge      eth0
 27:       1059         36         48       4208   PCI-MSI 1048576-edge      eth1
 28:        134        136        133        135   PCI-MSI 442368-edge      snd_hda_intel
 29:        448        415        327        395   PCI-MSI 32768-edge      i915
NMI:         21         23         19         24   Non-maskable interrupts
LOC:      14095      13475      12569      18994   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:         21         23         19         24   Performance monitoring interrupts
IWI:          0          0          0          0   IRQ work interrupts
RTR:          0          0          0          0   APIC ICR read retries
RES:       3384       2553       2742       2649   Rescheduling interrupts
CAL:       3211       2034       1604       1655   Function call interrupts
TLB:       2734       1654       1366       5511   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
DFR:          0          0          0          0   Deferred Error APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:          1          1          1          1   Machine check polls
ERR:          0
MIS:          0
PIN:          0          0          0          0   Posted-interrupt notification event
PIW:          0          0          0          0   Posted-interrupt wakeup event

$ aplay -D hw:2,0 /home/daniel/BACHHARP.WAV
Lejátszás WAVE '/home/daniel/BACHHARP.WAV' : Signed 16 bit Little Endian, Rate 44100 Hz, Sztereó
aplay: pcm_write:1939: írási hiba: Kimeneti/bemeneti hiba 

$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe9f8000 irq 28
 1 [VGA            ]: USB-Audio - FaceCam VGA
                      KYE Systems Corp. FaceCam VGA at usb-0000:00:1d.7-4, high speed
 2 [InterWave      ]: AMD InterWave - AMD InterWave
                      AMD InterWave at 0x220, irq 11, dma 5&7

$ find /proc/asound/ -name hw_params | xargs -I FILE grep -v -l "closed" FILE | grep '/proc/asound/card./pcm.p/sub./hw_params'
/proc/asound/card2/pcm0p/sub0/hw_params
$

---

