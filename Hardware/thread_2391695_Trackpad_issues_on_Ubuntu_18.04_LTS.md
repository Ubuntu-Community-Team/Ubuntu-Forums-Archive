---
title: "Trackpad issues on Ubuntu 18.04 LTS"
date: 2018-05-12
forum: Hardware
---

### Post by Tlarhices on 2018-05-12
I was running ubuntu without issues up to a few days ago when I reinstalled my laptop entirely with ubuntu 18.04.

On the live ubuntu and the installed one, the trackpad is missbehaving:

[LIST]
[*]The mouse cursor moves when I slide my finger, extremely gently on the trackpad
[*]The mouse cursor stops responding as soon as there is even a little bit of pressure on the trackpad
[*]It is impossible to click and move the mouse cursor
[/LIST]

After poking around, I did not see anything looking useful in dmseg. Searching on internet gave me several things to try and so far, the best is to run this after each restart:
```
sudo modprobe -r psmouse && sudo modprobe psmouse
```

This will make the cursor behave correctly, but any multi-finger gestures are then ignored (2 fingers swipes to emulate the wheel, ...) reducing usability of the system.

I have also tried bare and imps options for psmouse but the effect is the same.

Before modprobe the trackpad is detected as:
```
I: Bus=0011 Vendor=0002 Product=0011 Version=0001
N: Name="CyPS/2 Cypress Trackpad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input5
U: Uniq=
H: Handlers=mouse1 event7 
B: PROP=1
B: EV=b
B: KEY=e520 70000 0 0 0 0
B: ABS=660800011000003
```

After modprobe it is detected as:
```
I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input15
U: Uniq=
H: Handlers=mouse1 event7 
B: PROP=1
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3
```

According to the laptopt specs the trackpad is really a Cypress trackpad (I saw some issues talking about miss-detection)

Any ideas on how to fix / diagnose further the issue ?

---

### Post by Tlarhices on 2018-05-12
As I was reading [https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection) I found out that I was missing **xserver-xorg-input-synaptics**. Manually installing it resolved everything.
Sorry for the noise.

---

### Post by trethlyn on 2018-05-24
> **Tlarhices said:**
> As I was reading [https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection) I found out that I was missing **xserver-xorg-input-synaptics**. Manually installing it resolved everything.
Sorry for the noise.

Don't be sorry.  This fixed my issue and I was tempted to not use ubuntu because of it.  (Wasn't having the issue in other distros).  Thank you for your time and effort, the two resources you can never get back.

---

### Post by babboste on 2018-11-07
> **Tlarhices said:**
> As I was reading [https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection) I found out that I was missing **xserver-xorg-input-synaptics**. Manually installing it resolved everything.
Sorry for the noise.

That solved for me too (macbook pro retina late 2013), thanks!!

---

### Post by alesupper on 2018-11-14
Fixed it for me too.  Thanks very much.

---

### Post by teto0207 on 2019-02-20
I had the same issue on a late 2011 Macbook Pro and it helped after installing this.

---

### Post by mpuppet1 on 2019-03-30
FYI, I have the same problem on a Dell XPS 15Z, but when I installed xserver-xorg-input-synaptics, I lost keyboard functionality inside the OS. I say "inside" because the keyboard works when logging in, but after that, is rendered useless. I even tried plugging in an external kb, no dice.

---

### Post by bcarnes on 2019-04-27
> but when I installed xserver-xorg-input-synaptics, I lost keyboard functionality

@mpuppet1 - you didn't give any details, but this sounds like you're running afoul of the way xorg does its input package dependencies.

Try adding the package "xserver-xorg-input-all" and you should get your keyboard back.

For the reason why, look at the dependencies:
xorg -> xserver-xorg-> "xserver-xorg-input-all | xorg-driver-input"

the synaptics package provides "xorg-driver-input", so if you install that early enough (during a debootstrap or server/base to GUI/desktop upgrade), it thinks you're taking fine-grained control over the xserver-xorg-input-* packages, and you'll never get the other goodies in xserver-xorg-input-all, including basic keyboard support..

---

### Post by spode2 on 2019-09-22
> **bcarnes said:**
> > but when I installed xserver-xorg-input-synaptics, I lost keyboard functionality

@mpuppet1 - you didn't give any details, but this sounds like you're running afoul of the way xorg does its input package dependencies.

Try adding the package "xserver-xorg-input-all" and you should get your keyboard back.

For the reason why, look at the dependencies:
xorg -> xserver-xorg-> "xserver-xorg-input-all | xorg-driver-input"

the synaptics package provides "xorg-driver-input", so if you install that early enough (during a debootstrap or server/base to GUI/desktop upgrade), it thinks you're taking fine-grained control over the xserver-xorg-input-* packages, and you'll never get the other goodies in xserver-xorg-input-all, including basic keyboard support..

I have fallen into this trap too, and the laptop has no ssh. Without a keyboard I am a bit stuck. Is there a way out?

---

### Post by spode2 on 2019-09-22
OK, I figured out how to do it in recovery. Just enable networking and install from the root shell.

---

