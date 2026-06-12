---
title: "Micro-ATX motherboards for Intel 3G or 4G Core with floppy support?"
date: 2014-02-23
forum: Hardware
---

### Post by bcschmerker on 2014-02-23
I am looking at the problem of rebuilding my Hot Rod gPC™ (Gigabyte® GA-MA78GM-S2HP-based AMD® Athlon64® rig in an Everex® TC2502 micro-ATX mid-tower case) for Intel® hardware, as I could never get the Realtime or LowLatency Kernels to run right on my X2 5600+.  I anticipate needing specific legacy ports:  an Intel® P8042 or equivalent on a mini-DIN6 (Keyboard/Mouse common), an EIA-232D asynchronous serial port on a DE9 (TTYs0), and an Intel® P8272 or equivalent on a Shugart-compatible disquette interface port (definitely FD0; FD1 if the mobo supports it).  A planar IEEE 1284 port (LP0) is desirable but not critical.  I have judged the Intel® 3rd- and 4th-Generation Core Processors™ (LGA 1155 and 1150, respectively)) to be suitable for the rebuild; if the candidate motherboard is built for the 4th-Generation Core™, I have a contingency plan for drivers from the Ubuntu-X Team at Launchpad™ in the event that I cannot use one of the more recent Advanced Micro Devices® Radeon® HD™ 256-bit PCI-Express x16 video display adapters (I already have an Asus® EAH6850DC/2D1S/1GD5 VDA in my current Windows box and judge the HD 6850 appropriate for Ubuntu® 14.04-LTS).

Hardware to be retained includes the TC2502 case as modified; an Antec® TruePower® 750 Blue™ power-supply unit; a Mitsumi® FA404 combination disquette drive and card reader; a Creative Laboratories® SB0350 PCI 2.2 audio card with SB0250 I/O Drive™; and several USB 1.1 and/or 2.0 devices.  My new-hardware acquisition plan includes, in addition to a Logitech® G500s USB 2.0 mouse to replace a worn-out TrackMan® Wheel™, an IBM® 85xx/95xx-compatible Unicomp® keyboard of some sort; the Endurapro™ 104 and 105 are available with an optional single-mini-DIN6 cable, but ideally I'd use an On The Stick 122 emulator model with a specific set of keymaps, both terminal and X.org, for directly supporting UnIX wide-area-network communications, Console swapping, etc.

What micro-ATX motherboards by manufacturer are out there for the 3rd- and 4th-Gen Core that pack legacy keyboard/mouse, EIA-232D and disquette ports (IEEE 1284 desirable)?  Links to Website specs pages would be appreciated.

---

### Post by mastablasta on 2014-02-24
is that PS2 for mouse/keyboard? if so PS/2 to USB are cheap.

you could probably get USB floppy drive.

there mightbe some transitional motherboards out there. i got one with AGP and it has DDR as well as DDR2 ram, floppy, IDE and SATA etc. but i got it quite some time ago and it doens't have latest tech. still i could use everything from the old box. i only needed a new CPU (cheapest dual core celeron i could get solved that).

---

### Post by bcschmerker on 2014-02-24
Primarily keyboard, in fact, although specific Unicomp® models will also function as backup pointing devices in case of a USB driver crash.  A single mini-DIN6 for legacy keyboard and mouse is sufficient for my requirements.

I see a potential problem recognizing USB 3-1/2" floppies during boot.  LinUX Kernels 3.x would detect the Intel® P8272, Western Digital® WD17C7x, Nippon Electric Corporation® &#956;PD765AC and comparable controllers and assign them in UDevFS as /dev/fd0; don't know if that's the case with the integrated floppy controller in the Dell® P/N 6Y185-A02, a USB 2.0 device.  One planar EIA-232D single-channel serial port (assigned in UDevFS as /dev/ttyS0) is needful for diagnostic work in case the video display adapter goes down; additional EIA-232D and IEEE 1284 ports can be added in the form of a PCI-Express x1 multiprotocol adapter.

---

### Post by mastablasta on 2014-02-25
what is the reason behind the floppy drive need? perhaps there is a different solution available.

---

### Post by bcschmerker on 2014-02-25
The disquette transport in the Mitsumi® FA404 is a legacy device requiring a Shugart-compatible floppy controller, which I have searched for among currently-available PCI-Express x1 super-I/O cards, unsuccessfully as of February 2014.  I've read the specifications on the KryoFlux® USB 2.0 inline floppy controller (engineered for both archiving and serious diagnostics on several different formats by sectors per track on disquette drives of up to 84 cylinders), but suspect a lack of recognition by legacy-free systems as a valid boot device.

---

### Post by bcschmerker on 2014-03-09
**Update:**  I found two fallback candidates for my project. I'm limiting the search to micro-ATX mobos on account of the Everex® case; the ASRock® Z77 Extreme6 (LGA 1155), which meets my requirements for legacy hardware, would force a full-tower case for standard ATX mobos.

The ASRock® 775I65G R3.0, designed for the Intel® Pentium Processor® D™ (FCLGA 775), packs a full bag of legacy connections:  Integrated GPU driving a DE-15 port (VGA/XGA), three PCI 2.0 and one 8X AGP expansion slots, segregated i8042 mini-DIN6 jacks for keyboard and mouse, external IEEE 1284 and EIA-574 (backwards-compatible with EIA-232E) rear-panel connectors, one 34-pin disquette header, two Enhanced IDE and two SATA 1.0 hard-drive connectors, and three rear (ea. with two jacks) and two internal USB ports.

The ASRock® G41C-GS, designed for the Intel® Core2 Processor™ (LGA 775), also packs an integrated GPU driving a DE-15 port, rear EIA-574 serial port, internal header for IEEE 1284, two PCI 2.0 and two PCI-Express 1.0 (one x1 and one x16) expansion slots, segreated i8042 mini-DIN6 jacks, one 34-pin disquette header, one Enhanced IDE and four SATA 1.x hard-drive connectors, and two rear (ea. with two jacks) and two internal USB ports.

---

### Post by mastablasta on 2014-03-10
i have a few AsRocks. one died in less than a year others continue to function. it is difficult to find mobo supporting old HW. they are out there, but choice is very limited.

i bought a rather strange one featuring DDR and DDR2 slots for RAM. the hting was i had all these older components that worked fine but i had to replace motherboard and CPU as they were too slow for desktop. so i got one of those new mobo that support old stuff. the upgrade was cheap and computer has been in use now for over 4 years and still going quite strong. can even play some nice games on it.

---

### Post by bcschmerker on 2014-03-11
> **mastablasta said:**
> i have a few AsRocks. one died in less than a year others continue to function. it is difficult to find mobo supporting old HW. they are out there, but choice is very limited.

i bought a rather strange one featuring DDR and DDR2 slots for RAM. the hting was i had all these older components that worked fine but i had to replace motherboard and CPU as they were too slow for desktop. so i got one of those new mobo that support old stuff. the upgrade was cheap and computer has been in use now for over 4 years and still going quite strong. can even play some nice games on it.
Thanks for the confirmation.  ASRock® does support legacy hardware in a few full-size ATX mobos such as the Z77 Extreme6 and its gaming counterpart the FATAL1TY® Z77 Professional; but, as I mentioned Post 5, those models would force me to a larger case.  I'm leaning toward a single Enhanced IDE port on account of an older DVD-Multi optical drive, which would feed either my existing Creative Laboratories® SB0350's CD In, or the Asus® XONAR® Essence™ ST™ Auxiliary In; both cards are ALSA-supported.

Incidentally, I found two potential winners of my search from ASRock® as of 10 March 2014.  The P55M Pro (LGA 1156, for Intel® 2nd-Generation Core™ Processors) packs dual mini-DIN6's for keyboard and mouse, three rear (six total jacks) and three internal USB ports, four SATA ports, and internal headers for disquette, front-panel audio, single Enhanced-IDE, EIA-232, IEEE 1284, IEEE 1394, and TPM.  The Z68 Pro3-M (FCLGA 1155, for Intel® 3rd-Generation Core™ Processors) packs a mini-DIN6 keyboard port, five SATA ports (two V3), two rear (four jacks) and three internal USB 2.0 ports plus one (two jacks) USB 3.0 port, and internal headers for disquette, EIA-232, IEEE 1284, and front-panel audio.  I already anticipated a new fansink for either candidate due to the four-screw mounting (vs. the AMD® clip mount in my present rig).

---

### Post by bcschmerker on 2014-03-20
**I HAVE A WINNER:**  [ASRock® Z68 Pro3-M]("http://www.asrock.com/mb/Intel/Z68%20Pro3-M/") (FCLGA 1155).  Natively supports the Intel® 3rd-Generation Core Processors&#8482;, DDR3-1600 SDRAM, three SATA 2 and two SATA 3 devices, planar EIA-574, planar IEEE 1284 (I plan to build a custom dongle for an MDR36 jack retrofit), IR and CIR interfaces, a balanced set of USB 2.0 and 3.0 ports, and a single disquette transport (needed for the Mitsumi® FA404 as stated [Post 1 this Thread]("http://ubuntuforums.org/showthread.php?t=2207516&p=12938083#post12938083")).  Given my experience with the Advanced Micro Devices® Athlon 64® X2 5600+ and Athlon II® X2 220, I'm looking into several Intel® 3rd-Generation Core&#8482; i5-3500 desktop APU's in the 65W class (as of 20 March 2014); the [i5-3475S](http://ark.intel.com/products/65515/) (6MB L3 cache, 3.60*max* GHz CPU clock) packs the HD Graphics 4000, the other candidates the HD Graphics 2500. :KS

Due to the Unified Extensible Firmware Interface on the Z68 Pro3-M, I anticipate needing a Signed Kernel Package (e.g., **linux-signed-image-3.13.0-*n*-generic** or **linux-signed-image-3.13.0-*n*-lowlatency** series) as part of the Ubuntu® 14.04-LTS installation; I also anticipate adding the Repository PPA:ubuntu-x-swat/intel-graphics-updates to APT due to the constant bug-fixing underway on the eventual winning APU's internal HD Graphics.  If I run into unexpected issues, I'll let y'all know. ):P

---

