---
title: "Webcam wont work what am I doing wrong?"
date: 2006-04-09
forum: Hardware &amp; Laptops
---

### Post by PhilJ on 2006-04-09
Hi all,
 I downloaded Webcam with synaptic and checked dependencies which all appear to be there. I couldnt get that to recognise my camera (which shows up in device manager) . Downloaded Easycam2 to see if that would work. Found camera but get would not make error. Checked in config and found sqcam driver was located at sourceforge and downloaded it. Used Alien to covert tgz to deb. dpkg -i  filename to install. If I type webcam in terminal I get the following 
reading config file: /home/phillip/.webcamrc
v4l2: open /dev/video0: No such device
v4l2: open /dev/video0: No such device
v4l: open /dev/video0: No such device
no grabber device available

From Easycam2 startup screen choose camera
Bus 001 Device 003: ID 2770:9120 NHJ, Ltd Che-ez! Snap / iClick Tiny VGA Digital Camera

can anyone tell me where I am going wrong?:confused: 
thanks 

Philj 
will have to return later tonight. Under orders from wife:mrgreen:

edit
 tried ln -s /dev/video0 /dev/video . that I found in another thread but no luck

---

### Post by PhilJ on 2006-04-09
help please

bump

philj

---

### Post by dpicker on 2006-04-09
Does your webcam work in the GnomeMeeting application?

---

### Post by PhilJ on 2006-04-10
Hi thanks for reply,
nope cant get it to work in anything. 
Media selector comes up with cant make pipeline for v42 /v42l
have tried everthing I can think of. (newbie to linux)

philj

---

### Post by PhilJ on 2006-04-11
bump

---

### Post by mp3guy on 2006-04-15
Got the same camera, having troubling compiling/installing any of the sqcam drivers

---

### Post by pgatrick on 2006-10-09
Got the same cam also, but can't get the drivers to compile.

---

### Post by pgatrick on 2006-10-09
Never mind, I'm an idiot. the sqcam_for_kernel_2.6.... file works.:rolleyes:
EDIT: Kinda works, you have to change some remap_page_range to remap_pfn_range in sq905.c on line 816, and it will compile and modprobe sqcam works.. But for some reason /dev/video0 isn't working. :confused:
Turns out it uses /dev/video.. But I can't get camorama to load /dev/video, camorama -d /dev/video just hangs, and xawtv has soem problem. ](*,)

---

### Post by yusufk on 2007-02-19
Hi,

I also downloaded the sqcam source, edited line 808 to

```

 if (remap_pfn_range(vma, start, page>>PAGE_SHIFT, PAGE_SIZE, PAGE_SHARED))

```

and also commented out line 856 to work on kernel  > 2.6.16

```

        //.owner          = THIS_MODULE,

```

make worked fine, copied .ko file /lib/modules/2.6.17-11-386/kernel/drivers/usb/media/
did sudo depmod -a 

Now what? When I plug the device in nothing happens?

No /dev/video0 ???

---

### Post by crusti on 2007-03-25
While I don't have a specific answer to your question, I may have a bit of useful info as to how this whole thing went for me.

- I downloaded the cvs version using:
**$ cvs -z3 -d:pserver:anonymous@sqcam.cvs.sourceforge.net:/cvsroot/sqcam co -P sqcam26**
which created a folder in my current directory called sqcam26 with the source files in it.

- I entered the sqcam26 folder (that just got created):
**$ cd sqcam26**

- Ran the command:
**$ make**
and I got a bunch of compile errors. The first error was that there was no gamma.h file, and there were also errors about not mixing declarations with code, and an error about a pointer.

I tried installing EasyCam2 and gphoto2 but EasyCam2 still wouldn't compile my driver. Anyway, it seemed that g++ got installed when I installed Easycam2 so that's good I guess...I don't know if g++ is used in this compilation. Anyway...moving right along...

In order to get it to compile:

- Added a symbolic link in /usr/src so I didn't have to change the Makefile default directory of /usr/src/linux. My installation had no "linux" entry in /usr/src, only linux-2.6.17.11 and linux-2.6.17.11-generic. So I created a symbolic link /usr/src/linux pointing to /usr/src/linux-2.6.17.11-generic, so the line "KERNEL_DIR := /usr/src/linux/" in the Makefile would point where I needed it to point.
**$ sudo ln -s /usr/src/linux-2.6.17.11-generic /usr/src/linux**

- Created the folder /lib/modules/`uname -r`/kernel/drivers/usb/media because that didn't exist.
**$ sudo mkdir /lib/modules/`uname -r`/kernel/drivers/usb/media**

- Ran the command:
**$ gcc -std=c99 -o makegamma -lm makegamma.c**
which made the executable file makegamma

- Ran the command:
**$ ./makegamma**
which created the gamma.h file

- Ran the command:
**$ make**
and this still produced most of the original errors. It was time to go medieval on sq905.c and that's what I did. Basically I used the line number of the first compile error and attempted to fix that. Overall I think I fixed three things:
= Removed the reference to remap_page_range altogether because I didn't need it and it was confusing me.
= separated declarations from code where specified
= commented out the line ".owner          = THIS_MODULE,"

- Then I recompiled using the make command:
**$ make**
and the sqcam.ko file was created in the sqcam26 folder I'd been working in.

Here's my output:
-------------------------------------------------------------------------------------
**$ make**
make -C /usr/src/linux/ SUBDIRS=/home/me/sqcam26 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /home/me/sqcam26/sq905.o
  LD [M]  /home/me/sqcam26/sqcam.o
  Building modules, stage 2.
  MODPOST
  CC      /home/me/sqcam26/sqcam.mod.o
  LD [M]  /home/me/sqcam26/sqcam.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
**$ ls**
CVS Makefile makegamma.c README sq905.o sqcam.mod.c sqcam.o
gamma.h makegamma Modules.symvers sq905.c sqcam.ko sqcam.mod.o usbvideo.h
**$ sudo updatedb**
Password:
**$ locate sqcam.ko**
/home/me/sqcam26/.sqcam.ko.cmd
/home/me/sqcam26/sqcam.ko
-------------------------------------------------------------------------------------

- Copied the sqcam.ko file to its correct location:
**$ sudo cp sqcam.ko /lib/modules/`uname -r`/kernel/drivers/usb/media**

- Ran the depmod command:
**$ sudo depmod -a**

- Inserted the kernel module:
**$ sudo modprobe sqcam**


The camera is shown in the devices as a "Che-ez! Snap", and when I plug it in I get a prompt to download photos from it. It's recognized in the photo-importing dialog as an "Argus DC-1510" and the error output shows:
*An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.*

I followed this thread [http://ubuntuforums.org/showthread.php?t=383058&page=1](http://ubuntuforums.org/showthread.php?t=383058&page=1)
to downgrade libgphoto2-2 and libgphoto2-port0 from 2.3.0 to 2.2.1
and then I locked the version for each of those packages so I wouldn't get bugged about upgrading them (though that might not be such a good idea in the long run). Unfortunately, I made the mistake of selecting both at the same time and trying to downgrade both at the same time and it uninstalled other packages too, and I had to re-install them. So read the whole thread before you do it and save yourself the hassle.

After having downgraded those libraries I was able to use a "$ gphoto2 -P" command to communicate with the camera for downloading still pictures that I took just by clicking the button on the camera as you would do if you were outside or something.
Camorama still gave me an error *"Could not connect to video device (/dev/video0). Please check connection."*

I installed GQcam and I was able to see myself immediately, but the colors are reversed.
It turns out GQcam has a RGB->BGR color reversal setting, so I unchecked that and the color is fine.
I also tried effectv and that showed me in correct color as well. If you've never tried effectv, it's VERY cool.

I'm not sure where to go from here (like how to actually make a video with sound) but at least I have something showing video from my webcam.


I hope this was helpful in some way.

If you want me to post the full text of my edited sqcam.c I can do that. It's pretty long, that's why I didn't post it.

Cheers,
crusti

---

### Post by Pitxyoki on 2007-05-06
Wow! That was great!

This was the last thing I needed to have all hardware recognized by Ubuntu... Now I AM happy with it! :)

Perhaps you could try to create an HOWTO for this... I had followed more or less the same steps you provided and, after installing gqcam, I could finally see myself! :)

Here are the steps I followed:
```

$ cvs -z3 -d:pserver:anonymous@sqcam.cvs.sourceforge.net:/cvsroot/sqcam co -P sqcam26

$ cd sqcam26
```

This is what you can do to compile correctly without errors:
```
$ gedit Makefile
```
Edit the KERNEL_DIR line. It should be like this:
KERNEL_DIR := /lib/modules/`uname -r`/build

Save and exit

```
$gedit sq905.c
```
scroll to line 1183 and comment these lines:
	```
while (size > 0) {
		page = usbvideo_kvirt_to_pa(pos);
//#ifdef HAS_REMAP_PAGE_RANGE
//		if (remap_page_range(vma, start, page, PAGE_SIZE,
//                     PAGE_SHARED)) {
//#else
		if (remap_pfn_range(vma, start, page >> PAGE_SHIFT, PAGE_SIZE,
                    PAGE_SHARED)) {
//#endif
			up(&cam->busy_lock);
			return -EAGAIN;
		}
```

[COLOR="Red"](just add those "//"s)[/COLOR]
Save and exit

```
$ make makegamma
$ make
$ sudo make install
```

The make command will give some warnings, but let's hope it isn't anything too bad. :s

And to check that the camera is working,
```
$ sudo apt-get install gqcam
$ gqcam
```


I'm sorry for the messy post, but I'm in a rush now. I will clean it up as soon as I can. I just wanted to show you the way I finally accomplished this.

As I told you, I can only see images through gqcam. I would love to be able to use this with aMSN. It seems to recognise the cam, but it doesn't show any image  though.

[EDIT]I finally made it to make this cam compatible with aMSN and am currently testing video recording and other functions. I will post news shortly. :)[/EDIT]

---

### Post by Pitxyoki on 2007-05-07
Finally I made it to use this webcam's video successfully!
I have created an HOWTO here: [http://ubuntuforums.org/showthread.php?t=435463](http://ubuntuforums.org/showthread.php?t=435463)
Please give me any feedback if that goes well or not with you. :)

---

