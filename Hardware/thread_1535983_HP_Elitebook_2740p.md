---
title: "HP Elitebook 2740p"
date: 2010-07-21
forum: Hardware
---

### Post by rth on 2010-07-21
I have an HP Elitebook 2740p and it doesn't seem to let me install Ubuntu. I can boot (via USB), but once I pick live CD or install Ubuntu, it goes nowhere. So, I'm guessing hardware incompatibility...

Doing some searching on the tubes, I haven't seen anyone else with a 2740p and Ubuntu (or Linux for that matter).

Is there a way to see where the problem may lie in terms of hardware? I tried the 10.04 final ISO as well as the 10.10 release from earlier in July, both 64-bit.

---

### Post by pytheas22 on 2010-07-21
You might have better luck using the [Alternate Installation CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

It's also possible that the ISO image you used to make your live USB was corrupted; did you check the md5sum after downloading, or try running the utility at the boot screen (i.e., the same screen where you can select "Install Ubuntu" or boot in live mode) to verify the contents of the disk?

---

### Post by rth on 2010-07-21
I'll give the alternate CD a whirl and see what happens. Given that I tried two different ISOs, I'm pretty sure that both weren't corrupt...

---

### Post by rth on 2010-08-02
I get far enough in the Alternate CD to be able to start the process. It then asks me for the path to the CD, as I'm using the SD card, it wasn't straightforward. I'm thinking I need to do 
```
lsscsi
```
or similar to find the /dev/XXXX for my SD card as this laptop doesn't have an optical drive unless I get the docking station...

---

### Post by pytheas22 on 2010-08-02
You could try giving it the /dev/xxxx for your device and see if it works.  If it doesn't, let me know; I've had some experience with the alternate installer not knowing where media is located and might be able to offer some tips if you remain stuck.

---

