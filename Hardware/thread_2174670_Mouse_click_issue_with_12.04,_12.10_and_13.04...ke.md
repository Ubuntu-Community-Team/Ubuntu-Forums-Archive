---
title: "Mouse click issue with 12.04, 12.10 and 13.04...keyboard backlight conflict"
date: 2013-09-15
forum: Hardware
---

### Post by RrYfJsz on 2013-09-15
I have looked high and low for an easy resolution to this ridiculous issue. I have a Razer Death Adder mouse and a Saitek Eclipse 2 Keyboard. Anyway, the keyboard has 4 different options for backlight: blue, red, violet, and off. Blue is the default color the keyboard will start with upon booting up the computer. The basic desktop in Ubuntu without any applications open works fine. However, when you change the color of the keyboard after opening an application, Firefox, Libre Office, or anything, suddenly the mouse will not be able to click anything. At first I was using ALT+F4 to get the window closed and back to the desktop...which made things usually better for mouse clicking. Then I found this post: [http://ubuntuforums.org/showthread.php?t=1999076](http://ubuntuforums.org/showthread.php?t=1999076) that someone else had a similar issue, but said they were able to get mouse clicking back by cycling through the various backlight colors of the keyboard. So, I tried that and it worked for me too. I tried a different USB port for the keyboard since the mouse and keyboard were plugged into USB ports next to one another. It used to be that dual USB ports next to one another used the same hub, but I think today they use separate hubs even though they are next to one another. Anyway, I changed USB ports for the keyboard to a different port away from the mouse, but to no avail. Issue still prevails. So, it doesn't matter what USB port you use for the keyboard and mouse. That is irrelevant. Also, it is not a hardware issue because I also use Win7 Ultimate 64-bit and the mouse and keyboard work flawlessly. Yes, I am using the Ubuntu version for 64-bit too. This issue is definitely an OS issue and not hardware. Unless for some reason the conflict is due to Ubuntu not picking the correct mouse driver? You would think that the developers from Ubuntu would have figured this issue out by now with 13.04, but no. It can't be that difficult. Win7 doesn't have this issue. I wanted to make a dual boot computer with Ubuntu 64-bit and Win7 64-bit, but it is not practical the way Ubuntu becomes clunky and useless due to mouse click issues. By the way, I'm just testing the Ubuntu versions from DVD and not from HDD install. I do that to find issues first before I decide to install. Glad I did. You'd think this issue would have been resolved a long time ago in previous Ubuntu updates. I like Ubuntu, but this issue is just frustrating. I realize any fix may require Ubuntu install on a HDD so the changes can take. Does anyone out there have an easy, step-by-step fix short of using a keyboard without a backlight? Thanks for any and all help.

---

### Post by RrYfJsz on 2013-09-15
As a follow up to this issue, I discovered that PCLinuxOS 2013-07 version has the same issue with mouse clicking problems when you change the backlight on the keyboard. Since PCLinuxOS, the one I downloaded, uses the KDE desktop and Ubuntu uses the Unity desktop, that has nothing to do with this issue. I believe the issue is due to the driver that the OS thinks is the best driver for the keyboard, but isn't. Very frustrating and disappointing.:frown:

---

### Post by RrYfJsz on 2013-09-15
More stuff I found on this issue that might help developers figure out the source of the issue and fix it. Anyway, on this website: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311) I found this info about the exact same keyboard I have causing the mouse click problems from changing the backlight on the keyboard:
 
I should note that I don't have a Microsoft keyboard but a Saitek Eclipse II keyboard. Relevant inputs:


/dev/input/event5
   bustype : BUS_USB
   vendor : 0x6a3
   product : 0x8021
   version : 273
   name : "Chicony Saitek Eclipse II Keyboa"
   phys : "usb-0000:00:1d.0-1/input0"
   uniq : ""
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP


/dev/input/event6
   bustype : BUS_USB
   vendor : 0x6a3
   product : 0x8021
   version : 273
   name : "Chicony Saitek Eclipse II Keyboa"
   phys : "usb-0000:00:1d.0-1/input1"
   uniq : ""
   bits ev : EV_SYN EV_KEY EV_MSC


The feature that causes the problem here is the button to turn on/off/change the kb backlight color. input-events for /dev/input/event6:


First press (backlight off->blue): emulates left click
19:43:40.885931: EV_MSC MSC_SCAN -16646143
19:43:40.885936: EV_KEY BTN_0 (0x100) pressed
19:43:40.885941: EV_MSC MSC_SCAN -16646140
19:43:40.885942: EV_KEY BTN_3 (0x103) released
19:43:40.885943: EV_SYN code=0 value=0


Second press (blue->red): emulates middle click
19:43:43.101984: EV_MSC MSC_SCAN -16646143
19:43:43.101989: EV_KEY BTN_0 (0x100) released
19:43:43.101992: EV_MSC MSC_SCAN -16646142
19:43:43.101992: EV_KEY BTN_1 (0x101) pressed
19:43:43.101996: EV_SYN code=0 value=0


Third press (red->purple): emulates right click
19:43:38.005865: EV_MSC MSC_SCAN -16646142
19:43:38.005869: EV_KEY BTN_1 (0x101) released
19:43:38.005871: EV_MSC MSC_SCAN -16646141
19:43:38.005872: EV_KEY BTN_2 (0x102) pressed
19:43:38.005874: EV_SYN code=0 value=0


Fourth press (purple->off) emulates ???
19:43:39.765915: EV_MSC MSC_SCAN -16646141
19:43:39.765921: EV_KEY BTN_2 (0x102) released
19:43:39.765925: EV_MSC MSC_SCAN -1664614019
19:43:39.765926: EV_KEY BTN_3 (0x103) pressed
19:43:39.765928: EV_SYN code=0 value=0


It seems to me this might be fundamentally a udev issue.. but I'm not qualified to judge that.

So, the backlight changing on a keyboard act as different types of mouse clicks based on what color you switch to. Makes no sense to me why Ubuntu and PCLinuxOS would act that way when Windows has never done that. So, based on all the data for this issue, and based on Windows not showing this bug, it is definitely something related to the design of the Ubuntu and PCLinuxOS Operating Systems. Sounds to me it could be fixed fairly easily, but since I don't have the skill set as a developer, I can't do that. I wish in the next version after January 2014, this issue can be resolved. Really annoying and makes Ubuntu and PCLinuxOS basically useless if you don't buy a different keyboard w/o a backlight.:confused::frown:

---

### Post by mgmiller on 2014-08-04
I have created a bug report specific to this keyboard, quoting much of your information.  I am running 14.04 and the problem has affected me since 12.04, but I didn't realize what was causing it.  Here is the bug report, you should click on the it affects me too link.

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1352374](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1352374)

---

### Post by sven12 on 2014-09-03
Hello 
I have the same Problem.
Anyone any idea how to solve it?

---

### Post by mgmiller on 2014-09-04
My only work around is to select the color I like during boot before the log in page appears.  I try to change the color as soon as the power to the keyboard is restored and it lights up.  On my system, this happens twice.  Once during post, then the power is turned off and back on shortly after Ubuntu starts to load.  I do the color change after the second power event while Ubuntu is loading.  Since I only reboot this machine when a kernel update requires it, it's only a minor annoyance for me.

---

### Post by klytu on 2015-02-23
I've been away from the Ubuntu forums for a while but I've had this issue for several years. A recent post on launchpad put this on my radar. This is not a solution, but a workaround I use is switching to a text console, changing the backlight color, then exiting the text console and going back to the normal desktop/x11 session. I pulled this from a post I saw on some forum long ago, but I don't remember where. The workaround works reliably for me; your mileage may vary. Here are sample steps: 

1. Press CTRL-ALT-F1 to switch to a text console.
2. Press the backlight change key as desired to obtain the color you want.
3. Press CTRL-ALT-F7 to go back to your desktop/x11 session.

---

