---
title: "Keyboard Logitech G413 TKL SE : Drivers"
date: 2024-01-13
forum: Hardware
---

### Post by makem2 on 2024-01-13
I have just received this keyboard and as usual, drivers for Linux are not available from the makers.

I have found this:

[https://github.com/MatMoul/g810-led?tab=readme-ov-file](https://github.com/MatMoul/g810-led?tab=readme-ov-file)

This lists the G413 Carbon. Mine does not state carbon but all I want to do is control the keyboard light intensity which is too bright for me after plug and play.

I am considering giving it a try as it can be uninstalled. However, when I get to the install page I am am concerned when I see, "[COLOR=#1F2328][FONT=-apple-system]Debian (unstable, and 10 or later), Ubuntu 19.04 or later ":

[/FONT][/COLOR]I wonder if I should leave well alone? I am using a later Ubuntu.

It appears the following would be what I need to do if I do decide to install:

1. [COLOR=#1F2328][FONT=ui-monospace]sudo apt install g810-led
[/FONT][/COLOR]2. sudo apt-get install git g++ make libhidapi-dev[COLOR=#1F2328][FONT=-apple-system] # for hidapi
[/FONT][/COLOR]or sudo apt-get install git g++ make libusb-1.0-0-dev[COLOR=#1F2328][FONT=-apple-system] # for libusb
[/FONT][/COLOR]3. git clone [https://github.com/MatMoul/g810-led.git](https://github.com/MatMoul/g810-led.git)
cd g810-led
make bin[COLOR=#1F2328][FONT=-apple-system] # for hidapi
[/FONT][/COLOR]or
make bin LIB=libusb[COLOR=#1F2328][FONT=-apple-system] # for libusb[/FONT][/COLOR]
sudo make install

It appears straight forward but as I have never done this before I would appreciate comment on the risk.

The keyboard that is being replaced was a Razer Huntsman, far too fast for me but coped with for a year. My grandson has his eyes on it.

I do not want to mess up a nice dual boot two screen install for the sake of keyboard lighting.

---

### Post by BicyclerBoy on 2024-01-13
The Logitech G915 TKL allows you to set brightness without any special driver, just a direct special key stroke..
The K830 has a "fn" shifted key to cycle backlight brighness.

I recall having to connect Windows to the K830 to turn off touch stuff that did not work properly.
But never needed to connect Windows to the G915.

---

### Post by makem2 on 2024-01-13
Thank you, I will experiment.

---

### Post by #&amp;thj^% on 2024-01-13
> **makem2 said:**
> I have just received this keyboard and as usual, drivers for Linux are not available from the makers.

I have found this:

[https://github.com/MatMoul/g810-led?tab=readme-ov-file](https://github.com/MatMoul/g810-led?tab=readme-ov-file)

This lists the G413 Carbon. Mine does not state carbon but all I want to do is control the keyboard light intensity which is too bright for me after plug and play.

I am considering giving it a try as it can be uninstalled. However, when I get to the install page I am am concerned when I see, "[COLOR=#1F2328][FONT=-apple-system]Debian (unstable, and 10 or later), Ubuntu 19.04 or later ":

[/FONT][/COLOR]I wonder if I should leave well alone? I am using a later Ubuntu.

It appears the following would be what I need to do if I do decide to install:

1. [COLOR=#1F2328][FONT=ui-monospace]sudo apt install g810-led
[/FONT][/COLOR]2. sudo apt-get install git g++ make libhidapi-dev[COLOR=#1F2328][FONT=-apple-system] # for hidapi
[/FONT][/COLOR]or sudo apt-get install git g++ make libusb-1.0-0-dev[COLOR=#1F2328][FONT=-apple-system] # for libusb
[/FONT][/COLOR]3. git clone [https://github.com/MatMoul/g810-led.git](https://github.com/MatMoul/g810-led.git)
cd g810-led
make bin[COLOR=#1F2328][FONT=-apple-system] # for hidapi
[/FONT][/COLOR]or
make bin LIB=libusb[COLOR=#1F2328][FONT=-apple-system] # for libusb[/FONT][/COLOR]
sudo make install

It appears straight forward but as I have never done this before I would appreciate comment on the risk.

The keyboard that is being replaced was a Razer Huntsman, far too fast for me but coped with for a year. My grandson has his eyes on it.

I do not want to mess up a nice dual boot two screen install for the sake of keyboard lighting.

I know MatMoul, he is an active Arch Developer, and I trust him. (If that counts for anything)

---

### Post by BicyclerBoy on 2024-01-13
I have used solaar to manage logitech trackball & keyboard..
Forgot to install after upgrade to 23.10..
The version available in 23.10 appears to be able to manage keys & LEDs on the G915, nice surprise.

---

### Post by #&amp;thj^% on 2024-01-13
+1 for solaar, i use it myself :)

---

### Post by makem2 on 2024-01-14
I found this (well actually my son did):

[https://www.logitech.com/assets/66153/2/g413-se-mechanical-gaming-keyboard-qsg.pdf](https://www.logitech.com/assets/66153/2/g413-se-mechanical-gaming-keyboard-qsg.pdf)

---

