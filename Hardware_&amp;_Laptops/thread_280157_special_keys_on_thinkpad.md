---
title: "special keys on thinkpad?"
date: 2006-10-19
forum: Hardware &amp; Laptops
---

### Post by crash0 on 2006-10-19
hello.

i have an ibm thinkpad r40e. it's a bit old, 2.5 years now i guess. anyway, i'm using ubuntu for half a year now and i still haven't found a way to make the ibm special keys work. i just need the volume up/down keys.

i searched doc.gwos.org and ubuntuforums and google and found 3 or 4 ways to do this, but none of them worked, either on breezy nor dapper. i don't know, perhaps i did something wrong (i'm an intermediate newbie).

thank you in advance ;)

---

### Post by crash0 on 2006-10-19
update:

i tried tpb *again*... i successfully added my username to nvram and tried to configure the tpbrc. however, nothing works - the access ibm button doesn't do what i configured it to do and the volume buttons aren't working either. the only life sign of tpb i have is that when resume my screen (after it dims when the laptop is not used for a few minutes), tpb displays a brightness bar. but that's it. i can't change the brightness myself.

---

### Post by justplayin on 2006-11-06
Well under Dapper and Edgy I got some special keys of my r40e, type 2684-54G, bios version 1SET79WW [1.38]("http://www-307.ibm.com/pc/support/site.wss/license.do?filename=mobiles/1suj27us.exe") from 2005/11/28 to work by turning off acpi. But then you loose other functions, like display of the battery state. And my laptop won't power off completely after switching off acpi. I have to pull the power chord and take out the battery.
Switching to apm instead of acpi won't help because if I boot with ```
acpi=off apm=on
``` as boot parameters and do a```
sudo apm --suspend
``` it says "No APM support in kernel". Now I don't know if enabling APM support in the kernel would solve this issue.

Anyway, to get the special keys to work just do a```
sudo gedit /boot/grub/menu.lst
``` and change
```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-386
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=5937da97-4780-4d51-a3ec-dbeb40225eaf ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot
```
too look like this:
```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-386
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=5937da97-4780-4d51-a3ec-dbeb40225eaf ro quiet splash acpi=off
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot
```

Now we switched acpi off and the special keys get recognized.
But still "suspend to ram" doesn't work on my r40e, as stated in the bug report  [here.]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/68734") Probably because with acpi=off there is no power management at all left.

Maybe you can add your experiences to the bug report or confirm it.

---

