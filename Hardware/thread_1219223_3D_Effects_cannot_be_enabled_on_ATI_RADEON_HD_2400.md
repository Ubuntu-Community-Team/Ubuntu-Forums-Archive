---
title: "3D Effects cannot be enabled on ATI RADEON HD 2400 PRO"
date: 2009-07-21
forum: Hardware
---

### Post by murshedbd on 2009-07-21
I am using ubuntu 9.04 on ATI RADEON HD 2400 PRO Card. After installing ubunbtu when i tried to enable ati restricted driver from system-hardware (for enabling 3d Effects ie compiz ) I found a blank screen and on above it shows "No Proprietary Drivers are in use on this system".
 
Though when I boot my system by using live CD It show the restricted driver if I use sysytem-Hradware Drivers

Where is the problem ?


I also tried to enabling extra visual effects under Appearance Preference Menu ( screen shoot enclosed) but without success.

And  I use the** lspci -nn | grep VGA** command in terminal mode it shows the following :

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO] [1002:94c3]


Can anyone help me to resolve the problem?

---

### Post by litspliff on 2009-07-21
you have to install the drivers.


the no-effort method i use:
insert your install disc, make sure you have an open connection to the internet....you need a source for the drivers.
run all your updates (System-->Admin-->Updates). let it do the work for you.
once you have the updated kernel, go to system--->Admin-->Hardware Drivers.
as long as you are connected to a legitimate source, it should list the proprietary driver in the list. 
activate it, then restart X, or just a soft reboot.

if not, hit google up with your video card brand.

---

### Post by kmacphail on 2009-07-25
I am having exactly the same problem.  When I attempt to use the proprietary drivers I get a successful message and then am told to reboot.  However whenever the X windows systems starts up I get a black screen.  I have removed the driver and then installed the driver directly from ati's website however this produces the same result.  

This is the effect on the 64 bit system, but on the 32 bit system the proprietary drivers work fine and 3D effects can be enabled.  However the reason I just installed a new system was to upgrade to 64 bit.

---

