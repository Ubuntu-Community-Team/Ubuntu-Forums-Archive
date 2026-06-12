---
title: "Canon Scanners - DR-C125 and DR-C225"
date: 2017-08-02
forum: Hardware
---

### Post by tatonqek on 2017-08-02
Hello everyone,

I have 2 Canon Scanners and two different Ubuntu versions that behave in an unreliable manner.

The first is a Canon DR-C125 running on 14.0405LTS x64. The only driver available through Canon is a i386 driver (installed as a deb using dpkg -i). After installing the driver, SANE fails to initialize it with the following message:

From EXPORT SANE_DEBUG_DLL=255

[dll] load: dlopen() failed (usr/lib/;obsame=canondr.so.1: Wrong ELF Class: ELFClass32

My understanding is that this indicates that Sane is 64bit, and is unable to process the 32 bit driver. I can install sane:i386, but the i:386 versions of scanning programs require libraries are no longer available.

The second issue is pertaining to the Canon DR-C225 on Ubuntu 16.04.2 LTS x64. The driver will install fine, and there is a 64 bit version available. Initiating a scan can take anywhere from 15 seconds to 2 minutes before the scanning starts taking place. Using the debug, there are no error messages, and the delay between the scanning start and the receiving of data from the scanner has no messages, only a blinking cursor (when being viewed live in the terminal. This only seems to affect newer machines with a USB 3.0 controller (the Unit we use is specifically the Intel NUC series), and older units with only USB 2.0 don't seem to have this issue.

I know that's a bit of an info dump, but I was hoping people could at least point me in the right direction for possibly dealing with these issues.

Thanks for the help!

---

