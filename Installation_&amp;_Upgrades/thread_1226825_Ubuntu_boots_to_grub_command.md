---
title: "Ubuntu boots to grub command"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by bcosmann on 2009-07-30
Hello,

I just recently installed Ubuntu 9.0.4 desktop on my Intel Macbook Pro which is dual booting mac osx and ubuntu with rEFIt. Everything was working fine until I restarted after installing some desktop customization programs such as avant and screenlets. I also modified appletouch.fdi using

sudo gedit /etc/hal/fdi/policy/appletouch.fdi

then pasting the following information

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
   <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
   <merge key="input.x11_options.TapButton1" type="string">1</merge>
   <merge key="input.x11_options.TapButton2" type="string">3</merge>
   <merge key="input.x11_options.TapButton3" type="string">2</merge>
   <merge key="input.x11_options.FingerLow" type="string">10</merge>
   <merge key="input.x11_options.FingerHigh" type="string">20</merge>
   <merge key="input.x11_options.PressureMotionMinZ" type="string">10</merge>
   <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
   <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
   <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
  </match>
 </device>
</deviceinfo>

After rebooting and selecting linux from rEFIt it goes to loading grub stage 2 then leaves me at a grub> command prompt.

Any help with the would be greatly appreciated.

Thanks!

---

### Post by dstew on 2009-07-30
At the grub> prompt enter```
find /boot/grub/menu.lst
```If it returns a value, like (hd0,1), enter that as the partition in the command```
configfile (hd0,1)/boot/grub/menu.lst
```That should get you a menu, if you have one.

Another thing to try is to boot Ubuntu using the command line. Use the result of the **find** command above as the argument to the **root** command as below, and use the **kernel** and **initrd** commands to set up Ubuntu to boot. You can use the tab-complete feature of grub to show what kernels are available, and then re-enter the command to pick the one you want.```
root (hd0,1)
kernel <tab>
initrd <tab>
boot
```If this doesn't work, the behavior of the commands should give us a clue as to what is going wrong.

---

### Post by bcosmann on 2009-07-31
> **dstew said:**
> At the grub> prompt enter```
find /boot/grub/menu.lst
```If it returns a value, like (hd0,1), enter that as the partition in the command```
configfile (hd0,1)/boot/grub/menu.lst
```That should get you a menu, if you have one.

Another thing to try is to boot Ubuntu using the command line. Use the result of the **find** command above as the argument to the **root** command as below, and use the **kernel** and **initrd** commands to set up Ubuntu to boot. You can use the tab-complete feature of grub to show what kernels are available, and then re-enter the command to pick the one you want.```
root (hd0,1)
kernel <tab>
initrd <tab>
boot
```If this doesn't work, the behavior of the commands should give us a clue as to what is going wrong.
Ok so I tried that and got the error file not found. I did some more research and it looks like my mac osx install mounted the linux partition probably because I originally partitioned it in mac osx so deleted the partition and created a new one with the ubuntu partition manager and reinstalled. All seems well...so far....

---

