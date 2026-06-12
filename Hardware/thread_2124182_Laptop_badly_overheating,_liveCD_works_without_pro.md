---
title: "Laptop badly overheating, liveCD works without problems"
date: 2013-03-10
forum: Hardware
---

### Post by rounder8 on 2013-03-10
Hi,

I just installed Ubuntu 12.10 (64bit) on my laptop (Lenovo W500). Computer keeps rebooting itself randomly and sometimes even before system has fully started. I get critical temperature warnings sometimes. These errors only happen when running installed copy of Ubuntu 12.10, not when using the ubuntu from usb stick or when using Windows 7.

I tried stress testing when booting from Ubuntu LiveCD. I ran two instances of burnP6 (cpuburn) simultaneously and the computer stayed stable. I monitored the temperature with psensor and core temperatures were about 80c.

What might be causing these (temperature?) problems only when running Ubuntu from hard drive?

---

### Post by rounder8 on 2013-03-10
I tried running two instances of burnP6 on Ubuntu that was installed on hard disk. Temperatures reached around 96c and then Ubuntu shut down itself. Looks like this is overheating problem. Why does this only happen when running Ubuntu from hard disk?

/usr/lib/evolution/evolution-calendar-factory keeps on crashing right after startup by itself. This is a fresh installation, I only installed cpuburn, ma-sensors and psensor.

---

### Post by black veils on 2013-03-10
open the terminal and paste this
```
sudo lshw
```
type your password, nothing will show, then press the Enter key.

when the results appear, highlight all, then copy-paste to [[COLOR=#0000cd]ubuntu pastebin[/COLOR]]("http://paste.ubuntu.com/"), you can post the resulting link to this thread.

---

### Post by rounder8 on 2013-03-10
> **black veils said:**
> open the terminal and paste this
```
sudo lshw
```
type your password, nothing will show, then press the Enter key.

when the results appear, highlight all, then copy-paste to [[COLOR=#0000cd]ubuntu pastebin[/COLOR]]("http://paste.ubuntu.com/"), you can post the resulting link to this thread.

Here is the output from "sudo lshw":

[http://paste.ubuntu.com/5602371/](http://paste.ubuntu.com/5602371/)

I have switchable graphics (integrated Intel and ATI Radeon) on this computer. I did disable the switchable mode from BIOS and now it's ATI Radeon always. This might have solved the issue as computer has stayed on all day (idling) without rebooting once. I will investigate whether some cpu/gpu load will crash the OS.

---

