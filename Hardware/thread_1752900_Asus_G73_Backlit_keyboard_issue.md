---
title: "Asus G73 Backlit keyboard issue"
date: 2011-05-08
forum: Hardware
---

### Post by Byron79 on 2011-05-08
Hello I am running Ubuntu 11.04 and I absolutely love the Unity UI! anyway I have an Asus G73sw (new sandy bridge) and I am wondering how to get my backlit keyboard working or is it just not possible. Thanks in advance

---

### Post by lwarranty on 2011-05-09
> **Byron79 said:**
> Hello I am running Ubuntu 11.04 and I absolutely love the Unity UI! anyway I have an Asus G73sw (new sandy bridge) and I am wondering how to get my backlit keyboard working or is it just not possible. Thanks in advance

[http://scottsautorepair.net/microsoft.sucks/G73SW.keyboard.lights.html](http://scottsautorepair.net/microsoft.sucks/G73SW.keyboard.lights.html)

have a couple of *.deb packages with instructions or compile your own with instructions, based on kernel.org 2.6.39-rc6...

This is for G73SW - with asus-wmi patch compiled into *.deb kernel and header packages...

including info on suspend, ssd setup and trim options, gnome 3, etc...

[SIZE=3]**This is for G73SW Ubuntu 11.04 and others, wmi acpi keyboard backlights, function keys, special keys, whatever you wish to call it! These kernel / headers were compiled from the latest kernel.org source with asus-nb-wmi patch applied.**[/SIZE]
 

 [SIZE=3]Links to my *.deb kernel image and modules for G73SW using Ubuntu Natty, running Unity, Gnome 3, LXDE, with Nvidia proprietary OR native nouveau drivers.[/SIZE]
 

 [[SIZE=3]http://scottsautorepair.net/linux-image-2.6.39-rc6_2.6.39-rc6-10.00.Custom_amd64.deb[/SIZE]]("http://scottsautorepair.net/linux-image-2.6.39-rc6_2.6.39-rc6-10.00.Custom_amd64.deb")
 [[SIZE=3]http://scottsautorepair.net/linux-headers-2.6.39-rc6_2.6.39-rc6-10.00.Custom_amd64.deb[/SIZE]]("http://scottsautorepair.net/linux-headers-2.6.39-rc6_2.6.39-rc6-10.00.Custom_amd64.deb")
 

 [SIZE=3]1. Download them to a folder of your choosing.[/SIZE]
 

 [SIZE=3]2. Terminal method &#8211; open terminal, if using Debian based, you will need root privileges, if you don't know sudo and/or just want to run as root, in a terminal type &#8220;sudo su&#8221;, then enter your password, then type &#8220;passwd&#8221; and enter a new root password - then you can su to root at anytime![/SIZE]
 

 [SIZE=3]3. cd /where-ever-you-downloaded-them OR use software center....[/SIZE]
 

 [SIZE=3]4. Type &#8220;sudo dpkg -i lin*39*.deb&#8221; without quotes.[/SIZE]
 

 [SIZE=3]5. Sometimes dual booting and/or function keys can get out of sync, put this in your /etc/rc.local &#8211; just before last line:[/SIZE]
 [SIZE=3]echo 0x00050021 > /sys/kernel/debug/asus-nb-wmi/dev_id[/SIZE]
 [SIZE=3]echo 0x82 > /sys/kernel/debug/asus-nb-wmi/ctrl_param[/SIZE]
 [SIZE=3]cat /sys/kernel/debug/asus-nb-wmi/devs[/SIZE]
 

 [SIZE=3]6. Reboot and you should be good to go![/SIZE]
 

 [SIZE=3]7. If using Nvidia proprietary drivers, to enable screen dimming, put this line in your /etc/X11/xorg.conf file just below &#8220;DPMS&#8221; - the entry for your notebook screen if your using dual monitors.[/SIZE]
 [SIZE=3]Option "RegistryDwords" "EnableBrightnessControl=1"[/SIZE]
 

 [SIZE=3]8. Reboot and you should be good to go![/SIZE]

---

### Post by deere on 2011-05-10
Hello,

I'm thinking about buying an Asus G73SW laptop.
Can you confirm that it is working well with Ubuntu?
I don't care too much about backlit keyboard.
What is most important for me:
- Nvidia with proprietary driver and HDMI with dual screen works
- Hibernation works
- Sound, microphone, and other things you would normally expect to work on an everyday laptop work

Are there problems with any other things besides backlit keyboard?

Thanks very much.

---

### Post by lwarranty on 2011-05-10
> **deere said:**
> Hello,

I'm thinking about buying an Asus G73SW laptop.
Can you confirm that it is working well with Ubuntu?
I don't care too much about backlit keyboard.
What is most important for me:
- Nvidia with proprietary driver and HDMI with dual screen works
- Hibernation works
- Sound, microphone, and other things you would normally expect to work on an everyday laptop work

Are there problems with any other things besides backlit keyboard?

Thanks very much.

These are some of my observations working with Ubuntu, I have three SW's with multiple distro's, Fedora, OpenSuse, Debian, Mint, etc - on each.  These items may have changed in the latest builds, as I usually deviate immediately and start hacking - but out of the box, I was surprised. 

NVidia proprietary drivers scream (Ubuntu will notify you additional drivers are available and installation requires you clicking "activate") works great with dual monitors, setup as twin view.  No good with Unity trying separate screens, but choosing Ubuntu "standard" or some such works great IF you wish separate vs twin view.
Sound works through HDMI - but SW's sound is awesome as it is.
Suspend works with a few minor configs.
Sound, Microphone, Camera, working great.  (Skype friendly)
SD/MMC card reader, still working on that one...
Wireless and LAN working.
Touchpad works great, scroll n all.
Special function keys are a work in progress, most important one's work and a few work-a-rounds get you more.

Otherwise, it won't take long for the coders to catch up on little "gotcha's"...

---

### Post by lwarranty on 2011-05-10
2.6.39-rc7 compiled and posted - keep in mind, these CAN break your system, keep a few previous linux-image-xx.xx.xx installed so you can reboot into previous versions.  If you wish to remove these or older kernels on your system, open Synaptic Package Manager and type linux-image in your search window, right click and choose "mark for complete removal"...

No warranty expressed or implied - these are latest kernels downloaded from kernel.org with asus keyboard backlight patch compiled in.

---

### Post by deere on 2011-05-12
I appreciate your help. Thank you.
> **lwarranty said:**
> .

---

### Post by jeffberyl on 2011-05-18
[SIZE=3]I attempted to implement the procedures on my G73/Ubuntu11/(Windows 7) but in step 4 I obtained:

dpkg: error processing linux-headers-2.6.39-rc6_2.6.39-rc6-10.00.Custom_amd64.deb (--install):
 package architecture (amd64) does not match system (i386) dpkg: error processing linux-image-2.6.39-rc6_2.6.39-rc6-10.00.Custom_amd64.deb (--install):
 package architecture (amd64) does not match system (i386)
Errors were encountered while processing:
 linux-headers-2.6.39-rc6_2.6.39-rc6-10.00.Custom_amd64.deb
 linux-image-2.6.39-rc6_2.6.39-rc6-10.00.Custom_amd64.deb [/SIZE]

[SIZE=3]What extra do I need to do earlier?[/SIZE]

---

### Post by Zhukov on 2011-05-18
The debs are for 64 bits systems, you have installed a 32 bit one.

So two choices, either compile for 32 or reinstall the system for 64.

---

### Post by 2briancox on 2011-08-26
This works great to fix the keyboard issues.

And it it breaks my ability to attach my Microsoft Bluetooth Notebook Mouse 5000.

How do I fix both?

I have to boot into the old kernel to get my mouse to work again.

---

### Post by s1hr on 2011-08-26
> **2briancox said:**
> This works great to fix the keyboard issues.

And it it breaks my ability to attach my Microsoft Bluetooth Notebook Mouse 5000.

How do I fix both?

I have to boot into the old kernel to get my mouse to work again.

do you wanna say that Bluetooth not work at all? or you can connect to some other Bluetooth device?

---

### Post by 2briancox on 2011-08-26
Well, the bluetooth dongle I plug in is recognized.  But my Mouse is the only Bluetooth device I can connect to test it at the moment.

The mouse gets recognized but it always immediately fails on any attempt to pair the device.

---

### Post by 2briancox on 2011-08-29
I guess I should have left more information.

I am running Pinguy 11.04 (Ubuntu 11.04) and it came with 2.6.38-9 which runs my bluetooth mouse just fine.  But when I upgraded with this specially compiled ASUS keyboard kernel it fails.  I thought perhaps I could try my hand at compiling a 2.6.38 kernel with this ASUS keyboard driver as described on the site listed, but I get an error when I try to patch.  And I don't know how to continue.

Is there a way to fix the bluetooth issue in the 2.6.39 kernel?

---

### Post by enzymaticboom on 2011-09-13
I got Ubuntu 11.04 to work on my new Asus G73SW but like others the key board backlight is not working and all function keys except for the screen backlight keys (fn+F4/F5) do not work, also the three real buttons at the top of the keyboard do not work.

So I tried the .deb files and procedure above and it ruined my resolution and seemed to go into a safe mode like setting, and the backlight still did not work.  Perhaps this is having some effect on my nVidia card?  I re-reinstalled 11.04 so that I could get my resolution back (I am sure there was a more simple and less time consuming way, but I am a old-noob).  I really do not want to reinstall again, but I would really like the function keys to work and the backlight, but I need the resolution, part of the reason why I bought a new laptop.

Still kinda new at the whole linux thing... (first post to ubuntu forums)

---

### Post by 2briancox on 2011-09-13
I also had to remove then reinstall the nVidia driver to get the graphics better.

But if you're having difficulty with the function keys still not functioning then something seems off with the install of the new kernel.  

Maybe try the kernel install first?  Did you get the most recent version of the kernel image and header?

---

### Post by force13 on 2011-09-17
whats up, 
ok first I have to say nice work 

but im having some issues:
vmware 7.14 and 3.14 wont work in the kernal rc6 or rc7
 the mouse lock does not work (fn +   f9)
and lastly for some odd reason the wireless card wont auto connect to the internet
this is when first booting or resuming from  a suspend

using ubuntu 11.04 on asus g74sx everything else works flawless

the only one that bothers me is the wireless one I know the vmware is not your fault and not your problem to fix

---

### Post by force13 on 2011-09-17
um yeah sorry for the double post but 

i figured out what was wrong with the wireless (nothing to do with the kernal i might add) but i did find another issue

my resolution was stuck on 1024 x 768 when it should be at 1600 x 900

---

### Post by alain.roger on 2011-11-08
I'm very interested in this solution however i run Ubuntu 11.10 so kernel is v3.0.0-12-generic and the solution here is based on version 2.6.39-rc6_2.6.39-rc6-10.00.

is there an updated version for ubuntu 11.10 ?
thx.

---

### Post by Bocete on 2012-02-02
+1 on this. Need my keyboard backlight for G74 (but would try a G73 fix) for 3.0.0.14, running Kubuntu 11.10

EDIT:

I found a solution. Run this:
```
sudo su
echo 0x00050021 > /sys/kernel/debug/asus-nb-wmi/dev_id
echo 0x82 > /sys/kernel/debug/asus-nb-wmi/ctrl_param
cat /sys/kernel/debug/asus-nb-wmi/devs
```And reboot. Backlight will be on, though control buttons for it do not work. I don't mind having the backlight on all the time.

Much more information (with some useful links dead, sadly!)
[URL="http://forum.notebookreview.com/asus-gaming-notebook-forum/553474-g73-asus-wmi-linux-driver-i-need-your-help-6.html#post7470992"]
http://forum.notebookreview.com/asus-gaming-notebook-forum/553474-g73-asus-wmi-linux-driver-i-need-your-help-6.html#post7470992[/URL]

- Bo

---

### Post by lalitpur on 2012-03-09
[U][FONT=Arial]Bocete's solution worked for me.   Cheers![/FONT]
[/U]

---

