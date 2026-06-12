---
title: "Intermittent scanning problem"
date: 2017-04-02
forum: Hardware
---

### Post by phoenix1963 on 2017-04-02
Hi all, I'm having an intermittent problem with my Samsung MFP M288x printer/scanner.
Sometimes it scans fine with simple-scan, sometimes it completely fails.
This is the sort of output I get when I run simple-scan -d :
```
[dll] sane_get_devices: found 1 devices
[+6.49s] DEBUG: scanner.vala:338: sane_get_devices () -> SANE_STATUS_GOOD
[+6.49s] DEBUG: scanner.vala:350: Device: name="smfp:usb;04e8;346a;071UBJDF80004PF" vendor="Samsung" model="M288x Series on USB" type="Scanner"
[+17.41s] DEBUG: ui.vala:2124: Saving state to /home/user/.cache/simple-scan/state
[+17.64s] DEBUG: ui.vala:2124: Saving state to /home/user/.cache/simple-scan/state
[+17.80s] DEBUG: ui.vala:2124: Saving state to /home/user/.cache/simple-scan/state
[+18.31s] DEBUG: ui.vala:2124: Saving state to /home/user/.cache/simple-scan/state
[+24.76s] DEBUG: ui.vala:2124: Saving state to /home/user/.cache/simple-scan/state
[+24.92s] DEBUG: ui.vala:2124: Saving state to /home/user/.cache/simple-scan/state
[+25.28s] DEBUG: ui.vala:2124: Saving state to /home/user/.cache/simple-scan/state
[+26.61s] DEBUG: ui.vala:2124: Saving state to /home/user/.cache/simple-scan/state
[+26.68s] DEBUG: simple-scan.vala:404: Requesting scan at 300 dpi from device 'smfp:usb;04e8;346a;071UBJDF80004PF'
[+26.68s] DEBUG: scanner.vala:1560: Scanner.scan ("smfp:usb;04e8;346a;071UBJDF80004PF", dpi=300, scan_mode=ScanMode.COLOR, depth=8, type=ScanType.SINGLE, paper_width=0, paper_height=0, brightness=0, contrast=0)
[+26.68s] DEBUG: scanner.vala:803: Processing request
[dll] sane_open: trying to open `smfp:usb;04e8;346a;071UBJDF80004PF'
[+26.80s] DEBUG: ui.vala:2124: Saving state to /home/user/.cache/simple-scan/state
[+28.46s] DEBUG: ui.vala:2124: Saving state to /home/user/.cache/simple-scan/state
[+60.99s] DEBUG: scanner.vala:864: sane_open ("smfp:usb;04e8;346a;071UBJDF80004PF") -> SANE_STATUS_IO_ERROR
[+60.99s] WARNING: scanner.vala:868: Unable to get open device: Error during device I/O
[+61.36s] DEBUG: ui.vala:2124: Saving state to /home/user/.cache/simple-scan/state

```

As you can see, it's failing to talk to the device.
The fact that it's intermittent makes me suspect some sort of usb sleep problem?

I'd be grateful for any insight.

phoenix1963

---

### Post by pdc on 2017-04-02
if one googles on ```
WARNING: scanner. Unable to get open device: Error during device I/O
```

one finds hardware issues reported eg [https://ubuntuforums.org/showthread.php?t=1964953&page=2](https://ubuntuforums.org/showthread.php?t=1964953&page=2)

You say the device is an Samsung MFP M288x but when I google I see things like Samsung MFP M2885FW and its predecessor, the MFP M2875FW

It looks a very nice machine, and it is only 2 yrs old? [http://au.pcmag.com/samsung-multifunction-xpress-m2885fw/35965/review/samsung-multifunction-xpress-m2885fw](http://au.pcmag.com/samsung-multifunction-xpress-m2885fw/35965/review/samsung-multifunction-xpress-m2885fw)

---

### Post by phoenix1963 on 2017-04-10
All the results I get from googling the error are about *never* connecting to it, not the intermittent fault I get.

It is the M2885FW, all the M28xx series seem to have the same drivers etc. It seems a good b/w printer.

phoenix1963

---

### Post by phoenix1963 on 2017-04-10
I'll add - the other aspect to it is that it's connected by both USB and the network. Is sane getting confused?

phoenix1963

---

### Post by efflandt on 2017-04-11
What do you get for list of scanners with scanimage -L if you think it might be confusing USB and network?```
scanimage -L
device `lexmark_nscan:libnet/SPECIFY_DEVICE' is a Lexmark Network Scanner
device `lexmark_nscan:libnet/0021B7009DA6' is a Lexmark Lexmark C543 Ethernet Scanner
device `lexmark_nscan:libnet/0021B7C8A365' is a Lexmark Lexmark X204n Ethernet Scanner
```For example in this case the Lexmark network scanner driver thinks that both of my printers can scan, but only the X204n can. If the other was an X543 it would also be able to scan, but the C543dn is just a printer (duplex color laser).

But I have other issues that the 64-bit Lexmark network scanner driver works in 14.04 and 32-bit driver works in 32-bit 16.04, but 64-bit driver does not work in 64-bit 16.04 or 16.10 (No scanners were identified.). So the above was actually 64-bit 14.04 virtualbox in 64-bit 16.10 host and it is possible that a driver might work in one Ubuntu version, but not another.

---

### Post by phoenix1963 on 2017-04-11
Hi Efflandt - I get ```
device `smfp:usb;04e8;346a;071UBJDF80004PF' is a Samsung M288x Series on USB Scanner

```
 But also a pop-up warning ```
HPLIP cannot detect devices in your network. This may be due to existing firewall settings blocking the required ports like (5353/udp). When you are in a trusted network environment, you may open the ports for network services like mdns and slp in the firewall. For detailed steps follow the link.

 http://hplipopensource.com/node/375
```
Turning the firewall off (I couldn't find the right ports to enable) gives ```
device `smfp:usb;04e8;346a;071UBJDF80004PF' is a Samsung M288x Series on USB Scanner
device `smfp:net;172.16.1.113' is a Samsung M288x Series on 172.16.1.113 Scanner

```
But I don't see how that could give an intermittent error - either it gets through the firewall or it doesn't.

phoenix1963

---

