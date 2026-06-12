---
title: "How to remove the default driver of webcam in 8.10 ?"
date: 2008-11-04
forum: Hardware
---

### Post by chunchengch on 2008-11-04
I am using ASUS F3Jc notebook with a built-in webcam Syntek DC-1125,
this webcam worked normally in Ubuntu 8.04 without the need to install extra driver.

However, just after upgrading my Ubuntu 8.04 to 8.10 on last Saturday, I found the light of webcam is still on after Cheese is closed, and the most unacceptable thing is that the only way to shutdown the webcam is to power off the computer. (reboot can not shutdown the webcam, that is weird)

I would like to install the particular drive for Syntek DC-1125 to make the webcam work normally, but I don't know how to remove the default driver, thanks for any suggestion.

---

### Post by nixscripter on 2008-11-04
See if this will remove the driver (and perhaps cause the light to go out): ```
sudo modprobe -r stk11xx
```

---

### Post by chunchengch on 2008-11-04
Thanks for reply.

I find these three modules, but I don't know which one is the driver for webcam?

$ slocate stk*.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/rtc/rtc-stk17ta8.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/gspca/gspca_stk014.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/stkwebcam.ko

---

### Post by seeebek on 2008-11-05
I have the same Laptop and (K)Ubuntu 8.10 is using stkwebcam.ko for it. I don't know how to remove it permanently. Maybe you just need to delete the file. If you find it out let me know. I would be very happy to know.
And yes I also have all the issues you have. 
Wish you good luck.

---

### Post by nixscripter on 2008-11-05
> **chunchengch said:**
> Thanks for reply.

I find these three modules, but I don't know which one is the driver for webcam?

$ slocate stk*.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/rtc/rtc-stk17ta8.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/gspca/gspca_stk014.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/stkwebcam.ko

See which ones are loaded: ```
lsmod | grep stk
```

If you can't tell, try the third one first:

```
sudo modprobe -r stkwebcam
```

---

### Post by ebooa on 2010-06-10
Greetings.

I have the same laptop and i have recently installed ubuntu lucid.
However i can't seem to install the webcam driver. i know i can get some images with the built in driver but i can't find a way to stream video through pidgin or any other kind of software.
i know the driver for the webcam is the stk1125, but wherever i try to find a way to install it i can't seem to get any help.

can you guys give me a hand or any kind of support on this?

thks

---

