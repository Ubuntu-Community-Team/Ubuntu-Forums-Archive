---
title: "cannot mount camera"
date: 2017-10-30
forum: Hardware
---

### Post by gian on 2017-10-30
Hello All,

this is the scenario..

I have a Pentax camera with an SD card: I can either mount the camera with an USB cable or extract the SD and insert it with an adapter in an USB port.

The card is detected and mounted in the adapter, but the camera won't be detected and mounted, and dmesg will return:

FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE

To complicate the situation, on another identical PC - same hardware and OS, Ubuntu 16.04 - everything works fine.

Any ideas?

Thanks for reading,

-Gian

---

### Post by Autodave on 2017-10-30
Are you trying to mount in a USB 3.0 port? I know that it is supposed to be bacxkward compatible with USB 2.0, but I have often found that that just ain't so.

---

### Post by gian on 2017-10-30
well, I don't know... I use front ports on both pc, but I also tried different ports with no success.

Also, I am sure that I was able to mount the camera time ago, but something happened (an upgrade?!) and now it doesn't work anymore.

---

### Post by ajgreeny on 2017-10-30
Is there some setting on the camera to set it as a USB mass storage device?

---

### Post by gian on 2017-10-30
I should say no, because on the other machine it just works, i.e. I connect the camera and download the files.

---

