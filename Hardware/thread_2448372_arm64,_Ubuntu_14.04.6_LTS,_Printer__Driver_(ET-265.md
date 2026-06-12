---
title: "arm64, Ubuntu 14.04.6 LTS, Printer / Driver (ET-2650 not working)"
date: 2020-08-06
forum: Hardware
---

### Post by riverdingo on 2020-08-06
Hello.
I am extremely unfamiliar with Ubuntu / Linux.
On the other hand I am a seasoned Win32 C++ programmer so am not ignorant of the basics.

I am tired of 'supporting' my Wife's HP all-in-one Windows 10 machine and need to replace it.
Suffice it to say all She needs is something to:
-- Play solitaire.
-- Access things via a browser (email, YouTube, shopping!)
-- Listen to audio.
-- Print something every one in a while.


I have a small arm64 machine with Ubuntu 14.04.6 LTS installed.
It does everything She needs except printing.


She has an Epson ET-2650.
I would prefer to utilize the printer via wireless connection.
It seems Epson only supplies a driver package for arm32 (Crap!)

1.)
From my limited reading I am not sure if it is possible to make the Epson arm32
package run on an arm64 machine. If it is not a huge dance does anyone have any pointers?

2.) Is there some sort of generic print driver (via a USB connection) that will work
with the ET-2650?

3.)
I would be more than happy to ditch the 2650 and replace it with a different
ink jet printer (Tank style. not cartridge style) 
3.1) Anyone aware of a tankless ink jet printer and driver combination 
that I can utilize with via a wireless IP connection?
3.2) Anyone aware of a tankless ink jet printer and driver combination 
that I can utilize with via a USB connection?

Thanks.

---

### Post by Skaperen on 2020-08-06
this is where process or system level emulation might help.  if every component of the driver package runs in user space (e.g. not in the kernel) you can run it under process emulation which *qemu* can do.  system emulation involves running a virtual machine (e.g. a kernel and all the processes under it).  basically this lets you run the amd_64 or i386 versions.

i don't know if arm32 can run directly on arm64 but it might be worth checking out.  otherwise emulation is a choice if emulation targets include arm32.  maybe arm32 emulation can run faster under arm64.

---

### Post by CatKiller on 2020-08-06
> **riverdingo said:**
> I have a small arm64 machine with Ubuntu 14.04.6 LTS installed.

14.04 is End-of-Life. LTS releases get 5 years of support. You should upgrade to something that's supported.

On the plus side, doing that might also sort out your printer issue: I understand that work has been ongoing to use AirPrint, which makes actual printer drivers less relevant than they used to be.

---

