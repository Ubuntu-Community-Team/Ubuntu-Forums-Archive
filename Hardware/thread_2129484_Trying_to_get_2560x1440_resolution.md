---
title: "Trying to get 2560x1440 resolution"
date: 2013-03-26
forum: Hardware
---

### Post by tirengarfio on 2013-03-26
Hi,

I have this [motherboard]("http://www.evga.com/Products/Product.aspx?pn=111-IB-E692-KR") and this [monitor]("http://www.google.es/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CC4QFjAA&url=http%3A%2F%2Fwww.samsung.com%2Fhk_en%2Fconsumer%2Fcomputer-peripherals%2Fmonitors%2Fcommercial%2FLS27A850DS%2FXK%3Fsubsubtype%3Dsa650-and-sa850-led&ei=Wq5RUYehE9CihgeykIHoAw&usg=AFQjCNEsSRMSfXTylQ5g0LokbPknnk4zsA&bvm=bv.44158598,d.ZG4"). 

It is supposed I could get 2560x1440 resolution using HDMI 1.4, but i don't know how..

NOTE: I have a HDMI cable and a DVI-HDMI adapter, I don't know if they support HDMI 1.4 or not..how can i know it? is maybe that the problem?

Any help?

Javi

---

### Post by Cheesemill on 2013-03-26
It's not possible I'm afraid.

The Intel HD 4000 graphics doesn't support dual link, therefore your maximum available resolution over both HDMI and DVI is 1920x1200.

If you want to be able to use your monitors native resolution you will need to buy a discrete graphics card that supports DVI dual link or use Displayport.

---

### Post by tirengarfio on 2013-03-26
Thanks, but if I use DisplayPort interface (without the discrete graphics card), will i get 2560x1440? 

Anyway I have to add this to my first question:

 I have just bought a HDMI to DVI-D (Dual link), and have run this:

```
xrandr | grep maximum &
sleep 2
gtf 2560 1440 60.0 &
sleep 2
xrandr --newmode "2560x1440_60.00" 311.83  2560 2744 3024 3488  1440 1441 1444 1490  -HSync +Vsync &
sleep 2
xrandr --addmode HDMI2 2560x1440_60.00 &
sleep 2
xrandr --output HDMI2 --mode 2560x1440_60.00 &
exit 0
```

Then I get 2560x1440 but I get this output and everything is pixelated like in the image of the first question of this [thread]("http://phoronix.com/forums/showthread.php?77594-Problem-with-2560x1440-resolution-via-HDMI"):

```
Screen 0: minimum 320 x 200, current 2560 x 1440, maximum 8192 x 8192

  # 2560x1440 @ 60.00 Hz (GTF) hsync: 89.40 kHz; pclk: 311.83 MHz
  Modeline "2560x1440_60.00"  311.83  2560 2744 3024 3488  1440 1441 1444 1490  -HSync +Vsync

X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  38
  Current serial number in output stream:  38
```

Note 1: The last five lines are not shown if i run the script in default Ubuntu desktop environment instead of on xfce.

Note 2: The Display manager tag my monitor as "Samsung Electric Company 24" instead of 27.

Javi

---

### Post by Cheesemill on 2013-03-26
You should be able to get 2560x1440 if you use the displayport connector on your motherboard without needing a discrete card..

This thread may be useful for you...
[http://communities.intel.com/thread/30360](http://communities.intel.com/thread/30360)

---

