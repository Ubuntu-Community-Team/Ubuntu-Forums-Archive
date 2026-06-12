---
title: "PS3 Eye error"
date: 2009-02-10
forum: Hardware
---

### Post by mysticrider92 on 2009-02-10
Over at the nuigroup.com forums, there has been some work on drivers to use the PS3 Eye as a webcam. However, Linux support is somewhat lacking, so I am hoping you guys can figure out what my problem is here.

Basically, when I open the camera in any program, it shows a picture properly for maybe 30 seconds, then freezes. Depending on the program used, the freeze will either kill the program, or last a few seconds then go back to normal. I get a few different different errors depending on what program. Here they are:
```
Unable to dequeue buffer: Input/output error
Error grabbing
Cleanup done. Exiting ...

```
```
select timeout
```
```
[00000409] v4l2 demux error: Failed to wait (VIDIOC_DQBUF)
```
```
libv4l2: error dequeuing buf: Input/output error
```

These are all using the gspca_ov534 driver. The annoying part is, out of the three or four others who have reported on this, I am the only one getting the freezes. I can't figure out if it is my computer, kernel, the driver, the webcam itself, or what..

Some other stuff:
Ubuntu 8.10, kernel 2.6.29_rc2 AMD64, new Gigabyte mobo (AMD Phenom processor). The only other thing in my USB ports is a Logitech wireless mouse, but removing it doesn't affect the freezes. We know that the YUYV format used by the Eye is bandwidth demanding, but I don't know if that is the problem or not.

I know it is harder to debug these problems with a non-stock kernel, but this is the only one with the gspca_ov534 driver built in (which is why I am using it).

---

### Post by geraldm on 2009-02-10
There is some problem with the I/O and the buffer.
Usually the buffer size is allocated, used, and then dequed. 
If you are writing the driver, try setting the timeout much higher to see if the 
device will complete its transfer.  I would guess that it is a problem with the
driver, or possibly a kink in the device that needs a workaround.

You might find some hints by looking at the code of other drivers in the kernel source.  Good luck.

regards,
Gerald

---

### Post by mysticrider92 on 2009-02-10
I didn't write the driver, but since I compiled it from source, it shouldn't be too hard to change that. I will take a look at that tomorrow and see. 

Someone else suggested the "DPC Latency". I can't find any information on this for Linux, so.. Using the latency checker for Windows, my computer should be able to handle the video just fine. It does seem to be a driver bug, from what this program shows.

---

### Post by mysticrider92 on 2009-02-14
Sorry about the double post..

I checked through the source, and found the timeout. It was set to 500ms, and I upped it to 2500ms. This helps a little (less frequent "select timeout" errors, and only a few dropped frames), but its not really smooth like most people say. 

Should I try changing the max number of frame buffers? Or is there some other trick to try?

---

### Post by mysticrider92 on 2009-02-16
Anyone? 

Should this be in the programming section, since the problem is with the driver?

---

