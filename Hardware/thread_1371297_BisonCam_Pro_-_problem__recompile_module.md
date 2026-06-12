---
title: "BisonCam Pro - problem / recompile module?"
date: 2010-01-03
forum: Hardware
---

### Post by Xerp on 2010-01-03
Hi,

I have a laptop with a built-in webcam which should work, but doesn't.

It is marked as working here:

[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

Its 'BisonCam' - USB ID is 5986:0241. dmesg shows

"No valid video chain found."

I am using Ubuntu 9.10 - fully updated.

I also found this thread which talks about it:

[http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg04136.html](http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg04136.html)

but I'm afraid its way over my level of comprehension!

I tried downloading the latest tarball for uvc and running "make", but it stopped with errors. I would try to make just the modules I need, but I don't know how :(

Does anyone have any ideas / guidance as to how I can get this webcam to work? I'm guessing that the latest version of linux uvc would do it, if only I could get it to compile!

Thanks!

---

### Post by weijoewang on 2010-01-18
Hi Xerp,

This is Michael Wang, and maybe u have read my [_blog_]("http://weijoewang.blogspot.com/2009/10/standard-linux-uvcvideo-doesnt-work-for.html") for the same problem with urs..

I believe that the attachment is what u are looking for...;-)
I don't know ur system so I assumed that it's kernel 2.6.31.x.

Again, it is just a workaround...;-)

Unzip uvcvideo-2.6.31 to ur system, open a terminal and cd into it.
Power-off ur camera first (via hotkey for example).
Then Issue commands:

$ sudo apt-get install build-essential (This is optional..)
$ sudo modprobe -rf uvcvideo
$ make clean; make all

If no errors, you can now install kernel module:
$ sudo make install
$ sync; sync; sudo reboot

Done...;-)
But everytime u update ur kernel, u have to repeat above steps...

---

### Post by narcisgarcia on 2010-01-28
Thanks for the work, Michael Wang.

How about including this patch in the main UVC/V4L stream?
This could make possible that everybody receives updated and good detection+work for the 5986:0241 device.

---

### Post by adenewton on 2010-02-12
This just fixed an issue with the webcam on a no brand laptop I purchased from ebuyer just after Christmas, been searching for the solution for a while, so was glad to find this new post today.

Agree with poster above that this should be submitted to the main stream so that everyone can receive the update.

Thanks Michael.

---

### Post by tw33 on 2010-05-11
This fixes my laptops webcam. I would love to see it built into the main uvc stream as it is annoying to have to keep reapplying it after every kernel upgrade.

---

