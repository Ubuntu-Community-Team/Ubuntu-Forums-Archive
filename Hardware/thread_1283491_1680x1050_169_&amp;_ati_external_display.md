---
title: "1680x1050 16:9 &amp; ati external display"
date: 2009-10-05
forum: Hardware
---

### Post by ZaaBI_AlonSo on 2009-10-05
Hello,

have a toshiba laptop with ati graphics card hd3650, and i want to connect an external 22' widescreen display.The driver i'm using is fglrx ati non open source drivers, but when i go system->preferences->display the system becomes really slow and the resolution for the external is 1680x1050 16:10, when i want 16:9 aspect ratio not 16:10.


please give me some help

the result of the lspci -nn |grep VGA is 
> 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3650 [1002:9591]



---

### Post by markbuntu on 2009-10-05
You need to use the Catalyst Control Center with the ati proprietary driver. You will find it in your menus.

---

### Post by ZaaBI_AlonSo on 2009-10-06
> **markbuntu said:**
> You need to use the Catalyst Control Center with the ati proprietary driver. You will find it in your menus.


there the only resolution i can get is 1280x800 which is my laptops

---

### Post by markbuntu on 2009-10-06
Are you using the latest driver from ati?

---

### Post by iladw on 2009-10-06
Hello ZaaBI_AlonSo

Use the buil-in drivers updater from:
   System -> Administration -> Hardware Drivers

Enable the proprietary driver for your graphics cards, just like i have (check attachment). I'd probably have to restart.

After that go to System -> Administration and look for the configuration tool (mine is called NVIDIA X Server Settings). There you should find more options and configs than preferences -> display.

---

### Post by ZaaBI_AlonSo on 2009-10-09
> **markbuntu said:**
> Are you using the latest driver from ati?

yeap i'm using the latest drivers

---

### Post by ZaaBI_AlonSo on 2009-10-09
> **iladw said:**
> Hello ZaaBI_AlonSo

Use the buil-in drivers updater from:
   System -> Administration -> Hardware Drivers

Enable the proprietary driver for your graphics cards, just like i have (check attachment). I'd probably have to restart.

After that go to System -> Administration and look for the configuration tool (mine is called NVIDIA X Server Settings). There you should find more options and configs than preferences -> display.


yeap

i have ati catalyst control center but still can't do anything from there

---

### Post by markbuntu on 2009-10-09
If you are having trouble getting the Catalyst Control Center (Superuser) to open then you can type in a terminal

sudo amdcccle

and it should open after you type in your pasword. Then you can make changes, be careful through and only make one change at a time.

---

### Post by ZaaBI_AlonSo on 2009-10-10
> **markbuntu said:**
> If you are having trouble getting the Catalyst Control Center (Superuser) to open then you can type in a terminal

sudo amdcccle

and it should open after you type in your pasword. Then you can make changes, be careful through and only make one change at a time.


still can't enable xinerama from there....

---

