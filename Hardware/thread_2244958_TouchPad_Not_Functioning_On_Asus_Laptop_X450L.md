---
title: "TouchPad Not Functioning On Asus Laptop X450L"
date: 2014-09-20
forum: Hardware
---

### Post by wstay3 on 2014-09-20
I bought an Asus Laptop X450L recently with Wndows 8 pre-installed.
Later, I installed Ubuntu 14.04 LTS on a separate partition as a dual-boot with Windows 8.
The Ubuntu 14.04 I installed boots and login to the Desktop alright.
The problem is I cannot use the TouchPad (it is not functioning) on the Ubuntu system.
I did installed all the 10 or 20 things to do after installing Ubuntu 14.04.
So why is it that the TouchPad is not functioning on the Ubuntu system that I had successfully installed?
Can someone please help.

---

### Post by wstay3 on 2014-09-21
[SIZE=2]I bought an Asus Laptop X450L recently with Wndows 8 pre-installed.
Later, I installed Ubuntu 14.04 LTS on a separate partition as a dual-boot with Windows 8.
The Ubuntu 14.04 I installed boots and login to the Desktop alright.
The problem is the TouchPad on the Laptop is not working (functioning) when boot to the Ubuntu system.
I did installed all the 10 or 20 things to do after installing Ubuntu 14.04.
Why is it that the TouchPad is not working/functioning on the Ubuntu system that I had successfully installed?
Can someone please help.             [/SIZE]


                                                                                                                                                                                  [INDENT]                     .                 
[/INDENT]

---

### Post by varunendra on 2014-09-23
Please open a terminal (Ctrl-Alt-T) and show us the outputs of -
```
xinput
synclient
```
..and in the meanwhile, please take a look at this thread and try what is suggested there : [http://ubuntuforums.org/showthread.php?t=2241520](http://ubuntuforums.org/showthread.php?t=2241520)

---

### Post by QIII on 2014-09-23
Threads merged.  Please do not start duplicate threads.

If a post is not answered in a reasonable amount of time, please "bump" it to the top by adding a new post with the word "bump" rather than starting a new thread.

Thanks

---

### Post by wstay3 on 2014-09-26
> **varunendra said:**
> Please open a terminal (Ctrl-Alt-T) and show us the outputs of -
```
xinput
synclient
```


tayws@ASUS-LAPTOP:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SIGMACHIP Usb Mouse                         id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam                        id=10    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
tayws@ASUS-LAPTOP:~$ synclient

tayws@ASUS-LAPTOP:~$ synclient
Couldn't find synaptics properties. No synaptics driver loaded?
tayws@ASUS-LAPTOP:~$

---

### Post by wstay3 on 2014-09-27
tayws@ASUS-LAPTOP:~$ synclient
Couldn't find synaptics properties. No synaptics driver loaded?
tayws@ASUS-LAPTOP:~$ 				

My Synaptic Package Manager shows that I have 'xserver-xorg-input-synaptics
Synaptics TouchPad driver for X.Org server. Version 1.7.4-Oubuntu1 (trusty)' installed.
So how come the touchpad for my Laptop does not seem to do anything at all?

---

### Post by derek.rollend on 2014-11-05
I have the same issue on an ASUS Zenbook (UX303LN).  The basic functionality of the trackpad works, but I can't configure anything and synclient shows the same output as yours.  Have you made any progress on this?

---

### Post by wstay3 on 2014-11-08
> **derek.rollend said:**
> I have the same issue on an ASUS Zenbook (UX303LN).  The basic functionality of the trackpad works, but I can't configure anything and synclient shows the same output as yours.  Have you made any progress on this?

I installed Touch-Pad Indicator and also Synaptiks. Both of them didn't work. Touch-Pad Indicator although installed cannot be enabled. Synaptiks gives an error message as follow:

[HTML]
 No touchpad found  No touchpad was found in this system. If the system has a touchpad, please make sure that the synaptics driver is properly installed and configured. 
If your touchpad is not found, though the driver is installed and configured correctly, please compile detailed information about your touchpad hardware and report this issue to the issue tracker.
[/HTML]

I read that new coming updates to Ubuntu may solve this Touch-Pad problem on Asus LapTop. By the way, when you say 'trackpad' , are you refering to TouchPad or something else?

---

### Post by Pilot6 on 2014-11-08
We need to know which touchpad you have Elantech or Focaltech. With each the problem is solvable. Focaltech driver patch is basically ready and kernel images are available.
Please give output

dmesg | grep pnp

Here is the bugreport

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1342561](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1342561)

---

### Post by wstay3 on 2014-11-09
> **Pilot6 said:**
> We need to know which touchpad you have Elantech or Focaltech. With each the problem is solvable. Focaltech driver patch is basically ready and kernel images are available. Please give output dmesg | grep pnp   [HTML] tayws@ASUS-LAPTOP:~$  dmesg | grep pnp [    0.283398] pnp: PnP ACPI init [    0.283642] pnp 00:01: [dma 4] [    0.283664] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active) [    0.283686] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active) [    0.283814] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active) [    0.284053] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active) [    0.284286] pnp 00:09: Plug and Play ACPI device, IDs ETD0108 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active) [    0.284332] pnp 00:0a: Plug and Play ACPI device, IDs ATK3001 PNP030b (active) [    0.285547] pnp: PnP ACPI: found 14 devices tayws@ASUS-LAPTOP:~$  [/HTML]  I don't know which touchpad I am using, Elantech or Focaltech. Please advise on how can I figure it out.

---

### Post by Pilot6 on 2014-11-09
You have an Elantech touchpad. As I understood, it is already supported in newer kernels starting from 3.17 or even 3.16.
Just install 3.17 kernel form Ubuntu mainline ppa, and the touchpad will work.

---

### Post by Pilot6 on 2014-11-09
But those who has FLT101, 102, or 103 there, will need a custom kernel image until the kernel team applies the focaltech patch.
ASUS installs can install eithere of touchpads into same laptop model.

---

### Post by wstay3 on 2014-11-16
> **Pilot6 said:**
> You have an Elantech touchpad. As I understood, it is already supported in newer kernels starting from 3.17 or even 3.16.
Just install 3.17 kernel form Ubuntu mainline ppa, and the touchpad will work.

After installing Kernels 3.17, the touchpad works and function very well. Thanks.

---

### Post by tjqt06 on 2014-11-19
what is your current kernel version?

---

### Post by Pilot6 on 2014-11-19
> **tjqt06 said:**
> what is your current kernel version?

The whole point is which touchpad you have. If you give output of 

dmesg | grep pnp

i will tell you which kernel supports your touchpad.

The problem is that ASUS ships same laptop models with varios touchpads.

---

### Post by gtomorrow on 2014-11-19
> **Pilot6 said:**
> The whole point is which touchpad you have. If you give output of 

dmesg | grep pnp

i will tell you which kernel supports your touchpad.

The problem is that ASUS ships same laptop models with varios touchpads.

Hello, all. I'm having the same problem with the touchpad intermittently coming and going. I have an Acer Aspire One D250 netbook. I've searched the forums and searched the internet and have found these "solutions", none of which have permanently solved the touchpad problem. The truly frustrating thing is that it's never reproducible.

1) ```
sudo modprobe -r psmouse
sudo modprobe psmouse
xinput list
```
sometimes it works, sometimes it doesn't. My .bash_history is 95% just these commands! It was also suggested to do this (without the xinput command) from another TTY (ctrl-alt-F1) but again no permanent love.

2) ```
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```
no permanent solution here either.

3) xserver-xorg-input-synaptics is up to date (1.7.4) but i reinstalled anyway,just to make sure.

4) and according to this very thread, updating the kernel to 3.17 will solve the touchpad problem...but it didn't!

Here is the output of dmesg | grep pnp...
```
[    0.504969] pnp: PnP ACPI init
[    0.576454] pnp 00:00: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.2 BAR 13 [io  0x1000-0x2fff]
[    0.576910] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.577157] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.577416] pnp 00:03: Plug and Play ACPI device, IDs SYN1b1c SYN1b00 SYN0002 PNP0f13 (active)
[    0.577643] pnp: PnP ACPI: found 4 devices
[    2.062816] isapnp: Scanning for PnP cards...
[    2.373599] isapnp: No Plug & Play device found

```

The touchpad is working right now as I type. Very frustrating. I started with Ubuntu 10.10 and have upgraded up to 14.04 LTS. This problem happened very rarely but as of 12.04 LTS has worsened to a daily reoccurance.

Any help would be greatly appreciated. Thanks for reading this long post.

---

### Post by Pilot6 on 2014-11-19
Acer is quite a different story. Open a new thread.

---

### Post by gtomorrow on 2014-11-19
OOPS!

You're right about Acer/Asus! I'm always confusing the two. Nevertheless, are all touchpads THAT different?

---

### Post by gmoutso on 2015-04-01
> **wstay3 said:**
> [HTML] tayws@ASUS-LAPTOP:~$  dmesg | grep pnp [    0.283398] pnp: PnP ACPI init [    0.283642] pnp 00:01: [dma 4] [    0.283664] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active) [    0.283686] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active) [    0.283814] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active) [    0.284053] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active) [    0.284286] pnp 00:09: Plug and Play ACPI device, IDs ETD0108 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active) [    0.284332] pnp 00:0a: Plug and Play ACPI device, IDs ATK3001 PNP030b (active) [    0.285547] pnp: PnP ACPI: found 14 devices tayws@ASUS-LAPTOP:~$  [/HTML]  I don't know which touchpad I am using, Elantech or Focaltech. Please advise on how can I figure it out.

Description of bug is mouse does not work at all. Laptop Asus TP500LN, touchpad Elantech ETD0108 (same as yours). Dmesg gives "lost sync at byte 6" messages. Mouse does work with proto=imps parameter but no two-finger functionality. If this is the same with you, after sudo su try
echo 1 > /sys/devices/platform/i8042/serio4/reg_07
(or serioX?)
and see if it fixes the issue.

For at least asus TP500LN a kernel patch is under consideration
[https://bugzilla.kernel.org/show_bug.cgi?id=84491](https://bugzilla.kernel.org/show_bug.cgi?id=84491)
[https://www.marc.info/?t=142731893400011](https://www.marc.info/?t=142731893400011)
Many thanks to Ulrik de Bie!

Perhaps you can post on bugzilla that it affects your laptop too.

---

### Post by craig-bauer on 2015-05-07
I've been struggling with an Asus tp300la for a while now.  In my case, the touch pad is recognized as PS/2 mouse, and has basic functionality, but I have been unsuccessful at enabling actual touchpad functions.

```
 $ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Atmel                                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech Wheel Mouse                   id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; USB2.0 UVC HD Webcam                        id=9    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
```

No matter what I have tried, the touchpad is always recognized as PS/2 Logitch wheel mouse.  It appears I have an Elantech ETD0108 touchpad.


```
$ dmesg | grep pnp
[    0.189439] pnp: PnP ACPI init
[    0.189759] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.189920] pnp 00:06: Plug and Play ACPI device, IDs ETD0108 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.189953] pnp 00:07: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.190878] pnp: PnP ACPI: found 11 devices

```

I started with Ubuntu Gnome on this new laptop in January, quickly updated to a newer kernel to get wifi working, and have updated to kernel 3.18 and 4.0 in hopes of getting trackpad working too.  No luck.  I also tried the older elantech dkms driver, but before that I had thought I was struggling with a focaltech touch pad and tried Pilot6's focaltech dkms driver (and maybe some other things as well?)  I am really hoping to get this working, but worried there is not a solution yet, based on the discussion above surrounding similar Asus model TP500L.

Any help with further troubleshooting strategy greatly appreciated.

---

### Post by craig-bauer on 2015-05-07
And also, not sure if it is relevant, but in relation to the bug report above, my system does not contain /sys/devices/platform/i8042/serio4/.  Is this a clue?  (I have serio0 and serio1).

'locate reg_07' returns nothing.  Not sure if this path would be model-specific, though.  In any case, I cannot try the workaround suggested on the bug report linked above.  And, actually, now that I think of it, when I tried to install the elantech driver psmouse-elantech-x551c.tar.gz, I believe I received an error message that it could not locate something... perhaps it was this?  (dkms status did show the driver loaded after reboot, though...  I have since uninstalled.)

Thanks in advance for any help.

---

### Post by Pilot6 on 2015-05-07
It looks like this touchpad is not supported by any driver yet. You can try to write to a kernel mailing list.

---

### Post by craig-bauer on 2015-05-07
OK, thanks for the suggestion, and for all your help to others on this forum.

Any recommendation for kernel mailing list?  This would be my first time with such a route, but I'm a huge proponent of open source and community backed software, so certainly willing to try and provide input to get this hardware working for myself and others.

---

### Post by Pilot6 on 2015-05-07
This is a manual.
[https://wiki.ubuntu.com/Bugs/Upstream/kernel](https://wiki.ubuntu.com/Bugs/Upstream/kernel)

Address to send is

[email]linux-input@vger.kernel.org[/email]

---

### Post by craig-bauer on 2015-07-22
It has been fixed in kernel 4.1.3 (perhaps earlier--I upgraded from 4.0 where it was not working).  I upgraded tonight and multitouch scrolling just works.

---

### Post by Pilot6 on 2015-07-22
That's correct. It has been fixed for most of laptops in 4.0. Additional fixes for the rest appeared in 4.1.
Palm detection feature will appear in 4.2.

---

### Post by Pilot6 on 2015-07-22
For those who use kernel 3.19 I made a ppa that backports same driver.
It can be installed by

sudo add-apt-repository ppa:hanipouspilot/focaltech-dkms
sudo apt-get update
sudo apt-get install focaltech-dkms

This is only for Focaltech touchpads that report "FLT010x" in "dmesg | grep pnp"

---

### Post by Johanc on 2015-08-22
Hi 

I am having quite the similar problem on my Asus e403sa. The touchpad doesn't work at all under linux (ubuntu 15.04, but works fine under windows). It does not seem, that I have the Focaltech driver and not the Elantech either (am I wrong?). 

Here is my dmesg:
 ... dmesg | grep pnp
[    0.328948] pnp: PnP ACPI init
[    0.329080] pnp 00:00: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.329862] pnp 00:03: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.334094] pnp: PnP ACPI: found 6 devices
[    1.083331] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
(the boot option i8042.nopnp doesn't work)


And my xinput looks like this:
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; AT Translated Set 2 keyboard            	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; USB Camera                              	id=11	[slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                        	id=12	[slave  keyboard (3)]

My synclient output looks like this:
Couldn't find synaptics properties. No synaptics driver loaded?

Could anyone point me in the direction of solving the problem I would be very thankful.
If you need any extra input I am very willing to give it...

---

### Post by Pilot6 on 2015-08-23
This maybe an Elantech. But in new kernels something is broken in detection of some devices. This is a kernel bug.

---

### Post by Johanc on 2015-08-23
Thanks for the quick reply...  So at the moment I can just wait for a kernel update (I'm on 3.19 in Ubuntu 15.04)?

---

### Post by Pilot6 on 2015-08-23
Older kernels work with the default elantech driver. This is a regression.

---

### Post by Johanc on 2015-08-23
Sad for sure.. I must wait for a kernel update then?

---

### Post by Pilot6 on 2015-08-23
I do not know what broke Elantech touchpads in the latest kernels. Try kernel 3.13, if it show Elantech and works report a bug to launchpad. It needs bisection and fixing. Just waiting may be very long, if noone makes a fix.

---

### Post by Johanc on 2015-08-23
Thanks again... Can't I just install the Elantech-drivers instead? (I'm afraid the old kernels doesn't support my graphics card)

---

### Post by Pilot6 on 2015-08-23
The Elantech driver is in kernels. But in the latest kernels they changed something. Older revisions of Elantech touchpads are not detected for some reason.
There are no standalone Elantech linux drivers. Some people made psmouse source for older kernels including elantech module when it was not supported by kernels. But I suspect it won't build for the new ones. That needs some work done as I said before. If nobody does this work, that will be never fixed.

---

### Post by Johanc on 2015-08-23
Okay thanks... I will try to install the old kernel then, and see if it fixes the problem :-) ... have a nice day...

---

### Post by Johanc on 2015-08-23
Just to let the forum know. I tried booting the laptop with ubuntu 12.04 LTS, that is running on a 3.13 kernel without any luck on the touchpad. 

Unfortunately it seems the only solution is an external mouse...

---

### Post by leoverdolaga on 2015-09-24
> **wstay3 said:**
> tayws@ASUS-LAPTOP:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SIGMACHIP Usb Mouse                         id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam                        id=10    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
tayws@ASUS-LAPTOP:~$ synclient

tayws@ASUS-LAPTOP:~$ synclient
Couldn't find synaptics properties. No synaptics driver loaded?
tayws@ASUS-LAPTOP:~$

I have an ASUS X452EP 

leo@leo-X450EP:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Genius USB Optical Mouse                    id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam                        id=12    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=13    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]
leo@leo-X450EP:~$ synclient
Couldn't find synaptics properties. No synaptics driver loaded?

---

### Post by eu1985 on 2015-09-29
Hello everybody, I am in a bit of a mess. 

I have an ASUS UX303LA and after some tweaking (which I do not remember) I got the touchpad to work, with TouchEgg installed in the end.
I do not remember all the other steps. Thing is, the laptop got broken and the maintenance guys changed its motherboard. 
And of course the touchpad stopped working.

Can anybody help me?

As far as I understand, the touchpad came back to work as a 2 button mouse. Very bad for me.

This is the information I can gather around...

```
[    0.235016] pnp 00:06: Plug and Play ACPI device, IDs ETD0105 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
```

```
~$ xinput &#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech Wheel Mouse                   id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; USB2.0 UVC HD Webcam                        id=9    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

```

I am running Ubuntu 14.04LTS

```
$ uname -aLinux eu-UX303LA 3.16.0-28-generic #38 SMP Sun Dec 14 11:24:05 MSK 2014 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by jeremy9856 on 2015-10-03
> **Johanc said:**
> Just to let the forum know. I tried booting the laptop with ubuntu 12.04 LTS, that is running on a 3.13 kernel without any luck on the touchpad. 

Unfortunately it seems the only solution is an external mouse...
Hello Johanc,

I sent you a PM to ask you some questions about your Asus E403SA. I hope you can answer me ;)

If anyone else have it I will be pleased if you can answer these questions: 

Is there anything that doesn't work ?
Is the installation easy or did you have to do some workaround ? (on some computer with eMMC "SSD" the installation can be problematic)
Is the boot time fast ? (on some computer with eMMC "SSD" the boot can be very slow)

Thank you

---

### Post by jkkuha on 2016-03-09
> **jeremy9856 said:**
> Hello Johanc,

I sent you a PM to ask you some questions about your Asus E403SA. I hope you can answer me ;)

If anyone else have it I will be pleased if you can answer these questions: 

Is there anything that doesn't work ?
Is the installation easy or did you have to do some workaround ? (on some computer with eMMC "SSD" the installation can be problematic)
Is the boot time fast ? (on some computer with eMMC "SSD" the boot can be very slow)

Thank you
I have asus e403S

just hit lubuntu 15.10 in it. 

everythin that I have tested work's.. except touchpad. 

touchpad works just as .. mouse. I've tried to update my kernel to newer but then it starts to freeze as told here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1536038](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1536038)

at the moment I just use external mouse. 

I did try, for fun, the lts beta. there touchpad is knows as elantech touchpad and work's as it should.. for a moment. then it just freezes. 
the bug says one should upload to  [COLOR=#333333][FONT=monospace]Kernel 4.5 rc1 to make it work.. but I've been so long out of linux world that I wouldn need to find really simple walktrough to do it.. therefore.. I use external mouse. 

but this is really nice computer if you are not gamer.. fast, awesome batterylife.. all is fine.. with lubuntu I mean. with win10 it was slow.. and I got the new kind of bluescreen all the time. so.. I stick with lubuntu and wait until I find a way to update my kernel.[/FONT][/COLOR]

---

