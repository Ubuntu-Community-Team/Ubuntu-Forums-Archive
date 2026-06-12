---
title: "bluetooth mouse and keyboard, how to use?"
date: 2004-12-28
forum: Hardware &amp; Laptops
---

### Post by nehalem on 2004-12-28
I installed the bluez tools but don't know where to go from here.  The biggest problem is that tutorials are very confusing since they disagree with each other (mostly because bluetooth related stuff keeps changing).  

There is this site for a driver to use. [HERE](http://www.visi.com/~pmk/msbtkb-linux.html).  But I think that there may be a better solution built into bluez itself (this is over a year old and the author said that the bluez guys are working on their own driver, which I'm guessing would be included with Ubuntu)

Also I can do this:
hcitool scan
Scanning ...
        00:02:EE:E1:4A:47       n/a
        00:07:61:0A:B8:FD       Logitech Elite Keyboard


But again have no idea what to do from here.  Where do I go from here?  Thanks much.

---

### Post by banadushi on 2004-12-28
[QUOTE=nehalem]I installed the bluez tools but don't know where to go from here.  The biggest problem is that tutorials are very confusing since they disagree with each other (mostly because bluetooth related stuff keeps changing).  

There is this site for a driver to use. [HERE](http://www.visi.com/~pmk/msbtkb-linux.html).  But I think that there may be a better solution built into bluez itself (this is over a year old and the author said that the bluez guys are working on their own driver, which I'm guessing would be included with Ubuntu)

Also I can do this:
hcitool scan
Scanning ...
        00:02:EE:E1:4A:47       n/a
        00:07:61:0A:B8:FD       Logitech Elite Keyboard


But again have no idea what to do from here.  Where do I go from here?  Thanks much.[/QUOTE]
 Here is what I did to get my bluetooth mouse working:

1. edit /etc/defualt/bluez-utils.  Change the line:
    HIDD_ENABLE = 1
to enable the HIDD deamon.  (PS. this is all from memory, so it might be called something else.  But its HIDD_something)

2.  Restart bluez-utils

3.  Run `hcitool scan` to get the ID of the device your trygin to connect.

4.  Run `hidd --connect [ID]` to connet the device

5. Everything should just start working. 

Rock on!

Jason

---

### Post by nehalem on 2004-12-28
Thanks for the response!

Looks like your directions work.  I'm connected but when I type nothing actually happens??

Here is my CLI output:
root@ubuntu-laptop:/home/cendrizzi # hidd --connect 00:07:61:0A:B8:FD
root@ubuntu-laptop:/home/cendrizzi # hidd
00:07:61:0A:B8:FD HID Boot Device [046d:b301] connected


(nothing happens when i type)

Could it have something to do with the PIN?  I changed it from the default.

Do I have to setup a new keyboard in my X11 setup file (this doesn't make much sense howeer since I can plug in the docking thing that comes with this setup via USB (so it's the bluetooth server) and it works fine).

---

### Post by nehalem on 2004-12-28
So I'm waiting for my mouse to charge.  After that I'll try it, I'm curious to see if keyboards need more configuration.

---

### Post by banadushi on 2004-12-28
Just a thought, as I've never used a bluetooth keyboard, but if you are running hoary with xorg, check that you are using the kbd driver for the keyboard section and not keyboard.  The kbd driver (I believe) allows multiple instances, whereas the keryboard driver is builtinto the core and does not allow multiple instances.

Have a good one.

Jason

---

### Post by nehalem on 2004-12-28
Just warty for me.  And I can plug in a normal USB keyboard and it's works fine so it's something with bluetooth.  I guess the most important thing is to find out if it's all of bluetooth or just bluetooth+keyboard (hopefully my mouse will be done charging soon)

---

### Post by nehalem on 2004-12-28
OK, 
so I got the mouse to connect, but like the keyboard it doesn't do anything. 

From the CLI:
hidd
00:07:61:13:E4:70 HID Boot Device [046d:b001] connected
00:07:61:0A:B8:FD HID Boot Device [046d:b301] connected

does yours say Boot Device?  That seems a little suspect to me.

 I'm inclined to think it may be my xconfiguration since I use an ATI produced one for my ATI driver.

I really don't know what to do at this point since I'm clueless with bluetooth.

---

### Post by scoon on 2004-12-29
Hey there, 

I use the same kb's and mouse set that you do.  They work just fine but only with the kernel patch from [www.bluez.org](www.bluez.org).  If you do not use the patch from there then you will end up using the vanilla kernel modules which HID does not work.  


scoon

---

### Post by nehalem on 2004-12-29
Uh oh,
I have never patched (compiled?) a kernel.  Any chance you can give me the heads up on how to go about this?

Also is this the latest patch?  Or the one for whatever Ubuntu uses (2.6.8.4 I think)

Thanks for your help!

P.S.  Will they include this patch in the kernel later on?

---

### Post by scoon on 2004-12-29
Hey there, 

Even though the article is dated, it still works like this.

[http://www.holtmann.org/linux/kernel/debian.html](http://www.holtmann.org/linux/kernel/debian.html)


scoon

---

### Post by nehalem on 2004-12-30
Uh, so it's not just a patch eh?

You have to recompile and everything.

What about things like USB support and all that junk (project utopia for example).  Will those stop working.

I'm ready to just forget about getting linux working on this laptop, it's too much work, I've already spent probably ten hours I don't have trying to get things working right....

---

### Post by scoon on 2004-12-30
Hey there, 

Anytime a patch is applied to the kernel source, the kernel source must be recompiled.  I gave you that link becuase it seemed to be pretty self explanatory. 

scoon

---

