---
title: "ASUS G1 webcam in feisty"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by moodog on 2007-04-16
Has anyone had any luck getting the webcam in an ASUS G1 working? I picked up one of these on Friday (after a long wait) and spent a bit of time trying to get it working, but didn't have any luck. I tried with gscpa, but when trying to run camorama it gave an error saying couldn't find /dev/video0. i then used a script I found somewhere to check if /dev/video0 existed, and if not, to create it, but it still didn't work.

any useful tips would be very much appreciated.

---

### Post by argotnaut on 2007-04-21
Have you tried anything other than Camorama? I can't seem to get that to work with much.

---

### Post by luder on 2007-04-26
[This tutorial]("http://hamacker.wordpress.com/2007/03/14/webcam-syntek-semicon-dc-1125-driver-no-ubuntu-feisty/") is in portuguese but if you follow all of the commands you'll get the webcam working.

Basic translation of each step:

1) Update PCI and USB library

2) After lsusb you should get this id, instead:
**Bus 005 Device 004: ID 05e1:0501 Syntek Semiconductor Co., Ltd**

3) Install dependencies

4) Extract kernel sources

5) Some make files use /bin/sh. Ubuntu default is set to 'dash', so you need to remove it - it will change to 'bash' by itself. If you don't want to remove 'dash', then you can try to change sh with **update-alternatives**.

6) Compile the kernel (it will take a lot of time, so go grab a coffee). IIRC, I had to install fakeroot.

7) Create a directory to keep the sources and compile the driver. I had to install subversion to make the svn command work.

After **make driver**, try to run **make install**. If it doesn't work, follow the sudo modprobe block.

Run **camorama** and see if it is working. The image will probably have a blue tint, so under effects add the **Color Correction filter**. If the image is too dark, adjust the white balance as needed.

If you could run **make install**, then you're done. If not, continue. This will make the driver load automatically when you boot:

8 ) Press ALT + F2 and run ‘**gksu gedit /etc/modules**’. Append the lines:
```
# modules for video support
videodev
v4l1-compat

```

9) Press ALT + F2 and run ‘**gksu gedit /etc/rc.local**’. Add the line ```

 insmod /home/<yourlogin>/syntekdriver/trunk/driver/stk11xx.ko

```  _before_ the last line(**exit 0**). Don't forget to replace <yourlogin> with you real user name.

10) Done, it should be working now.

The author says he had success with most video software, except with Ekiga.

This guide should work on many Asus laptops with webcams, not only G1.

Now, I'll be glad if someone can tell me how to put sleep mode and the OLED screen working properly ;).

---

### Post by Xephrey on 2007-04-29
Is there ANY easier way? I have no idea how to do all the crap. I'm not a programmer... 

?

Im running an ASUS F3Jm


-Thanks

---

### Post by lancest on 2007-04-29
This webcam may be working. ASUS
Try this: [http://www.rothlaender.net/a8js.html](http://www.rothlaender.net/a8js.html)
Google it otherwise!   I hope you enjoy the Linux difference.

---

### Post by Xephrey on 2007-05-25
well, I got it working in Camorama, that is a breakthrough in and of itself! But the idea is to have it working for chat in aMSN and Kopete. But when it comes up in those programs, its either flashing black or just really really black - if I look really closely, I can see that its working, but the sliders are locked in position (the contrast / brightness ones). Any more ideas?

---

### Post by robertpolson on 2007-05-28
I followed the guide [http://ubuntuforums.org/showthread.php?p=2699093#post2699093](http://ubuntuforums.org/showthread.php?p=2699093#post2699093)

And have it working, but the colors are a mass. It is as if it is in a Night shot mode, or I can even say black and white.

Also this can be done simply like so:

Download and unpackage the sources - [http://syntekdriver.sourceforge.net/](http://syntekdriver.sourceforge.net/)
cd to the folder where you unpacked the source
make clean
make
modprobe videodev
insmod stk11xx.ko

That's all. Now the webcam is working.

Taken form here: [http://wiki.archlinux.org/index.php/Asus_G1#Webcam](http://wiki.archlinux.org/index.php/Asus_G1#Webcam)

---

### Post by Xephrey on 2007-05-29
The last step gave me this:

insmod: error inserting 'stk11xx.ko': -1 File exists


However, the file is actually there...  I dont understand.

---

### Post by robertpolson on 2007-05-29
Try this for the last 2 commands:

sudo modprobe videodev
sudo insmod stk11xx.ko


When you say the file actually exists, which file are you talking about and where is it specifically located ?

---

### Post by dcomsa on 2007-06-05
hehe, thanks mates. this was the thing that bothered me. i have this asus laptop with ubuntu on it for about 2 years now. i didn't had any clue on how to make the webcam work. the single issue now is that the image is upside down. does anyone hay a hint on this one?
thanks again folks \\:D/

---

### Post by robertpolson on 2007-06-06
What about the quality of the image? Is it good and with right colors ?

---

### Post by dcomsa on 2007-06-07
> **robertpolson said:**
> What about the quality of the image? Is it good and with right colors ?

The quality is ok, but the colors ... well that's something else:). They look like having a sepia effect. Unfortunately, I didn't find the controls to correct that, if those controls even exists. Another issuse that I've seen is that if I use the camera with other apps (like ekiga), the picture is a black square until i move the brightness slider.

---

### Post by stevewabc on 2007-06-07
here this works well for the web cam on the g1 laptops

[http://syntekdriver.sourceforge.net/](http://syntekdriver.sourceforge.net/)

---

### Post by robertpolson on 2007-06-08
> **stevewabc said:**
> here this works well for the web cam on the g1 laptops

[http://syntekdriver.sourceforge.net/](http://syntekdriver.sourceforge.net/)

No, it does not work well.

Read  posy #7

The colors are not working properly.

---

### Post by adam_r on 2007-07-04
i didnt want to add a new thread, does anyone know of a "MSN Messenger" compatible program that works with this driver, because the only place i'm able to use the cam is "camorama" and allmost "keopte" but that dosent help much, so did anyone had any luck with a diffrent prog? (i tried kmess, aMsn, Licq, Keopte)

---

### Post by gobbles414 on 2007-08-11
Hi all,

I just followed robertpolson's (EDIT) procedure on my Asus G1 and it worked as advertised. Thanks to all of those who worked on the driver. You Rock :guitar: ! I did get an error part way through the install, but I just ignored it and completed the last two commands as sudo. I too get a sort of "night vision" effect instead of full color. But that's not worth whining about as far as I am concerned. Besides, I am sure that the issue will be resolved in a future release of the driver.

Regarding Adam's question, Mercury Messenger might work. I tried to get the webcam working using the wizard in MM. It was detected but I was not allowed to select it and continue the wizard. That could be because I didn't restart my computer after installing the driver. It could also be because I have sort of a hacked version of MM installed right now. I'll report back if/when I learn more.

EDIT: Luder's solution looked a bit too complex for me.

---

### Post by davidme on 2007-11-20
Any update on the issue ?

---

### Post by gobbles414 on 2007-12-23
davidme,

I can report that upgrading to Ubuntu 7.10 using the Update Manager caused the webcam to no longer work in Ubuntu. However, I see that there is a new release of the webcam driver. I will try installing it as my time allows, and report back.

---

### Post by gobbles414 on 2007-12-31
Hi all,

As I had to reinstall Ubuntu Gusty on my laptop anyway, I took the opportunity to reinstall the webcam driver. I did have to tweak the directions a little bit. I used the directions in the README plus the procedure from [here]("http://sourceforge.net/forum/forum.php?thread_id=1876454&forum_id=616183") (the posts at 2007-11-25 07:06 and 2007-11-25 16:13). Color is still incorrect. But the README describes a trial-and-error method for fixing that problem. If I do not report back soon, assume that I have fixed the color.

**2007-11-25 07:06**
modprobe videodev 
insmod stk11xx.ko

**2007-11-25 16:13**
sudo cp stk11xx.ko /lib/modules/2.6.22-14-generic/kernel/drivers/media/video/usbvideo/stk11xx.ko 
depmod -a 

and then just edit your /etc/modules: 
videodev 
stk11xx 
 
save and exit 
now type: 
modprobe videodev 
modprobe stk11xx 
 
it will work after restart too.

---

### Post by davidme on 2007-12-31
If you will get it fully working, then please let us all know the exact steps from the very beginning that you took to make it work.

---

### Post by gobbles414 on 2008-01-02
davidme,

I am able to get very close to an accurate image in a program called Camorama by applying the "Color Correction" effect. I have absolutely no idea if modifications made to the webcam in Camorama are applied system-wide or not; and I won't have the time to mess with the command line options for a few days at least. I'll try to keep you up-to-date as my time allows.

---

### Post by gobbles414 on 2008-02-13
Hi all,

Again, I have not had a chance to tinker with the command line settings for the webcam. However, I have discovered that changing to *Video for Linux 2* in *System => Preferences => Multimedia Systems Selector => Video* results in a perfect picture in the test window. Note, you may need to go *System => Preferences => Main Menu* to enable the Multimedia Systems Selector. So, I guess that any application that supports *Video for Linux 2* will capture/display a correct picture.

---

