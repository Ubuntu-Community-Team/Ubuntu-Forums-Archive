---
title: "&quot;kill switch&quot; on wireless device"
date: 2005-10-02
forum: Hardware &amp; Laptops
---

### Post by jamesabruce on 2005-10-02
Ive experiemented afew times with linux but never really found it suitable. Ive now decided the time is right to put Ubuntu on my acer tablet pc. Im planning to work on the whole wacom tablet thing later, but its not urgent and i dont use it that much. For now, my most urgent thing is a working stable system capable of accessing the internet through my linysys router at home, via the wireless interface. this is essential, since the ethernet port is broken and only works if i jam in the cable and hold it up, which obviously makes it prtty unuseable.

so, heres the deal, apart from this problem, everything else is working correctly. sound, x, plug in usb stuff. problem is, wireless.

during install, it tells me that;

"eth0 appears to have a kill switch disabling it currently" (or along those lines). "it is suggested you enable the device before continuing".

now, im pretty sure my acer c110 has no kill switch, i mean ive had it for 2 years now you know, i think i wouldve found it. so i just ignored this and continued as normal. however, even with no WEP encryption it fials to find the network being broadcast, and even if i tell it the EESID it cant get a lock. seems to me like it isnt even trying to be honest. 

i do have a wireless button on the top row, but that only work in windows when you have the special buttons drivers installed, and all it does it switch between bluetooth, wireless, both, or both off. plus, i dont think its this because the light is on for wireless, off for bluetooth, like one would hope it to indicated. plus, pressing it does nothing during install of or once running ubuntu. that doesnt bother me, as long as i can keep it ON all the time thats fine. 

in the bios, i have a setting similar that allows me to control at startup which device is enabled by default, so ofcourse ive set that to wireless only. 

help! please! is there some archaic device setting for wireless that i can only access through window device property sheets? do i really have a physical kill switch or is ubuntu install actually lying to me/?!

ahhh, sorry for all this. from what ive been playing with so far, i love ubuntu in every other. i just really need wireless working. 

ps; im a relative newbie, so im not too happy with command lines but happy to use them as long as you can guide me through it. mainly im wondering if anyone has experienced this kind of false physical kill switch and how to fix it / what the hell it really means.

tech: acer c11o travelmate TABLET PC. Wireless is intel 2100 (?), being assigned as eth0 with dead ethernet port as eth1 which i wont be using.

---

### Post by Buffalo Soldier on 2005-10-02
I think this use to happen to me once when i was installing Ubuntu 5.04 on my Inspiron 510m.

What I did was I logon back to WinXP, turn off the Winxp control of my wireless card and let the intel driver/utility have control and set it to "enable".

And then reboot. Go into BIOS. There's a page that lets you choose whether to enable or disable the wifi card. Choose disable.

Another option page will let u set whether an "application" or "application & FN+F7 key" that should do the enable/disable of wifi.. i choose "application & FN=F7 key".

I'm not sure if the same solution applies to your tablet pc. but hope it can give u some idea on what to do next.

---

### Post by dave1111 on 2005-10-02
I have the ACER Aspire 1694 WLMi and also had some Problems with the WLAN and killswitch. The fix was to load a kernel Module which turned the wireless-card on.
Have a look at 
[http://www.informatik.hu-berlin.de/~tauber/acerhk/](http://www.informatik.hu-berlin.de/~tauber/acerhk/)
For my laptop the options for this module are force_series=1680 autowlan=1 usedritek=1, but maybe you have to use others.

Maybe you can get it to work with this. For me I had also have to load a custom DSDT because ACER didn't provide a ACPI-conform BIOS. (Before this I had to boot with acpi=off)
And I also had to update the ipw2200 driver for the wireless card.

---

### Post by jamesabruce on 2005-10-07
update; still not working

ill tell you, trying to install these things has never made me feel like so much of a linux newbie before. 

(a) i downloaded the updated drivers, as a debian package, but cant figure out how to install the damn thing. i tried "apt-get install ...." but that just checks registered repositiories. i tried double cliking on the deb and it opened in an srchive manager. arghhh! its on my usb drive, do i have to add that as a repository? i tried, but it would only let me add cds or network locations. 

i also download hk buttons driver.&#12288;firstly, i cant find the correct location for the kernel headers/source. can anyone tell me where this is in hoary? do i need to install extra packages, i only have the base system but i checked and it osudned like the "headers" were installed already, i just couldnt find them.


(b) i also tried downloading and installing breezy badger, rc, to see if that might work. i guess it has some updated ipw2100 drivers, becuase i didnt get the killswitch message during install. however, it still doesnt work, even with no WEP. so then i tried the whole hk buttons thing again. this time when i type "make hk-0.5...." it says cant find command make!!! wth? can u not make things in preview releases? waaaaaaaaaah. i feel stupid. please help me! all i need is wireless running....

---

### Post by dave1111 on 2005-10-11
For building apps there is a package called build-essentials which includes make and gcc. If you install build-essentials yous should have make.
The kernel-headers are installed with a package linux-headers-XYZ where XYZ is the string that you see with the command "uname -r" after the last - (e.g. 686)

This should give you the might to compile new ipw-drivers and the acerhk-module.
For the acerhk this is:
make
make acerhk.ko
cp acerhk.ko /lib/modules/<kernelversion>/kernel/drivers/char/
   where <kernelversion> is the same as the result from uname -r
depmod -a
modprobe acerhk

This can also be read in the INSTALL-File.
If you compiled it maybe you have to give it some options, for me it was 
 force_series=1680 autowlan=1 usedritek=1
but I think the series must be adopted for your case. The force_series must be set to 110 I think. The usedritek - I don't know but the autowlan might physically turn on the wlan if you press the button at your laptop. I had also have to give the ipw2200-driver the option led=1
You give parameters on loading modules by
modprobe acerhk force_series=110 autowlan=1

If you have a .deb file for the driver you can install it with dpkg mybe, but I have only used apt-get so far...
But I think according to dpkg --help this is what you need:
dpkg -i yourdebfile.deb


By the way is ACPI working properly? I had to get this working, otherwise the acerhk module couldn't turn on the wlan power. If you have files in /proc/acpi it is working, but if this directory doesn't exist maybe you have to fix the acpi also...

---

