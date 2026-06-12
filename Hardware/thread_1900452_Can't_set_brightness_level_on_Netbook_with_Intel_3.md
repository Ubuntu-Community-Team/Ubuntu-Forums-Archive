---
title: "Can't set brightness level on Netbook with Intel 3150"
date: 2011-12-26
forum: Hardware
---

### Post by El Potro on 2011-12-26
Hello everyone,

I have been given a Classmate Netbook with an Intel motherboard, chipset and microprocessor. Specifically, video chipset is the Intel 3150.

Along with Windows 7, Ubuntu 10.04 came pre-installed.

Bright control keys work fine on Windows 7, but on Ubuntu 10.04 they simply don't.

I have read a lot of different threads here and in other forums, blogs, looked for solutions, tried different things but nothing helped.

The curious thing is that in the GRUB screen, the Bright keys work just fine, but when the kernel image is selected, you can actually see how the brightness decreases and when you are in the login screen, or in the user's account, the keys are completely useless. And screen bright is set very low. 

I have tried many things, but I'm going to list a few

1. ```
sudo setpci -s 00:02.0 f4.b=ff
```

Didn't change anything.

2. Adding some arguments to the grub, such as

```
nomodeset acpi_backlight=vendor
nolapci

```

And others I've found here and there. Perhaps I'm not doing it right, I still can't get this to work and it's pretty annoying.

Can anybody please help? What should I do?

Thank you very much in advance

---

### Post by Toz on 2011-12-26
Have you tried _just_ **acpi_backlight=vendor**?

What is the results of the following commands:
```
sudo lspci -vnn | grep -A10 VGA
```

What backlight interfaces do you have?
```
ls /sys/class/backlight
```

And what is the model of the netbook?

---

### Post by El Potro on 2011-12-26
Thank you very much for helping, **Toz**.

I tried writing just acpi_backlight=vendor and there's no change at all.

This is the output of sudo lspci -vnn | grep -A10 VGA

```
sudo lspci -vnn | grep -A10 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
	Subsystem: Elitegroup Computer Systems Device [1019:997a]
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at f0200000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 18d0 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at f0000000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [d0] Power Management version 2
	Kernel driver in use: i915
	Kernel modules: i915

```

Seems I have a different chipset than what I thought... Intel 915.

And folder /sys/class/backlight is completely *EMPTY*!

The netbook manufacturer is a local one, Coradir. In the manufacturer's website it is listed as "CDR Class". Here's a link [http://www.coradir.com.ar/producto/detalle/57](http://www.coradir.com.ar/producto/detalle/57)
In the back it also says Model: E11-S2.

I hope this can give you some more ideas to tell me what I should do.

Thank you

---

### Post by Toz on 2011-12-26
> And folder /sys/class/backlight is completely EMPTY!
Check the contents of this folder both with and without the acpi_backlight=vendor kernel parameter. Lets see if we can get an interface.

Can you post back your complete kernel command line?
```
cat /proc/cmdline
```

And finally, the results of these commands to see how the computer is identifying itself:
```

sudo dmidecode -s system-manufacturer
sudo dmidecode -s system-product-name

```

EDIT: And can you also try this:
```
sudo setpci -s 00:02.0 f4.b=7f
```
(lets try 7f instead of ff)

EDIT2:
Do you have anything at this folder: /sys/devices/virtual/backlight ?

---

### Post by El Potro on 2011-12-26
With this line (acpi_backlight=vendor) there's no file in /sys/class/backlight, the folder remains empty. After removing this argument and booting the folder is empty also, so there's no change.

Here is the output of cat /proc/cmdline with acpi_backlight=vendor

```
BOOT_IMAGE=/boot/vmlinuz-2.6.32-37-generic-pae root=UUID=61091c01-5a9d-4681-b1c1-dc95180ea318 ro acpi_backlight=vendor quiet splash

```
Without it it's the same, the only difference is that it lacks that line.
```

BOOT_IMAGE=/boot/vmlinuz-2.6.32-37-generic-pae root=UUID=61091c01-5a9d-4681-b1c1-dc95180ea318 ro quiet splash

```
This is what dmidecode returned
```

sudo dmidecode -s system-manufacturer
Coradir S.A.

sudo dmidecode -s system-product-name
CDR/E11-S2

```

And I tried as you suggested

```
sudo setpci -s 00:02.0 f4.b=7f 

```

but it didn't make any change. Why is this not working?

In the folder /sys/devices/virtual there's no backlight folder. After booting with acpi_backlight=vendor and without it.  Although there's a "graphics" folder in there.

```
/sys/devices/virtual$ ls
bdi    dmi       hwmon  mem   net  sound    tty     vc
block  graphics  input  misc  ppp  thermal  usbmon  vtconsole

```
Inside it, there's another folder, fbcon, and these are the files inside it:

```
cursor_blink  power  rotate  rotate_all  subsystem  uevent

```
One more thing, the Kernel driver in use: i915, is correct for the GMA 3150 Intel chipset? I guess it is, right?

Sorry for my ignorance and thank you for your help.

---

### Post by Toz on 2011-12-26
> **El Potro said:**
> 
One more thing, the Kernel driver in use: i915, is correct for the GMA 3150 Intel chipset? I guess it is, right?
Yes, that should be the correct driver.

Is this laptop a re-branded Samsung netbook? If so, have a look here: [http://ubuntuforums.org/showpost.php?p=9517612&postcount=21]("http://ubuntuforums.org/showpost.php?p=9517612&postcount=21") - there is a PPA for installing samsung tools to control backlight, etc.

Also, if possible, could you run a newer version of ubuntu (11.10) from LiveCD and see if brightness works? Perhaps 10.04 is too old for that netbook.

---

### Post by El Potro on 2011-12-27
> Is this laptop a re-branded Samsung netbook? If so, have a look here: [http://ubuntuforums.org/showpost.php...2&postcount=21](http://ubuntuforums.org/showpost.php...2&postcount=21) - there is a PPA for installing samsung tools to control backlight, etc.

Doing a little research I found out that the netbook is actually a Lenovo Classmate Plus. More info here: [http://newsroom.intel.com/community/intel_newsroom/blog/2011/03/09/lenovo-and-intel-extend-digital-learning-with-new-lenovo-classmate-pc](http://newsroom.intel.com/community/intel_newsroom/blog/2011/03/09/lenovo-and-intel-extend-digital-learning-with-new-lenovo-classmate-pc)

So I guess I shouldn't try the Samsung tools... or should I?

> Also, if possible, could you run a newer version of ubuntu (11.10) from LiveCD and see if brightness works? Perhaps 10.04 is too old for that netbook. 

I did this, but it was a little painful. I couldn't directly download the last .iso from Ubuntu's website. So I had to do it with a .torrent. And I'm afraid to say that usb-creator-gtk does not work at all. So I had to find an alternative program. Luckily I came across with unetbootin which did the job correctly.

So I started to try all what you suggested me to do in the previous posts.

First, this didn't work.

```

ubuntu@ubuntu:/sys/class/backlight$ sudo setpci -s 00:02.0 f4.b=ff
ubuntu@ubuntu:/sys/class/backlight$ sudo setpci -s 00:02.0 f4.b=7f

```

Second, this is the output of lspci -vnn | grep -A10 VGA

```
sudo lspci -vnn | grep -A10 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011] (prog-if 00 [VGA controller])
	Subsystem: Elitegroup Computer Systems Device [1019:997a]
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at f0200000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 18d0 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at f0000000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Kernel driver in use: i915
```

Bright adjusting buttons don't work. Neither if I add the booting parameter acpi_backlight=vendor.

The folder /sys/devices/virtual/backlight doesn't exist.

But here's the interesting part of all this. I found out that **there is a backlight device interface**


```
ubuntu@ubuntu:/sys/class/backlight$ ls
cmpc_bl  intel_backlight

```

What can I do now?

---

### Post by Toz on 2011-12-27
> **El Potro said:**
> But here's the interesting part of all this. I found out that **there is a backlight device interface**


```
ubuntu@ubuntu:/sys/class/backlight$ ls
cmpc_bl  intel_backlight

```

What can I do now?

In each of these folders (cmpc_bl & intel_backlight) there should be a number of files.
- max_brightness - should hold the maximum brightness value the device can take
- actual_brightness - should be the current brightness level
- brightness - is where you can echo a value to change the brightness like this:
```
echo <value> | sudo tee brightness
```
...where <value> is a number between 0 and the contents of the file max_brightness.
Example:
```
echo 5 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

Try changing the brightness this way for both interfaces and see if one works.

Also, try booting with the kernel parameter **acpi_backlight=legacy** to see if you get only one backlight interface.

---

### Post by El Potro on 2011-12-27
Thank you very much again **Toz** for your disinterested and invaluable help. I'll try this tomorrow and post back. 

In case it works, how could it be possible to set this configuration under the pre-installed Ubuntu 10.04? Because due to limitations of the contract under which I was given this computer, I can't change/replace the operative system. I can edit it but to a certain point. So if this works (that I hope it will) then I'll need to have this configuration on the Ubuntu 10.04 currenty installed.

Thanks again.

---

### Post by El Potro on 2011-12-28
> Also, try booting with the kernel parameter acpi_backlight=legacy to see if you get only one backlight interface. 

Didn't change anything. There's still two devices.

If I try this:
```
echo 5 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

Nothing happens, but doing instead
```
echo 5 | sudo tee /sys/class/backlight/cmpc_bl/brightness
``` 
finally **increases the screen brightness!**

This is good news! I tried from 0 to 10, but it apparently only goes up to 7. Afterwards, it doesn't change. - Edit: It gives back a message: "Invalid argument".

So great! Thank you very much **Toz**. But now, how can I port this configuration to the pre-installed Ubuntu 10.04? Is there a way to do it? Perhaps I have to update the Intel drivers? Or it has to do with the kernel? I don't know how to do this anyway.

Thank you very much in advance.

---

### Post by Toz on 2011-12-28
I believe you're brightness keys are affecting the intel_backlight interface - which as you can see, is the one that doesn't work.

I can think of two possible solutions and one workaround.

1. Try  booting with this kernel parameter:
```
thinkpad_acpi.brightness_enable=0
```
...and see if it gets rid of the intel_backlight interface. If so, do brightness keys work?

2. Try disabling the video module from loading:
```
sudo bash -c "echo blacklist video >> /etc/modprobe.d/blacklist.conf"
```
...and reboot. Check to see if intel_backlight is gone. If not, edit (as root) **/etc/modprobe.d/blacklist.conf** and remove the last line (*blacklist video*) and reboot again.

The workaround we can look at if the above two don't work.

---

### Post by El Potro on 2011-12-29
```
thinkpad_acpi.brightness_enable=0
```

This didn't make intel_backlight go away, and the keys still don't work. 

And I couldn't do the last step, I mean adding blacklist video to the /etc/modprobe.d/blacklist.conf. I'm using a pendrive made with unetbootin, because the netbook lacks a cd-rom drive. I don't know why, but although I set the option to assign extra space to save data in unetbootin, the configurations or files I create under the live-pendrive session don't persist.

So, I just couldn't try it. And I can't install any new operative systems to this netbook, I'm forbidden to do it.

I'd like to get at least this configuration and maybe that workaround you thought, but under Ubuntu 10.04, the version that came pre-installed. Do you understand my situation? I know it's not the best, but I'd like to know if there's a chance to at least have the possibility to change the brightness through a terminal in Ubuntu 10.04.

Thank you very much

---

### Post by Toz on 2011-12-29
Lets try the workaround then. 

1. Create a a file called br in /usr/local/bin:
```
sudo gedit /usr/local/bin/br
```
...with the following content:
```
#!/bin/bash
# /usr/local/bin/br
# wrapper script to change brightness values
# make script executable

# constants - edit as required
UPPER=7
LOWER=0
INCREMENT=1
DECREMENT=1

# current value
CURRENT=`cat /sys/class/backlight/cmpc_bl/brightness`
NEW=$CURRENT

case $1 in
	up)
		if [ $(($CURRENT+$INCREMENT)) -le $UPPER ]; then
			NEW=$(($CURRENT+$INCREMENT))
		fi
	;;
	down)
		if [ $(($CURRENT-$DECREMENT)) -ge $LOWER ]; then
			NEW=$(($CURRENT-$DECREMENT))
		fi
	;;
	*)
	;;
esac

# set the new brightness value 
echo $NEW > /sys/class/backlight/cmpc_bl/brightness

exit 0

```
...save the file and make it executable:
```
sudo chmod +x /usr/local/bin/br
```

2. Setup the brightness file to allow for regular user manipulation. Edit /etc/rc.local:
```
sudo gedit /etc/rc.local
```
...and above the *exit 0* statement, add the following:
```
chmod 666 /sys/class/backlight/cmpc_bl/brightness
```

3. To test it, first run this command:
```
sudo chmod 666 /sys/class/backlight/cmpc_bl/brightness
```
...then to increase brightness:
```
br up
```
...and to decrease brightness:
```
br down
```

4. You might also be able to assign the brightness function keys to these commands.

---

### Post by El Potro on 2011-12-30
Thank you very much again **Toz** I'll definitively try this.

But anyway if I can't get this to work with the pre-installed Ubuntu 10.04 all this is pretty much nothing for me, since I can't install/upgrade to 11.10.

What do I have to do to be able to have the same video configuration Ubuntu 11.10 brings out of the box, in my already installed Ubuntu 10.04? Is it possible to do it? Do I have to update the Kernel, or perhaps the Intel drivers? I haven't got a clue, so any kind of information regarding this would be **hugely **appreciated.

---

### Post by Toz on 2011-12-30
The best way to try out 11.10 is to boot with the Live CD (it won't affect your system in any way). Then you can try the newer kernel and drivers. The latest intel drivers will already be included.

It would be interesting to see if in 11.10 you still get 2 backlight interfaces.

---

### Post by El Potro on 2011-12-30
Yes, I'm booting 11.10, I was doing all these tests on 11.10 (because on 10.04 no matter what I add to the kernel booting parameters I get no backlight device listed).

The only one I couldn't perform was this one

>  2. Try disabling the video module from loading:
Code:
sudo bash -c "echo blacklist video >> /etc/modprobe.d/blacklist.conf"

And it was just because I couldn't save the session, it was a live-pendrive session.

What I'd like is to at least have the same possibility of changing the backlight intensity on the installed 10.04. Did I understand you right? If I simply install the latest Kernel (3.0.0-14) then it would be possible?

---

### Post by Toz on 2011-12-30
> **El Potro said:**
> Yes, I'm booting 11.10, I was doing all these tests on 11.10 (because on 10.04 no matter what I add to the kernel booting parameters I get no backlight device listed).
Oh, ok. I didn't understand that this was what you were doing.

> The only one I couldn't perform was this one

And it was just because I couldn't save the session, it was a live-pendrive session.
Then this would be irrelevant in 10.04 if there are no backlight interfaces. I was trying to remove one of them.

> What I'd like is to at least have the same possibility of changing the backlight intensity on the installed 10.04. Did I understand you right? If I simply install the latest Kernel (3.0.0-14) then it would be possible?
In theory, yes.

---

### Post by El Potro on 2011-12-30
Thank you very much again.

I did it, the backlight works through a terminal, just like in Ubuntu 11.10. But as far as my ignorance can tell, it seems that the Kernel is having some kind of incompatibility with Ubuntu 10.04. For example the first thing I noticed is that it doesn't detect my wireless card, and I can't work without it.

I don't have an idea of what I should do now. Maybe is better to manually install the latest Intel drivers in the recommended kernel for Ubuntu 10.04? What do you think I should do?

---

### Post by Toz on 2011-12-30
Can you try booting with the older 2.6 kernel with the following kernel parameter:
```
acpi_osi=Linux
```
Does this allow your brightness keys to work and/or do you get an backlight interface?

Otherwise, what make/model is your wireless card?

---

### Post by El Potro on 2011-12-31
> Can you try booting with the older 2.6 kernel with the following kernel parameter:
Code:

acpi_osi=Linux

Does this allow your brightness keys to work and/or do you get an backlight interface?

No, sadly it didn't add any backlight device nor made the brigthness keys to work.

So I was looking how to update the Intel drivers in Ubuntu 10.04. I came across with this [http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx) 

That's a guide that basically tells you how to add the x-org edge repositories and to update the video drivers, and also it advices to update the kernel to the version 2.6.35 to get all working.

So I did this. But kernel won't boot with the latest 2.6.35.31 kernel. It freezes at ```
udev: starting version 151
```

So I started to install older releases of the same kernel version, the next one was 2.6.35-30 generic. Which also gave the same result.

But the next one, 2.6.35-25 generic, works. I mean, I can boot it, and also I get only one backlight device: **cmpc_bl**.

And I tried to modify the brightness the way you told me, sudo echo X | sudo tee brightness. And it works perfectly.

Now the only thing I ask myself is:

Why are 2.6.35.31 and 30 not working, but 2.6.35.25 is? 
Is it better to simply use 2.6.35.25? or to find out the way to get the latest -at the moment- 2.6.35.31 to work? Or is it the best to solve the wireless card issue in 3.0.0-14? 

By the way, the wireless card is ```
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)

```

---

### Post by Toz on 2011-12-31
You should use what works. With 2.6.35-25, does the wireless work as well? If so, stick with it.

---

### Post by El Potro on 2011-12-31
Yes it does. All I tested works perfect. But my question was because I was thinking, isn't it better to stick with the last version of the kernel? I mean, maybe the last 2.6.35, or the last 3.0.0. Just because the improvements and fixes. Are you sure it is safe to stick with an old kernel? Sorry for my ignorance.

Also I have another question, when I set the brightness to a high level, after some seconds of keyboard/mouse inactivity, the screen dims a little. I think this may be happening to automatically save power, if so, where can I set this to a different timing? Where to edit this?

---

### Post by Toz on 2011-12-31
> Yes it does. All I tested works perfect. But my question was because I was thinking, isn't it better to stick with the last version of the kernel? I mean, maybe the last 2.6.35, or the last 3.0.0. Just because the improvements and fixes. Are you sure it is safe to stick with an old kernel? Sorry for my ignorance.

Although there are improvements with every release of the kernel, I think that in your particular case, you should stick with the kernel version that works.
> Also I have another question, when I set the brightness to a high level, after some seconds of keyboard/mouse inactivity, the screen dims a little. I think this may be happening to automatically save power, if so, where can I set this to a different timing? Where to edit this?
Unfortunately, I use xubuntu, which is a little different - especially with respect to configurations. There should be a settings option somewhere in preferences that controls the dimming of the screen after a certain time of inactivity. Have a look at this thread: [ubuntuforums.org/showthread.php?t=1024735]("ubuntuforums.org/showthread.php?t=1024735")

---

