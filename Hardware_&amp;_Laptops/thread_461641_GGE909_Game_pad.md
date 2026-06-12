---
title: "GGE909 Game pad"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by dracule on 2007-06-01
I have the GGE909 game pad bought from walmart and am having troubles.  I loaded the modules via:
```
sudo rmmod joydev
sudo modprobe joydev
```

opened up zsnes to play specified "dev/input/js0" since that is the path that was displayed when i used joystick calibrator. but the problem is that the d-pad doesnt work. it works in joy stick calibrator. I tried turning analog off. so I thought hmmm and tried gsnes. the problem is when I did that, no games would even run with joy pad support enabled! 

so I was thinking and thought hey what about joy2key maybe emulate directional keyboard buttons. so i downloaded it put in this code:
```
joy2key  -dev {/dev/input/js0}

```

and was greeted by this:
```
Error opening {/dev/input/js0}!
Are you sure you have joystick support in your kernel?

```

any ideas (the path is dev/input/js0 since that is what i specify in gsnes to set my keys which shows up working (just no games work))

---

### Post by dracule on 2007-06-04
bump

---

### Post by mlitty on 2007-06-26
I've been using this pad since Dapper Drake with little problem.  It only works for me in "analog" mode (with the light on), but rarely needs any command line configuration.  I use it with Torcs, Trigger, Tuxkart, gl-117...

If I remember correctly, I did have to do some tweaking in Dapper to get it functioning, but that was over a year ago and I can't remember what I did.  I do remember that I found the info with Google, and that it wasn't very difficult.

With Feisty Fawn, I just plugged it in and it worked.  I had to calibrate it in each game, but that was all.

I also had to make sure that it was plugged into a usb port directly.  The first time I tried to plug it in to a hub, and there wasn't enough power to run it, though it looked like it was on.  I discovered this by running 
```
dmesg
```
after plugging it in.  The last few lines said something about not enough power or something, so I used a different port on the motherboard and it worked.

I haven't been able to get this to control the mouse via the mouse button, the esc, enter, select, and start buttons don't seem to do anything, and there's no rumble feed-back, but otherwise I've been happy with it.  Some of those buttons may work with some extra effort, but I'm not certain.

I hope this helps.

---

### Post by mlitty on 2007-06-26
I'm looking for info on getting this to control my mouse.
I've found a good generic howto on setting up a gamepad with ubuntu at
[http://onlyubuntu.blogspot.com/2007/03/how-to-set-up-gameportgamepad-or.html]("http://onlyubuntu.blogspot.com/2007/03/how-to-set-up-gameportgamepad-or.html")

In case it helps, here's my lsmod output minus the obviously irrelevent stuff...
```

Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
xt_limit                3584  8 
xt_tcpudp               4224  10 
ipt_TOS                 3200  0 
ipt_REJECT              5632  1 
xt_state                3456  6 
ppdev                  10116  0 
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
ac                      6020  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
dock                   10268  0 
button                  8720  0 
container               5248  0 
sbp2                   23812  0 
parport_pc             36388  0 
fuse                   46612  1 
psmouse                38920  0 
xpad                    9988  0 
serio_raw               7940  0 
usblp                  14848  0 
k8temp                  6656  0 
shpchp                 34324  0 
tsdev                   8768  0 
joydev                 10816  0 
evdev                  11008  4 
jbd                    59816  1 ext3
usbhid                 26592  0 
hid                    27392  1 usbhid
generic                 5124  0 [permanent]
sg                     36252  0 
sd_mod                 23428  3 
ohci1394               36528  0 
ehci_hcd               34188  0 
forcedeth              46728  0 
ohci_hcd               22532  0 
usbcore               134280  6 xpad,usblp,usbhid,ehci_hcd,ohci_hcd
capability              5896  0 
commoncap               8192  1 capability
tileblit                3584  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit


```

I'd note the usb stuff, ohci, hid, softcursor, joydev, xpad, and anything else that looks mildly relevant.  I'm not a modules guy, but these look important.

and ```
 dmesg
``` reveals these lines relevant to the controller
```

[   43.825578] usbcore: registered new interface driver hiddev
[   43.839612] input: Jess Tech GGE909 PC Recoil Pad as /class/input/input1
[   43.839661] input: USB HID v1.10 Joystick [Jess Tech GGE909 PC Recoil Pad] on usb-0000:00:0b.0-6

```

Again, keep in mind that I'm running Ubuntu Feisty Fawn, so your results may vary.  My game pad is a "Game-Elements" GGE909 from Wal-Mart  but it's recognized as a "Jess Tech GGE909"

Best of luck...

---

