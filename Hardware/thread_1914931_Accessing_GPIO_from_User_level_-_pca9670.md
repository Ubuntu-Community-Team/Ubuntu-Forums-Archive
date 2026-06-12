---
title: "Accessing GPIO from User level - pca9670"
date: 2012-01-25
forum: Hardware
---

### Post by bluestorm7 on 2012-01-25
Hi,

I was hoping someone with a good understanding of the GPIO framework can shed some light into a problem. 

I am working on a custom board (SBC - Xpedite 7370)
I need to trigger an output from a GPIO chip inside of the board. The chip is pca9670 and it is on the i2C bus.
I am running Ubuntu Desktop 10.04 (2.6.38-8-generic)
It would be great if I could use the GPIO framework to avoid having to write a kernel driver.
As far as I understand, Ubuntu already has the pcf857x driver as a kernel option. 
I have read the /documentation/gpio.txt document, but it is not very clear to me.
The kernel does not seem to be recognizing the pca9670 since dmesg does not show the driver being able to find anything. 
What steps should I follow? Do I need to configure the driver in someway before loading it?

Here are things I have tried:

I have tried loading the pcf857x driver.
However, if I load it, nothing comes up on dmesg

I understand I should see something along these lines: (this is from the manufacturer on their custom build kernel...I have to run Ubuntu though...)

pcf857x 0-0020: gpios 0..7 on a pca9670
pcf857x 0-0026: gpios 8..15 on a pca9670
pcf857x 0-0027: gpios 16..23 on a pca9670
pcf857x 0-0024: gpios 24..31 on a pca9670

It seems that the PCA9670 is not detected.
So I manually instantiated the i2c device

# echo pca9670 0x27 > /sys/bus/i2c/devices/i2c-0/new_device

if I then run 

# modprobe pcf857x

I get the following 

[ 9065.165261] [drm] GMBUS timed out, falling back to bit banging on pin 0 [i915 gmbus disabled]
[ 9065.165282] pcf857x: probe of 0-0027 failed with error -12

I am still not sure why I get this message.

I have also been trying to understand how the i2C driver operates. 
Been trying with i2c-tools with no luck

# i2cdetect 0 

does not seem to find anything.

I am not sure how to use i2cdetect. I just loaded i2c-dev module and then i2cdetect was able to run....but it did not find any device in a ny port (I tried bus 0,1,2)

There seems to be a problem with even detecting the i2c devices all together 
What are the steps to find a device in i2c busses?


Any help is greatly appreciated
Thank you in advance


Pablo

---

