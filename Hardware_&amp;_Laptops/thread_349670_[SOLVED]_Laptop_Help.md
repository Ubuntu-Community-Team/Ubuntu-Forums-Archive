---
title: "[SOLVED] Laptop Help"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by MrFSL on 2007-01-30
Hello All,
    Having a problem installing Ubuntu on a Compaq Presario 1625, Its an old laptop with an AMD 266 cpu and 98 MB of system RAM. I was hoping to use this old computer as a headless CUPS print server supporting 3 printers in my home office.

     I downloaded Edgy Server install CD and the installation goes well with no errors. When I restart after the installation is complete the GRUB bootloader comes up and then I get the part saying "Starting" and the then the computer restarts.

     The computer runs knoppix just fine and Debian. I thought it might be a Grub setting so I disabled "quiet" and tried several different vga settings and fb settings. None of the log files are giving me any information. Where do I go from here? What do I try next? Any help would be greatly appreciated.

Thank You.
MrFSL

---

### Post by dannyboy79 on 2007-01-30
try noapic and or irq=poll in your boot line that's within your /boot/grub/menu.lst file. when grub starts, hit esc and then the grub menu shows up, then you can modify the grub lines prior to booting. it should boot, then you can fix it permanently. old machines like yours and mine need these cause the bios is so old. i have a pentium mmx 266MHZ with 128MB ram and I was able to install xubuntu dapper drake. it makes then thing purr.

---

### Post by MrFSL on 2007-01-30
Thank You for the reply.

I have tried your suggestions as well as numerous combinations of other GRUB options such as:

failsafe
single
noapic
nolapic
irqpoll
irq=poll
acpi=off
fb800x600


In all cases I get the same result. I see the words "Starting Up...", then the screen flashes once and the computer reboots. I have successfully installed Debian Stable and it boots this computer with no additional GRUB options.

WHAT AM I DOING WRONG!!!??

Thank You.
MrFSL

---

### Post by MrFSL on 2007-01-30
Got it to boot finally.

Read here: [http://www.linuxquestions.org/questions/showthread.php?t=512053](http://www.linuxquestions.org/questions/showthread.php?t=512053)

and found a post explaining the problem with K6 processors and the default Ubuntu Server kernel image. I used a Debian CD to boot the laptop mounted the the local HDD and then chroot.

From here I did an apt-get install linux-image-386 and then restarted.

To boot correctly I modified the GRUB bootloader to include:

pci-noacpi
vga=771
noapic
nolapic
irq=poll

(Thanks for the hint there dannyboy79! ;) )

Everything booted. Once in I made permanent changes to /boot/grub/menu.lst and also did a:
sudo apt-get remove linux-image-server so this kernel would not automatically get updates with a apt-get upgrade.

Thank you for the help once more. It was greatly appreciated.

---

### Post by dannyboy79 on 2007-01-31
glad you got it! that's weird that ubuntu would include a default kernel that not compatible with "most" computers?

---

### Post by MrFSL on 2007-02-01
I agree but it is the server install disk. I suppose someone figured that if one was to create a server they would want it on modern hardware. In most cases i would agree. In my case however I couldn't be happier. Thanks to CUPS and OpenSSH I have a great headless print server supporting 2 computers. --PLUS -- Thanks to this forum I was able to 

1) Get this old laptop running Linux
2) Setup this print server
3) Gain USB support through an add on card and some grub command line options
4) Get my Lexmark x1150 driver installed and working 100%

Appreciate all the help.

---

