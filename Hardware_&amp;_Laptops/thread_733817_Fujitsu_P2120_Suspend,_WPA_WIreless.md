---
title: "Fujitsu P2120: Suspend, WPA WIreless?"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by TrevorBradley on 2008-03-24
I've got an old Fujitsu P2120 laptop.  I've tried a few times to install Ubuntu on it in the past few months, but have got frustrated and given up a couple of times now.  I thought I'd give it a real go this time.  I'm installing Ubuntu 7.1.  I've got 11 years of linux experience under my belt, and I'm running 4 Slackware installs in the house, but I thought it was time to try something new)

I manged to get many of the video issues resolved with a great thread here:

[http://ubuntuforums.org/showthread.php?t=68489&highlight=p2120](http://ubuntuforums.org/showthread.php?t=68489&highlight=p2120)

and the system is significantly faster than when I first installed ubuntu.

I have two major issues remaining that are show stoppers.  I tried reading through the forums and trying several ideas posted there, but couldn't seem to get them to work.

1) I can't seem to connect to my WPA wireless network.  Network Manager can see the network, but by default it wants to connect to a WEP encrypted network.  If I specify the name of the network, it accepts WPA as an option, but it can't seem to get an IP address.  I've tried a few options on the forums here, including wpa_supplicant, but I can't seem to get it working. The wireless card is an onboard Intersil Prism Wireless PCI 802.11b.

I'm really considering getting a PCMCIA 802.11G card for the system.  Are there any cards out there that work well with linux and ubuntu?

2) My laptop screen goes off when I close it up, but it doesn't shut off. Sleeping or Hibernating manually seem to cause everything to lock up.  It looks as if this may be a video issue... the computer uses an onboard ATI Radeon Mobility with 8MB of ram.

Reading the forums it sounds like this is a common problems for laptop users and 7.1,  Should I wait for Ubuntu 8?  Should I try the beta to see if the problem goes away?

Any info/links you can provide me would be very useful,.  I'll provide any info you need.  Thanks in advance!!

---

### Post by Whiffle on 2008-03-27
I found this on the suspend issue:
> 
Suspend to RAM (S3) works, do not use s3_bios, remove the ohci_hcd module before suspending, mouse stops working on resume, press Fn F4 (mouse) key twice to re-enable it.

here
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsFujitsu](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsFujitsu)

Sounds to me like there is some module issues going on here, you may try adding the module ohci_hcd to the /etc/default/acpi-support file, it has a list of modules to be unloaded on suspend and reloaded on resume.  s3_bios you may have to research a bit more, I don't know off the top of my head what that entails.

---

