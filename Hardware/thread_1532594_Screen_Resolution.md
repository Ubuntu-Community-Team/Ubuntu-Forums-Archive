---
title: "Screen Resolution"
date: 2010-07-16
forum: Hardware
---

### Post by Searock on 2010-07-16
Hi

My screen resolution in windows and previous version of ubuntu (9.04) was 1152 x 864.

But in Ubuntu 10.04 it gives me an option of 1024 x 786 and 1360 x 786, how can I change it to 1152 x 864 ?

And I guess I have *Intel*® *Graphics* Media  Accelerator built in graphic card.

Is there any way I can change my screen resolution to 1152 x 864 ?

Thanks.

---

### Post by Searock on 2010-07-18
bump..........

---

### Post by efikkan on 2010-07-19
Check out [Adding undetected resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions")

---

### Post by Searock on 2010-07-19
Thanks to[ Matan Eldan]("http://superuser.com/users/41521/matan-eldan") and  [Lord.Quackstar]("http://superuser.com/users/39898/lord-quackstar"),  my problem is solved. This is what I have tried.

> searock@searock-desktop:~$ cvt 1152   864

 1152x864 59.96 Hz (CVT   1.00M3) hsync: 53.78 kHz; pclk: 81.75 MHz Modeline "1152x864_60.00"  81.75   1152 1216 1336 1520 864 867 871 897   -hsync +vsync

 searock@searock-desktop:~$ xrandr   --newmode "1152x864_60.00" 81.75 1152 1216 1336 1520 864 867 871 897  -hsync   +vsync

 searock@searock-desktop:~$ xrandr   --addmode S-video 1152x864
 xrandr: cannot find output   "S-video"

  searock@searock-desktop:~$ xrandr
  Screen 0: minimum 320 x 200, current   1024 x 768, maximum 4096 x 4096
  VGA1 connected 1024x768+0+0 (normal   left inverted right x axis y axis) 0mm   x 0mm
 1360x768 59.8
 1024x768   60.0*
 800x600 60.3 56.2
 848x480 60.0
 640x480 59.9   59.9
 1152x864_60.00 (0x124) 81.0MHz
 h: width 1152 start 1216  end 1336 total 1520 skew 0 clock   53.3KHz
 v: height 864 start 867 end 871 total 897 clock   59.4Hz

 searock@searock-desktop:~$ xrandr   --addmode VGA1 1152x864_60.00

**Source : **[Superuser]("http://superuser.com/questions/164926/why-cant-i-get-the-right-screen-resolution-in-ubuntu")

---

