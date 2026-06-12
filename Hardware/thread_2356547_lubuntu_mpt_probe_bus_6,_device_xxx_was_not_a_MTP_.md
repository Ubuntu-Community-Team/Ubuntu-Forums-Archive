---
title: "lubuntu mpt probe: bus: 6, device: xxx was not a MTP device install caught in loop."
date: 2017-03-24
forum: Hardware
---

### Post by luigiwriter2 on 2017-03-24
Lubuntu install does fine right up to the "The installation will end soon" screen and goes into a loop trying to find a usb device that is MTP. 

I have let it run for over an hour and a half and it constantly repeats "lubuntu mpt probe: bus: 6, device: xxx was not a MTP device." it tests all of the bus6-1 usb devices [more than 126] then restarts back at usb1 and continues probing up past usb126 again. 

It remains in this continuous loop until I use ctrl+alt+del to stop it. [the only thing that shuts it down, however leaving the system un-bootable] and me to start the installation all over from the start. [Looking at a third try.].

To eliminate the DVD iso, I have burned a new Lubuntu 16.10-desktop-amd64.iso from [http://cdimage.ubuntu.com](http://cdimage.ubuntu.com) DVD creating it with K3B. I Followed the checklist, confirmed hash, and the install disk inspection found no faults.

This was a working dual boot Win8 and Ubuntu machine. However the HP110-220z 1.8 Ghz processors were too slow for either win8 or Ubuntu 16.04 even with a RAM upgrade to 16 GiB.

I re-partitioned creating a 1028 MiB EFI partition on the hard drive and formatting everything but sda11/home with the intention of installing Lubuntu 16.10. 

Does anyone have a workaround?

I have looked at Xubuntu and Kubuntu, but if both use the same Ubuntu mpt probe as Lubuntu relies on and will not install with out a MPT usb device I'm sunk. 

Another question is if the same probe is in Ubuntu 16.04, because it installed sucessfully, just kept graying out Libre-Office and FireFox windows for minutes at a time waiting for the processors to catchup with the IO wait backlog?[ATTACH=CONFIG]274283[/ATTACH][ATTACH=CONFIG]274284[/ATTACH]

---

