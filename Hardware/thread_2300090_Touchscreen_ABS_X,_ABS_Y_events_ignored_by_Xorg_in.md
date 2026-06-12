---
title: "Touchscreen ABS_X, ABS_Y events ignored by Xorg in Ubuntu 14.04"
date: 2015-10-23
forum: Hardware
---

### Post by tr1976 on 2015-10-23
Hi all,

I am trying to get a touch screen (GMK) working with Ubuntu 14.04. I can get the display work as a touch pad using
Xorg mouse driver with /dev/input/mouse0, but when I try to use the 'evdev' driver and /dev/input/event3,
I can only get the button pressed and released events to X, i.e. the pointer is not moving anywhere. I can
run evtest to see that there are ABS_X and ABS_Y events coming from the device with correct coordinates,
but somehow these are not used by Xorg. I think I have tried all possible evdev options in Xorg configs.
I would appreciate any info on how to dig more information or better yet, a solution to fix the problem.
I can provide more information if needed. Thanks.

Here are some screenshots from the system giving some information:

evtest output: [https://drive.google.com/file/d/0B432-jkCZeXgakQ0WXZ1MGZ5dXM/view?usp=sharing](https://drive.google.com/file/d/0B432-jkCZeXgakQ0WXZ1MGZ5dXM/view?usp=sharing)
mtdev-test output: [https://drive.google.com/file/d/0B432-jkCZeXgTWxiNElkdzZOdVE/view?usp=sharing](https://drive.google.com/file/d/0B432-jkCZeXgTWxiNElkdzZOdVE/view?usp=sharing)
xinput list: [https://drive.google.com/file/d/0B432-jkCZeXgSjJlZjBjakM1ZmM/view?usp=sharing](https://drive.google.com/file/d/0B432-jkCZeXgSjJlZjBjakM1ZmM/view?usp=sharing)
xinput props: [https://drive.google.com/file/d/0B432-jkCZeXgQUI5NXRONzdrWGc/view?usp=sharing](https://drive.google.com/file/d/0B432-jkCZeXgQUI5NXRONzdrWGc/view?usp=sharing)
xinput test: [https://drive.google.com/file/d/0B432-jkCZeXgeDV0Yno3c2tMMkU/view?usp=sharing](https://drive.google.com/file/d/0B432-jkCZeXgeDV0Yno3c2tMMkU/view?usp=sharing)
xorg.log: [https://drive.google.com/file/d/0B432-jkCZeXgaVVCVWdaeS12Njg/view?usp=sharing](https://drive.google.com/file/d/0B432-jkCZeXgaVVCVWdaeS12Njg/view?usp=sharing)

BR,
Teemu Rinta-aho

---

### Post by tr1976 on 2015-10-26
Oh, forgot one important piece of information. The display works fine with Ubuntu 10.04, using evdev driver.

---

