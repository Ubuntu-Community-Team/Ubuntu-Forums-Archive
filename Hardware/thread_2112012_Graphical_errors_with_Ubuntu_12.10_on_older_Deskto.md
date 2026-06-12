---
title: "Graphical errors with Ubuntu 12.10 on older Desktop"
date: 2013-02-03
forum: Hardware
---

### Post by S Hartwell on 2013-02-03
My parents(formerly mine)desktop is a good 8 years old and was bought when I was entering high school. It's sporting a **Nivida GEforce 6200 Turbocache** Graphics card.

I'm not 100% new to Ubuntu to linux distro's however I'm no expert and command-line has always been a loss for me since I've grown up in the GUI days of computing only rarely using a CLI.

I'm looking to install Ubuntu 12.10(Or any other version that'll function) as Windows Xp just isn't cutting it anymore. It's possible the hardware is simply failing but I think this desktop has reached it's limit with Windows and can benefit in many ways from the use of Ubuntu.

The problem occurs when I'm running Ubuntu 12.10 live from the USB(Same one I used to re-install for my laptop.) The GUI simply glitches out with all sorts of colors and just general disarray. I'm assuming this has occurred due to the age of the hardware and lack of support or made drivers so I felt some of the experts here could help me out. Prepared to share any information required.


A separate problem occurs with my laptop(Low concern) and my inability to adjust brightness via the Function Up and down arrow keys. I don't think it works via the brightness settings as well.

Keen to receive support!

---

### Post by Mark Phelps on 2013-02-03
Not really an Nvidia expert, but a chipset that old is likely not to work well with a new Ubuntu version.  AMD/ATI drops Linux driver support every couple of Ubuntu versions, and while Nvidia is not nearly that bad, I don't think your chipset is supported anymore.

Perhaps someone more versed in Nvidia versions can come along and provide more information.

---

### Post by S Hartwell on 2013-02-03
Well the 12.04 LTS seems to work right. No glitches in the graphics. I manged to install 12.10 but then the screen resolution was a complete mess and made it impossible to navigate properly. Hopefully once I get the LTS to install(Downloading the LTS .Iso right now!) it'll be smooth sailing.

---

### Post by S Hartwell on 2013-02-03
Also, the computer is making a loud grinding noise as if the HDD or possibly a fan is having trouble running. Oh boy!

---

### Post by ahallubuntu on 2013-02-03
~

---

### Post by S Hartwell on 2013-02-03
Works fine in Gnome I guess it was just Unity that simply can't run on this old computer. That Dockme or whatever it's called application might work, though. It's a shame as I was quite fond of Unity but will make due -- Shouldn't be using this desktop too much.

Thank you for the support guys. I think it was a combination of using Gnome and switching the drivers in 'Software Sources' as it wasn't set to Nivdia.

---

### Post by ahallubuntu on 2013-02-03
~

---

### Post by S Hartwell on 2013-02-04
Alright now there is only two things I need help with.

My NV54 Gateway Laptop can't adjust brightness settings. Well, I can sort of.

If I set the brightness with Function 'Arrows Keys(Up and Down)' then reboot the brightness will change. I just can't change it live while running(installed on HDD.)

As per the Desktop I'm looking to get a USB wireless adapter since I'm going to need it. I could run a cable but that would require some time and effort(drilling hole in the ceiling to run cable,etc.)

My mother is being nice and offering to go to Futureshop. I told her what I need "Wireless USB Adapter" I also made sure she noted "Running Linux/Ubuntu 12.10"

Does it matter which one I obtain? I know some will require drivers but those can be downloaded. Might need help installing them though.

This is the one I'm looking at getting.

[http://www.futureshop.ca/en-CA/product/linksys-linksys-dual-band-wireless-n-usb-adapter-ae3000-ca-ae3000-ca/10204183.aspx?path=052f2c4acead8abd49e7ccb0d7d5bc9een02](http://www.futureshop.ca/en-CA/product/linksys-linksys-dual-band-wireless-n-usb-adapter-ae3000-ca-ae3000-ca/10204183.aspx?path=052f2c4acead8abd49e7ccb0d7d5bc9een02)

One last thing is...Printers. How exactly do printers get setup in Ubuntu? I tried it with my mothers printer(Lexmark 3500) however it didn't work. It added it but when printing simply wouldn't.

Would it be different for my girlfriend and I's wireless printer(HP)?

---

### Post by Yellow Pasque on 2013-02-04
> This is the one I'm looking at getting.
[http://www.futureshop.ca/en-CA/produ...b0d7d5bc9een02](http://www.futureshop.ca/en-CA/produ...b0d7d5bc9een02)

No. Don't. At least some hassle will be involved with that (it has a RT3573 chipset): [http://geekniggle.blogspot.com/2012/07/cisco-linksys-ae3000-wifi-usb-dongle.html](http://geekniggle.blogspot.com/2012/07/cisco-linksys-ae3000-wifi-usb-dongle.html)

A better choice would be: [http://www.futureshop.ca/en-CA/product/netgear-netgear-wireless-usb-adapter-wna1100-100ens-wna1100-100ens/10209681.aspx?path=3a3683f40011b377ae7e353aeceea25den02](http://www.futureshop.ca/en-CA/product/netgear-netgear-wireless-usb-adapter-wna1100-100ens-wna1100-100ens/10209681.aspx?path=3a3683f40011b377ae7e353aeceea25den02)
That one has an Atheros 9271 chipset, and I've personally used it on Linux. It should work "out of the box" as long as you have linux-firmware package installed. The downside is that it's N150, but I doubt you'll notice the difference between N150/N300 on such an old box.

> My mother is being nice and offering to go to Futureshop. I told her what I need "Wireless USB Adapter" I also made sure she noted "Running Linux/Ubuntu 12.10"
That's probably a mistake. Even if you write that stuff down for your mother, don't trust a salesman to know anything about Linux hardware compatibility. You have to do your own homework..

---

### Post by S Hartwell on 2013-02-04
Well apparently the future shop tech support(Such as BestBuy's Geek Squad) said that it will work with Ubuntu however it clearly says on box 'Compatible with Windows' and I can't find any drivers(officially) that are listed as Linux/Ubuntu.

Sadly, none of the other options listed are in the store. Our Futureshop is actually being shut-down so stock is...**** to say the least.

IS there ANY way for me to make this thing work? I'm taking it over as of tomorrow and would really like having this working.

EDIT: I'm following [http://geekniggle.blogspot.ca/2012/07/cisco-linksys-ae3000-wifi-usb-dongle.html](http://geekniggle.blogspot.ca/2012/07/cisco-linksys-ae3000-wifi-usb-dongle.html)
I'm at the Sudo make -j10 step. 

When I process to command 'Sudo make -j10' the output is:
make -C UTIL/ osutil
make[1]: Entering directory `/home/s-hartwell/Desktop/Linux/UTIL'
make[1]: warning: jobserver unavailable: using -j1.  Add `+' to parent make rule.
cp -f os/linux/Makefile.6.util /home/s-hartwell/Desktop/Linux/UTIL/os/linux/Makefile
make -C /lib/modules/3.5.0-23-generic/build SUBDIRS=/home/s-hartwell/Desktop/Linux/UTIL/os/linux modules
make: Entering an unknown directory
make: *** /lib/modules/3.5.0-23-generic/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [osutil] Error 2
make[1]: Leaving directory `/home/s-hartwell/Desktop/Linux/UTIL'
make: *** [all] Error 2

Followed everything to the TEE. Might just end up running an Ethernet cable threw the ceiling.

---

### Post by Yellow Pasque on 2013-02-04
Well, you can look at the link I gave above and you might make it work.

Sighhh........ At times, I wonder why I bother at all.
You: Will this adapter work?
Me (a couple hours later): Don't buy that. You'll have to jump through hoops to get it to work. Don't trust the salesman to have Linux knowledge either.
You (a few couple hours later): So I bought that adapter and the salesman said it would work, but it doesn't.

LMFAO!

---

### Post by S Hartwell on 2013-02-04
I'm sorry but I'm not online all the time and It was too late by the time I saw your post.

It was NOT the salesman that said it would work. It was a technical support guy that suposed to know what they're talking about. He claimed he used this all the time.

I've tried using the link you posted however it's giving me problems at the "Sudo Make -j10" command which I've posted on my post before this one. I'm close to getting it working(According to your link.)

If all else fails I'll return this and just drill a hole in the ceiling and pickup a network cable.

---

### Post by Yellow Pasque on 2013-02-04
Do you have linux-headers-generic package installed?

---

### Post by ahallubuntu on 2013-02-04
~

---

### Post by S Hartwell on 2013-02-04
[/CODE]EDIT: Thankfully I got it to work. With a combination of installing the packages and executing the commands in the proper directory. :)

THANK YOU soooooo much. I know I've been a bit of a bother but I'm just glad to have it working. You're all wonderful and I can't wait to partcipate in other parts of the forums. Heck, maybe I'll even learn more about Linux. I've always been a computer 'geek' just lost touch when I noticed 12 year olds could build things I couldn't even understand, haha.

Okay only one last thing to do so I wont have to rerun commands upon every reboot. This is the solution offered but I'm not sure what it means.

"No you wouldn't have to repeat entire step 6 every time you reboot.

Create a WPA supplicant configuration (below) and edit your startup script with


wpa_supplicant -B -c/etc/wpa_supplicant.conf -ira0 -Dwext
ifconfig ra0 up
dhclient ra0


 
vim /etc/wpa_supplicant.conf

network={
priority=1
ssid="HUMAN-NETWORK-5G"
proto=RSN
key_mgmt=WPA-PSK
pairwise=CCMP TKIP
group=CCMP TKIP
psk="dingdong"
}
network={
priority=2
ssid="HUMAN-NETWORK-24G"
proto=RSN
key_mgmt=WPA-PSK
pairwise=CCMP TKIP
group=CCMP TKIP
psk="dingdong"
}"

Once I know what that is telling me to do I'll be golden :)

---

### Post by Yellow Pasque on 2013-02-04
Glad you got it working (and without a drill too!) 
Please mark the thread solved (in thread tools menu up top).

---

