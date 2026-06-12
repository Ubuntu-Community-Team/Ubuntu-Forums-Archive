---
title: "Laptop Thunderbolt USB C support"
date: 2019-11-03
forum: Hardware
---

### Post by John_Kirk on 2019-11-03
Hi Guys.

I just bought this Laptop and installed a fresh Ubuntu 19.10 after a bios tweak [https://www.amazon.co.uk/gp/product/B0764HSC5K/ref=ppx_yo_dt_b_asin_title_o01_s00?ie=UTF8&psc=1](https://www.amazon.co.uk/gp/product/B0764HSC5K/ref=ppx_yo_dt_b_asin_title_o01_s00?ie=UTF8&psc=1) 

Everything seems to be epic :) Ubuntu running great. Laptop itself a beautiful thing. 
Could have had more rom with a plastic case or this USB C equipped aluminium machine with less rom.. Its Soooooooo nearly perfect.

Until I tried to charge from USB C instead of the barrel charger provided. = Laptop not charging with USB C

I'm not sure if the laptop has USB C charge hardware anyway as I wiped windows off without booting it. And I have no manual for the laptop.

I do note that in Ubuntu's settings:-

"No Thunderbolt Support - Thunderbolt security level could not be determined"

I have read that this can be a Bios issue but I have found no advice relevant to my machine online.

Please help... What can I try ?

Thanks.

---

### Post by John_Kirk on 2019-11-03
Ok.... in trying to find a option in the bios to enable Thunderbolt access I stumbled opon a selection under 'chipset' which was set to 'windows' .. I saw the option 'linux' so I thought it made good sense to select it, save and reboot.

I can't get back into the bios now using the del button or any other.. The manufacturers logo does not appear at boot any more (which was the point at which I selected the del/bios button)

Ubuntu still working... just cant get into bios to make changes that might be needed ????

---

### Post by John_Kirk on 2019-11-03
BIOS Vendor       : American Megatrends Inc.
BIOS Version      : XW-BI-14-S133AR120-AA54M-043-B
BIOS Release Date : 10/30/2017
Board Name        : NC14V1008 

Found that info out above... hope it helps .. 

Tried many combinations to get back into the Bios at boot.. always progresses to load Ubuntu.

---

### Post by John_Kirk on 2019-11-04
right... I noticed that my screen brightness slider appears to have reversed its operation ...

So, what are the chances of my wrong selection in the bios reversing brightness at bios boot ?
So, maybe I am accessing the Bios, I just can't see it ??
I can certainly stop the boot ubuntu process by pressing del ... I had assumed I had paused the code.. Maybe im in the bios and I just cant see it ?

Ideas ??

---

### Post by oldfred on 2019-11-04
Cold boot to get into UEFI or BIOS, remove battery or fwsetup
[http://askubuntu.com/questions/652966/unable-to-access-bios-menu-after-installing-windows-8/653006#653006](http://askubuntu.com/questions/652966/unable-to-access-bios-menu-after-installing-windows-8/653006#653006) & 
[https://askubuntu.com/questions/652966/unable-to-access-bios-menu-after-installing-windows-8]("http://askubuntu.com/questions/652966/unable-to-access-bios-menu-after-installing-wi")

Cold boot is to turn off all power, not warm reboot.
Unplug from power. If laptop also remove battery. Hold power switch when off or 10 sec or so to drain all power. Then boot and immediately press correct key to get into UEFI/BIOS.
That is controlled by fast boot setting in UEFI, which is separate or different from fast start up in Windows. But both settings are to make Windows boot faster as it is so slow.  Fast boot in UEFI assumes no system changes, so UEFI does not rescan system for what hardware you have. Then it starts boot so quick, you normally do not have time to press any key before boot starts.

Escape key should take you to grub menu, if you do not normally get it. 
Last entry in grub menu should take you back into UEFI.

And from within Ubuntu you can reboot into UEFI.

Reboot into UEFI:
sudo systemctl reboot --firmware
or
sudo systemctl reboot --firmware-setup

---

### Post by John_Kirk on 2019-11-04
Many thanks :) ... I will try the above suggestions.

I have a fanless laptop.. I have seen a video of people taking the back off (a set of screws) ... but the battery maybe looks a bit integrated. Would this type of laptop have a separate bios battery ?

---

### Post by oldfred on 2019-11-04
Some systems with battery built in like that have a tiny hole in back for reset.
It may have motherboard battery or not, no idea.
Hopefully the other ways to get into UEFI/BIOS work.


Have you updated UEFI/BIOS from vendor for your model.
Many systems need UEFI updates.

---

### Post by John_Kirk on 2019-11-07
Had a couple of things happen this week setting back my progression with the fix. RTC with airbags deployed.
Have not forgot the thread.

---

### Post by John_Kirk on 2019-11-15
Hi Guys.. Got my Bios sorted. :) 

Unscrewed the back and disconnected the battery.. scary times ! :) 

So... here is a photo I took of the bios and the setting I changed to 'Intel Linux' ... By changing this I could not get into the Bios and my screen brightness slider reversed polarity.. ??
Anyway... back to normal now with the Windows setting.

Now... Hopefully I can try some things in the Bios with guidance to see if USB charging is possible on this laptop ?
With thanks. 

[IMG]https://ibb.co/84gZVn9[/IMG]
[IMG]https://ibb.co/84gZVn9[/IMG]https://ibb.co/84gZVn9

---

### Post by John_Kirk on 2019-11-15
Hi Guys.. Got my Bios sorted. :) 

Unscrewed the back and disconnected the battery.. scary times ! :) 

So... here is a photo I took of the bios and the setting I changed to 'Intel Linux' ... By changing this I could not get into the Bios and my screen brightness slider reversed polarity.. ??
Anyway... back to normal now with the Windows setting.

Now... Hopefully I can try some things in the Bios with guidance to see if USB charging is possible on this laptop ?
With thanks. 
[can't get pics to display in thread so here is a link to bios pic]

[IMG]https://ibb.co/84gZVn9[/IMG]
[IMG]https://ibb.co/84gZVn9[/IMG]https://ibb.co/84gZVn9

---

### Post by oldfred on 2019-11-15
Windows is typically UEFI Secure Boot. My UEFI has Windows or "Other". 
And Other is suggested if you are using Windows 7 as it does not support UEFI Secure Boot.
Then with my "Other" setting I can have UEFI (without Secure Boot) or CSM/BIOS boot options. But Secure boot is still another setting.
You may have multiple settings combined into one?

I might try your Windows 7 setting, or possibly others?

---

### Post by John_Kirk on 2019-11-16
Many thanks... By selecting the default Bios .. the 'windows chipset' option Ubuntu is working and I can access the Bios again.

Any way for me to check if my laptop supports Thunderbolt USB charging in the Bios ? ... what do I look for ?

---

### Post by oldfred on 2019-11-16
I do not know thunderbolt & its issues.
It looks like it is both vendor & Linux/Ubuntu. 
Mainstream vendors are making improvements to work. 
And Linux kernel is getting updates, but those will not be in standard distributions for a while. Unless you want to install a new kernel, but may need drivers also.

[https://www.phoronix.com/scan.php?page=news_item&px=Thunderbolt-3-SCM-Linux-5.5](https://www.phoronix.com/scan.php?page=news_item&px=Thunderbolt-3-SCM-Linux-5.5)

---

### Post by John_Kirk on 2019-11-20
Arrr. thanks.. Its in the works then. :) 

I have settings/devices/Thunderbolt section within Ubuntu. Guess its in anticipation. :)

With thanks
John

---

