---
title: "Disable AMD CPU performance boost"
date: 2014-03-03
forum: Hardware
---

### Post by 3djake on 2014-03-03
Hi folks,

I want to disable AMD CPU performance boost, as it is causes my Windows system to be unstable and overheat.

But turning it off seems to cause problems for ubuntu 13.10, Ubuntu just freezes as soon as it reaches the desktop.

I have a GA-970A-D3 mobo and a FX-4100 CPU, is there something I need to do to prepare ubuntu for the change of settings in the bios?
Disabling the setting just brings the CPU back to stock settings.

Thanks
Regards, Jake

---

### Post by Yellow Pasque on 2014-03-03
1. Make sure your BIOS is up to date
2. Try installing amd64-microcode package if it's not installed already.

---

### Post by 3djake on 2014-03-05
Thanks, installing the amd64-microcode package seems to fix the problem.

---

