---
title: "Ubuntu 10.10 Netbook nVidia drivers"
date: 2011-01-11
forum: Hardware
---

### Post by Slotkenov on 2011-01-11
Hi all,

I was interested in trying out Ubuntu Netbook 10.10 on my laptop, in stead of Windows 7 I've used all this time. Downloaded, burned and then installed it. All worked fine.
On first boot, after a minute or so, it told me there were drivers available for my graphics card; nVidia drivers. It gave me two options:
- version xxx (I don't know which number that was anymore)
- latest version [Recommended]

So I chose the recommended drivers. I reboted my computer, and then, it booted directly into the terminal. When I enter the command startx it told me it couldn't detect any devices.

After a fresh install of Ubuntu I also tried to download the nVidia drivers myself from the nVidia site and installe them. But that resulted in the same problem.

Anybody any idea what I could do about this?

I have a Sony Vaio VGN-Z51XG with an nVidia GeForce 9300M GS.

Thanx in advance!

---

### Post by Slotkenov on 2011-01-12
Here is a more detailed version of what happend:

I do a fresh install of Ubuntu. When it tells me the installation is finished and I click "Restart". After a few seconds I see a terminal which tells me how it's shutting down. And then, the installation cd pops out and the screen fills up with the following error message:

```
[ 4056,691372] end_request: I/O error, dev sr0, sector 569444
```

With the second and last number changing per line.
Then, nothing.
I press enter, and it continues rebooting. Then Ubuntu launches and I can log in.

A minute after being loged in it tells me there are restricted drivers available. I click on it and it opens an "Additional Drivers" window which shows me the following two drivers:

```
NVIDIA accelerated graphics driver (version 173)
NVIDIA accelerated graphics driver (version current) [Recommended]
```

Both are not activated. I chose the recommended driver (have tried the other before too). I need to enter my password and then it's downloading and installing the driver. I need to restart the computer to activate the driver, so I restart. And I end up in the terminal.

I log in in the terminal. Enter the command: ```
startx
```
Among other output this is what I see:

```
(==) Log file: "/var/log/Xorg.0.log", Time: ...
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) No devices detected.

Fatal server error:
no screens found
```

Any ideas what I can do?

---

### Post by Slotkenov on 2011-01-13
Nobody who knows a solution to this problem?

Thats so disappointing. I was very optimistic about ubuntu and the laptop version. But now I don't seem to be able to install it properly. I can use it without installing any video drivers, but thats not realy using it as you should be able to.

Then just back to Windows 7 unfortunately, I guess.

---

