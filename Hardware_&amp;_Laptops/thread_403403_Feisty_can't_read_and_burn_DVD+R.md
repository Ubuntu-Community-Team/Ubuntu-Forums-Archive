---
title: "Feisty can't read and burn DVD+R"
date: 2007-04-07
forum: Hardware &amp; Laptops
---

### Post by Vstar on 2007-04-07
My laptop&#65306;Acer TM4652Lmi
DVD recorder&#65306;TSSTcorp CD/DVDW TS-L632B
OS&#65306;Feisty
kernel:Linux generic 2.6.20-12~2.6.20-14
I can't connect to [https://answers.launchpad.net/ubuntu,so](https://answers.launchpad.net/ubuntu,so) I publish it here.

When I insert blank DVD+R disk ,system can't identify it ,and the dist can't be ejected for a long time.The following is my test report.

type&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;identify&#12288;&#12288;read&#12288;&#12288;burn
DVD+R(not blank)&#12288;&#12288;yes&#12288;&#12288;&#12288;&#12288;yes&#12288;&#12288;&#12288;-
DVD+R(blank)&#12288;&#12288;&#12288;&#12288;no&#12288;&#12288;&#12288;&#12288;no&#12288;&#12288;&#12288;no
DVD-R(not blank)&#12288;&#12288;yes &#12288;&#12288;&#12288;&#12288;yes &#12288;&#12288;&#12288;-
DVD-R(blank)&#12288;&#12288;&#12288;&#12288;yes&#12288;&#12288;&#12288;&#12288;yes&#12288;&#12288;&#12288;yes
DVD+RW(not blank)&#12288;yes&#12288;&#12288;&#12288;&#12288;yes&#12288;&#12288;&#12288;no(can't be formated)
DVD+RW(blank)&#12288;&#12288;&#12288;not test
DVD-RW&#12288;&#12288;&#12288;&#12288;&#12288;&#12288;yes&#12288;&#12288;&#12288;&#12288;yes&#12288;&#12288;&#12288;yes

There is no problem to burn DVD+R under edgy or windows.

---

### Post by Vstar on 2007-05-27
I noticed the dvdplusr and dvdplusrw is disabled through hal-device-manager.

  info.capabilities = { 'storage', 'block', 'storage.cdrom' } (string list)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.support_multisession = false  (bool)
  storage.cdrom.hddvdr = false  (bool)
  storage.cdrom.mrw_w = true  (bool)
  storage.drive_type = 'cdrom'  (string)
  storage.cdrom.mrw = true  (bool)
  storage.cdrom.read_speed = 4234  (0x108a)  (int)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.mo = false  (bool)
[COLOR="Red"]  storage.cdrom.dvdplusr = false  (bool)[/COLOR]
  storage.cdrom.write_speed = 4234  (0x108a)  (int)
  storage.cdrom.cdr = true  (bool)
  linux.fstab.mountpoint = '/media/cdrom0'  (string)
  storage.cdrom.bdr = false  (bool)
  storage.cdrom.dvdram = true  (bool)
[COLOR="Red"]  storage.cdrom.dvdplusrwdl = false  (bool)[/COLOR]
  storage.cdrom.write_speeds = { '4234', '2822', '1411', '706' } (string list)
  storage.cdrom.dvdr = true  (bool)
[COLOR="Red"]  storage.cdrom.dvdplusrdl = false  (bool)[/COLOR]
  storage.cdrom.bd = false  (bool)
  storage.cdrom.hddvdrw = false  (bool)
  storage.cdrom.cdrw = true  (bool)
[COLOR="Red"]  storage.cdrom.dvdplusrw = false  (bool)[/COLOR]
  storage.cdrom.dvdrw = true  (bool)
  storage.cdrom.hddvd = false  (bool)
  scsi.type = 'cdrom'  (string)

It goes well before feisty.

---

### Post by tawk on 2007-06-16
I have exactly the same problem. Same drive, same behaviour. See the syslog in the attachment for errors after inserting an empty DVD+R.

EDIT:
With the previous kernel-version 2.6.20-16.28 the problems are solved! I just downloaded and installed it:
[linux-image-2.6.20-16.28-generic]("https://bugs.launchpad.net/ubuntu/feisty/i386/linux-image-2.6.20-16-generic/2.6.20-16.28")
[linux-restricted-modules-2.6.20-16.28-generic]("https://bugs.launchpad.net/ubuntu/feisty/i386/linux-restricted-modules-2.6.20-16-generic/2.6.20.5-16.28")

---

### Post by ubuntujonez on 2007-07-03
same here. This is like the 3rd or 4th major thing i can't do in Feisty that worked fine in Efty. I guess we have to install k3b.

---

### Post by ubuntujonez on 2007-07-03
> **ubuntujonez said:**
> This is like the 3rd or 4th major thing i can't do in Feisty that worked fine in Efty.

Actually, I stand corrected. It seems that I was slightly over the limit of a single layer DVD and when I put one less file at the DVD creator, it is no longer asking for a dual layer disc (which my drive is not capable of writing). If you don't hear back it worked! (This is putting in a blank dvd in and just dragging and dropping files onto the "Blank DVD +R Disc" icon that shows up on the desktop.)

Sounds like I had a different problem than you guys are having :(  

Good luck!
-jonez

---

