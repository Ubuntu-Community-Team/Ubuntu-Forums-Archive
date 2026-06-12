---
title: "Feisty / Logitech MX Revolution Mouse"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by justaguynpc on 2007-04-27
I received a MX Revolution mouse today, and am in the midle of trying to configure all it's functions into my Feisty install.

After investigation, I ran across this thread : [http://ubuntuforums.org/showthread.php?t=277388&highlight=mx+revolution+mouse+setup](http://ubuntuforums.org/showthread.php?t=277388&highlight=mx+revolution+mouse+setup)
which seems pretty comprehensive.

I question it's validity secondary to the ubuntu version it was written for, as well as unfortunately feisty sees my mouse and identifies it erroneously as :

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0 event0 ts0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I am unsure how to proceed, knowing that any future references to "Logitech USB Receiver" could produce unwanted results.  I think the first route to address would be to "rename" the device, but how do I go about doing that?

Has anyone any leads toward configuring this mouse, or better yet, have successfully configured theirs in a feisty install?

Cheers!

---

### Post by KaMZaTa on 2007-04-28
I want know to! Please, help us!

---

### Post by sandman55 on 2007-04-29
MX revolution is covered in [_THIS_](http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware#Activate_side-mouse-buttons_in_FireFox) how to I tried it with my MX500 and it worked so I got greedy and changed my xorg.conf to 8 buttons and it messed up my side buttons and when I put xorg.conf back to 7 buttons still no good my scroll button wants to scroll and go back a page Grrrr.... I should have left it alone. I will try a how to for Dapper even though I'm on Feisty. Good luck with yours.

---

### Post by kdkirsch on 2007-05-01
> **sandman55 said:**
> MX revolution is covered in [_THIS_](http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware#Activate_side-mouse-buttons_in_FireFox) how to I tried it with my MX500 and it worked so I got greedy and changed my xorg.conf to 8 buttons and it messed up my side buttons and when I put xorg.conf back to 7 buttons still no good my scroll button wants to scroll and go back a page Grrrr.... I should have left it alone. I will try a how to for Dapper even though I'm on Feisty. Good luck with yours.

Unfortunately, the HOWTO you referenced does not address the question at hand. Enabling the side forward/back buttons leaves a lot of the MX/VX Revolution's functionality unavailable. We (there are a lot of us) want to use the wheel's side scroll, the thumb button/wheel, and the "Search" button.

The HOWTO at the beginning of this thread is inadequate and cumbersome. Ubuntu Logitech Revolution users need an Ubuntu analog of [uberOptions]("http://www.mstarmetro.net/~rlowens/"). uberOptions enables full and comprehensive customizability of the mouse functions, including application-specific customization. If someone is able to do this, your efforts would be greatly appreciated.

---

### Post by sandman55 on 2007-05-01
Im sorry that site didnt help I posted it because it listed the Logitech MX Revolution I eventually managed to get my mouse going and for those reading with a MX500 it is [HERE](http://ubuntuforums.org/showthread.php?t=219894)

---

### Post by KaMZaTa on 2007-05-02
:(

---

### Post by zzelinski on 2007-05-31
I would like to bump this thread, I am interested in making the MX revolution work as well!

---

### Post by daou on 2007-06-02
The MX Revolution howto is outdated. The new method is to use btnx:

[http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

However, if you aren't getting the right Product and Vendor IDs in /proc/bus/input/devices, then btnx cannot help you.

This is a shot in the dark, but does Logitech's Setpoint software in Windows update the firmware of the MX Revo? I think I noticed my version ID change at some point (or then I'm imagining). If this is the case, then running Setpoint in Win might fix it.

---

### Post by xeocub on 2007-06-06
I seem to be having the exact same problem. 

However, this seems quite odd: 

cat /proc/bus/input/devices has three references to what seems to be my mouse?


> 
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0 event0 ts0 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=046d Product=c51a Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:10.0-1/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse1 event3 ts1 
B: EV=7
B: KEY=ffff0000 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=046d Product=c51a Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:10.0-1/input1
S: Sysfs=/class/input/input4
H: Handlers=kbd event4 
B: EV=f
B: KEY=7fff002c3027 bf00444000000000 1 f808807c000 667bfad9415fed 8e000000000000 0
B: REL=40
B: ABS=100000000

---

### Post by daou on 2007-06-07
If you do get the lines: Vendor=046d Product=c51a
then Ubuntu has recognized your MX Revo and you should be able to use btnx. The Mac mouse is new to me, I haven't seen that before, but it might not interfere with btnx.

---

### Post by mfratt on 2007-06-11
I'm interested in making the search button my middle click button....anyone?

---

### Post by kotiledon on 2007-06-14
[http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware#Activate_side-mouse-buttons_in_FireFox](http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware#Activate_side-mouse-buttons_in_FireFox)

settings in the link **work **well with my **VX Revolution** mouse... 
thx..

---

### Post by drapaki on 2007-07-09
I had the mac mouse com up on mine, with all generic but btnx worked fine... 


thanks guys!  makes me mo' happy!

---

