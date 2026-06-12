---
title: "Network Card Firmware missing in 9, worked in 8.5?"
date: 2010-03-02
forum: Hardware
---

### Post by PoppyLoch on 2010-03-02
I'm getting the following message on startup as well as when I configure my network card and restart networking:

[    9.994947] e100 0000:01:07.0: firmware: requesting e100/d101m_ucode.bin
[   10.043451] e100: eth1: e100_request_firmware: Failed to load firmware "e100/d101m_ucode.bin": -2
[   10.064123] e100 0000:01:07.0: firmware: requesting e100/d101m_ucode.bin
[   10.070517] e100: eth1: e100_request_firmware: Failed to load firmware "e100/d101m_ucode.bin": -2

A brief history of this machine:
This system was running as a web server on Ubuntu server 8.04 for a year and a half when both hard drives started reporting imminent failure. We replaced both drives, and installed server os version 9.1 instead of 8.04.

Post-install, I reconfigured the network cards - one internal on the local network, one external with direct internet access - and found that only the built-in network card was functioning. The add-in card - an Intel 10/100 PCI card - is generating the error given above.

I've searched for a solution to no avail. I'm hoping someone with more experience than I will be able to point me in the right direction.

Thanks,

--Poppy

---

