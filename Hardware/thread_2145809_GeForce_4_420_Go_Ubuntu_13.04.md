---
title: "GeForce 4 420 Go Ubuntu 13.04"
date: 2013-05-16
forum: Hardware
---

### Post by Theredbaron1834 on 2013-05-16
So I have a zx5000 laptop that has a GeForce 4 420 Go. I can't get video drivers to work right, I believe I am just using FB. I can't get the correct closed drivers to install, they say it doesn't work, even using the 96.x drivers. I have also tried Nouveau, but it isn't running.


Here is the video output's of lsmod:
```

i2c_nforce2            12876  0 
video                  18894  0

```
lshw -c video
```

   *-display UNCLAIMED     
   description: VGA compatible controller
   product: NV17M [GeForce4 420 Go 32M]
   vendor: NVIDIA Corporation
   physical id: 0
   bus info: pci@0000:01:00.0
   version: a3
   width: 32 bits
   clock: 66MHz
   capabilities: vga_controller bus_master cap_list
   configuration: latency=64 maxlatency=1 mingnt=5
   resources: memory:ea000000-eaffffff memory:f8000000-fbffffff memory:fc000000-fc07ffff memory:fc080000-fc09ffff

```Anyone know how to get it to work?

---

### Post by Yellow Pasque on 2013-05-16
Nouveau should work out of the box, and if it doesn't, you should file a bug. What version of Ubuntu are you running?  Oh, and you might have borked nouveau when trying to install the proprietary drivers, which won't run on newer versions of Ubuntu.

---

### Post by Theredbaron1834 on 2013-05-16
I am running Ubuntu 13.04. On a fresh install the video doesn't work. I had to use an ext moniter, install and then install the closed drivers. Upon boot it says it doesn't work with my card, but then it actually uses the moniter. I can remove the closed drivers after the fact, and it still works. I just can't get nouveau to work.


Can you tell me for sure that Nouveau isn't running? I assume that it isn't because it isn't in lsmod, but I am not sure. Is there another way to check?

---

### Post by papibe on 2013-05-16
Hi Theredbaron1834.

I have a Toshiba laptop with a Nvidia GeForce 4 440 Go. Unfortunately, the graphics stopped working long time ago. Since it works OK in text mode, now it is a 'closet' server.

If I remember correctly the last working driver was in 96.xx family around when 10.04 came out. My first thought was to suggest the 96.xx family but I see that didn't work.

To see what driver the card is using run this:
```
lspci -nnk | grep -iA2 vga
```
The output will have a line that says:
```
Kernel driver in use: xxxxx
```
where 'xxxx' is the driver.

Is is possible for you post the content of the X log? I refer to this file:
```
/var/log/Xorg.0.log
```
Please paste it here: [paste.ubuntu.com]("http://paste.ubuntu.com/") and post back the link to it.

There may be some clues there.
Regards.

---

### Post by Theredbaron1834 on 2013-05-17
lspci -nnk | grep -iA2 vga

```
 01:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV17M [GeForce4 420 Go 32M] [10de:0176] (rev a3)	Subsystem: Hewlett-Packard Company Device [103c:006d]
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

```[X.org log]("http://paste.ubuntu.com/5673518/")

I tried reading the log, but it is almost all unknown to me.

---

### Post by papibe on 2013-05-17
Thanks.

Here's what I can say from the X log:
[LIST]
[*]There is one version of the Nvidia driver yet installed.
[*]The Nvidia fails to load during the boot process.
[*]Nouveau is next in the effort, but also fails.
[*]Finally vesa tries to do its part, but somewhere in the process X crashes.
[/LIST]
This is what I would do:

Getting into text mode by either pressing Ctrl+Alt+F1, or booting into recovery mode.

Uninstall all nvidia drivers:
```
sudo apt-get remove nvidia-*
```
Restart your machine:
```
sudo reboot
```
Now that the Nvidia driver is out of the process, nouveau may be able to work. Confirm if it is loaded by posting the output of these 2 commands:
```
lspci -nnk | grep -iA2 vga

lsmod | grep -i nou
```
(Please note that what you posted earlier it is not exact the output of that lspci command).

If nouveau is not working, or you don't feel comfortable with the current situation, there's another think we can try. Since there's also this error on the log:
```
(EE) [drm] KMS not enabled
```
We can try to set grub to boot using the nomodeset option. To do that edit this file:
```
gksudo gedit /etc/defualt/grub
```
Look for a like that looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Add nomodeset to it so it looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```
Save the file, and reboot.

Repeat the steps to see if nouveau is loaded and working. Note that if you got nouveau working with the nomodeset option, chances of using an Nvidia driver are up again.

Let us know how it goes.
Regards.

---

### Post by Theredbaron1834 on 2013-05-18
So I did that, and now it is back to how it was on install, ie the laptop screen is useless. I have to have it hooked up to an ext monitor on boot to do any thing. Here is a pic of my screen...
[http://i.imgur.com/wV1DMh7.jpg](http://i.imgur.com/wV1DMh7.jpg)

lspci -nnk | grep -iA2 vga

```
 01:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV17M [GeForce4 420 Go 32M] [10de:0176] (rev a3)    Subsystem: Hewlett-Packard Company Device [103c:006d]
    Kernel driver in use: nouveau

```

lsmod | grep -i nou
```
 nouveau               834513  2 mxm_wmi                12893  1 nouveau
ttm                    71289  1 nouveau
drm_kms_helper         47545  1 nouveau
video                  18894  1 nouveau
drm                   228750  4 ttm,drm_kms_helper,nouveau
i2c_algo_bit           13197  1 nouveau
wmi                    18590  2 mxm_wmi,nouveau

```

Trying the nomodeset right now...


Edit:

And I just rebooted with nomodeset. Works perfectly now. Thank you so much. Everything is so much smoother now. :)
Even have XBMC working now. Thanks for that alone, tis my favorite video player. Still not quite up to playing youtube video's, but that is where xbmc and minitube come in handy.

---

