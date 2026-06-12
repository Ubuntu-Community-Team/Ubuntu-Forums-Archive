---
title: "Brother HL-L2395DW Scanner"
date: 2020-05-12
forum: Hardware
---

### Post by steven43 on 2020-05-12
I'm at the end of my rope on this one.

Scanner worked fine in Ubuntu 16.04.

On Ubuntu 20.04 ... nothing.

[FONT=courier new]Error opening device: opening device 'brother4:bus2;dev1': Invalid argument[/FONT]

Scanner is found:

[FONT=courier new]$ scanimage -L
device `brother4:bus2;dev1' is a Brother HL-L2395DW USB scanner
device `escl:[http://127.0.0.1:60000](http://127.0.0.1:60000)' is a ESCL HL-L2395DW series flatbed scanner[/FONT]

[FONT=courier new]$ lsusb 
Bus 003 Device 004: ID 04f9:0429 Brother Industries, Ltd HL-L2395DW series[/FONT]

Printer works.

Like I said, end of my rope.  I've installed everything I know to install.

Any suggestions?

---

### Post by brian_p on 2020-05-12
This is the result of a scanning change in 20.04. It can be fixed. Can you scan with ```
simple-scan escl:http://127.0.0.1:60000
``` Are you still able to print?

---

### Post by steven43 on 2020-05-12
[FONT=courier new]simple-scan escl:[http://127.0.0.1:60000](http://127.0.0.1:60000)[/FONT]

Comes back with:

[FONT=courier new]Unable to connect to scanner[/FONT]

---

### Post by brian_p on 2020-05-12
> **steven43 said:**
> [FONT=courier new]simple-scan escl:[http://127.0.0.1:60000](http://127.0.0.1:60000)[/FONT]

Comes back with:

[FONT=courier new]Unable to connect to scanner[/FONT]

Does ```
scanimage -d "escl:http://127.0.0.1:60000" > image.pnm
``` work?

How about printing?

---

### Post by steven43 on 2020-05-12
I think I got it to work by bypassing the USB.

Figured out how to setup the printer wireless (didn't really know it had that until I saw the WiFi label printed on it).  And now it works over the network.

I did:

[FONT=courier new] brsaneconfig4 -a name=Brother model=HL-L2395DW ip=<<printers ip>>[/FONT]

I don't know if that made any difference or not.

Everything seems to be working now.

Printing was working with the USB connection.  But I've now changed all of that to use the network printing.  I disconnected the USB from the printer.

No clue why all of this worked on Ubuntu 16.04 but decided to stop working in Ubuntu 20.04.

---

### Post by brian_p on 2020-05-12
> **steven43 said:**
> I think I got it to work by bypassing the USB.

Figured out how to setup the printer wireless (didn't really know it had that until I saw the WiFi label printed on it).  And now it works over the network.

That's good initiative and a good solution. A network connection is more flexible than a USB one.

> Printing was working with the USB connection.

Thanks for confirming that.

> No clue why all of this worked on Ubuntu 16.04 but decided to stop working in Ubuntu 20.04.

20.04 starts the ippusbxd daemon automatically. It takes over the USB bus and only allows the escl protocol to be used to scan.. You should have been able to scan with escl:[http://127.0.0.1:60000](http://127.0.0.1:60000).

---

### Post by steven43 on 2020-05-12
escl:[http://127.0.0.1:60000](http://127.0.0.1:60000) would start to scan, the scanning beam would move (sometimes), but it would never produce an image and it errored out... sorry, I didn't keep the exact error.  It was generic "failed to scan" or something like that.

At least that change in 20.04 explains why it wasn't working in 20.04 but was in 16.04.  That's always my issue - I usually need to know a why something's not working.  I had read where a lot of people had solved this problem by going through the network.  I knew the printer had an ethernet port, but I'm a little short on ethernet cables at the moment.  It just did not dawn on me to try WiFi.  But I really wanted to solve the issue with USB.  But knowing that about the ippusbxd daemon at least satisfies that part of my curiosity.
escl:[http://127.0.0.1:60000](http://127.0.0.1:60000).

---

### Post by brian_p on 2020-05-12
> **steven43 said:**
> escl:[http://127.0.0.1:60000](http://127.0.0.1:60000) would start to scan, the scanning beam would move (sometimes), but it would never produce an image and it errored out... sorry, I didn't keep the exact error.  It was generic "failed to scan" or something like that.

"Didn't scan" is a good enough summary. Please would you give what you get for ```
avahi-browse -rt _ipp._tcp
``` ```
avahi-browse -rt _uscan._tcp
```

> 
At least that change in 20.04 explains why it wasn't working in 20.04 but was in 16.04.  That's always my issue - I usually need to know a why something's not working.  I had read where a lot of people had solved this problem by going through the network.  I knew the printer had an ethernet port, but I'm a little short on ethernet cables at the moment.  It just did not dawn on me to try WiFi.  But I really wanted to solve the issue with USB.  But knowing that about the ippusbxd daemon at least satisfies that part of my curiosity.
escl:[http://127.0.0.1:60000](http://127.0.0.1:60000).

ippusbxd is for making scanning and printing immediately available when a device is plugged into a USB bus. Essentially, it is intended to replace the use of vendor drivers. Your printer continued to use the Brother driver, it seems. That's ok. But you can only have one scanner URI on a USB bus and escl gets preference. That is why the Brother scanner driver was shut out.

---

### Post by kurt18947 on 2020-05-12
I had scanning problems with a Brother MFD on a wired network. It worked using Brother's installer script on one machine (IBM ThinkPad T530) but not on a Ryzen Desktop. The Ryzen desktop started working right around the release of 20.04. Your problem with the USB connection reminds me of a problem Brother has had with scanning. The fix was editing a Udev file. The tip off in that case was being able to scan as a privileged user but not as a desktop user. Based on what BrianP is saying that may no longer be the case.

---

