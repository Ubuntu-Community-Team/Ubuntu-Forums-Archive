---
title: "So damn slow tranfer speeds!"
date: 2006-02-08
forum: Hardware &amp; Laptops
---

### Post by pelle.k on 2006-02-08
This is >>really annoying<<

I've been up all night trying to transfer 55 GB from my internal HD to my external USB HD. Copying a file at a time seems to be ok, but when i choose to copy all files at once it starts up nicely, but after a few seconds it halts, and the file dialog windows says "stalled", and then changes to "10 mb/s". So basically it switches between these two modes, and takes for ever to do anything.

It takes a lot of CPU, and my disk cache is eating every last bit of memory availiable.

Maybe i should add that i use kubuntu, but ive tried this commandline too, and i just choked at me as well.
I dont know what to do. This shouldn't be an issue. Can it be more basic than copying files from one drive to another? Advice?

---

### Post by goatflyer on 2006-02-08
Since the cache is filling up, the internal hard drive is not the bottleneck.

So lets look at which USB does your computer and drive support?

Max speed for USB 1.1 is only 12 Mb/sec  Might this be all that your comp or your drive supports? 

If both are USB 2.0 then maybe check if you should have special drivers?

---

### Post by pelle.k on 2006-02-08
I do have USB 2.0. The external drive is a Lacie P3 250 GB, formatted with ext3.
I am tired and stupid :) , so i didn't check the output of syslog or dmesg, which i have done now.
```
Feb  8 05:57:14 localhost kernel: [4296102.871000] SCSI error : <2 0 0 0> return code = 0x70000
Feb  8 05:57:14 localhost kernel: [4296102.871000] end_request: I/O error, dev sdc, sector 459825511
Feb  8 05:57:14 localhost kernel: [4296102.871000] Buffer I/O error on device sdc1, logical block 57478181
Feb  8 05:57:14 localhost kernel: [4296102.871000] lost page write due to I/O error on sdc1

```
Then I tried a kernel from the 2.6.15 series, which seems to have cured the problem. :D
I guess it's time for me to try out dapper anyway.

I do appreciate your help goatflyer!

---

### Post by pelle.k on 2006-02-08
Time for an update:

Maybe i rushed my conclusion a bit...
Allthough kernel 2.6.15 seem to work much better than the 2.6.12 kernel in breezy, my usb hd did eventually reset ehci during heavy loads.
It also seems i'm NOT alone in this matter. Lots of people on furums on the net, have the same problem. There is no apparent solution as of now, so i'll guess i'll just have to wait this one out :(

---

