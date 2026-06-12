---
title: "Which (x)Ubuntu image to choose?"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by Snam on 2008-12-12
Hello,

I want to create a Persistent (K)Ubuntu Live Usb Pendrive. So I follow the instructions on [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

One of the steps is downloading an Ubuntu image.
On [http://ftp.hostrino.com/pub/ubuntu/cdimage/intrepid/](http://ftp.hostrino.com/pub/ubuntu/cdimage/intrepid/) several images are available for download:

[LIST]
[*]PC (Intel x86) desktop CD
For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows, as well as newer Apple Macintosh systems based on Intel processors. Choose this if you are at all unsure.
[*]64-bit PC (AMD64) desktop CD
Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core 2). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the Intel x86 images instead. 
[*]Low-Power Intel Architecture MID USB image
For devices using the Low-Power Intel Architecture, including the A1xx and Atom processors.
[/LIST]

I find this a bit confusing.

I'v got an Intel Core 2 Duo - processor SU9400 (1,40 GHz, 800 MHz, 3 MB) [Centrino 2].

So I've got a 64-bit processor, but it's not AMD. It is an Intel processor that, according to [http://ark.intel.com/cpu.aspx?groupId=36697](http://ark.intel.com/cpu.aspx?groupId=36697) is 1.050V-1.150V (which sounds like low-power to me), but is not an A1xx or Atom.

Which image should I choose?
[LIST]
[*]The 64-bit PC (AMD64) desktop CD image, because my processor is 64-bit?
[*]The PC (Intel x86) desktop CD image, because I have an Intel processor?
[*]The Low-Power Intel Architecture MID USB image? Because my processor is 1.050V-1.150V and this image gives me the longest battery life?
[/LIST]

I've got an [Samsung X360 AA02-NL notebook]("http://www.samsung.com/nl/consumer/detail/spec.do?group=computersperipherals&type=notebook&subtype=xseries&model_cd=NP-X360-AA02NL&fullspec=F"). So I want Ubuntu to be as energy efficient as possible. Therefore the Low-Power Intel Architecture MID USB image sounds most appealing to me.

Which image is the best choice for me? And why?

Thnx,

Snam

---

### Post by meindian523 on 2008-12-12
amd64 is just a name,AMD processors are also clones of the x86 architecture,it's only used to signify 64 bit.It is also sometimes called Intel x86_64 architecture.So any of the amd64 or Intel x86 images will do for you.Are you sure that 1.050-1.150 V IS a low power?Best thing,IMO,would be to go for the x86/x86_64 architecture image.Later you can tweak the resultant install to get power savings.

---

### Post by Bear Knuckle on 2008-12-12
The pros and cons of a 64 Bit linux are described here: [64 Bit discussion at ubuntuforums.org]("http://ubuntuforums.org/showthread.php?t=765428").

They are not completely interchangeable and there are significant differences you should take into consideration.

I can't tell anything about the low power version.

---

### Post by zvacet on 2008-12-12
Download 32bit version. PC (Intel x86) desktop CD

---

