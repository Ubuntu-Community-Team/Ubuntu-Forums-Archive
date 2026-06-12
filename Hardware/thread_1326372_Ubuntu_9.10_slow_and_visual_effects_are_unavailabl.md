---
title: "Ubuntu 9.10 slow and visual effects are unavailable"
date: 2009-11-14
forum: Hardware
---

### Post by bblinn on 2009-11-14
Background:

My notebook computer by Jetbook previously was a dual-boot system with Win XP and Ubuntu 9.04. I installed Win 7 and everything was fine -- both Ubuntu and Win 7 performed fine. Then I upgraded Ubuntu to 9.10. This version reminds me of Vista.

I like the visual effects, but I cannot enable either "normal" or "extra". The system tries to enable them and then provides the enormously "useful" message, "Desktop effects could not be enabled."

The advanced effects worked fine in 9.04 and Win 7 Aero has no problems, so it's not the hardware. I'm guessing that I need drivers. Under 9.04, this wasn't a problem, but I don't see how to obtain them in 9.10.

In addition, 9.10 is horrifically slow opening applications and switching from one application to another. Firefox is so slow under this version that it's unusable.

Hardware:

Intel Core Duo 2.26GHz
3GB RAM
Graphics - Intel Mobile 4 Series Chipset (subsystem Compal)

Request:

I'm not entirely new to Ubuntu (this is the 3rd or 4th version I've used in a dual-boot scenario), but I'm not as familiar as I need to be to solve whatever problems exist.

I'll be grateful for any recommendations.

---

### Post by opolette on 2009-11-15
Hi,

I definitely agree with you.
Ubuntu 9.10 is the vista of Linux : slow, buggy,... 
What a mess, I want to downgrade!

---

### Post by xieu90 on 2009-11-15
hi
I havent tried ubuntu 9.10 yet, because i am waiting for mint 8
but it might be something happened when you download the iso file or when you burned the cd.
try to download another one and burn another cd.
it is the best if you get the original cd from canonical (i cant get any more >.< )

---

### Post by HuaiDan on 2009-11-15
Got to a terminal and type 
uname -r


It will return your running kernel number. Make sure this kernel version is what is showing in the menu.lst . All should be 2.6.31-14-generic as of this date. If not, run

sudo update-grub

and find out which kernels you have installed. Edit your menu.lst to reflect the return data from the grub update.


Next, if you're using an NVidia card (don't know what to tell you if you're not), go to system/administration/hardware drivers and remove the linux nvidia driver. Then go to the NVidia site and download the latest linux driver for your card. Put it in the root directory.

To install the NVidia driver, you must stop the display manager. Go to a terminal and type

sudo /etc/init.d/gdm stop

You'll need to hit alt-f4 if you can do anything from there. Enter you login information. cd .. down to the root directory, and type

sudo sh (name of the nvidia package)

(**hint type "sudo sh n" then hit the tab key. The package name should autofill there.)

Yes/Yes/OK/ all the way through the setup program. If it asks you to rebuild the kernel or warns you there's an old driver installed, have it rebuild the kernel/remove the driver and continue.

When that finishes, you need to


sudo /etc/init.d/gdm start

If all goes well, you can go to system/preferences/appearance and enable effects.

---

### Post by Yellow Pasque on 2009-11-15
> The system tries to enable them and then provides the enormously "useful" message, "Desktop effects could not be enabled."


Start compiz from the terminal to get a more specific error message. Another useful command to check your direct rendering:
```
LIBGL_DEBUG=verbose glxinfo
```

---

