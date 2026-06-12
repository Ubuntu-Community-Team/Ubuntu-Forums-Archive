---
title: "Can't Install Ubuntu"
date: 2008-10-03
forum: Hardware
---

### Post by carterw65 on 2008-10-03
Hello All!

Yesterday I couldn't even spell linux, today I can't load ubuntu! I have a Dell Inspiron 1200 1.4 GHZ Celeron M, 760 MB Ram, and a clean 40 GB HD.  (I know, I know, you're green with envy!:D) I can hit f12 and get the cd to boot, then I checked the intergrity, passed. Then onto the install. It acts like it is installing, then the screen goes black, flickers a couple of times, and an "X" shows up for my cursor. And after that....well, nothing. It has done this a couple of times and I can't get past it. I downloaded the latest ubuntu yesterday and burned the iso with Infrarecorder. Please help, I feel so trapped inside my Windows!!

Thanks, Bill

---

### Post by Bucky Ball on 2008-10-03
How long did you leave it with the black screen and cross? This bit can sometimes take awhile. Also, which version of Ubuntu are you attempting to install? The desktop i386 version of Hardy 8.04? Sometimes the alternate version does the trick. Make sure you burn slow to a good quality cd and the most reliable method of download is with torrent client. You will find the torrent files by going to alternative downloads at the bottom of the download page I think it is. :)

---

### Post by felker2 on 2008-10-03
Have you tried the Safe Graphics Boot option (second or third in the list)?

---

### Post by carterw65 on 2008-10-03
I thought it was failing when everything just stopped with a black screen and cross. I let it sit the first time for a few minutes and nothing happened. I downloaded the latest version yesterday desktop 8.04 i beleive.

How long should I let it sit?

Thanks,

Bill

---

### Post by carterw65 on 2008-10-03
Do you think it has something to do with graphics? I have not tried that yet. I do not know hardly anything about linux based stuff. Trying to learn. 

Thanks,

Bill

---

### Post by Bucky Ball on 2008-10-03
> **felker2 said:**
> Have you tried the Safe Graphics Boot option (second or third in the list)?

I'd give it 5 then I would try felker2's suggestion then I would try downloading the alternate cd and giving that a go. Your specs shouldn't be a problem. Plenty of RAM for Ubuntu to install and run.

---

### Post by carterw65 on 2008-10-03
OK, I will let you all know what happens. I have a busy day ahead, so I may not get to it until tomorrow. Keep you posted.

Thanks!

---

### Post by iponeverything on 2008-10-03
While is sitting at the X type <ctl><alt><f2>

login 
type:

cd /var/log

if you have a usb flash drive, pop it in and mount it with:

mount /dev/sdb1 /mnt

if does not work, type:
tail /var/log/messages 

to see where flash is and mount it. sd<something>

type:

cp Xorg.0.log /mnt
umount /mnt

take your flash driver to another pc and post your Xorg.0.log

---

### Post by Bucky Ball on 2008-10-03
iponeverything, as Ubuntu is not installed yet, I doubt there will be an Xorg.0.log. :)

---

### Post by carterw65 on 2008-10-03
Thanks for the reply. When I try to get the log I get "No such file or directory"

Here's an update. Sometimes I get past the "X" and then I start getiing I/O errors and it will evtually fail. Once in a while it will start scrolling the I/O errors by the thousands!

Thanks!!!

Bill

---

### Post by Bucky Ball on 2008-10-03
carterw65, I reckon try the alternate installer or try another desktop. The iso download itself may be corrupt, depending on how it was downloaded. Therefore you can burn another disc but it would do the same. If you have the disks, try burning another and see if that is the case.

If you are into torrenting, that is the most reliable way to get the iso. You can get the torrent file from the list at the bottom of the page here:

[http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)

i386 I think would be the one for your machine unless it's 64bit. 

Something springs to mind. Is the 40gb the only drive in the box? There is not SATA and IDE? Just wondering about disconnecting any drive you are not installing to and trying. But maybe the new disc installer first.

---

### Post by carterw65 on 2008-10-03
The HD is the only drive in the box. I did a hash on the iso and it came out good. I am not familiar with torrenting. I looked at the list and I am not sure which one to choose.

I did a chkdsk just to make sure my HD wasn't toast. It came in error free. I wish I could take a screen shot of what is going on.

I have burned several disks. I did one at 1x and it was corrupt. I am not sure what it doesn't like here.

What is the alternate installer?

Just call me Baffled Bill!

Thanks,

Bill

---

### Post by Bucky Ball on 2008-10-04
[ubuntu-8.04.1-alternate-i386.iso]("http://releases.ubuntu.com/8.04/ubuntu-8.04.1-alternate-i386.iso")  

Try that.

From the bottom of this page:

[http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)

:)

---

### Post by carterw65 on 2008-10-07
Well I have figured it out. I used Unetbootin ( I think that's it) to install 8.10 on a flash drive and loaded it from there. I had so much trouble with 8.04 I didn't go back to it. First I tried 7.10 and it worked so I just went straight to 8.10.

Thanks to all for your help. Now....If I could just get this darn PX-500 to work!

Thanks,

Bill

---

