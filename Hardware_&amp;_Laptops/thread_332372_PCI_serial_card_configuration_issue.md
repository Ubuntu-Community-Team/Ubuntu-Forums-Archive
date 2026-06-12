---
title: "PCI serial card configuration issue"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by alexheizer on 2007-01-05
Hi,

Here's the problem I'm having: 

Background info: I have a PCI card which adds a 9-pin 16550A serial port to my computer. It works in Windoze (its own bootable partition), it works in Linux (autodetected and assigned to /de/vttyS4, and it shows up in dmesg properly). In both OSes I can connect a Wacom tablet and get movement, which means it works enough for me. I also am running Parallels Workstation to boot into another instance of WinXP on a virtual machine. Everything works perfectly on the VM, except for this one thing. 

The problem: when I boot into Parallels, it autodetects the serial PCI card without a problem and adds it to the config file for this VM, but gives me an error which says...
"Serial port 1 disabled because Parallels Workstation is unable to exclusively lock the port to this virtual machine. Please check the real port is not used by another process."
...even though I have disabled all of my getty processes (I don't think anyone is going to be dialing in since the computer doesn't even have a modem!) and don't have anything plugged into that port. I've also tried putting the card into different slots with no change in behavior, and disabled any serial configuration (including built-in modem, which this model doesn't have anyway) in my BIOS without affecting the error message.

So my questions are:
1. How can I troubleshoot to see what is happening (or what my computer *thinks* is happening) on /dev/ttyS4? Running 'ps aux' doesn't show anything running on ttyS4, and neither does 'ps at'.
2. How can I manually configure the PCI card to put this serial port on another /dev/ttySx? (I'm wondering if the fact that Windows only has COM1-COM4, which normally translate to ttyS0-ttyS3 is what's causing this error)

Thanks for any help you can give, I've been knocking my head against the wall for the last 3 days.

Alex

---

