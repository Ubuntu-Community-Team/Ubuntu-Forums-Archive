---
title: "Unknown model for ALC662"
date: 2008-04-01
forum: Hardware &amp; Laptops
---

### Post by dbworker on 2008-04-01
Ubuntu Server 7.10
Mother Board: GA-G33M
Northbridge G33 Southbridge ICH9
Realtec ALC662 Codec HD Audio integrated

First install of Ubuntu ...
On boot I get the following message
kernel: hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...

I did a search and a few old messages made reference to this codec and how one should get the latest drivers.

Newbie question: Where does one best get these drivers? How does one install these drivers?
I found a site:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=24&Level=4&Conn=3&DownTypeID=3](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=24&Level=4&Conn=3&DownTypeID=3)
These are the Linux drivers, do they work for Ubuntu Server?
How can one check which (if any) drivers and versions are installed?

Thank you in advance

---

### Post by efittery on 2008-04-12
I downloaded the linux package and ran the install script.

It was a bad idea and required a lot of work to recover.

Anyhow, this was the problem:

1.  The script removed files and directories.
2.  The script then tried to install files..... so far so good, but it tried to install files and directories in directories that did not exist.
3.  The script aborted.

This left me without some files and directories.  When I tried to boot ubuntu, it would never let me log in.

I had to boot the machine and let it get to the point where I could press the ESC key when I saw GRUB was about to start.  This dropped me into BIOS where I switch my primary boot device to be the CD.  Then I rebooted the machine so it started UBUNTU from CD.

Then I just installed UBUNTU again.

I am a newbi and this was the only way I knew to fix the problems I incured by loading the install script from for my ALS662 from [http://www.realtek.com.tw/downloads/...3&DownTypeID=3:lolflag:](http://www.realtek.com.tw/downloads/...3&DownTypeID=3:lolflag:)

---

