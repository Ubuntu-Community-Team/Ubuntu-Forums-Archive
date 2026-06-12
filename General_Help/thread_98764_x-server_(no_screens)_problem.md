---
title: "x-server (no screens) problem"
date: 2005-12-04
forum: General Help
---

### Post by Tallowwood on 2005-12-04
Running the Hedghog so please excuse me posting here. There IS a Breezy angle. 

I am seeking help/ direction to resolve an x-server error which occured when I ran the Breezy LIVE CD on my machine (which has Hoary installed). 

I am not sure if there is a connection - I assume there should not be - but I experienced streaky graphics with BB LIVE and when I tried to load up Hoarythe x-server failed with the error "Fatal server error: no screens found".

I have checked the LOG (/var/log/Xorg.0.log) and read the X-Org FAQ (ErrorMessages) which says (inter alia):  "Screen(s) found, but none have a usable configuration. In most cases this means there are no video modes available for your configuration. Each entry in the list of specified or default video modes gets checked if it lies withing the limit or the hardware: if it lies within the sync range specified or probed for the monitor, if it will work with the memory available on the video card or if the pixel clock lies within the range supported by the chipsets. There are many more limits. For each rejected mode you can see in the log file the reason for rejection:
(II) VGA(0): Not using default mode "320x200" (vrefresh out of range)
(II) VGA(0): Not using default mode "720x400" (insufficient memory for mode)
(II) VGA(0): Not using default mode "360x200" (hsync out of range)"

I my case I can see no such lines in the log. The main clue seems to be the error report: (EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
[extract from log is below]

I don't know much about compiling kernal modules or where to find the x-org settings files or which settings to adjust. 

Can one of you helpful people give me a few pointers about how to fix this? Is there an x-server configuration tool with the Ubuntu distribution that I could be using?

cheers, Tallowwood

========= extracts from log file ==============
X Window System Version 6.8.2 (Ubuntu 6.8.2-10.1 20050831033957 [snip]
X Protocol Version 11, Revision 0, Release 6.8.2 [snip] 
Build Operating System: Linux 2.6.10 i686 [ELF] [snip]
Module Loader present
OS Kernel: Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) [snip]
(II) NVIDIA X Driver  1.0-7174  Tue Mar 22 06:48:37 PST 2005
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found [snip]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo"
(--) NVIDIA(0): Linear framebuffer at 0xF0000000
(--) NVIDIA(0): MMIO registers at 0xEE000000
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
====================

---

### Post by grimmson on 2005-12-04
Just some thoughts. Is this a laptop? This is an Nvidia card? Onboard? What modle? Md5sum the breezy disk (check for bad burn?) What works in xorg.config Hoary? Whats different in Breezy (other than the really obvious)?  I wish I was smarter. Good luck.

---

