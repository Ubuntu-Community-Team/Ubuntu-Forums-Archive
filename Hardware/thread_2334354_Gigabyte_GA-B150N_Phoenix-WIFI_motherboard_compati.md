---
title: "Gigabyte GA-B150N Phoenix-WIFI motherboard compatibility"
date: 2016-08-18
forum: Hardware
---

### Post by stefano78 on 2016-08-18
Hi,



I am trying to choose a motherboard for a new PC (powerful enough to virtualize "windows 10" inside linux [kubuntu]).
I almost decided for the following : GA-B150N Phoenix-WIFI ([http://www.gigabyte.com/products/product-page.aspx?pid=5639#sp](http://www.gigabyte.com/products/product-page.aspx?pid=5639#sp)), but I am not sure if everything on this board is fully supported by linux.

(I would like to avoid some tricky situations such as compiling some drivers with "make / make install", because I almost never succeded in doing it, and at each kernel update I would have to compile it again...)

Could some hardware and linux expert help me please :-) ?



I hereafter write some info about the chips on this board :

N.B. The specifications are vague [I don't know where to look for, beside Gigabyte website and the user manual], they give the brands but not the reference numbers, so I could not understand how to follow the advice "Due to different Linux support condition provided by chipset vendors, please download Linux driver from chipset vendors' website or 3rd party website." written in Gigabyte website... and therefore how to check compatibility.


Intel B150 Express -> I think there are no problems ([http://askubuntu.com/questions/691216/no-version-of-ubuntu-can-be-installed-with-any-skylake-6th-generation-intel-proc](http://askubuntu.com/questions/691216/no-version-of-ubuntu-can-be-installed-with-any-skylake-6th-generation-intel-proc))

Intel HD graphics [Intel® HD Graphics 530 if I choose the "Intel Core i3-6100" CPU] -> Everything OK [[https://wiki.archlinux.org/index.php/intel_graphics#Skylake_support]](https://wiki.archlinux.org/index.php/intel_graphics#Skylake_support]) [[http://www.intel.com/content/www/us/en/support/graphics-drivers/000005526.html]](http://www.intel.com/content/www/us/en/support/graphics-drivers/000005526.html])

Realtek ALC892 -> No problem with some (hopefully) straightforward trick : [https://ubuntuforums.org/showthread.php?t=2293912](https://ubuntuforums.org/showthread.php?t=2293912)    If I understand well, dkms allows the driver to automatically update the driver whenever the kernel changes ?

Intel GbE LAN chip (10/100/1000 Mbit)-> A lot of ethernet controllers that I saw in Intel website are supported by Linux, so can I be optimistic ?

Wi-Fi and Bluetooth 
[Wi-Fi 802.11 a/b/g/n/ac, supporting 2.4/5 GHz Dual-Band
Bluetooth 4.2, 4.1, BLE, 4.0, 3.0, 2.1+EDR
Support for 11ac wireless standard and up to 867 Mbps data rate]
-> [https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi). Once again, I don't know the reference number of the chip... Can I be optimistic ?
N.B. There is a small issue with "WiFi / Bluetooth coexistence". They explain that I can use Wi-Fi if I disable bluetooth, but I am wondering if I can use bluetooth (if I disable Wi-Fi) ?

Chipset+ASMedia® USB 3.1 Controller -> OK if it is an ASM1142 [[http://www.asmedia.com.tw/eng/e_show_products.php?cate_index=160&item=161]](http://www.asmedia.com.tw/eng/e_show_products.php?cate_index=160&item=161]). What if it is something else ?...

Hope I didn't forget anything.



I hope that my questions and links make sense (eight years since the last time I bought a PC, so I feel like a newbye... ^^ I remember that the graphics chip was not compatible with linux, so, at that time, I had to buy a graphics card. For this new one, I want to assemble a mini-PC (no space for cards) : hence I feel that I cannot make any mistake!)



Thanks !

---

### Post by giantenemycrab on 2016-08-19
I use [COLOR=#000000]GA-B150N Phoenix-WIFI with Ubuntu 16.04. 

The parts that I use in this build: [/COLOR]http://pcpartpicker.com/list/8tMcTH
They are working fine so far, including WiFi (up to 802.11n for sure, but because I don't have 802.11ac wireless router, can't confirm ac) and Intel Graphics 530 from i5-6500 works fine.

I don't have any UBS3.1 device, so I am not able to test it.
I don't have M2 2280 SSD to test.
I haven't used LAN ports yet.
Haven't tested the audio ports either. I've used HDMI's audio from motherboard, which works fine.
Haven't connected Bluetooth device yet but I can attempt to do so.

One minor problem is GTX 1060 NVidia driver that causes screen flickering after suspend + wake. But this is most likely their driver issue, probably not related to motherboard (because switching to beta version of the nvidia driver changed the behavior)

Let me know if you need me to do anything specific.

---

### Post by Yellow Pasque on 2016-08-19
You shouldn't need to do the ALSA dkms upgrade on Ubuntu 16.04. The relevant patch is now in the stock kernel.

---

### Post by stefano78 on 2016-08-20
Thank you for all your answers !

I am happy that I don't have to use the ALSA upgrade :D
And relieved that WiFi is fine (still wondering about bluetooth, but it doesn't matter so much...).

So I am quite sure that I will take it.
Could I just ask you to try the red USB port with some USB2 or USB3 device (USB3.1 should be backward compatible) ?

I really hope that LAN will work... I will let you know when I test it.

Thanks again :D

---

### Post by stefano78 on 2016-08-21
Update : I found more specs about the motherboard : [http://www.heise.de/preisvergleich/gigabyte-ga-b150n-phoenix-wifi-a1368195.html](http://www.heise.de/preisvergleich/gigabyte-ga-b150n-phoenix-wifi-a1368195.html)
and [http://www.notebooksbilliger.de/gigabyte+ga+b150n+phoenix+wifi+mainboard](http://www.notebooksbilliger.de/gigabyte+ga+b150n+phoenix+wifi+mainboard)

- The USB3.1 is an "ASM1142" so it should be perfect for linux.
- The LAN is an "Intel I219-V", so I guess that I will use WiFi, while waiting for some kernel upgrade with the "latest" e1000e driver.
(cf. [http://unix.stackexchange.com/questions/294753/intel-ethernet-connection-i219-v-not-working-under-linux-on-an-asuspro-b-laptop](http://unix.stackexchange.com/questions/294753/intel-ethernet-connection-i219-v-not-working-under-linux-on-an-asuspro-b-laptop) )

---

### Post by giantenemycrab on 2016-08-24
I can say that Bluetooth worked fine for me.
Tried it with Apple Magic Trackpad and Apple Keyboard.
I was able to pair fine. For Magic Track pad, I needed sudo apt-get install blueman to initially make it work, but maybe I didn't need to.

---

### Post by stefano78 on 2016-08-28
OK, that's fantastic. I ordered it. Thank you so much !

---

