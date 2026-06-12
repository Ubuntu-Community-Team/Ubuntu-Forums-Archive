---
title: "Does diNovo Edge Work?"
date: 2006-11-08
forum: Hardware &amp; Laptops
---

### Post by marco999 on 2006-11-08
Hello,

Can someone please tell me if the diNovo Edge from Ligtech works in Linux or not?

I would like to know if it works in Edgy.

Marco

---

### Post by redman5087 on 2006-11-25
I want to know too.

---

### Post by pacha on 2006-11-26
Just installed Edgy with diNovo Desktop. Keyboard works fine but the MX Laser mouse is not working at all... it is not detected.

---

### Post by pacha on 2006-11-27
Ok, the mouse works now. Every time i start the computer i have to change the bluetooth receiver from one usb port to another in the login screen... then the mouse is detected... weird. I forgot to mention that the mouse and keyboard work with minimal functionality... special keys and buttons are mostly dead

---

### Post by gerick on 2006-12-01
Does the touchpad work?

---

### Post by Fliberty on 2006-12-18
The DiNovo Desktop and DiNovo Edge are two completely different things. Does anyone know if there is compatibility with the DiNovo Edge? I really like this keyboard.

---

### Post by gerick on 2006-12-19
> **gerick said:**
> Does the touchpad work?

This is the best answer I could find:
[http://glyf.livejournal.com/62855.html]("http://glyf.livejournal.com/62855.html").

Hopefully I will be getting one for Christmas, then I can answer for those here myself.

---

### Post by redu on 2006-12-21
> **pacha said:**
> Ok, the mouse works now. Every time i start the computer i have to change the bluetooth receiver from one usb port to another in the login screen... then the mouse is detected... weird. I forgot to mention that the mouse and keyboard work with minimal functionality... special keys and buttons are mostly dead
Pacha,
in my Ubuntu login screen, there is no way to change receiver usb port? Please let me learn better.

Redu

---

### Post by gerick on 2006-12-27
> **Fliberty said:**
> The DiNovo Desktop and DiNovo Edge are two completely different things. Does anyone know if there is compatibility with the DiNovo Edge? I really like this keyboard.

Have only used it for 20 minutes so far.  
Out of the box, running under Kubuntu 6.10.
[LIST]
[*]typing keys work
[*]volume slider works
[*]was able to mute sound
[*]unmute did not work
[*]mousepad does not work
[*]doesn't look like special function keys work
[/LIST]

This is just plugging in as is.  I haven't tried to set anything up yet.

Did not have to do anything with bluetooth, just pluged the receiver dongle into a usb and booted up.

---

### Post by ten on 2007-01-01
[COLOR="Red"]**[SIZE="4"]UPDATE:[/SIZE]**[/COLOR]

> Mouse device shows multiple reports with the same usage, which makes
hid-input.c remap those instances of this usage to different events. As a
result, the actual GenericDesktop.X and .Y usages end up mapped to .Z and .RX
events, which prevents the mouse from working

Link to patch:
[http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg17777.html](http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg17777.html)

---

### Post by gerick on 2007-01-02
> **ten said:**
> [COLOR="Red"]**[SIZE="4"]UPDATE:[/SIZE]**[/COLOR]



Link to patch:
[http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg17777.html](http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg17777.html)

Does this mean that support will be native in some kernel update, 
or do we have to apply a patch to source code and recompile?

---

### Post by ShiftyPowers on 2007-01-04
this would be huge, so is there a step by step way that an experienced user of linux can show us on how to get this to work?  I'm seriously thinking of one of these for my HTPC

---

### Post by benlen on 2007-01-16
Anybody got this to work? didn't understand how to use the patch

---

### Post by ten on 2007-01-18
It's patched in the latest RC kernel. (also the same used in herd2)

Will try to verify that it work on herd2+ this weekend

---

### Post by gerick on 2007-01-19
> **ten said:**
> It's patched in the latest RC kernel. (also the same used in herd2)

Will try to verify that it work on herd2+ this weekend

Thanks.  
So, when we upgrade from Edgy 6.10 to Feisty 7.xx, the touch pad should work?

---

### Post by ten on 2007-01-23
[https://launchpad.net/bugs/81090](https://launchpad.net/bugs/81090)

please add to this if you can

---

### Post by ten on 2007-02-02
And we have liftoff, Kubuntu Herd 3 is confirmed, Dinovo Edge works. Mousepad AND keys. (Not tried the FN keys yet)

---

### Post by LadFromWales85 on 2007-02-23
So, the DiNovo Edge now works with the stock Feisty kernel (currently 2.6.20-8)?
Is it as simple as plug it in, scan for the devices and add them to the bt conf?  Can the same BT dongle be used with other devices at the same time, or will it only function with the keyboard?

I have a DiNovo Desktop Laser at the moment, which I've never been able to get working (I've disabled bluetooth on the system so it falls back to native) and would be willing to get the Edge and MX revolution of they work flawlessly under Linux now.

---

### Post by orengolan on 2007-04-20
1. I want to buy Dinovo Edge wireless keyboard and wonder if it will work with Ubuntu 7.04.
Does Anyone using it and can give me some tips/feedback before I spend $200 on this beautiful keyboard?

2. If I buy a Blue Tooth mouse, will it communicate via the Dinovo receiver or should i use another USB receiver for the mouse?

3. does MX revolution works with Ubuntu?

thanks

---

### Post by orengolan on 2007-04-29
I bought the Dinovo and it works out of the box!

one question - there is a CD with an app (SetPoint 3.1) that customizes the keyboard.
It's for Windows.  how can Intall it?

---

### Post by wonko on 2007-05-02
diNovo Edge works fine with me too, (on ubuntu feisty) but some shift/control/alt button "hangs" when I first boot gnome (did so on edgy too)... I usually solve this by just hammering a little on all of them, but it is a bit irritating. I don't think I had this problem when I tried KDE for a couple of days before switching back to gnome, and I'm sure I don't have it in windows...
Anyone experiencing something similar?

---

### Post by furunculus on 2007-05-17
is the touchdisk fully functional now?

cheers

---

### Post by orengolan on 2007-05-17
does anyone know how to install the additional app on Ubuntu?

---

### Post by Succendo on 2007-07-03
Works out of the box for me (just hit the box and hit connect). I love the feel of the keyboard... it's sturdy but comfortable (and GORGEOUS). In Ubuntu 7.04, the touchpad, scrolling, volume slider, all the mouse buttons, and all keys work out of the box. The function keys do NOT work (except FN+F3 starts Evolution), including media keys, which is a bummer. I'm sure there's a workaround, but I haven't done any tinkering yet.

I'd love to configure the zoom keys to interact with Expo in my Compiz Fusion install, so if anyone has any info on how to customize this, let me know! But for most functions, this is a go right out of the box in Feisty.

---

### Post by cdinoz on 2007-07-14
So you are giving this product a Thumbs Up for functionality on Feisty? :)

How are you going with the touchpad / mouse on the Edge. Good enough for a HTPC?

---

### Post by modulok on 2007-07-24
yes, works well plug and play

some of the special functions work (noted previously) and the touchpad works.  would be nice to see logitech make a linux app for customization and battery status.

---

### Post by gcwjr85 on 2007-10-18
DINOVO EDGE WORKS WITH UBUNTU LINUX!!!  IT WASN'T WORKING, THEN IT WORKED!  I INSTALLED TURBOPRINT AND ADDED THE HP DESKJET AS A PRINTER (NO SPECIFIC MODEL JUST THE DESKJET) AND THEN I INSTALLED HPLIB (A UTILITY TO MAKE HP PRINTERS WORK ON LINUX) AND CHOSE MANUAL INSTALL AND CHOSE YES TO INSTALL EVERY "MISSING REQUIRED DEPENDANCY"; IT WAS DURRING THAT PROCESS THAT I REALIZED THAT THE LIGHT RING AROUND THE TOUCHDISC STARTED GLOWING!  IT WORKS NOW!  I DON'T KNOW WHAT I DID BUT THE DINOVO EDGE WORKS WITH UBUNTU LINUX!  I could take the time to figure out which specific step made it work but I'm a working father of 2 so you single guys figure it out!

---

### Post by digital_exhaust on 2007-10-18
Um...wow.... 

I'm a father of three, and all is fine here on Feisty and Fedora 7... works great.

And seriously, I can understand some excitement over your board working, but really... no need for yelling... we are a peaceful people here:)

---

### Post by skyhi on 2007-10-22
Dinovo Edge worked perfectly in Feisty. Did a clean install of Gutsy and now having problems.

Takes several keypresses to get the keyboard alive but after that it works as it used to. Dmesg:
[   17.668000] Bluetooth: RFCOMM socket layer initialized
[   17.668000] Bluetooth: RFCOMM TTY layer initialized
[   17.668000] Bluetooth: RFCOMM ver 1.8
[   17.896000] usb 1-4.1: new full speed USB device using ohci_hcd and address 7
[   18.020000] usb 1-4.1: configuration #1 chosen from 1 choice
[   18.072000] Bluetooth: HCI USB driver ver 2.9
[   18.076000] usbcore: registered new interface driver hci_usb
[   18.500000] Clocksource tsc unstable (delta = -112988173 ns)
[ 1484.528000] usb 1-4: USB disconnect, address 3
[ 1484.528000] usb 1-4.1: USB disconnect, address 7
[ 1484.792000] usb 1-4.2: USB disconnect, address 5
[ 1484.792000] usb 1-4.3: USB disconnect, address 6
[ 1485.464000] usb 1-4: new full speed USB device using ohci_hcd and address 8
[ 1485.684000] usb 1-4: configuration #1 chosen from 1 choice
[ 1485.688000] hub 1-4:1.0: USB hub found
[ 1485.688000] hub 1-4:1.0: 3 ports detected
[ 1486.020000] usb 1-4.2: new full speed USB device using ohci_hcd and address 9
[ 1486.144000] usb 1-4.2: configuration #1 chosen from 1 choice
[ 1486.160000] input: Logitech Logitech BT Mini-Receiver as /class/input/input10
[ 1486.160000] input: USB HID v1.11 Keyboard [Logitech Logitech BT
Mini-Receiver] on usb-0000:00:02.0-4.2
[ 1486.372000] usb 1-4.3: new full speed USB device using ohci_hcd and
address 10
[ 1486.496000] usb 1-4.3: configuration #1 chosen from 1 choice
[ 1486.516000] input: Logitech Logitech BT Mini-Receiver as /class/input/input11
[ 1486.516000] input,hiddev96: USB HID v1.11 Mouse [Logitech Logitech
BT Mini-Receiver] on usb-0000:00:02.0-4.3
[ 1576.880000] usb 4-4: USB disconnect, address 2
[ 1576.880000] unregister_netdev()
[ 1581.164000] usb 4-4: new high speed USB device using ehci_hcd and address 3
[ 1581.432000] usb 4-4: configuration #1 chosen from 1 choice
[ 1581.432000] idVendor = 0x7d1, idProduct = 0x3c03

---

### Post by skyhi on 2007-10-25
more dmesg:

```
[   22.000000] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
[   22.000000]  [<f8937628>] hid_output_report+0x2a8/0x320 [hid]
[   22.000000]  [<f89404a8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   22.000000]  [<c0131470>] process_timeout+0x0/0x10
[   22.000000]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[   22.000000]  [<c013bead>] finish_wait+0x2d/0x70
[   22.000000]  [<f894076b>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   22.000000]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[   22.000000]  [<f8942ea6>] hiddev_ioctl+0x446/0xb50 [usbhid]
[   22.000000]  [<c01610d1>] filemap_nopage+0x181/0x340
[   22.000000]  [<f88896ff>] usb_open+0x8f/0xf0 [usbcore]
[   22.000000]  [<c011fc6e>] kunmap_atomic+0x5e/0xa0
[   22.000000]  [<c011fc7a>] kunmap_atomic+0x6a/0xa0
[   22.000000]  [<c016ce18>] __handle_mm_fault+0x288/0xb00
[   22.000000]  [<f8942a60>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   22.000000]  [<c018ca74>] do_ioctl+0x84/0xc0
[   22.000000]  [<c02f5d99>] do_page_fault+0x389/0x690
[   22.000000]  [<f8942a60>] hiddev_ioctl+0x0/0xb50 [usbhid]
[   22.000000]  [<c018cb0c>] vfs_ioctl+0x5c/0x290
[   22.000000]  [<c018cdb2>] sys_ioctl+0x72/0x90
[   22.000000]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[   22.000000]  =======================
[   22.000000] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
[   22.000000]  [<f8937628>] hid_output_report+0x2a8/0x320 [hid]
[   22.000000]  [<f89404a8>] hid_submit_ctrl+0x58/0x200 [usbhid]
[   22.000000]  [<c0131470>] process_timeout+0x0/0x10
[   22.000000]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[   22.000000]  [<c013bead>] finish_wait+0x2d/0x70
[   22.000000]  [<f894076b>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
[   22.000000]  [<c013
```

and it keeps going on...

---

### Post by tahiti on 2007-11-03
hello, i have the same driver warning with a gutsy clean install,
the keyboard don't work at the login screen, just have to switch it off/on.
can't use zoom keys and Fn + A,B,C or D.
anyway this is better than my old ubuntu edgy without the touchpad ;)
Regards.
> 
 [   47.269919] WARNING: at build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/hid-core.c:777 implement()
 [   47.269942]  [<f89d6628>] hid_output_report+0x2a8/0x320 [hid]
 [   47.270005]  [<f8a114a8>] hid_submit_ctrl+0x58/0x200 [usbhid]
 [   47.270012]  [process_timeout+0/16] process_timeout+0x0/0x10
 [   47.270022]  [schedule_timeout+71/208] schedule_timeout+0x47/0xd0
 [   47.270034]  [finish_wait+45/112] finish_wait+0x2d/0x70
 [   47.270049]  [<f8a1176b>] usbhid_submit_report+0x11b/0x1b0 [usbhid]
 [   47.270056]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50
 [   47.270076]  [<f8a13ea6>] hiddev_ioctl+0x446/0xb50 [usbhid]
 [   47.270082]  [<f8a1198f>] usbhid_open+0xf/0x20 [usbhid]
 [   47.270104]  [<f88806ff>] usb_open+0x8f/0xf0 [usbcore]
 [   47.270126]  [<f8880670>] usb_open+0x0/0xf0 [usbcore]
 [   47.270146]  [chrdev_open+173/400] chrdev_open+0xad/0x190
 [   47.270162]  [chrdev_open+0/400] chrdev_open+0x0/0x190
 [   47.270165]  [__dentry_open+351/448] __dentry_open+0x15f/0x1c0
 [   47.270207]  [fasync_helper+38/224] fasync_helper+0x26/0xe0
 [   47.270222]  [<f8a13a60>] hiddev_ioctl+0x0/0xb50 [usbhid]
 [   47.270234]  [do_ioctl+132/192] do_ioctl+0x84/0xc0
 [   47.270245]  [<f8a13a60>] hiddev_ioctl+0x0/0xb50 [usbhid]
 [   47.270260]  [vfs_ioctl+92/656] vfs_ioctl+0x5c/0x290
 [   47.270277]  [sys_ioctl+114/144] sys_ioctl+0x72/0x90
 [   47.270292]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9


---

### Post by orengolan on 2007-11-03
after upgrading to 7.10 I have the same problem - 
on the username screen my dinovo doesn't respond.
I have to turn it off and on.

can anyone suggest a solution?

---

### Post by BatPenguin on 2007-11-03
Hello everybody. I'm using this keyboard on Gutsy and even though it works fine (both keyboard and mousepad) I'm having problems with the volume control. It seems to control the microphone level, not the system sound level. Anybody had this problem? How can I change what it controls?

Also, in the login screen the keyboard and mousepad are unresponsive for a while but after wiggling the mousepad for 10 seconds or so, it seems to "wake up" and start working.

Anyway, I'd really appreciate help on getting the volume control working correctly. Thanks!

---

### Post by Dennishansendeh on 2007-11-03
I have the DiNovo Edge keyboard and is running Gutsy Gibbon.. It works flawlessly besides som of the Fn specialkeys.
The touchpad also works neat and nice

---

### Post by PlantHead on 2007-11-13
Also having problems with my diNovo.
Doesn't work at login until I switch it on and off, and even then during normal operation its stops and I have to switch it off and on again.
Worked flawlessly in Feisty.

---

### Post by AJerman on 2007-11-16
Hmm... okay, so I guess I'm not the only one with the on off issue. I was pleased with the keyboard at first since the included BT dongle allows it to work without OS sync. That made it the best keyboard I've ever used to get Linux installed since I had the touchpad. Once I got everything setup I synced up my MS BT mouse as well and was all set. Now if we could only figure out what's going on with that sync at the login screen we'd be perfect.

---

### Post by tahiti on 2007-11-16
Hello,
I just found a temporary solution for the gdm login screen keyboard response problem:
no more driver warning
> 
I'm having this problem too. Running fully updated Gutsy Beta.
My Logitech Dinovo Edge doesn't work after a reboot until I turn the keyboard off and then on again, or remove and plug in the usb dongle.
**Disabling bluetooth under System > Administration > Services is the easiest workaround for me.**

source: [https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/148290](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/148290)

Does the Dinovo edge keyboard can work as bluetooth HUB under linux?

there is a workaround proposed by logitech for windowsXP in the last comment of this article:
 (google translation)
[http://64.233.179.104/translate_c?hl=fr&langpair=fr%7Cen&u=http://www.clubic.com/actualite-67499-logitech-dinovo-edge-bluetooth.html](http://64.233.179.104/translate_c?hl=fr&langpair=fr%7Cen&u=http://www.clubic.com/actualite-67499-logitech-dinovo-edge-bluetooth.html)

Regards.

---

### Post by riggits on 2007-11-17
Turning off Bluetooth or uninstalling *bluez will fix the problem for Edge and the regular DiNovo BT keyboard & mouse.
It looks like Gutsy does not support BT keyboards without extra work.
I think the real problem is bluez??

---

### Post by tahiti on 2007-11-24
Hi everyone
Up, for this question: anyone knows if the Dinovo edge keyboard can work as bluetooth HUB under linux?
cheers.

---

### Post by rommel74 on 2007-12-18
> **tahiti said:**
> Hi everyone
Up, for this question: anyone knows if the Dinovo edge keyboard can work as bluetooth HUB under linux?
cheers.

no, it doesn't it is just an embedded BT device only used for keyboard and mouse, does not have any profiles which is a shame

I did manage to connect a Microsoft Laser Mouse 8000 to it but the scrollwheel is not functioning

see this[ link]("http://logitech-en-ap.custhelp.com/cgi-bin/logitech_en_ap.cfg/php/enduser/std_adp.php?p_faqid=5635&p_created=1161965039&p_sid=pXeg*uTi&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MTA0LDEwNCZwX3Byb2RzPSZwX2NhdHM9JnBfcHY9JnBfY3Y9JnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9ZGlub3ZvIGVkZ2U*&p_li=&p_topview=1") for more info

I can also confirm the same problem with Gutsy 64bit however I do not have to turn off the keyboard,    hammer away at the keyboard or touchpad and it starts working after about 15s

---

### Post by Hans Kurppa on 2007-12-29
Best keyboard I've ever had, even though it's not fully working... :KS

Buttons not working; zoom buttons, VoIP, and the four programmable ones. Kernel's HID driver seems to silently ignore those buttons. [Possible fix is here](http://bugzilla.kernel.org/attachment.cgi?id=10848&action=edit), haven't tested it yet though.

Also the volume slider didn't work because it kept changing the Master-control (which doesn't have any effect, even when muted). On my PC the PCM controls the volume.

To workaround the volume problem, I installed [keyTouch](http://keytouch.sf.net), selected a Logitech diNovo keyboard and changed the Mixer Channel in Preferences tab to PCM. Also I had to stop KDE's KMilo service (System Settings - Advanced - Services... ), so that keyTouch could capture the volume control buttons.

*keyTouch is also in universe-repository*

keyTouch comes with a *Logitech diNovo Cordless Desktop for Notebooks (Y-RW42 Y-RX43) (USB)* keyboard profile, which works just fine with Edge. Also, I've done a profile for diNovo Edge which is pretty much the same as the diNovo for notebooks, but it includes the missing buttons (altough they don't work because of the HID driver, and the default actions are just dummy actions so that keyTouch accepts the profile :-( ).

To use the diNovo Edge profile, download the attached file and import it in keyTouch Keyboard selection window.

---

### Post by Hans Kurppa on 2007-12-29
*Had an error in the above attachment, Media button wasn't working. Fixed version below.*

---

### Post by .lobo on 2008-01-24
Ditto - DiNovo Edge on Ubuntu 7.10:

What works:
Keyboard
Volume Contol
Mute Button

What doesn't work:
4 function buttons on the left (3 zoom & sys sleep)
Windows media-center button on the top right

Sweet keyboard, great action, obscene range (25-30m :o), easy on the eye too.

(P.S. Also works flawlessly on my MacBook Pro - I leave the dongle plugged into the Linux box and re-pair to switch between the two machines).

---

### Post by Bishops_Pappy on 2008-02-03
Has anyone had success with the dead buttons so far (3 zoom buttons, phone button and the a-d buttons)?

---

### Post by 23meg on 2008-04-29
> **Bishops_Pappy said:**
> Has anyone had success with the dead buttons so far (3 zoom buttons, phone button and the a-d buttons)?

No, still not working in Hardy (final). 

I'd like to increase the touchpad's sensitivity; (how) is this possible? Since Hardy's xorg.conf has no entry for touchpads, I'm not sure which device it sends on and how to tweak it.

---

### Post by knx2 on 2008-05-07
Just bought this keyboard and waiting for it in the mail.  Hope I can get everything to work ;)

---

### Post by laluz on 2008-05-11
Regarding the touchpad sensitivity - in the System settings -> Keyboard and Mouse -> Mouse -> Advanced
set Pointer Aceleration 3,0
Pointer Threshold 4 pixels
Drag start time 500 msec
Drag start distance 1 pixel
Mouse Wheel scrolls by 12 lines 
and afther that hopefully you will feel the touch pad as being more responsive.

---

### Post by manca on 2008-05-16
I have thic keyboard and it works flawlessly in Hardy. However installing keytouch and using the configuration file posted above, doesn't let me change songs in amarok... It starts amarok with Media button, locks down the screen with Sleep button, controls volume, but swiching songs doesn't work....

---

### Post by BatPenguin on 2008-06-01
> **manca said:**
> I have thic keyboard and it works flawlessly in Hardy. However installing keytouch and using the configuration file posted above, doesn't let me change songs in amarok... It starts amarok with Media button, locks down the screen with Sleep button, controls volume, but swiching songs doesn't work....

I can't seem to get the keytouch software to do anything with that profile. I've installed it and taken the profile...doesn't seem to change a thing. This is with Hardy and the bluetooth Logitech Dinovo Edge.

The only way I can change anything is by going to the normal System -> Preferences -> Keyboard shotrcuts and assigning the ones that can be assigned there - which actually seem to be mostly (with one exception) the same ones you guys can adjust with that program, meaning everything but the 3 zoom buttons, VOIP and a-d. Plus I can't adjust the sleep button which is the only one I really NEED to adjust. I want to disable it or swith it to something else, it's really annoying as I (or rather, my 2,5-yearold) seem to hit it constantly and it leads to the machine's screen dimming and it hanging. I have to reboot with the power button. I have no idea what it's doing...suspending maybe? But still, it's the "crash" button now and I'd love to disable it. Any idea what file I could edit directly to just get rid of it?

Anohter thing: whenever I boot the computer, I have to wiggle the mousepad for a while for the keyboard to wake up at the login screen. This an issue with anybody else? I've noticed that this isn't necessary if the keyboard is in the charging station when booting up.

---

### Post by Bloemetjesgordijn on 2008-06-19
> **BatPenguin said:**
> Anohter thing: whenever I boot the computer, I have to wiggle the mousepad for a while for the keyboard to wake up at the login screen. This an issue with anybody else? I've noticed that this isn't necessary if the keyboard is in the charging station when booting up.

I have the same issue. Just waiting of wiggle the mousepad helps...

Question....Does anybody have the dead keys working??? (Zoom keys etc).

Kind regards,

Bloemetjesgordijn

---

### Post by wonko on 2008-06-19
> **BatPenguin said:**
> Anohter thing: whenever I boot the computer, I have to wiggle the mousepad for a while for the keyboard to wake up at the login screen. This an issue with anybody else? I've noticed that this isn't necessary if the keyboard is in the charging station when booting up.
And you've tried disabling bluetooth?
> **tahiti said:**
> I'm having this problem too. Running fully updated Gutsy Beta.
My Logitech Dinovo Edge doesn't work after a reboot until I turn the keyboard off and then on again, or remove and plug in the usb dongle.
Disabling bluetooth under System > Administration > Services is the easiest workaround for me.

---

### Post by BatPenguin on 2008-06-19
> **wonko said:**
> And you've tried disabling bluetooth?

Won't doing this, umm, disable Bluetooth? :) I use Bluetooth for receiving and sending files to/from my phone and Nokia N810 Internet Tablet, it's used quite a bit by me so I didn't even really consider disabling it.

---

### Post by wonko on 2008-06-20
Ah.. Then you have a problem. But it sounds like it's the same problem I have; the keyboard takes ages "waking" after a boot. You could of course try turning off the automatic start of the bluetooth service, and manually start it when needed, but I guess that's pretty cumbersome. Maybe try one of these:
[https://help.ubuntu.com/community/BluetoothInputDevices](https://help.ubuntu.com/community/BluetoothInputDevices)
[http://ubuntuforums.org/showthread.php?p=2334318#post2334318](http://ubuntuforums.org/showthread.php?p=2334318#post2334318)

---

### Post by BatPenguin on 2008-06-20
> **wonko said:**
> Ah.. Then you have a problem. But it sounds like it's the same problem I have; the keyboard takes ages "waking" after a boot. You could of course try turning off the automatic start of the bluetooth service, and manually start it when needed, but I guess that's pretty cumbersome. Maybe try one of these:
[https://help.ubuntu.com/community/BluetoothInputDevices](https://help.ubuntu.com/community/BluetoothInputDevices)
[http://ubuntuforums.org/showthread.php?p=2334318#post2334318](http://ubuntuforums.org/showthread.php?p=2334318#post2334318)

Thanks! I'll give those a try when I get home (will be out of town for another week and a half). Looks like good options for fixing it, can't believe I never saw those before.

---

### Post by Gwillmeister on 2008-07-07
I just NEED to point out, reading through other forums and this one about the dinovo - on login try the caps-lock key - seems to work for me, also it's not GDM specific.

Also, anyone complaining about slow scroll speeds seem to have not noticed that for proper scrolling;
run your finger (or thumb) over a bumpy scrolling thingy
then continue moving your finger around in a circle motion - depending on which way you wish to scroll.

otherwise this keyboard is awesome! worked out of the box, except on my 2.6.18.8 install..  LOVE the metal brush, only wish i owned it myself...

Also, i saw something somewhere else about those keys, but i cant remember where.. :(

---

