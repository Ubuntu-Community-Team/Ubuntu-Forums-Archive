---
title: "egalax touchscreen rotate"
date: 2007-12-03
forum: Hardware &amp; Laptops
---

### Post by simplyw00x on 2007-12-03
I have the egalax touchscreen on my hp tx1000 laptop configured beautifully, but when I rotate the screen using xrandr, the touchscreen calibration doesn't change. How could I force the driver to use a different calibration when the screen is rotated?

---

### Post by noah.bronstein on 2008-02-04
Sorry to ask another question and not answer yours, but could you give me some pointers for how to get the touchscreen set up at all?  I'm working with a tx1000z, Ubuntu Gutsy 7.10, and an AMD64 processor, for whatever difference it makes.

---

### Post by Glogggtarr on 2008-02-04
I just finished setting this up myself.

To get the touchscreen to work you need to edit your xorg.conf in /etc/X11/

In Section "ServerLayout" there should be a part that says "#Uncomment if you have a wacom tablet" followed by some commented out lines.  Just uncomment those lines and restart X by pushing ctrl+alt+backspace.

To get the orientation of the pen input to change when you change the screen look at the scripts [here.]("http://ubuntuforums.org/showthread.php?t=301380&page=2")

---

### Post by noah.bronstein on 2008-02-04
Hmm, I tried it but that seemed to change nothing, even after rebooting X a couple of times and doing a hardware reboot once.

Do I need a special driver or package of some sort?

---

### Post by simplyw00x on 2008-02-04
Wacom is the *wrong driver*. There are many instructions in the "helpful (sic) hints for a tx1000" thread --- [http://ubuntuforums.org/showthread.php?p=4264350#post4264350](http://ubuntuforums.org/showthread.php?p=4264350#post4264350)

I found the egalax binary drivers to be the best, but they don't work on hardy and EETI  ignored my email about the possibility of updating the driver for new xorg.

I can post my (currently-non-working-but-probably-would-work-on-gutsy) xorg.conf if you'd like.

---

### Post by noah.bronstein on 2008-02-04
That'd  be helpful.
I'll try to work my way through that other thread sometime, but it's going to be a while before I take the time to tackle this problem.  So I'll let you know once I do.

Thanks!

---

### Post by Murphy2712 on 2008-02-15
There's a new EETI driver on their website :
[http://www.eeti.com.tw/](http://www.eeti.com.tw/)
or directly
[http://210.64.17.162/web20/TouckDriver/linuxDriver.htm](http://210.64.17.162/web20/TouckDriver/linuxDriver.htm)

---

### Post by hojthojt on 2008-03-04
I used this instruction

[http://ubuntuforums.org/showpost.php?p=4241341&postcount=579]("http://ubuntuforums.org/showpost.php?p=4241341&postcount=579")

Note that you need to reboot the computer or restart X (with Ctrl+Alt+Backspace) before you test the rotation (or if you know of another way of getting the system to re-read xorg.conf I would be glad to know how).

Unfortunately, it does not rotate the touch screen coordinates, which makes it pretty useless.

I have an idea to solve this, but haven't solved it fully yet. What I did was to calibrate 4 different touchscreen calibration files, one for each screen rotation. Between each calibration I copied the calibration data into separate files:
```
<calibrate>
sudo cp /etc/egalax.cal /etc/egalax_normal.cal
<rotate screen with rotate.sh>
<calibrate>
sudo cp /etc/egalax.cal /etc/egalax_left.cal
<rotate screen with rotate.sh>
<calibrate>
sudo cp /etc/egalax.cal /etc/egalax_inverted.cal
<rotate screen with rotate.sh>
<calibrate>
sudo cp /etc/egalax.cal /etc/egalax_right.cal

```
Then the idea was to change calibration file used together with the screen rotation script. The problem is to get the touch screen driver to re-read the calibration file.

The calibration is normally saved in /etc/egalax.cal and is referenced from /etc/X11/xorg.conf
To change the calibration settings when the screen is rotated, we need a way to get the xorg.conf file to be re-read or to restart the Xserver when we rotate the screen. Or even better, just get the driver to use another calibration file. Any ideas are welcome.

My workaround so far is to have four different xorg.conf files which references different egalax.cal files, then I change the xorg.conf that match my screen rotation and restart X with <Ctrl+Alt+Backspace>.

Or has anyone got a better solution posted somewhere that I just haven't found yet?

regards

---

