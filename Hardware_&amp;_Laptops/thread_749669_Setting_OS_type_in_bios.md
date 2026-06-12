---
title: "Setting OS type in bios"
date: 2008-04-08
forum: Hardware &amp; Laptops
---

### Post by Deb.Early on 2008-04-08
I'm trying to run down a communications problem between apcupsd and a serial port which I suspect might be an IRQ issue, and realized I have no idea how the "Plug & Play OS" setting in the system bios should be set for Ubuntu. I've never had to touch that setting before, and I've googled until I'm blue in the face -- some say "yes", some say "no".  :confused:

The machine has an Asus M2A-VM motherboard, and I'm running Gutsy i386 server as a headless fileserver. Right now the PnP OS setting is "no". Anybody know what it *should* be for Ubuntu?

Thanks for any help!

---

### Post by seapahn on 2008-04-19
I had to set plug-and-play OS to YES to get ubuntu (Gutsy) to install properly on my m2a-vm. After that, I haven't touched it. I did have problems with the serial port but I am now using a USB to serial dongle and didn't spend too much time trying to debug the on-board com port.

I suspect my problem was with the connector I used to go from the motherboard out to my serial port device but again, not sure why it didn't work (ubuntu seemed to detect and run the drivers for it just fine when I did enable the onboard com port though).

---

