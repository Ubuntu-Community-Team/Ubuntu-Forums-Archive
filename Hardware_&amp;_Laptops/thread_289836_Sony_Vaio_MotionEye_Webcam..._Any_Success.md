---
title: "Sony Vaio MotionEye Webcam... Any Success?"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by SendDerek on 2006-10-31
On my Sony Vaio VGN-FE550G, I havn't had any luck in tracking down a solution to getting the built-in MotionEye webcam to work and I was wondering if there has been any success or progress on these forums.  

So, has anybody been able to get these cameras to work?  What's the word?

Thanks for the help in advance!


**Things I have tried: **
EasyCam2
Camorama Webcam Viewer
Video4Linux (v4l)
motioneye from the repositories
[SIZE="1"]> 
This program captures images and movies with your Sony Vaio
PictureBook Motion Eye camera. Motioneye requires the Motion Eye Camera
Driver (kernel > 2.4.7) since it uses the private interface
for accessing some extended parameters (camera sharpness, agc, video
framerate), the shapshot and the mjpeg capture facilities.

You can capture ppm or jpg snapshots or mjpeg compressed video.
[/SIZE]


**I have checked these resources:**
[http://www.qbik.ch/usb/devices/search_res.php?pattern=sony](http://www.qbik.ch/usb/devices/search_res.php?pattern=sony)
[http://www.exploits.org/v4l/](http://www.exploits.org/v4l/)
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

When I open EasyCam2 from the administration menu, it gives me this error message:
> 
No camera, or no compatible camera found


When I open Camorama from the Graphics menu, it gives me this error message:
> 
Could not connect to video device (/dev/video0).
Please check connection.


---

### Post by KaMZaTa on 2006-11-02
I've a Sony Vaio VGN-FE21M with Motion Eye camera and I'd like know to how I can do it works...

---

### Post by SendDerek on 2006-11-02
Well, good.  I'm not the only one! lol

Now, keymaster just has to post here so we can get some more support for this little "project".

---

### Post by hayalperest on 2006-11-04
I've  a Sony Vaio VGN-FE11M with Motion Eye camera also, and waiting for solution. I'm with you. Who will help us?

---

### Post by SendDerek on 2006-11-05
Since we probably need somebody with knowledge of how to build/make hardware drivers, who would we talk to in order to get help with this?

It's something that I (and apparently a lot of other people) would like to be able to accomplish.

---

### Post by SendDerek on 2006-11-05
An interesting link to check out??

[http://www.popies.net/meye/](http://www.popies.net/meye/)

Unfortunatly, I can only search for things related to the installation of these cameras but I'm too much of a newb to figure out how to get them to work.  A how-to would definatly be very cool.

---

### Post by KaMZaTa on 2006-11-06
This is the output of the command *lsusb* type in my pc:

```
Bus 003 Device 002: ID 046d:c518 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 044e:300c Alps Electric Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 054c:0281 Sony Corp. 
Bus 001 Device 005: ID 0ac8:c002 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 0000:0000  

```

The Sony Vaio Web Camera ID's should be **054c:0281**. It's the same of yours?

---

### Post by SendDerek on 2006-11-06
I'll have to try this when I get back home to let you know.

---

### Post by SendDerek on 2006-11-06
I tried to type lsubs without any success.  I tried sudo lsubs without any success.

I found lsusb to work though.  Here's the output:

> 
Bus 005 Device 004: ID 0ac8:c002 Z-Star Microelectronics Corp.
Bus 005 Device 003: ID 054c:0281 Sony Corp.
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 046d:c510 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000


And, yup!  The Sony Vaio Web Camera ID's is 054c:0281.

---

### Post by KaMZaTa on 2006-11-07
Ok, this is already a good new. But, now, how can we do to gettin' it works? :)

---

### Post by Zhukov on 2006-11-07
There are no drivers.
A project was started but nothing was achieved.
You must catch usb information exchange with Windows and reverse engineer the driver.
I also have that camera and im trying to get my hands dirty with the driver development for months but haven't got the time yet.

---

### Post by SendDerek on 2006-11-08
That is the question KaMZaTa!  lol

We can't let this thread die...  we've got to get as much support as possible. ;)

Or at least keep it alive until somebody tells us it can't be done.

---

### Post by SendDerek on 2006-11-08
Here's a nice link.

[http://tuxmobil.org/sony.html](http://tuxmobil.org/sony.html)

At the bottom of the page, there are a bunch of links for the sony laptops.  Maybe this is a good place to start?

---

### Post by SendDerek on 2006-11-08
Oops, sorry Zhukov.  I missed your post somehow.  

What a bummer... it seems like the tools are all there though. motioneye, meye, video4linux.

---

### Post by Zhukov on 2006-11-08
There some issues to take in account:

-> This is a different Motion Eye, it's USB connected.
-> Although there is no driver as it is USB it is a lot easier to develop the driver.

I'll try to find some time this month and (hope) to get started somehow.
I believe the new macs also have a USB connected webcam and a driver was released recently, i'll try to get in touch with the developer and see what comes out.

Here is the page of he project I mentioned earlier:
[http://r-engine.sourceforge.net/](http://r-engine.sourceforge.net/)

And some other interesting links:
[http://www.linuxjournal.com/article/7353](http://www.linuxjournal.com/article/7353)
[http://www.linuxjournal.com/article/4786](http://www.linuxjournal.com/article/4786)
[http://linuxtv.org/v4lwiki/index.php/USBVideo](http://linuxtv.org/v4lwiki/index.php/USBVideo)

---

### Post by SendDerek on 2006-11-08
Hey, thanks a lot for your interest and help.  We'd appreciate any help we can get on this "little" project.

In the meantime, I'm going to read up on the material you presented us with.

---

### Post by KaMZaTa on 2006-11-26
Any new boyz?

---

### Post by Zhukov on 2006-11-27
No news here :S

---

### Post by guitarist549 on 2006-12-04
Gah... I really wish ricoh would release drivers for this stupid webcam.. it's the only thing that is making me seriously consider going back to Windows... That and the fingerprint sensor.

---

### Post by thumper on 2006-12-05
Aparently there are some pam modules for biometrics, so technically it is possible to plug into the fingerprint sensor (I have one too).

But AFAIK what is missing is the training app and nice gui.

---

### Post by Zhukov on 2006-12-05
The finger sensors can be tricked :P

---

### Post by guitarist549 on 2006-12-08
Would there be any way of installing the motioneye drivers in Wine? It wouldn't be the best set-up but, if it worked, we would be able to use the camera.

---

### Post by klmklm1967 on 2006-12-13
I have the Sony Vaio SZ330P Laptop

I receive the following when I do a lsusb
(typing the applicable lines since I am not on the laptop at the moment)

05ca:1830 Ricoh Co., Ltd
0483:2016 SGS Thompson Microelectronics Fingerprint Reader

I would assume that the Ricoh entry relates to the motion eye camera...

---

### Post by KaMZaTa on 2006-12-15
Any news?

---

### Post by Juan_Garcia on 2006-12-25
Hello.

First, sorry for my english (im from Spain). The device of webcam is not Sony Corp... It is 0ac8:c002 Z-Star microelectronics Corp.

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

I have installed driver (gspcav1) in my vaio fe31z (0ac8:0002) and now... I have working the webcam :-D :-D .

See you.

---

### Post by Zhukov on 2006-12-25
Congratulations! :D
And thanks a lot, of course! 
Now everything works on my laptop :)

---

### Post by PierreNel on 2006-12-30
Okay, I've also got the Bus 001 Device 002: ID 0ac8:c002 Z-Star Microelectronics Corp. in my Sony Vaio FE28GP - I've modprobed the spca module, the meye module etc etc, but applications like camorama are still looking for a device called /dev/video0 which doesn't exist: any ideas how I go about fixing that? :neutral:

---

### Post by KaMZaTa on 2007-01-02
Great! It works! Unbelievable! Now everything works in my laptop to :)

---

### Post by KaMZaTa on 2007-01-02
**How To Install:**
[list]
[*] Download the driver [here](http://mxhaard.free.fr/spca50x/Download/gspcav1-20061216.tar.gz)
[*] Extract the archive.
[*] After extract, you must go into directory created.
[*] Compile the driver:
```
make
```
[*] Install the driver:
```
sudo make install
```
[*] Reboot your machine
[/list]

_Note_: If you want Test your Webcam you can install *Camorama* (*sudo apt-get install camorama*)

---

### Post by hayalperest on 2007-01-05
thanks a lot... thanks a lot... my webcam is working :) :)
If u have problems on compiling. U have to make this first.
For installing kernel source 
sudo apt-get install linux-source-2.6.15
cd /usr/src
sudo tar -xvjf linux-source-2.6.15.tar.bz2
sudo ln  -s /usr/src/linux-source-2.6.15 /lib/modules/2.6.15-27-386/build

and last

sudo aptitude install linux-headers-'uname -r'
now u can compile

thaks vaio-ubuntu club and sorry for my good english :)

---

### Post by StyleWarZ on 2007-01-06
Hello everyone

Found your Thread about the Cam i have tried your description of how to install it.

```
**Distro:**Kubuntu 6.10 Edgy
**Kernel:** 2.6.17-10-generic
**lsusb:**
style@slim:~/cam/gspcav1-20061216$ lsusb
Bus 005 Device 003: ID 054c:0281 Sony Corp.
Bus 005 Device 006: ID 046d:c510 Logitech, Inc.
Bus 005 Device 002: ID 05e3:0606 Genesys Logic, Inc.
Bus 005 Device 005: ID 05ca:1830 Ricoh Co., Ltd
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 0000:0000
```

I installed the gspcav1-20061216 package with make; sudo make install. Now errors occurd. Then you write i have to reboot!? Anyways.. Done.. But unfurtanatly i dont get a device.
I read in a post about modprobing. So i tried it with sudo modprobe meye. It loaded and dmesg says this:
```
[17180177.444000] Linux video capture interface: v1.00
[17180177.460000] meye: using 2 buffers with 600k (1200k total)for capture
```
But i dont get a device. Can somebody help me?!

Sorry for misspelling (Switzerland) and a big thx

Style

---

### Post by nofaber on 2007-01-07
Hello,

@StyleWarZ : I have exacly the same problem. 

In lsusb, the following is the webcam (I'm sure of this):
```

Bus 005 Device 004: ID 05ca:1830 Ricoh Co., Ltd

```

And I have exactly the same messages in dmesg.

So I think we should find a driver for Ricoh device...

I have not found it yet ](*,) 

Maybe someone can help :confused: 

nofaber

---

### Post by nofaber on 2007-01-07
Ok after more search the response is that there is no linux driver for ricoh webcam

see the following link [http://avilella.googlepages.com/vaiosz]("http://avilella.googlepages.com/vaiosz")

And maybe sign the letter to Ricoh to ask the for a linux driver

nofaber

---

### Post by StyleWarZ on 2007-01-08
Well and how did the others get der cams to work? They have the same one! It's the only thing that is not working on my Notebook and it would be a blast to see myself :P (then i can get rid of the mirror ;) )

---

### Post by nofaber on 2007-01-08
No, the others have:
```
0ac8:c002 Z-Star microelectronics Corp.
```
And we have:
```
05ca:1830 Ricoh Co., Ltd 
```

These are not the same ! and the driver for Z-Start does exist whereas the driver for ricoh does not :( 

nofaber

---

### Post by jackhynes on 2007-01-14
The latest release of the driver is [here]("http://mxhaard.free.fr/download.html"). They seem to remove any older versions.

---

### Post by alberto666 on 2007-01-19
> **StyleWarZ said:**
> Well and how did the others get der cams to work? They have the same one! It's the only thing that is not working on my Notebook and it would be a blast to see myself :P (then i can get rid of the mirror ;) )

Is is possible to success with:
Bus 005 Device 004: ID 0ac8:c002 Z-Star Microelectronics Corp.
camera?

Where can I find the information?

Thanks!

---

### Post by auscult on 2007-02-05
Hi.  I'm bumping this because I cannot find the updated drivers.  Could someone point me through where to get the driver for:
ID 0ac8:c002 Z-Star Microelectronics Corp.

I also could use a little help on how to install the driver.  Thanks guys!  Ben

---

### Post by auscult on 2007-02-05
Nevermind..... i got it to work....

basically for any new guys out there:

go to [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

Download which ever version you need for the kernel you have.

then unpackage the tar file

open terminal and cd to the folder

then type these two commands

make
sudo make install

---

### Post by paulflook on 2007-02-14
hi all,

I just wanted to add my experience with the motioneye, im running ubuntu 6 (running fluxbox and idesk as my interface) on an old pcg-c1f (p266mmx with 128mb ram, 4.6gb h/d) im actually surprised at how quick it is! 

the only piece of hardware i cannot install is as you guessed - the motion eye.

the only information ive got so far is that its a pci device yet "scanpci" shows no information about any capture device. Apparantly this version of the motion eye maybe the version on the actual neomagic graphics bus, which there is no information.

Does anyone here know of any utils that i could try to scan for this hardware to get a bit more info about it? 

Thankyou and good luck in trying to get it working!

---

### Post by jnorth on 2007-03-03
actually, a ricoh driver does exist.  i use a vgn-sz220 with the ricoh device and this driver is working for me:
[http://lsb.blogdns.net/ry5u870](http://lsb.blogdns.net/ry5u870)

download link at the bottom

notes - does not work in camorama

---

### Post by guitarist549 on 2007-03-04
Yes, the drivers from the post above me do work.
Thank God!
The only problem I see now is that with Kopete, the preview screen shows everything with a green tint, and with a darkened bar near the bottom.

---

### Post by jnorth on 2007-03-04
yeah - this one still has issues, but at least i can see myself now :)

---

### Post by guitarist549 on 2007-03-04
> **jnorth said:**
> yeah - this one still has issues, but at least i can see myself now :)

Yes, it's very nice to have. The webcam is really the only reason I keep a Windows Partition. That and the biometric sensor.

Does the camera work better with any other programs with this driver?

---

### Post by jnorth on 2007-03-04
> **guitarist549 said:**
> Yes, it's very nice to have. The webcam is really the only reason I keep a Windows Partition. That and the biometric sensor.

Does the camera work better with any other programs with this driver?

Seems to work well with xawtv, webcam/webcamd, camstream, gqcam, basically anything that can use video4linux devices...

How are you testing with Kopete, I'm interested to see what you are talking about with the weird display?  I'm used to Gaim so nto familiar with Kopete

---

### Post by Zhukov on 2007-03-05
That's akward has I would expect Kopete to use the video4linux interface (I'm assuming your camera worked ok with other programs).
Maybe it is just some settings.

---

### Post by guitarist549 on 2007-03-08
> **Zhukov said:**
> That's akward has I would expect Kopete to use the video4linux interface (I'm assuming your camera worked ok with other programs).
Maybe it is just some settings.

I suspect it is, but I'm not sure as to how to change them other than what Kopete lets you chage... but this is as good as I've gotten it:

[http://i17.tinypic.com/2j287sn.png](http://i17.tinypic.com/2j287sn.png)

The problem seems to be with objects that are too bright... my fingers on that pic are under direct light from a lamp above and so have that pink band going across.

---

### Post by jnorth on 2007-03-08
> **guitarist549 said:**
> I suspect it is, but I'm not sure as to how to change them other than what Kopete lets you chage... but this is as good as I've gotten it:

[http://i17.tinypic.com/2j287sn.png](http://i17.tinypic.com/2j287sn.png)

The problem seems to be with objects that are too bright... my fingers on that pic are under direct light from a lamp above and so have that pink band going across.

Now that's weird... I have the same problem with Kopete (now that I figured out how to use it)...  only I have green bands, more dense, not quite as prominent as the pink ones in yours.  Doesn't seem to change much with light in my case either.

The thing is that the camera works fine with say xawtv for example - matter of fact for me it looks even better in xawtv than it ever did under Windows.

Now - I have discovered a problem with xawtv also - it doesn't work if you're using the Nvidia card - which I almost always am... otherwise good though.

---

### Post by fdrake on 2007-03-09
finaly i'm able to use my webcam!!!!

---

### Post by G-Izzat on 2007-03-26
tried the driver. won't work on my sz43.

> Bus 005 Device 006: ID 05ca:1835 Ricoh Co., Ltd 


anyone can help me out?

---

### Post by gigi on 2007-04-01
Just to give an aditional solution how I came to success.
I have got an Sony Vaio VGN-SZ3HP

Download the current driver ( ricoh-webcam-r5u870_0.9.1-1.tar.gz  )from Page:
[http://www.arakhne.org/packages/pool/ricoh-webcam-r5u870/](http://www.arakhne.org/packages/pool/ricoh-webcam-r5u870/)


save the file somewhere open a console
> gunzip ricoh-webcam-r5u870_0.9.1-1.tar.gz
> tar xvf ricoh-webcam-r5u870_0.9.1-1.tar
>cd ricoh-webcam-r5u870-0.9.1/upstream/r5u870-0.9.1
>make
>make install

to see a picture i installed xawtv
apt-get install xawtv

reboot and voila after starting xawtv I could see myself :-))))))

There is also a package for the driver on this page (seen later)
[http://lsb.blogdns.net/ry5u870/](http://lsb.blogdns.net/ry5u870/)


Hope this can help someone to get the camera work

---

### Post by astadolfo3 on 2007-04-04
Hello,

I have an SZ450, and my lsusb shows:

Bus 005 Device 005: ID 05ca:1835 Ricoh Co., Ltd 

I installed the drivers mentioned above (r5u870-0.9.0) following the instructions and got no errors. However the camera does not work.

Any ideas?

thanks

---

### Post by fdrake on 2007-04-04
when you run the application what does it say (are you using camorama?)
can you paste here the the make and make install output.

---

### Post by Dafydd on 2007-04-07
> **fdrake said:**
> when you run the application what does it say (are you using camorama?)
can you paste here the the make and make install output.


I'm in the same problem (and have been since I started using Ubuntu 18 months ago on a Sony Vaio PCG-TR5MP with a Motion Eye - Bus 002 Device 002: ID 054c:0107 Sony Corp. VCC-U01 Visual Communication Camera).

Just done installed gspcav1-20070110 but to no avail.

I've sort of given up but occasionally check the forums to see if things have changed.


My understanding is that the motioneye's with 054c:0107 and the above Ricoh  (05ca:1835)  do not work under Linux...

Is that right? Or has anyone had any luck?

Dafydd

---

### Post by jnorth on 2007-04-07
> **Dafydd said:**
> I'm in the same problem (and have been since I started using Ubuntu 18 months ago on a Sony Vaio PCG-TR5MP with a Motion Eye - Bus 002 Device 002: ID 054c:0107 Sony Corp. VCC-U01 Visual Communication Camera).

Just done installed gspcav1-20070110 but to no avail.

I've sort of given up but occasionally check the forums to see if things have changed.


My understanding is that the motioneye's with 054c:0107 and the above Ricoh  (05ca:1835)  do not work under Linux...

Is that right? Or has anyone had any luck?

Dafydd

Nope - read the rest of this thread ;)

Drivers exist and work... links in thread.  I'm chatting with Kopete right now using my Ricoh motioneye.

---

### Post by nowamacuser on 2007-04-08
Hello,

I joined this forum because of finding this after a google search. I'm having the same issues with my VAIO inbuilt webcam. The motioneye. My issues are after installing software on my computer then I get the same error message.

"No Input" on the VAIO camera utility. MSN reports that the camera isn't there or in use.

I'm running Windows Vista and after installing Office 2003, I get the problems. Uninstall and it's fine. I've advised sony of the problem and the only support they tell me is not to use Office. It also happens after installing internet security (no matter which one). I'm not going to not run any kind of security software. Seems crazy with the amount of adware and viruses circulating!

I'm going to try the software included here and will report back after.

Thank you,
Lisa

---

### Post by nowamacuser on 2007-04-08
Oops nevermind. 

I see this is for Linux users. I guess my webcam will never work and Sony support just sucks on the matter :(

If anyone knows of a fix for Windows users on this please PM me.

Thanks,
Lisa

---

### Post by Dafydd on 2007-04-08
> **jnorth said:**
> Nope - read the rest of this thread ;)

Drivers exist and work... links in thread.  I'm chatting with Kopete right now using my Ricoh motioneye.

I wish I were wrong but...

"Bus 005 Device 004: ID 05ca:1830 Ricoh Co., Ltd" appears to be supported.

Unfortunately "Bus 002 Device 002: ID 054c:0107 Sony Corp. VCC-U01 Visual Communication Camera" DOES NOT appear to be supported.

Next time I buy a computer it will NOT be Sony. Just trying to get extra RAM was a nightmare (two months wait to be told that it was no longer available even though another local store sold me the kingston RAM at a third of the price).

The webcam, though, is the only thing that does not work under linux.

daf

---

### Post by jnorth on 2007-04-08
> **Dafydd said:**
> I wish I were wrong but...

"Bus 005 Device 004: ID 05ca:1830 Ricoh Co., Ltd" appears to be supported.

Unfortunately "Bus 002 Device 002: ID 054c:0107 Sony Corp. VCC-U01 Visual Communication Camera" DOES NOT appear to be supported.

Next time I buy a computer it will NOT be Sony. Just trying to get extra RAM was a nightmare (two months wait to be told that it was no longer available even though another local store sold me the kingston RAM at a third of the price).

The webcam, though, is the only thing that does not work under linux.

daf

Yeah, their support sucks.  Sorry dude, I saw other posts in the first of this thread that covered a "Sony Corp" device and assumed that was yours.

Ahh well, guess you won't be using it :)

---

### Post by sheltered on 2007-04-16
Hi I'm using Sony SZ28 and I've got my webcam to work using Ricoh R5U870 Webcam Driver for Linux

[http://lsb.blogdns.net/ry5u870/](http://lsb.blogdns.net/ry5u870/) <== try it out

---

### Post by SendDerek on 2007-04-30
I just finished reading an article on how one guy managed to create some 235 web cam drivers for linux.  I checked out his homepage and this is what I found:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

Z-STAR 	* 	Another v4L1 driver 	* 	 ZC030X based Cameras 	

Logitech 	117 	0x046d 	0x08a0 	QuickCam IM 	  	zc030x 	hdcs2020 	Yes 	Jpeg 	spca5xx/LE gspca v4l1/v4l2 	****


This jibberish might not make much sence until you actually view the list of compatible cameras.  

Dunno... maybe this helps us out a bit?

---

### Post by andreids on 2007-05-05
I've just bought a sony vaio vgn-fe41e laptop, and guess what... sony offers drivers only for windows vista so xp is excluded. I've installed ubuntu feisty on it and everything works like a charm. Guess that windows is not ready for the desktop yet :P 
However, the webcam was not autodetected, but it was a matter of minutes to download the driver from [http://lsb.blogdns.net/ry5u870/](http://lsb.blogdns.net/ry5u870/) , untar, make, make install, modprobe and it simply works now. IMHO this driver should go in the default install of ubuntu. Kudos to the developer and the ubuntu team for making linux so competitive on this field of device drivers. I escaped from that dreadful french vista which came preinstalled :)

---

### Post by jckdnk111 on 2007-05-08
> **Dafydd said:**
> I wish I were wrong but...

"Bus 005 Device 004: ID 05ca:1830 Ricoh Co., Ltd" appears to be supported.

Unfortunately "Bus 002 Device 002: ID 054c:0107 Sony Corp. VCC-U01 Visual Communication Camera" DOES NOT appear to be supported.

Next time I buy a computer it will NOT be Sony. Just trying to get extra RAM was a nightmare (two months wait to be told that it was no longer available even though another local store sold me the kingston RAM at a third of the price).

The webcam, though, is the only thing that does not work under linux.

daf

I have 05ca:1835 Ricoh Co., Ltd and it does NOT work on feisty with the ry5u870 driver ([http://lsb.blogdns.net/ry5u870/)](http://lsb.blogdns.net/ry5u870/)). I installed it with no problem then rebooted and tried kopete, xawtv, and camstream: none of them display anything. Camstream gives a "error -19 (no such device)" though I can clearly see /dev/video0 does exists.

I installed the motioneye package and did a "sudo modprobe meye" and got no errors. 
However, a "motioneye -d" gives "ioctl MEYEIOC_G_PARAMS: Invalid argument".

This has been painful to say the least ... if anyone has further suggestions I'd appreciate any help.

---

### Post by el10t on 2007-05-11
Hello everyone - I'm new here.

I have a Sony Vaio VGN-FE21M.  After reading this thread I was dreading getting the built-in MotionEye working.  However, after installing Camorama and firing it up, the camera just worked! (except for the contrast/brightness controls).  This seems to be a major improvement in Feisty.

---

### Post by jckdnk111 on 2007-05-11
> **el10t said:**
> Hello everyone - I'm new here.

I have a Sony Vaio VGN-FE21M.  After reading this thread I was dreading getting the built-in MotionEye working.  However, after installing Camorama and firing it up, the camera just worked! (except for the contrast/brightness controls).  This seems to be a major improvement in Feisty.


Could you give us the output of an lsusb command ... it seems some models work just fine but others are having problems (like me :( )

---

### Post by el10t on 2007-05-12
Sure!  Here you go:
```
Bus 005 Device 003: ID 0ac8:c002 Z-Star Microelectronics Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 044e:300c Alps Electric Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

```

---

### Post by IntuitiveNipple on 2007-05-12
I've just ordered a Sony Vaio VGN-FE41Z based on what I've read here. I intend installing Feisty on it, so I'll let you know how I get on.

---

### Post by astadolfo3 on 2007-05-17
Hello,

I finally could see the webcam working for a while.  Vaio sz 450, with ricoh camera and Feisty 7.04.

 lsusb gives: 
Device 005: ID 05ca:1835 Ricoh Co., Ltd

Added the following repository to synaptics plus the two GPG keys as described here:

[http://www.arakhne.org/spip.php?article51](http://www.arakhne.org/spip.php?article51)

Reload synaptics packages and search for "ricoh". One of the packages that showed up was:
ricoh-webcam-r5u870-2.6.20-15-generic

After installing the package, the webcam worked with Kopete and Camorama without reboot.

The camera image was flashing a bit and distorted in Camorama. but at least it workes and it was recognized by the applications! The green LED besides it turned on as well.

The camera so far works only with the stamina Intel graphic card and not with the speed nvidia configuration

---

### Post by sreddyt on 2007-05-23
i have model **vgn-fe21m sony vaia model **in this lap top webcam drivers are not working any body knows where shall i get drivers please help me that would be great full for me thnks

---

### Post by IntuitiveNipple on 2007-05-23
> **IntuitiveNipple said:**
> I've just ordered a Sony Vaio VGN-FE41Z based on what I've read here. I intend installing Feisty on it, so I'll let you know how I get on.
Confirming that the r5u870 drivers do work with this model. There is a caveat however.

The current source code has a slight formatting glitch that causes the PCI ID of the camera in the FE41 to be omitted from the compiled driver. It's a trival issue to fix and I've let the driver author know.

To save repeating the fix here, read my [article about the VGN-FE41Z]("http://ubuntuforums.org/showpost.php?p=2702973&postcount=30") where I detail how to fix it.

---

### Post by el10t on 2007-05-25
> **sreddyt said:**
> i have model **vgn-fe21m sony vaia model **in this lap top webcam drivers are not working any body knows where shall i get drivers please help me that would be great full for me thnks

That's exactly the same model I have and the built-in MotionEye just worked by istelf - no additional drivers seemed to be needed.  See my post above.

---

### Post by MeduZa on 2007-05-27
Hi all, I finished installing 7.04 yesterday on a VAIO PCG-TR3A with a 054c:0107 Sony Corp. VCC-U01 Visual Communication Camera, and looking for the driver (because everything else work out of the box) I found that is unsupported, I need to know if somebody have any success to make the webcam work, I already read all the threat and no body, but I'll keep an eye here to know
Thanks all!

---

### Post by MoHamm on 2007-05-29
great thread, thanks guys, I got the camera working on my sz220, I used the  [URL="http://lsb.blogdns.net/ry5u870"]http://lsb.blogdns.net/ry5u870 
[/URL] link

xawtv didn't work though except with this command;

xawtv -nodga -device /dev/video0

something about nvidia not supporting dga, check this link[URL="http://ubuntuforums.org/showthread.php?t=334508"] http://ubuntuforums.org/showthread.php?t=334508
[/URL]

peace out

---

### Post by Depressed Man on 2007-05-30
I got the webcam working (sorta) with the drivers there. Though Camorana shows me black and white and it's split down the side a little so if I hold up my hand to the camera, there are two hands.

---

### Post by fpooon on 2007-06-14
I must say..  I have a Sony Vaio VGN-FJ170 using the gutsy repos and I've been messing around trying to get everything on my laptop working.  

The webcam works perfectly with the GSPCA module found at [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

If your camera is listed on [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) - fetch and compile that module.

I couldn't be happier. :D

---

### Post by jnorth on 2007-06-15
> **MoHamm said:**
> great thread, thanks guys, I got the camera working on my sz220, I used the  [URL="http://lsb.blogdns.net/ry5u870"]http://lsb.blogdns.net/ry5u870 
[/URL] link

xawtv didn't work though except with this command;

xawtv -nodga -device /dev/video0

something about nvidia not supporting dga, check this link[URL="http://ubuntuforums.org/showthread.php?t=334508"] http://ubuntuforums.org/showthread.php?t=334508
[/URL]

peace out

awesome - i've been rather pissed off at this problem until now :)

---

### Post by SendDerek on 2007-06-15
Well, as the originator of this thread I wanted to give my update on my motioneye camera!

IT WORKS!

After loading fiesty and getting all of the updates, it finally works.  I didn't have to do anything special either.  I can use Camorama with it and everything.

I found out when trying to fix the black video mode with compiz and I ran across the video input text in gstreamer-properties.

I hope the updates work for a lot of you as they did for me.

---

### Post by SendDerek on 2007-06-21
Hmmm... interesting.

Something happened between then and now, cuz It don't work no more!

I'm getting this error message:

Video for Linux (v4l): Device "/dev/video0" does not exist.

I'll keep chuggin' along and see what happens.

---

### Post by fdrake on 2007-06-21
> **SendDerek said:**
> Hmmm... interesting.

Something happened between then and now, cuz It don't work no more!

I'm getting this error message:

Video for Linux (v4l): Device "/dev/video0" does not exist.

I'll keep chuggin' along and see what happens.

something like that happened to me when i upgraded from dapper to edgy. to solve the problem i had to reinstall the driver again and reboot.

---

### Post by SendDerek on 2007-06-21
Thanks!

I just rebooted and everything works again.  Now that I think about it, I don't think I shut Ubuntu down properly last time so it must have messed things up a bit.

---

### Post by jpb39 on 2007-06-21
Has anyone had any luck with the motion eye webcam in theVaio FZ series? lsusb returns:

Bus 006 Device 002: ID 05ca:1837 Ricoh Co., Ltd 

which is a slightly different Ricoh model from the models reported to work above. After downloading, compiling and loading the current r5u870 driver and rebooting, neither Ekiga nor Kopete find the webcam.

Any suggestions?

Thanks,

 JPB

---

### Post by fdrake on 2007-06-21
you mean FS serie ([look]("http://www.sony.net/Products/VAIO/"))

---

### Post by jpb39 on 2007-06-21
No, I mean the recently-released FZ11S, based on the Centrino Duo (Santa Rosa) chipset and, alas, containing a slightly newer Ricoh webcam ...

 JPB

---

### Post by uglowp on 2007-07-05
Thank you for the information so far.

I have the same issue.

My laptop is a Sony Vaio VGN-SZ420N

My lsub output is also:

Bus 005 Device 003: ID 054c:0281 Sony Corp. 
Bus 005 Device 005: ID 05ca:1835 Ricoh Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 044e:300d Alps Electric Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:00e1 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  

I also am looking forward to solving this issue.

Otherwise everything else works like a charm.

Thanks again.

---

### Post by uglowp on 2007-07-05
Thank you for the information so far.

I have the same issue.

My laptop is a Sony Vaio VGN-SZ420N

My lsub output is also:

Bus 005 Device 003: ID 054c:0281 Sony Corp.
Bus 005 Device 005: ID 05ca:1835 Ricoh Co., Ltd
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 002: ID 044e:300d Alps Electric Co., Ltd
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 045e:00e1 Microsoft Corp.
Bus 002 Device 001: ID 0000:0000

I also am looking forward to solving this issue.

Otherwise everything else works like a charm.

Thanks again.

---

### Post by koe on 2007-07-16
Hi

For those who have a camera with the USB id 05ca:1837 I might have a fix (which is at least working on my VGN-FZ18M notebook). I've just added the id to the driver using the existing VGP-VCC4 firmware. Additionally I had to flip the picture (this is more a hack then a real solution since the picture now will be flipped for all other camera types, but I think it is ok to use until the driver has real support for this camera version).
You can find the patch at [http://www.gup.jku.at/~tkoeck/r5u870-0.10.0_VGN_FZ18M.patch](http://www.gup.jku.at/~tkoeck/r5u870-0.10.0_VGN_FZ18M.patch)


Regards,
koe

---

### Post by rishiamrit on 2007-07-28
Well ... I applied the patch and now it does not give me the /dev/video0 device not found error. Apparently it detects the cam now and when i start xawtv the LED next to my cam starts as if the cam is on. But no picture appears in the xawtv windows. Its a blank grey screen. Any idea why ?? Btw I too am using FZ-190 ... santa rosa chipset with the 1837 cam motion eye cam model.

---

### Post by David A Knight on 2007-07-29
The patch gets the cam working on an fz11m

---

### Post by uglowp on 2007-07-29
Thank you koe.

I appologize, newbie to ubuntu.  

How do you specificly add the driver?

Thanks!

Phil.

---

### Post by lfvsouza on 2007-08-31
I am not sure about which model of webcam all Vaio system uses, but you can try the
ricoh-webcam-r5u870/2.6.20-16-generic
(make a quick google to find the above debian file which will install itself without prob)
It is good for several Vaio series, including of course the SZ which I use, but 5 other series i suppose.
Good luck all.

---

### Post by lfvsouza on 2007-08-31
here is a quick link result in google for the driver:
[http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/2.6.20-16-generic/](http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/2.6.20-16-generic/)

Good luck all again.
lol

---

### Post by eldergod on 2007-09-17
I have a Sony Vaio VGN-FE780G and my motioneye webcam works perfectly. Actually it works better in Ubuntu than it did in Windows XP.
If you want me to post specs or somehting tell me what you want and how to do it and I would be glad to help.

---

### Post by indraveni on 2007-10-03
I too have the same problem with motioneye in my SOny vaio laptop, and when I tried to downlaod the above. its broken. can someone please help me, in letting my motioneye webcamera, work.

I have 2.6.21-486 kernel version.

---

### Post by bivens55 on 2007-10-03
If your having trouble installing the deb go here.
[http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/](http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/)
download the .tar.gz file and extract all files to a directory.
Drill down inside and find the readme, follow the instructions, don't forget sudo in front of the make and make install commands!!!
Works on apps listed in this article, [http://lsb.blogdns.net/ry5u870](http://lsb.blogdns.net/ry5u870)

John D. Bivens

---

### Post by Zyaga on 2007-10-04
Someone should really create drivers for the "Sony Corp. VCC-U01 Visual Communication Camera" webcam. There are plenty of us out here wanting it. :)

That and the fact that the buttons on the side of the screen don't work(for me), are making me think about going back to Winblows.

---

### Post by kyalpani on 2007-10-08
> **koe said:**
> Hi

For those who have a camera with the USB id 05ca:1837 I might have a fix (which is at least working on my VGN-FZ18M notebook). I've just added the id to the driver using the existing VGP-VCC4 firmware. Additionally I had to flip the picture (this is more a hack then a real solution since the picture now will be flipped for all other camera types, but I think it is ok to use until the driver has real support for this camera version).
You can find the patch at [http://www.gup.jku.at/~tkoeck/r5u870-0.10.0_VGN_FZ18M.patch](http://www.gup.jku.at/~tkoeck/r5u870-0.10.0_VGN_FZ18M.patch)


Regards,
koe

I have the same sony VGN_FZ18M, and the patch worked for me, I didn't touch the "default=" line though, on mine it said "default=63", I just added the line

{ R5U870_DEVICE_UVC(0x05CA, 0x1837, R5U870_DI_VGP_VCC4) 

and then did "sudo make;sudo make install;modprobe..." and after that I got the /dev/video0 device (for now obvious reasons) and xawtv started and worked perfectly (great picture)

thanks for the patch

---

### Post by pigfluff on 2007-10-08
Any luck with Sony Corp. VCC-U01 Visual Communication Camera?

---

### Post by Depressed Man on 2007-10-11
Any luck for Gutsy? That only seems to work for Feisty.

---

### Post by Jaymac on 2007-10-21
> **Depressed Man said:**
> Any luck for Gutsy? That only seems to work for Feisty.

Works fine for me in Gutsy.

---

### Post by punong_bisyonaryo on 2007-10-21
Sorry to barge in, but I have a Z-Star Microelectronics Corp. ZC0303 WebCam. Worked fine in Feisty, but not in Gutsy. I already started a thread before I found this thread. Anyway, I hope you guys can also help. The thread is here: [http://ubuntuforums.org/showthread.php?p=3590254]("http://ubuntuforums.org/showthread.php?p=3590254")

ps. Did anyone of you guys that also had the Z-Star webcams tried it with Gutsy? Problems? Solutions?

---

### Post by Depressed Man on 2007-10-21
> **Jaymac said:**
> Works fine for me in Gutsy.

Which one? I think I tried the .deb for the ricoh FE series?

---

### Post by amxs on 2007-11-01
I've a sony vaio VGN-FZ18M..How I can use my camera motion eye?Shall I download any particular application?please help me,thank'you

---

### Post by bazzard on 2007-11-06
Ok. I'm using a VGN-SZ3HP Vaio on Gutsy 7.10.

lsusb gives me:

Bus 005 Device 003: ID 1058:1010 Western Digital Technologies, Inc. 
Bus 005 Device 005: ID 05ca:1830 Ricoh Co., Ltd 
Bus 005 Device 004: ID 054c:0281 Sony Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:008a Microsoft Corp. Wireless Keyboard and Mouse
Bus 001 Device 001: ID 0000:0000  

So I've installed both drivers that we're recommended.

1. [http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/](http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/) 

2. [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

When using camorama, I can see a black and white picture that has double vision with horizontal lines. However, when I try using xawtv, firstly the program wouldn't open, but when I typed the commmand:

xawtv -nodga -device /dev/video0

(this is a command to fix something to do with using the nvidia graphics [http://ubuntuforums.org/showthread.php?t=334508](http://ubuntuforums.org/showthread.php?t=334508))

a window pops up with a full working picture of me! SUCCESS! However, not useful when I want to use it in aMSN and hopefully Skype in the future (anyone know anything about that by the way).

So, it's working properly somehow, somewhere but not how I want it to be working. In aMSN it now believes that I have a webcam, which is a start, but just displays a black screen, same within facebook video.

Seems to me that the problem is that I am using the nvidia graphics. However, I can't change to the stamina graphics because the stamina/speed switch doesn't work and I don't know how to get it working. Also, I don't even know for sure that it will work fully on the stamina graphics.

So I know it can work, but how do I get it working fully using the nvidia graphics? If anyone knows how please help me! Also, the speed/stamina switch for the graphics might be useful if someone could tell me how to get that working. As well as the webcam, my built in mic and the socket for an additional mic aren't working too. Any help would be much appreciated.](*,)

---

### Post by frunns on 2007-11-13
I got the 05ca:1837 cam, how do you apply the previously mentioned patch?

---

### Post by albertbertal8 on 2007-11-24
Hey, I have a Sony Corp. VCC-U01 Visual Communication Camera and I was wondering if there are any working drivers for that yet.  If so, can I have a link to it and how to install it?  If not, is there anybody working on making drivers for it?  Thanks.

---

### Post by mickymouse on 2007-11-27
yes please tell us the right way to install the patch metioned before

---

### Post by daz4126 on 2007-11-28
I've recently bought a new sony vaio vgn-cr22g/w and lsusb lists
Bus 006 Device 003: ID 05ca:1839 Ricoh Co., Ltd 

I've installed the ricoh generic package listed above, but had no look with camorama - I just get the error message:
'Could not connect to video device (/dev/video0). Please check connection.'

Anybody got any ideas with this?

Thanks,

DAZ

---

### Post by PurposeOfReason on 2007-12-01
This isn't on my highest list of priorities, but it is a nice little thing. I'm using arch so no deb packages for me. lsusb gives me the 05ca:1837 Ricoh Co., Ltd webcam. The laptop in question is a sony fz series model.

---

### Post by gurps on 2007-12-02
I've got a VAIO FZ21S, and my webcam is:

Bus 006 Device 002: ID 05ca:183b Ricoh Co., Ltd

Is there anyone that succeded in using this webcam ?

The updated driver r5u870 doesn't mention this webcam at all !

---

### Post by mdoube on 2007-12-03
@gurps  I have the vaio vgn-sz650n with Ricoh Webcam on Bus 006 Device 003: ID 05ca:183a Ricoh Co., Ltd.  Cos I'm using 64-bit Ubuntu I compiled my own deb from the r5u870 sources and modprobed it with no errors.  But,  no user-land program can access the camera.  What's going on?

[http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/](http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/)

---

### Post by gurps on 2007-12-04
It looks like the firmware of VCC8 as 183a and 183b is missing.
Someone says that is possible to extract the firwmare from the Windows Driver and compile from sources the r5u870 driver, but I cannot even find that firmware !

[http://www.uuhaus.de/linux/Debian%20Linux%20on%20the%20Sony%20VGN-TZ21VN.html]("http://www.uuhaus.de/linux/Debian%20Linux%20on%20the%20Sony%20VGN-TZ21VN.html")

Bye

---

### Post by esodin on 2007-12-05
I am running Gutsy (2.6.22-14) on a Vaio SZ. 

As Skype did not have the video version for Linux until a couple of weeks ago ([Get it here]("http://www.skype.com/download/skype/linux/beta/") - select the Feisty version), I had not bothered getting the video to work. Using the info in in this tread I got it to work perfectly. This is what I did:

1. downloaded and installed Skype 2.0 (the video version)
2. downloaded and installed the [2.6.22-14 ricoh driver]("http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/2.6.22-14-generic/")

Skype video worked immediately. 


I hope someone finds this info useful. :)

---

### Post by lalala on 2007-12-07
> **gurps said:**
> It looks like the firmware of VCC8 as 183a and 183b is missing.
Someone says that is possible to extract the firwmare from the Windows Driver and compile from sources the r5u870 driver, but I cannot even find that firmware !

[http://www.uuhaus.de/linux/Debian%20Linux%20on%20the%20Sony%20VGN-TZ21VN.html]("http://www.uuhaus.de/linux/Debian%20Linux%20on%20the%20Sony%20VGN-TZ21VN.html")

Bye

Sorry for my English.

I found the firmware file under c:/windows/drivers/camera. Im gonna try that.
Edited: I followed the steps using my file. I Created a new patch and applied it. **And my camera is now working in ubuntu**. My model is **VGN-FZ21E and the camera is Ricoh 05ca:183b**.
I tried it with "Cheese" ( sudo apt-get install cheese) and I dont know if the camera worked before or because of my new modified driver. Please try cheese with no driver and tell me.

---

### Post by Hador on 2007-12-08
hello everyone~

@lalala
can you please post the exact steps you followed to get the 05ca:183b webcam working? I've been working on it for quite a while but can't get it to work properly (module loads and all, but it doesn't give me the /dev/video0 access point so it's sorta useless...)
thanks!

---

### Post by bigube on 2007-12-08
Okay. First of all I want to say that I have no ****ing idea of drivers and stuff. I was bored and tried what I saw on this page [http://www.uuhaus.de/linux/Debian%20Linux%20on%20the%20Sony%20VGN-TZ21VN.html](http://www.uuhaus.de/linux/Debian%20Linux%20on%20the%20Sony%20VGN-TZ21VN.html) mentioned some post before. 

My lsusb throws **Bus 006 Device 002: ID 05ca:183b Ricoh Co., Ltd**

First of all I took my R5U870FLx86.sys firmware file from C:\Windows\Drivers\Camera Driver Ricoh...

Then I took the [recode-fw.scm]("http://www.uuhaus.de/linux/recode-fw.scm") script, edited it (replaced 183a with 183b), ran it with guile in the same folder where the firmware file was:
```
sudo apt-get install guile
guile -s recode-fw.scm
```

Then I got a file called 5u870_183b.fw.

After that I modified the patch [r5u870-0.10.0-vcc7patch]("http://www.uuhaus.de/linux/r5u870-0.10.0-vcc7patch") to use it with this file (replaced again 183a with 183b and VCC7 with VCC8, yes, I´m a genius!) and applied it on the [r5u870 driver]("http://www.uuhaus.de/linux/r5u870-0.10.0.tgz"). Then i just did
```
make
sudo make install
sudo modprobe r5u870
``` Then reboot and it just worked. It works for me on Cheese. If you dont want to do the whole process, here is the modified driver that i used to get my webcam working:

---

### Post by Hador on 2007-12-08
thanks for the detailed info!
yet... i've followed the same procedure (many times, by now) and, even though the driver compiles without issues, dmesg returns the following error(s) : 
```
Linux video capture interface: v2.00
usbcam: registering driver r5u870 0.10.0uuh
r5u870-0: Detected Sony VGP-VCC8
usb 6-2: USB disconnect, address 2
r5u870-0: command a0[246] failed: -19
r5u870-0: initialization failed: -19
usbcore: registered new interface driver r5u870
usb 6-2: new high speed USB device using ehci_hcd and address 3
usb 6-2: configuration #1 chosen from 1 choice
r5u870-0: Detected Sony VGP-VCC8
r5u870-0: command a0[246] failed: -71
r5u870-0: initialization failed: -71
r5u870: probe of 6-2:1.0 failed with error -71
usb 6-2: USB disconnect, address 3
```

this happens both with a customized 2.6.23.9 kernel and the default ubuntu's 2.6.22-14 package/headers...

any help would be greatly appreciated!

---

### Post by Lord C on 2007-12-13
> **koe said:**
> Hi

For those who have a camera with the USB id 05ca:1837 I might have a fix (which is at least working on my VGN-FZ18M notebook). I've just added the id to the driver using the existing VGP-VCC4 firmware. Additionally I had to flip the picture (this is more a hack then a real solution since the picture now will be flipped for all other camera types, but I think it is ok to use until the driver has real support for this camera version).
You can find the patch at [http://www.gup.jku.at/~tkoeck/r5u870-0.10.0_VGN_FZ18M.patch](http://www.gup.jku.at/~tkoeck/r5u870-0.10.0_VGN_FZ18M.patch)


Regards,
koe

My friend has a sony vaio FZ18M motion eye cam built into his laptop.
I am going to get it working for him, if only I can figure out how.

I understand that ricoh-webcam-r5u870 can be downloaded [here]("http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/") and that the patch is [here]("http://www.gup.jku.at/~tkoeck/r5u870-0.10.0_VGN_FZ18M.patch"). But I have no idea what to do with either of them.

Could you please provide a lil installation guide for a newb =]

Thanks

---

### Post by rbressers on 2007-12-14
I also have a FZ21M from Sony with the 183b chip.

My dmesg output : 

[ 3032.108000] r5u870-0: Detected Sony VGP-VCC8
[ 3032.752000] r5u870-0: command a0[246] failed: -71
[ 3032.752000] r5u870-0: initialization failed: -71
[ 3032.752000] r5u870: probe of 6-2:1.0 failed with error -71
[ 3032.752000] usb 6-2: USB disconnect, address 105
[ 3033.028000] usb 6-2: new high speed USB device using ehci_hcd and address 106
[ 3033.164000] usb 6-2: configuration #1 chosen from 1 choice
[ 3033.164000] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183b)
[ 3033.164000] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[ 3033.164000] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).
[ 3033.164000] uvcvideo: Failed to initialize the device (-5).

I am VERY interested in a solution for this problem.

---

### Post by Dojjah on 2007-12-14
Hello, Im new to ubuntu and I've been trying to get the built-in camera on my Vaio working as well. Ive been following this forum and links on the early pages for drivers are now dead. The link from the poster below was working however, but with a newer version, so I have tried to install that following the steps the poster provided (changing all the file names and such to the newer version ofcourse). 

> **gigi said:**
> Just to give an aditional solution how I came to success.
I have got an Sony Vaio VGN-SZ3HP

Download the current driver ( ricoh-webcam-r5u870_0.9.1-1.tar.gz  )from Page:
[http://www.arakhne.org/packages/pool/ricoh-webcam-r5u870/](http://www.arakhne.org/packages/pool/ricoh-webcam-r5u870/)


save the file somewhere open a console
> gunzip ricoh-webcam-r5u870_0.9.1-1.tar.gz
> tar xvf ricoh-webcam-r5u870_0.9.1-1.tar
>cd ricoh-webcam-r5u870-0.9.1/upstream/r5u870-0.9.1
>make
>make install

to see a picture i installed xawtv
apt-get install xawtv

reboot and voila after starting xawtv I could see myself :-))))))

There is also a package for the driver on this page (seen later)
[http://lsb.blogdns.net/ry5u870/](http://lsb.blogdns.net/ry5u870/)


Hope this can help someone to get the camera work

Everything works fine until I try to make install. I receive the following error.

```
jerad@jerad-laptop:~/Downloads/ricoh-webcam-r5u870-0.10.0/upstream/r5u870-0.10.0$ make install
make -C /lib/modules/2.6.22-14-generic/build M=/home/jerad/Downloads/ricoh-webcam-r5u870-0.10.0/upstream/r5u870-0.10.0 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make INSTALL_MOD_PATH= INSTALL_MOD_DIR=extra \
                -C /lib/modules/2.6.22-14-generic/build M=/home/jerad/Downloads/ricoh-webcam-r5u870-0.10.0/upstream/r5u870-0.10.0 modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
mkdir: cannot create directory `/lib/modules/2.6.22-14-generic/extra': Permission denied
make[1]: *** [_emodinst_] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [install] Error 2
```

Any insight on what to do? Also i forgot to mention my camera is

```
Bus 005 Device 003: ID 05ca:1835 Ricoh Co., Ltd 
```

---

### Post by Hador on 2007-12-15
> **Dojjah said:**
> ...

Everything works fine until I try to make install. I receive the following error.

```
jerad@jerad-laptop:~/Downloads/ricoh-webcam-r5u870-0.10.0/upstream/r5u870-0.10.0$ make install
make -C /lib/modules/2.6.22-14-generic/build M=/home/jerad/Downloads/ricoh-webcam-r5u870-0.10.0/upstream/r5u870-0.10.0 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make INSTALL_MOD_PATH= INSTALL_MOD_DIR=extra \
                -C /lib/modules/2.6.22-14-generic/build M=/home/jerad/Downloads/ricoh-webcam-r5u870-0.10.0/upstream/r5u870-0.10.0 modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
mkdir: cannot create directory `/lib/modules/2.6.22-14-generic/extra': Permission denied
make[1]: *** [_emodinst_] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [install] Error 2
```
...

Looks like you should try running make install with sudo!

---

### Post by bigbrovar on 2007-12-15
i get a similar error .. i just cant seem to make webcam work on my sony vaio fz21e the thing seem to be jaded  

root@bigbrovar-laptop:/home/bigbrovar/Webcam drivers/untitled folder/r5u870-0.10.0# make
make -C /lib/modules/2.6.22-14-generic/build M=/home/bigbrovar/Webcam drivers/untitled folder/r5u870-0.10.0 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** No rule to make target `drivers/untitled'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2
root@bigbrovar-laptop:/home/bigbrovar/Webcam drivers/untitled folder/r5u870-0.10.0# 



:confused:

---

### Post by amxs on 2007-12-16
Hi all, my camera is us 006 Device 002: ID 05ca:1837 Ricoh Co., Ltd
I've a fz18m.
my camera doesn't work but look at that links, maybe you'll find out what we look for.
Sorry it's in italian 


[http://www.palmix.org/vaio.html](http://www.palmix.org/vaio.html)
[http://www.frank17.it/linux/fz18m.htm](http://www.frank17.it/linux/fz18m.htm)

---

### Post by Hador on 2007-12-16
> **bigbrovar said:**
> i get a similar error .. i just cant seem to make webcam work on my sony vaio fz21e the thing seem to be jaded  

root@bigbrovar-laptop:/home/bigbrovar/Webcam drivers/untitled folder/r5u870-0.10.0# make
make -C /lib/modules/2.6.22-14-generic/build M=/home/bigbrovar/Webcam drivers/untitled folder/r5u870-0.10.0 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** No rule to make target `drivers/untitled'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2
root@bigbrovar-laptop:/home/bigbrovar/Webcam drivers/untitled folder/r5u870-0.10.0# 



:confused:

weird, looks like make doesn't like those spaces in your directory tree... 
```
/Webcam drivers/untitled folder/
...
make[1]: *** No rule to make target `drivers/untitled'.  Stop.

```

try switching to another directory and see if it does the job.

---

### Post by Dojjah on 2007-12-16
> **Hador said:**
> Looks like you should try running make install with sudo!

not really the best reply for helping a beginner, so try sudo make install instead of just make install.

---

### Post by bigbrovar on 2007-12-19
when i try compiling the driver again i get this error .. 

[PHPcalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1231: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: warning: braces around scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: warning: braces around scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: warning: large integer implicitly truncated to unsigned type
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1233: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1233: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1233: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1233: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1234: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1234: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1234: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1234: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1235: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1235: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1235: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1235: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1236: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1236: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1236: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1236: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1237: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1237: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1237: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1237: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1238: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1238: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1238: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1238: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1239: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1239: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1239: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1239: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1240: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1240: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1240: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1240: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1241: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1241: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1241: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1241: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1242: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1242: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1242: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1242: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1243: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1243: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1244: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1244: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
make[2]: *** [/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.o] Error 1
make[1]: *** [_module_/home/bigbrovar/Desktop/r5u870-0.10.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2
root@bigbrovar-laptop:/home/bigbrovar/Desktop/r5u870-0.10.0# make
make -C /lib/modules/2.6.22-14-generic/build M=/home/bigbrovar/Desktop/r5u870-0.10.0 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.o
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1181: error: expected identifier before ‘.’ token
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1182: error: expected ‘}’ before ‘.’ token
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1183: error: unknown field ‘menu_names’ specified in initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1183: warning: missing braces around initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1183: warning: (near initialization for ‘r5u870_wdm_ctrls[17].base.ctrl.reserved’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1183: warning: initialization makes integer from pointer without a cast
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1184: error: unknown field ‘get_fn’ specified in initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1184: warning: excess elements in struct initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1184: warning: (near initialization for ‘r5u870_wdm_ctrls[17].base.ctrl’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1185: error: unknown field ‘set_fn’ specified in initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1185: warning: excess elements in struct initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1185: warning: (near initialization for ‘r5u870_wdm_ctrls[17].base.ctrl’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1186: error: unknown field ‘reg’ specified in initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1186: warning: initialization makes pointer from integer without a cast
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1187: error: unknown field ‘val_offset’ specified in initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1188: warning: initialization makes pointer from integer without a cast
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1189: error: array index in non-array initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1189: error: (near initialization for ‘r5u870_wdm_ctrls[17]’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1189: warning: braces around scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1189: warning: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1190: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1190: error: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1190: warning: braces around scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1190: warning: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1190: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1190: error: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1190: warning: braces around scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1190: warning: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1190: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1190: error: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1191: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1191: error: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1191: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1191: warning: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1192: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1192: error: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1192: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1192: warning: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1193: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1193: error: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1193: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1193: warning: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1194: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1194: error: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1194: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1194: warning: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1195: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1195: error: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1195: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1195: warning: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1196: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1196: error: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1196: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1196: warning: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1197: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1197: error: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1197: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1197: warning: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1198: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1198: error: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1198: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1198: warning: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1199: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1199: error: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1199: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1199: warning: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1200: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1200: error: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1200: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1200: warning: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1201: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1201: error: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1202: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1202: warning: (near initialization for ‘r5u870_wdm_ctrls[17].reg’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1203: error: array index in non-array initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1203: error: (near initialization for ‘r5u870_wdm_ctrls[17]’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1203: warning: braces around scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1203: warning: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1204: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1204: error: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1204: warning: braces around scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1204: warning: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1204: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1204: error: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1204: warning: braces around scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1204: warning: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1204: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1204: error: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1204: warning: large integer implicitly truncated to unsigned type
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1205: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1205: error: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1205: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1205: warning: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1206: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1206: error: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1206: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1206: warning: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1207: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1207: error: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1207: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1207: warning: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1208: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1208: error: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1208: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1208: warning: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1209: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1209: error: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1209: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1209: warning: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1210: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1210: error: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1210: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1210: warning: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1211: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1211: error: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1211: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1211: warning: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1212: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1212: error: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1212: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1212: warning: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1213: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1213: error: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1213: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1213: warning: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1214: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1214: error: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1214: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1214: warning: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1215: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1215: error: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1216: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1216: warning: (near initialization for ‘r5u870_wdm_ctrls[17].unit’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1217: error: array index in non-array initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1217: error: (near initialization for ‘r5u870_wdm_ctrls[17]’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1217: warning: braces around scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1217: warning: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1218: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1218: error: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1218: warning: braces around scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1218: warning: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1218: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1218: error: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1218: warning: braces around scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1218: warning: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1218: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1218: error: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1218: warning: large integer implicitly truncated to unsigned type
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1219: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1219: error: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1219: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1219: warning: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1220: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1220: error: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1220: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1220: warning: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1221: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1221: error: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1221: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1221: warning: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1222: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1222: error: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1222: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1222: warning: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1223: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1223: error: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1223: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1223: warning: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1224: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1224: error: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1224: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1224: warning: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1225: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1225: error: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1225: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1225: warning: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1226: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1226: error: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1226: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1226: warning: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1227: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1227: error: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1227: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1227: warning: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1228: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1228: error: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1228: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1228: warning: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1229: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1229: error: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1230: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1230: warning: (near initialization for ‘r5u870_wdm_ctrls[17].info’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1231: error: array index in non-array initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1231: error: (near initialization for ‘r5u870_wdm_ctrls[17]’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1231: warning: braces around scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1231: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: warning: braces around scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: warning: braces around scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1232: warning: large integer implicitly truncated to unsigned type
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1233: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1233: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1233: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1233: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1234: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1234: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1234: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1234: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1235: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1235: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1235: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1235: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1236: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1236: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1236: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1236: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1237: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1237: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1237: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1237: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1238: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1238: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1238: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1238: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1239: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1239: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1239: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1239: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1240: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1240: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1240: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1240: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1241: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1241: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1241: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1241: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1242: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1242: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1242: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1242: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1243: error: field name not in record or union initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1243: error: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1244: warning: excess elements in scalar initializer
/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.c:1244: warning: (near initialization for ‘r5u870_wdm_ctrls[17].size’)
make[2]: *** [/home/bigbrovar/Desktop/r5u870-0.10.0/r5u870_md.o] Error 1
make[1]: *** [_module_/home/bigbrovar/Desktop/r5u870-0.10.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2
root@bigbrovar-laptop:/home/bigbrovar/Desktop/r5u870-0.10.0# 
][/PHP]

its been weeks now that i have not been able to get my webcam to work on my sony vaio fz21e ... its sooo frustrating .. i have tried everything ...oh God why does linux have to be soooooooooooooooo Complicating

---

### Post by junkMonkey on 2007-12-22
I would suggest looking at this thread:
[http://www.linuxdriverproject.org/twiki/bin/view/Main/DriversNeeded#Video_for_Linux_devices_Input](http://www.linuxdriverproject.org/twiki/bin/view/Main/DriversNeeded#Video_for_Linux_devices_Input)

They list the hardware that is supported and the hardware that is not. It might save you folks some trouble. I have a Vaio CR with the 05ca:1834 Motion Eye... so I'm just going to have to wait for the drivers to be updated... Sux for me...

> Ricoh Webcam Ry5u870: 05ca:1830, 05ca:1832, 05ca:1833, 05ca:1834, 05ca:1835, 05ca:1836, 05ca:1870, 05ca:1810. There is a working driver ([http://avilella.googlepages.com/r5u870-0.10.0.tgz](http://avilella.googlepages.com/r5u870-0.10.0.tgz)) but needs to be incorporated in the mainstream kernel.
The above driver doesn't yet support Ricoh's new cameras like 05ca:1839, which is the Motion Eye included in the Sony Vaio CR, and possibly others. 

---

### Post by bigbrovar on 2007-12-23
it really sucks and embarrasing not to be able to get my webcam to work that is the only thing that makes me to bootup vista all because i want to use vista.. the annoying thing is that pple with similar lappy models as mine have managed to get thier web cam to work .. but i have tried everything i was told still i get error everything i compile a parched driver..

---

### Post by rcrc on 2007-12-24
My webcam is not supported. Here are some specifications, if this can help: 
7.10 updated. 

$ uname -a
Linux tux-laptop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

$ lsusb: 
Bus 006 Device 003: ID 05ca:1839 Ricoh Co., Ltd 

$ dmesg |grep video
[   12.092242] Boot video device is 0000:00:02.0
[   11.784000] Linux video capture interface: v2.00
[   11.904000] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:1839)
[   11.904000] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   11.904000] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).
[   11.904000] uvcvideo: Failed to initialize the device (-5).
[   11.904000] usbcore: registered new interface driver uvcvideo

There is no /dev/video nor /dev/video0 or whatever like this. 

I added to /etc/apt/sources.list: 
"deb [http://download.tuxfamily.org/arakhne/ubuntu](http://download.tuxfamily.org/arakhne/ubuntu) gutsy-arakhne universe"
and installed successfully ricoh-webcam-r5u870-2.6.22-14-generic. 

I saw on:
[http://www.linuxdriverproject.org/twiki/bin/view/Main/DriversNeeded#Video_for_Linux_devices_Input](http://www.linuxdriverproject.org/twiki/bin/view/Main/DriversNeeded#Video_for_Linux_devices_Input)

that: 
"The above driver doesn't yet support Ricoh's new cameras like 05ca:1839, which is the Motion Eye included in the Sony Vaio CR, and possibly others."

Please tell if we can post any other specifications to resove this,

---

### Post by mdoube on 2007-12-24
Hi all

 I have my webcam (05ca:183a) working on the Sony Vaio SZ650 by using this patched version of the r5u870 source:
[http://ubuntuforums.org/attachment.php?attachmentid=45530&d=1191746623](http://ubuntuforums.org/attachment.php?attachmentid=45530&d=1191746623)

untar, make, sudo makeinstall, reboot.

However, this only works up to kernel 2.6.22 (Gutsy).  Compilation fails on kernel 2.6.24 (Hardy) because the linux headers have changed name:

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-2-generic'
  CC [M] /home/michael/drivers/r5u870-0.10.0-tz17/r5u870_md.o
In file included from /home/michael/drivers/r5u870-0.10.0-tz17/r5u870_md.c:55:
/home/michael/drivers/r5u870-0.10.0-tz17/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/michael/drivers/r5u870-0.10.0-tz17/r5u870_md.o] Error 1
make[1]: *** [_module_/home/michael/drivers/r5u870-0.10.0-tz17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-2-generic'
make: *** [all] Error 2

---

### Post by bigbrovar on 2007-12-27
> mdoube  	
Re: Sony Vaio MotionEye Webcam... Any Success?
Hi all

I have my webcam (05ca:183a) working on the Sony Vaio SZ650 by using this patched version of the r5u870 source:
[http://ubuntuforums.org/attachment.p...0&d=1191746623](http://ubuntuforums.org/attachment.p...0&d=1191746623)

untar, make, sudo makeinstall, reboot.

However, this only works up to kernel 2.6.22 (Gutsy). Compilation fails on kernel 2.6.24 (Hardy) because the linux headers have changed name:

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-2-generic'
CC [M] /home/michael/drivers/r5u870-0.10.0-tz17/r5u870_md.o
In file included from /home/michael/drivers/r5u870-0.10.0-tz17/r5u870_md.c:55:
/home/michael/drivers/r5u870-0.10.0-tz17/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/michael/drivers/r5u870-0.10.0-tz17/r5u870_md.o] Error 1
make[1]: *** [_module_/home/michael/drivers/r5u870-0.10.0-tz17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-2-generic'
make: *** [all] Error 2 
Damn man u just saved my life.. yes   my life.. u cant believe it but i have spent a greater part of my time solving this webcam problem ... anyttime i try i get an error.. so after reading ur post .. i downgraded my kenel and whala .. my webcam is working better than it did on vista... thanks bro.. u gave me the best xmas present i can ever get

---

### Post by wmj on 2007-12-28
> **mdoube said:**
> Hi all

 I have my webcam (05ca:183a) working on the Sony Vaio SZ650 by using this patched version of the r5u870 source:
[http://ubuntuforums.org/attachment.php?attachmentid=45530&d=1191746623](http://ubuntuforums.org/attachment.php?attachmentid=45530&d=1191746623)

untar, make, sudo makeinstall, reboot.

However, this only works up to kernel 2.6.22 (Gutsy).  Compilation fails on kernel 2.6.24 (Hardy) because the linux headers have changed name:


I've got a Viao CR290 with Motion Eye 05ca:1839 and Kubuntu 2.6.22-14. Tried the above as well as pretty much everything else posted on this forum, but no luck ("error connecting to /dev/video0" because it doesn't exist). Here is what I get when I do dmesg|grep video : 

[   14.014210] Boot video device is 0000:00:02.0
[   11.928000] Linux video capture interface: v2.00
[   12.116000] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:1839)
[   12.116000] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   12.116000] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).
[   12.116000] uvcvideo: Failed to initialize the device (-5).
[   12.116000] usbcore: registered new interface driver uvcvideo

Do we need another patch in the driver or something else? Any tips will be great! Thanks.

---

### Post by amxs on 2007-12-28
If anyone has some ideas for ID 05ca:1837 Ricoh Co., Ltd (on vaio vgn-fz18m) please help me..thank you..

---

### Post by chiru on 2007-12-28
Hi all,

I've recently byued a Vaio FZ21S, with the Ricoh-from-hell cam. I've tried to install the ricoh driver first unpatched, later converting the windows driver into a fw file, and once again with a file someone submitted to this thread with the necessary modified files and i've just realized one thing.

You don't need them. I've tried Cheese without the module loaded and it just works the same way as it does with the driver loaded. In my laptop, running ubuntu gutsy, the video has not very good quality (colors look strange, as if i was dead or something), but it's acceptable. When taking a photo with cheese, it works nice (i get i picture of me "dead"). the problem comes with video.

Switching to video mode does apparently nothing, the preview remains in the window and you can see yourself moving. When you press the button to start recording, everything goes crappy. You see a bunch of lines and a distortioned image of what is supposed to be captured.

I just wanted to report this, for if someone can figure out what's going on...

(Ah, i'm very sorry for my english :P)


Ah yes, the lsusb output shows:
Bus 001 Device 002: ID 05ca:183b Ricoh Co., Ltd

---

### Post by OrionFyre on 2007-12-29
> **mdoube said:**
> Hi all

 I have my webcam (05ca:183a) working on the Sony Vaio SZ650 by using this patched version of the r5u870 source:
[http://ubuntuforums.org/attachment.php?attachmentid=45530&d=1191746623](http://ubuntuforums.org/attachment.php?attachmentid=45530&d=1191746623)

untar, make, sudo makeinstall, reboot.

However, this only works up to kernel 2.6.22 (Gutsy).  Compilation fails on kernel 2.6.24 (Hardy) because the linux headers have changed name:

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-2-generic'
  CC [M] /home/michael/drivers/r5u870-0.10.0-tz17/r5u870_md.o
In file included from /home/michael/drivers/r5u870-0.10.0-tz17/r5u870_md.c:55:
/home/michael/drivers/r5u870-0.10.0-tz17/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/michael/drivers/r5u870-0.10.0-tz17/r5u870_md.o] Error 1
make[1]: *** [_module_/home/michael/drivers/r5u870-0.10.0-tz17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-2-generic'
make: *** [all] Error 2

At the risk of being laughed at! How does one "make" "sudo makeinstall" ?

EDIT: mmkay i think I got the "make" there were no egregious errors or any warnings... When I do
sudo makeinstall [anything]
it says makeinstall is an unknown command.

EDIT: NEVERMIND! lol <-- stupid
I figured it out, but i misread the idenifiers that are supported.

I have the 05ca:1839 Ricoh
If my system is needed for testing I am available as long as you're patient with spelling everything out. :-)

---

### Post by murmel on 2007-12-30
Solved how to get the webcam for Sony Vaio CR21* (05ca:1839 Ricoh Co., Ltd) working!
Check it out [HERE](http://ubuntuforums.org/showthread.php?p=4041383)! =)

---

### Post by lpallara on 2008-01-02
Hi,
   I made work the 183b camera of a fz21m vaio, kernel 2.6.23, I tested the driver with skype 2 beta without problems.

In attach a tar with a couple of files, a script to extract the firmware from the vista (xp?) driver and a modified r5u870_md.c for 5u870-0.10.0 driver

if your windows driver version is different from mine you will need to change it into the r5u870_md.c, it's just a one-line change don't worry, dmesg will warn you about the expected version and the version found if there is a mismatch.

bests,
   Lorenzo Pallara

> **rbressers said:**
> I also have a FZ21M from Sony with the 183b chip.

My dmesg output : 

[ 3032.108000] r5u870-0: Detected Sony VGP-VCC8
[ 3032.752000] r5u870-0: command a0[246] failed: -71
[ 3032.752000] r5u870-0: initialization failed: -71
[ 3032.752000] r5u870: probe of 6-2:1.0 failed with error -71
[ 3032.752000] usb 6-2: USB disconnect, address 105
[ 3033.028000] usb 6-2: new high speed USB device using ehci_hcd and address 106
[ 3033.164000] usb 6-2: configuration #1 chosen from 1 choice
[ 3033.164000] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183b)
[ 3033.164000] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[ 3033.164000] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).
[ 3033.164000] uvcvideo: Failed to initialize the device (-5).

I am VERY interested in a solution for this problem.

---

### Post by franky76 on 2008-01-02
> **lpallara said:**
> Hi,
   I made work the 183b camera of a fz21m vaio, kernel 2.6.23, I tested the driver with skype 2 beta without problems.

In attach a tar with a couple of files, a script to extract the firmware from the vista (xp?) driver and a modified r5u870_md.c for 5u870-0.10.0 driver

if your windows driver version is different from mine you will need to change it into the r5u870_md.c, it's just a one-line change don't worry, dmesg will warn you about the expected version and the version found if there is a mismatch.

bests,
   Lorenzo Pallara

I've the same notebook of you, but it doesn't work for me.
I've extract the firmware from windows file (.sys) and cache the r5u870_md.c adding the right lines for VCC8....module was load, firmware too and web cam recognized, but when i try to use it doesn't work...could you send me your modified file ed your firmware?

---

### Post by rbressers on 2008-01-02
I'm still getting the same errors i got before : 

[ 2748.508000] r5u870-0: Detected Sony VGP-VCC8
[ 2749.160000] r5u870-0: command a0[246] failed: -71
[ 2749.160000] r5u870-0: initialization failed: -71
[ 2749.160000] r5u870: probe of 6-2:1.0 failed with error -71
[ 2749.160000] usb 6-2: USB disconnect, address 69
[ 2749.432000] usb 6-2: new high speed USB device using ehci_hcd and address 70
[ 2749.568000] usb 6-2: configuration #1 chosen from 1 choice
[ 2749.568000] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183b)
[ 2749.568000] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[ 2749.568000] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).
[ 2749.568000] uvcvideo: Failed to initialize the device (-5).
[ 2749.568000] r5u870-0: Detected Sony VGP-VCC8
[ 2750.208000] r5u870-0: command a0[246] failed: -71
[ 2750.208000] r5u870-0: initialization failed: -71
[ 2750.208000] r5u870: probe of 6-2:1.0 failed with error -71
[ 2750.208000] usb 6-2: USB disconnect, address 70

I hope you can get a solution for this, because this cam is driving me nuts :)
I am running the default Ubuntu 7,10 kernel 2.6.22-14-generic.

EDIT: Don't worry about it.. I copied the firmware to /lib/firmware, rerun depmod and now it's working.. wow!
Thanks a million!

---

### Post by lpallara on 2008-01-02
> **franky76 said:**
> I've the same notebook of you, but it doesn't work for me.
I've extract the firmware from windows file (.sys) and cache the r5u870_md.c adding the right lines for VCC8....module was load, firmware too and web cam recognized, but when i try to use it doesn't work...could you send me your modified file ed your firmware?


what dmesg says? everything seems fine? firmware version ? mine is: 0x0131

btw I am using it with skype beta 2, I don't know about others softwares behaviors...

bests,
    Lorenzo

---

### Post by franky76 on 2008-01-02
> **lpallara said:**
> what dmesg says? everything seems fine? firmware version ? mine is: 0x0131

btw I am using it with skype beta 2, I don't know about others softwares behaviors...

bests,
    Lorenzo

how can i kown the firmware version?...i use the F21M driver-pack downloaded from Sony's website.

This is my Vista DriverVer= 06/18/2007,6.1004.211.0

i've tried with r5u870 module e the uvcvideo module too.....no one works: both give me a I/O error message.

---

### Post by lpallara on 2008-01-02
> **franky76 said:**
> how can i kown the firmware version?...i use the F21M driver-pack downloaded from Sony's website.

This is my Vista DriverVer= 06/18/2007,6.1004.211.0

i've tried with r5u870 module e the uvcvideo module too.....no one works: both give me a I/O error message.

seems the same, my md5sum is:
9ac8ac6cd00100443ea6afd0a4ade8f7  /usr/src/r5u870-0.10.0/vista/R5U870FLx86.sys

can you copy and past your dmesg? are you sure you are loading the new firmware? if you change the version in the .c dmesg does report error about version mismatch?

bests,
   Lorenzo

---

### Post by franky76 on 2008-01-02
> **lpallara said:**
> seems the same, my md5sum is:
9ac8ac6cd00100443ea6afd0a4ade8f7  /usr/src/r5u870-0.10.0/vista/R5U870FLx86.sys

can you copy and past your dmesg? are you sure you are loading the new firmware? if you change the version in the .c dmesg does report error about version mismatch?

bests,
   Lorenzo

9ac8ac6cd00100443ea6afd0a4ade8f7 yes is the same.

_this is my dmesg:_

Linux video capture interface: v2.00
uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183b)
usbcore: registered new interface driver uvcvideo
USB Video Class driver (v0.1.0)
usbcam: registering driver r5u870 0.10.0

_this is my kern.log:_

Jan  2 15:43:35 Telemaco kernel: Linux video capture interface: v2.00
Jan  2 15:43:35 Telemaco kernel: uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183b)
Jan  2 15:43:35 Telemaco kernel: usbcore: registered new interface driver uvcvideo
Jan  2 15:43:35 Telemaco kernel: USB Video Class driver (v0.1.0)
Jan  2 15:43:35 Telemaco kernel: usbcam: registering driver r5u870 0.10.0
Jan  2 15:43:35 Telemaco kernel: usbcore: registered new interface driver r5u870

found the problem, kernel load both modules uvcvideo and r5u870....i unload the uvcvide an the web cam work perfectly.

---

### Post by teshne on 2008-01-03
I have a Sony FZ21S with this camera: Bus 006 Device 002: ID 05ca:183b Ricoh Co., Ltd 

So I put together my .sys file which is the same as lpallara has and after running the .scm with guile I got the .FW file.

I am stuck here, I have no clue how to load firmware in linux or how to unload it:

> found the problem, kernel load both modules uvcvideo and r5u870....i unload the uvcvide an the web cam work perfectly.

Where do I put the .fw so it's loaded by the OS when I reboot? and how do I unload uvcvideo        if it's going to cause problems?

If anyone can give me some advice I would really appreciate it.

Thanks.

---

### Post by teshne on 2008-01-03
looks like I will not be able to do it since I am running Gusty amd64. 
I found out I should install the .deb package for the ricoh camera first, I forced it to install in the amd64 architecture but it won't load:
> 
FATAL: Error inserting r5u870 (/lib/modules/2.6.22-14-generic/extra/r5u870.ko): Invalid module format

If any one knows how to get this camera working with Gusty amd64 please let me know.

Thanks a lot

---

### Post by chiacchio on 2008-01-04
> **chiru said:**
> Hi all,

I've recently byued a Vaio FZ21S, with the Ricoh-from-hell cam. I've tried to install the ricoh driver first unpatched, later converting the windows driver into a fw file, and once again with a file someone submitted to this thread with the necessary modified files and i've just realized one thing.

You don't need them. I've tried Cheese without the module loaded and it just works the same way as it does with the driver loaded. In my laptop, running ubuntu gutsy, the video has not very good quality (colors look strange, as if i was dead or something), but it's acceptable. When taking a photo with cheese, it works nice (i get i picture of me "dead"). the problem comes with video.

Switching to video mode does apparently nothing, the preview remains in the window and you can see yourself moving. When you press the button to start recording, everything goes crappy. You see a bunch of lines and a distortioned image of what is supposed to be captured.

I just wanted to report this, for if someone can figure out what's going on...

(Ah, i'm very sorry for my english :P)


Ah yes, the lsusb output shows:
Bus 001 Device 002: ID 05ca:183b Ricoh Co., Ltd

I have the same trouble of chiru. The same happens when I try to use the webcam with amsn. Do you have any suggestion?

---

### Post by bigube on 2008-01-05
> **lpallara said:**
> Hi,
   I made work the 183b camera of a fz21m vaio, kernel 2.6.23, I tested the driver with skype 2 beta without problems.

In attach a tar with a couple of files, a script to extract the firmware from the vista (xp?) driver and a modified r5u870_md.c for 5u870-0.10.0 driver

if your windows driver version is different from mine you will need to change it into the r5u870_md.c, it's just a one-line change don't worry, dmesg will warn you about the expected version and the version found if there is a mismatch.

bests,
   Lorenzo Pallara

Thanks a lot. It worked for me on fz21e. I tested it with Cheese and Ekiga.

---

### Post by chiacchio on 2008-01-07
@ chiru: try this [http://ubuntuforums.org/showthread.php?t=646241&highlight=vaio+webcam]("http://ubuntuforums.org/showthread.php?t=646241&highlight=vaio+webcam")

It worked to me!

---

### Post by vedel on 2008-01-08
> **lalala said:**
> Sorry for my English.

I found the firmware file under c:/windows/drivers/camera. Im gonna try that.
Edited: I followed the steps using my file. I Created a new patch and applied it. **And my camera is now working in ubuntu**. My model is **VGN-FZ21E and the camera is Ricoh 05ca:183b**.
I tried it with "Cheese" ( sudo apt-get install cheese) and I dont know if the camera worked before or because of my new modified driver. Please try cheese with no driver and tell me.


Hi lalala,

Is it possible to put your driver file or your r5u780_183b.fw-file on this thread ?
I have also a FZ21E but I cannot retrieve my driver-file from Windows anymore because I didn't setup a dual boot and wiped Windows completely from my Vaio when installing Ubuntu.

Thanks in advance !

---

### Post by chiru on 2008-01-08
@ chiacchio

I've tried that before with no luck. Seems like it will not load the firmware file or something, but it didn't work for me.

Also, when I set up /etc/modules to load the r5u780 module on startup, i get a bunch of tricky messages and the laptop won't boot up. I had to load into safe mode and comment out the line for the ricoh module in /etc/modules.

I'll try again soon, I hope I'l have better luck.

---

### Post by franky76 on 2008-01-08
ther is a tutorial in english and italian here:

[http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html) (english)
[http://www.palmix.org/r5u870.html](http://www.palmix.org/r5u870.html) (italian)

---

### Post by chiru on 2008-01-09
franky76, you've just became a God!!!

It works like a charm!!

Thank you very much!

---

### Post by amxs on 2008-01-10
Hi all,Franky76's guide make my webcam motion eye work.I have another question: what program shall I have to make fotos and videos? Camorama and Cheese don't work fine and Xawtv doesn't show these options. I really hope that someone help me..(Sorry for my english) thank'you all

---

### Post by chiru on 2008-01-10
As long as i've read, camorama will not detect the motioneye, but i can use cheese without problems.

You get some error from cheese?

---

### Post by amxs on 2008-01-10
No,just the image is green and deformed..What can I do?

---

### Post by chiru on 2008-01-10
i've got image in green when using the driver with the wrong firmware. Have you installed the package provided in [http://www.palmix.org/r5u870-en.html]("http://www.palmix.org/r5u870-en.html")?

When running "make install" make sure the firmware file which name ends with "183b.fw" gets copied to /lib/firmware, otherwise camera won't work as expected...

(of course you have all the effects cheese can do disabled, right?)

---

### Post by amxs on 2008-01-10
Maybe my camera is a little different; lsusb command in terminal return:
Bus 006 Device 002: ID 05ca:1837 Ricoh Co., Ltd
I've installed r5u870-0.10.0.tgz pached as described here:[http://www.frank17.it/linux/fz18m.htm](http://www.frank17.it/linux/fz18m.htm)
Do you know if  it is the best way to make work my camera?Thank'you for help me...

---

### Post by chiru on 2008-01-10
That's the wrong thing. The file you've downloaded doesn't contain a valid firmware file for "1837" model. I've been looking around in this thread, but could'nt find an archive containig the firmware you need. Seems not to be available?

Someone in this thread posted a method to extract the firmware files from the Vista drivers for the motioneye. I've tried a couple of times with no success but maybe you could try that method, and if it works, post the final package with the fw file.

---

### Post by amxs on 2008-01-10
Thank's for interest.I've read what Franky76 and lpallara have done,and I have understand what should be done for my camera (that is a little bit different from yours,I've a Sony Vaio FZ18M and Ricoh1837).However I know that for me is impossible to do that on my own because I'm a newbie.
I don't know if in this link ([http://www.frank17.it/linux/fz18m.htm](http://www.frank17.it/linux/fz18m.htm))  the pach applied on ricoh driver is the only things I can do to make work fine my webcam.
I've found this page ([http://lists-archives.org/video4linux/20120-usbsniff-file-for-05ca-1837-ricoh-co-ltd.html](http://lists-archives.org/video4linux/20120-usbsniff-file-for-05ca-1837-ricoh-co-ltd.html)) but I don't know if it is useful and what it means.
Maybe I should wait that some linux expert help me or wait the right driver for my webcam type.
So thank's a lot by now..

---

### Post by chiru on 2008-01-10
I' have the scripts i told that extract the firmware. I am posting them tonight and give the instructions i've followed. Maybe you'll be more lucky than me.

---

### Post by amxs on 2008-01-10
Thank's a lot..very very useful..):P

---

### Post by chiru on 2008-01-11
Hi again!

Sorry but yesterday some friends came to my house and i did not connect to internet.

Here's what i've tried to extract the firmware from windows drivers...

1.- The .scm file is a guile script. If you don't have guile installed, just fire up a terminal and type "sudo apt-get install guile".
2.- You need the file named "R5U870FLx86.sys" from the Windows driver package.
3.- Edit "recode-fw.scm" and locate a line that states "(define *destfile* "r5u870_183a.fw")" and change the file name to end in "..1837.fw". Save.
4.- Run the script. You'll see a bunch of lines scrolling in the terminal. When it is finished, you'll have the r5u870_1837.fw file. Copy it to /lib/firmware.
5.- Once done, just patch the driver with "patch < r5u870-0.10.0-vcc7patch". Make sure you are in the same folder as the driver source file.
6.- Compile and install.
7.- Cross your fingers and "modprobe r5u780"

If you are more lucky than me, then you could fire up cheese or skype and feel very happy to see your face in the screen. :D

Try this with your actual module unloaded. I don't know if this affects in some way the installation, but just to be safe.

Good luck!

---

### Post by teshne on 2008-01-13
Hi, 

Just to say that by following the guide at [http://www.palmix.org/r5u870-en.html]("http://www.palmix.org/r5u870-en.html") I made the webcam in a sony FZ21S (183b) work on Ubuntu 7.10 64-bit.

Thanks to all the posters of this thread!

---

### Post by ccplaore on 2008-01-15
> **franky76 said:**
> ther is a tutorial in english and italian here:

[http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html) (english)
[http://www.palmix.org/r5u870.html](http://www.palmix.org/r5u870.html) (italian)

Thanks a lot! it worked perfectly for me!

regards,

---

### Post by mdoube on 2008-01-17
A site to keep an eye on is this blog that has sprung up in the last few days, with new versions and active development of the r5u870 driver - thanks to Alex...

[http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870)

---

### Post by sammydadams on 2008-01-19
i have one of the stupid   05ca:1837 ricoh ones on my fz180 but i have found a site which seems to have drivers for this particular model used for downgrading to XP (cause everyone knows Vi$ta sucks!):

[ftp://ftp.vaio-link.com/PUB/OS/XPDOWNGRADE/FZ19/](ftp://ftp.vaio-link.com/PUB/OS/XPDOWNGRADE/FZ19/)

look under drivers...hopefully someone smarter than I can utilize this to get the newer ricoh cams to work under a better OS 	:rolleyes:

---

### Post by Redrazor39 on 2008-01-21
I have a Vaio SZ430N and I want my Motion Eye and my fingerprint reader to work :(

What's an easy, n00b-friendly way to make at least one of these work?

Also, to the above poster, Vista does not suck at all. It is a very good Operating System-- much better than XP or Mac OS X.x. That's why I dual boot Vista and Ubuntu-- so I can have the best of both worlds :)

---

### Post by orarnon on 2008-01-22
hi,
i can (also) confirm that the below tutorial:
```
http://www.palmix.org/r5u870-en.html
```

got the webcam to work on my fz-250e / ubuntu 7.10 32-bit

don't forget to add the lines in the link to the /etc/modules file!

enjoy!

---

### Post by Redrazor39 on 2008-01-27
> **guitarist549 said:**
> Gah... I really wish ricoh would release drivers for this stupid webcam.. it's the only thing that is making me seriously consider going back to Windows... That and the fingerprint sensor.

Me 2. I really want my camera, mic, and fingerprint reader to work! I dual boot vista and ubuntu (just wanted to check out linux) and ubuntu ROCKS! I'm seriously considering getting rid of ubuntu and going all Vista again if this is the crap I have to go through! As long as there's something simple to download and install I'm ALL FOR doing it as long as it gets this stuff to work!


Also, Hibernate, Suspend don't work. It blanks the screen and stuff but I can't get it back on w/out losing my session!

---

### Post by bigbrovar on 2008-01-28
My Webcam is Epileptic .. one time it would work.. another time cheese would tell me unable to find a webcam... like yesternight the cam worked.. but when i tried it this morning .. it told me that webcam not found.. i dont know what to do.. i have compiled and installed the motion eye driver.. r5u870 .. it worked at first then it just stopped after couple of days..i use sony vaio fz21e and my cam is the  183b type ... i dont know if anyone can help me

---

### Post by eldergod on 2008-02-01
> **eldergod said:**
> I have a Sony Vaio VGN-FE780G and my motioneye webcam works perfectly. Actually it works better in Ubuntu than it did in Windows XP.
If you want me to post specs or somehting tell me what you want and how to do it and I would be glad to help.

I'm having video/monitor issues with the default settings in ubuntu and for the life of me I can't out what monitor/graphics card settings I need for my Vaio VGN-FE780G.
Could be so nice as to check what graphics card and monitor your useing in settings?

---

### Post by sammydadams on 2008-02-02
i can confirm that the website posted above by mdoube has a working driver for the ricoh webcam...seems video is a little jacked up at the moment through cheese but i'll try another program to make sure

Thanks!\\:D/

---

### Post by sammydadams on 2008-02-02
ok...cheese is the only program that seems to identify the webcam...i also tried xawtv and camorama but neither seems to work...the problem with cheese is when you set it to capture video, it seems to ghost and zoom so the object is nearly completely obscured by this effect...:???: it works perfectly for taking single frames (ie still) ...can i configure cheese or something or does anyone have a suggestion of another program to try?

---

### Post by sammydadams on 2008-02-02
tried it again today and before actual recording it shows up double and squished to the top of the screen...but video now works and photo cap doesnt...the photo cap shows up like doubled and squished...weird

---

### Post by Valehru on 2008-02-03
Hey guys, 

Converting my girlfriends machine to linux.  Its pretty much a prerequisite that her webcam gets working.  She is pretty cute.  Anyhow, the details are below.  Is this card supported at all?

Bus 002 Device 002: ID 054c:0107 Sony Corp. VCC-U01 Visual Communication Camera


Everything else is working by the way.  Help me get a hot girl on nix.  :D

---

### Post by agent sharp on 2008-02-06
does that tutorial 'palmix' work for the Sony VGN-CR290 model?

i'm assuming it does so here's my real question: (oh and i'm an absolute noob at ubuntu) how the heck do i 'untar' something?

---

### Post by clovis_ll on 2008-02-07
or for cr320?

---

### Post by clovis_ll on 2008-02-07
help!! i get this error.
[B]
root@clovis2-utop:~/Documents/r5u870-0.11.2# modprobe r5u870
WARNING: /etc/modprobe.d/alsa-base.save.1 line 40: ignoring bad line starting with 'sudo'[/B]

---

### Post by petros85 on 2008-03-06
Guys please help I'm a beginner and i think i messed up. I followed the instructions found here [http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870) to install the ricoh drivers. The make install and the modprobe had permission problems so i used sudo in front of these and everything seemed fine.Except of course that the camera didnt work.The REAL problem is that now my system cannot boot!!!I get continuous messages like these:
```
[ 2750.208000] r5u870-0: command a0[246] failed: -71
[ 2750.208000] r5u870-0: initialization failed: -71
```
Its just this message over and over again and it doesn boot.The grub menu at the beginning appears normally but after that it stucks.PLEASE HELP i don't want to install the webcam anymore just to save my system!

---

### Post by chiru on 2008-03-06
Just remove the module from /etc/modules.d

It will not load the module at boot time, but if it doesn't works, it's not a big problem.

Cheers

---

### Post by petros85 on 2008-03-06
But how will i do that since it wont boot?

---

### Post by chiru on 2008-03-06
As long as I remember, i think i've used the "safe mode" option in the grub menu... or pressed ctrl+c or ctrl+break as if i were possesed 'till it booted.

If it doesn't work, you can just boot the install cd, edit the file in your hard drive and reboot.

---

### Post by petros85 on 2008-03-06
Ok  i pressed ctr -c and ctrl-break and nothing happened.Just the same message over and over.I put my live cd inside and pressed ESC on the VAIO logo screen ,selected the cdrom boot but after a few seconds of turning the cd around it still gets into grub.In grub i select recovery mode and it does the same thing.How do i get into safe mode???

---

### Post by chiru on 2008-03-06
How did you started the livecd to install ubuntu? That should work...

---

### Post by petros85 on 2008-03-06
I remember that it had given me trouble to boot from the cd but eventually it happened.At the vaio logo screnn u press ESC and select boot device.I do that but it won't load for some reason.

---

### Post by petros85 on 2008-03-06
Ok finally got in from the cd. The folder \etc has a modules file which has 3 lines:
fuse
lp
sbp2
what do i do??

---

### Post by petros85 on 2008-03-06
Please cone someone help me out on this?? I cant find the etc/modules.d folder.How will i remove the r5u870 that is causing the problem?

---

### Post by oooh on 2008-03-16
vaio fz21m here, with 05ca:183b Ricoh, did not test all possibilities, but will send the link here once i have it working !!

---

### Post by Redrazor39 on 2008-03-16
mine is having the same problems (exactly). I have a VGN-SZ430N and I would like to know how I can make it work. Also, my memory stick pro duo reader is not recognized and I haven't been able to find good software for my built-in fingerprint reader.


At least I want my webcam to work, then my memstick pro duo reader/writer to work, then the fingerprint reader in that order of priority.

Also, more speed in boot up and apps wouldn't hurt ;)

---

### Post by modafokaxx on 2008-03-19
> **petros85 said:**
> Guys please help I'm a beginner and i think i messed up. I followed the instructions found here [http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870) to install the ricoh drivers. The make install and the modprobe had permission problems so i used sudo in front of these and everything seemed fine.Except of course that the camera didnt work.The REAL problem is that now my system cannot boot!!!I get continuous messages like these:
```
[ 2750.208000] r5u870-0: command a0[246] failed: -71
[ 2750.208000] r5u870-0: initialization failed: -71
```
Its just this message over and over again and it doesn boot.The grub menu at the beginning appears normally but after that it stucks.PLEASE HELP i don't want to install the webcam anymore just to save my system!

2 things:
I had the same error: continuous messages just like yours.
It turns out that in fact, your system HAS loaded, it just floods you with error messages.
Get to a terminal (ctrl+alt+F1), enter your username and password (yes, keep on typing even if there is a continuous flow of text) and you'll be loged in.
Then unload the problem-causing module from the system:
```
sudo modprobe -r r5u870
```
you may need to unload the uvcvideo module too, as they can conflict:
```
sudo modprobe -r uvcvideo
```

It should stop the flow of message and bring you to the usual graphical login screen.

Next step: reread carefully the instructions here: [http://wiki.mediati.org/R5u870#Known_Issues](http://wiki.mediati.org/R5u870#Known_Issues)
What we have here is the -71 error.

To solve that, you must follow the instructions to compile from source, but using the trunk version of the driver, not the STABLE_CURRENT:
```

svn co http://svn.mediati.org/svn/r5u870/trunk r5u870
```
and NOT:
```
svn co http://svn.mediati.org/svn/r5u870/tags/STABLE_CURRENT r5u870
```

And the follow the rest of the instructions (enter the directory, make, make install, and finally modprobe).

It just got me to see myself on my webcam (05ca:183b Sony Visual Communication Camera VGP-VCC8) on my Vaio VGN FZ31M ! Works with Cheese anyway.
Problem: the picture is zoomed in and tilted to the side.
Oh well.. that will get better in future revisions of the r5u870 driver! :)

---

### Post by oooh on 2008-03-19
vaio fz21m with 183b camera:

MY STORY:

- Found that I have "Bus 006 Device 002: ID 05ca:183b Ricoh Co., Ltd" ("dmesg | grep video" is also interesting). Found WIKI and Palmix tutorial( [http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html)).

- Dowloaded the TAR file r5u870-0.11.0, uncompressed on a folder path with NO SPACES, and did make, make install, and then modprobe r5u870. Conflicts with module uvcvideo, thus computer hang afer restart. Solution: ubuntu life cd and modify /etc/modprobe/blacklist. Add "backlist uvcvideo", so that conflict does not happen. 

- Still r5u870 does not work. Error -71, can not initialize. Computer still hangs after restart.

NEXT TO TRY:

- Try the patch for the 183b. 

QUESTION:

I have NO VISTA and NO XP, so where can I get my firmware? Should it work with r5u870-0.11.0 and r5u870-0.10.0. Can somebody send me the firmware, or the TAR file already patched ?




> **lpallara said:**
> Hi,
   I made work the 183b camera of a fz21m vaio, kernel 2.6.23, I tested the driver with skype 2 beta without problems.

In attach a tar with a couple of files, a script to extract the firmware from the vista (xp?) driver and a modified r5u870_md.c for 5u870-0.10.0 driver

if your windows driver version is different from mine you will need to change it into the r5u870_md.c, it's just a one-line change don't worry, dmesg will warn you about the expected version and the version found if there is a mismatch.

bests,
   Lorenzo Pallara

---

### Post by oooh on 2008-03-19
Petro, I made the same mistake ....

When u boot from ubuntu life,you must mount your hardrive, and access it via /media/disk/etc/modprobe/blacklist , and not /etc/modprobe/blacklist.

The second file is the virtual ubuntu. The first one is your hard drive installed ubuntu. Naturally, you should add line "blacklist r5u870" to the first one ! That worked for me ...

> **petros85 said:**
> Please cone someone help me out on this?? I cant find the etc/modules.d folder.How will i remove the r5u870 that is causing the problem?

---

### Post by wozzinator on 2008-03-26
Worked for me in Hardy using the link in Franky76's post (which is now in my sig)

---

### Post by chris_77 on 2008-04-11
> **franky76 said:**
> ther is a tutorial in english and italian here:

[http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html) (english)
[http://www.palmix.org/r5u870.html](http://www.palmix.org/r5u870.html) (italian)

Works with Skype and Ekiga on a Sony Vaio VGN FZ18M, but not with Cheese. Any Ideas?

---

### Post by wozzinator on 2008-04-11
I wasn't able to get cheese to work, but xawtv works perfectly.

---

### Post by oooh on 2008-04-14
Good news ... 

Finally worked using the r5u870 driver base that can be found in [http://svn.mediati.org/svn/r5u870/trunk](http://svn.mediati.org/svn/r5u870/trunk). 

I substituted the r5u870.c and r5u870_183b.fw in that driver by the r5u870_md.c and the r5u870_183b.fw provided by l laparella in : [http://ubuntuforums.org/attachment.php?attachmentid=55005&d=1199267602](http://ubuntuforums.org/attachment.php?attachmentid=55005&d=1199267602) ([http://ubuntuforums.org/showthread.php?t=289836&page=14](http://ubuntuforums.org/showthread.php?t=289836&page=14)). 

I compiled once more (make, make install in su mode), loaded the driver (modprobe r5u870) commented the driver line in the blacklist file (to allow the system to load the driver), rebooted, and it works !!!

Now cheese show perfect image. Ekiga show also perfect image but can not control brightness, contrast or tone. Amsn detects it, but shows dark-almost-black image, as brightness and contrast controls do not work as well, I can not make video conferences with amsn, which was my tarjet.

Any idea why brightness control is not available, and why amsn could be showing complete dark image?

---

### Post by oooh on 2008-04-28
The new story of r5u870 with hardy heron in : [http://ubuntuforums.org/showthread.php?p=4826485#post4826485](http://ubuntuforums.org/showthread.php?p=4826485#post4826485)

---

### Post by pengko.eo on 2008-05-09
Does anyone can help me? I'm installing r5u870 driver for my vaio sz, i met this problem when i typed make install 

```
make -C /lib/modules/2.6.24-16-generic/build M=/home/pengko/ricoh-webcam-r5u870-0.11.0/upstream/r5u870-0.11.0 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  Building modules, stage 2.
  MODPOST 2 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make INSTALL_MOD_PATH= INSTALL_MOD_DIR=extra \
		-C /lib/modules/2.6.24-16-generic/build M=/home/pengko/ricoh-webcam-r5u870-0.11.0/upstream/r5u870-0.11.0 modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  INSTALL /home/pengko/ricoh-webcam-r5u870-0.11.0/upstream/r5u870-0.11.0/r5u870.ko
cp: cannot create regular file `/lib/modules/2.6.24-16-generic/extra/r5u870.ko': Permission denied
  INSTALL /home/pengko/ricoh-webcam-r5u870-0.11.0/upstream/r5u870-0.11.0/usbcam/usbcam.ko
mkdir: cannot create directory `/lib/modules/2.6.24-16-generic/extra/usbcam': Permission denied
cp: cannot create regular file `/lib/modules/2.6.24-16-generic/extra/usbcam': Permission denied
  DEPMOD  2.6.24-16-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
install -m 0644 -o root -g root r5u870_1830.fw r5u870_1832.fw r5u870_1833.fw r5u870_1834.fw r5u870_1835.fw r5u870_1836.fw r5u870_1870_1.fw r5u870_1870.fw r5u870_1810.fw r5u870_183a.fw r5u870_183b.fw r5u870_1839.fw  /lib/firmware
install: cannot create regular file `/lib/firmware/r5u870_1830.fw': Permission denied
install: cannot create regular file `/lib/firmware/r5u870_1832.fw': Permission denied
install: cannot create regular file `/lib/firmware/r5u870_1833.fw': Permission denied
install: cannot create regular file `/lib/firmware/r5u870_1834.fw': Permission denied
install: cannot create regular file `/lib/firmware/r5u870_1835.fw': Permission denied
install: cannot create regular file `/lib/firmware/r5u870_1836.fw': Permission denied
install: cannot create regular file `/lib/firmware/r5u870_1870_1.fw': Permission denied
install: cannot create regular file `/lib/firmware/r5u870_1870.fw': Permission denied
install: cannot create regular file `/lib/firmware/r5u870_1810.fw': Permission denied
install: cannot create regular file `/lib/firmware/r5u870_183a.fw': Permission denied
install: cannot create regular file `/lib/firmware/r5u870_183b.fw': Permission denied
install: cannot create regular file `/lib/firmware/r5u870_1839.fw': Permission denied
make: *** [install] Error 1

```

does anyone know how to fix this? i ve downloaded the deb file and tried using that to install, but ubuntu gave a message of: 
```
error:dependency is not satisfiable: linux-image-2.6.24-17-generic
```

please help me. thank you guys

---

### Post by jabberwockiq on 2008-05-12
Hi Guys,

Try this [http://www.arakhne.org/spip.php?rubrique26](http://www.arakhne.org/spip.php?rubrique26) i dont have the same model as this guys uses but it worked on mine

Bus 003 Device 002: ID 05ca:1839 Ricoh Co., Ltd 

It worked on aMSN, sadly cheese dosent work.

---

### Post by JamesNeko on 2008-05-13
I've got a PCG-C1MSX, with a "R-Engine" type MotionEye... sadly, there is no driver. It's the one bit of hardware I can't use.

Doesn't stop me from loving my little linux laptop though =)

lspci -nn gives me:
```
00:0a.0 Multimedia controller [0480]: Fujitsu Limited. Unknown device [10cf:2011]
```

---

### Post by bemnet4u on 2008-05-20
This links were helpful in fixing my sony vaio VGN-CR11S motion eye camera on Ubuntu 8.

[http://ubuntuforums.org/showthread.php?t=650790](http://ubuntuforums.org/showthread.php?t=650790)
[http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870)
[http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870)

Cheers,
Bemnet

---

### Post by Shannon_VanWagner on 2008-05-21
I'm testing the Sony Vaio VGN-TZ191N and here's the output from my lsusb:
Bus 005 Device 006: ID 05ca:183a Ricoh Co., Ltd

[SIZE="1"]
Bus 005 Device 006: ID 05ca:183a Ricoh Co., Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x05ca Ricoh Co., Ltd
  idProduct          0x183a 
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          350
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass         14 Video
      bFunctionSubClass       3 Video Interface Collection
      bFunctionProtocol       0 
      iFunction               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      1 Video Control
      bInterfaceProtocol      0 
      iInterface              0 
      VideoControl Interface Descriptor:
        bLength                13
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdUVC               1.00
        wTotalLength           78
        dwClockFrequency       24.000000MHz
        bInCollection           1
        baInterfaceNr( 0)       1
      VideoControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             3
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          1
        bSourceID               4
        iTerminal               0 
      VideoControl Interface Descriptor:
        bLength                26
        bDescriptorType        36
        bDescriptorSubtype      6 (EXTENSION_UNIT)
        bUnitID                 4
        guidExtensionCode         {1c624144-8989-4643-afb3-20f37590304e}
        bNumControl             1
        bNrPins                 1
        baSourceID( 0)          2
        bControlSize            1
        bmControls( 0)       0xff
        iExtension              0 
      VideoControl Interface Descriptor:
        bLength                18
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Camera Sensor
        bAssocTerminal          3
        iTerminal               0 
        wObjectiveFocalLengthMin      0
        wObjectiveFocalLengthMax      0
        wOcularFocalLength            0
        bControlSize                  3
        bmControls           0x00000000
      VideoControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      5 (PROCESSING_UNIT)
      Warning: Descriptor too short
        bUnitID                 2
        bSourceID               1
        wMaxMultiplier          0
        bControlSize            3
        bmControls     0x0000053f
          Brightness
          Contrast
          Hue
          Saturation
          Sharpness
          Gamma
          Backlight Compensation
          Power Line Frequency
        iProcessing             0 
        bmVideoStandards     0xff
          None
          NTSC - 525/60
          PAL - 625/50
          SECAM - 625/50
          NTSC - 625/50
          PAL - 525/60
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               6
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      VideoStreaming Interface Descriptor:
        bLength                            14
        bDescriptorType                    36
        bDescriptorSubtype                  1 (INPUT_HEADER)
        bNumFormats                        1
        wTotalLength                      161
        bEndPointAddress                  134
        bmInfo                              1
        bTerminalLink                       3
        bStillCaptureMethod                 0
        bTriggerSupport                     0
        bTriggerUsage                       0
        bControlSize                        1
        bmaControls( 0)                    27
      VideoStreaming Interface Descriptor:
        bLength                            27
        bDescriptorType                    36
        bDescriptorSubtype                  4 (FORMAT_UNCOMPRESSED)
        bFormatIndex                        1
        bNumFrameDescriptors                4
        guidFormat                            {59555932-0000-1000-8000-00aa00389b71}
        bBitsPerPixel                      16
        bDefaultFrameIndex                  1
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x02
          Interlaced stream or variable: No
          Fields per frame: 2 fields
          Field 1 first: No
          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         1
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            640
        wHeight                           480
        dwMinBitRate                147456000
        dwMaxBitRate                147456000
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         666666
        bFrameIntervalType                  1
        dwFrameInterval( 0)            666666
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         2
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                 36864000
        dwMaxBitRate                 36864000
        dwMaxVideoFrameBufferSize      153600
        dwDefaultFrameInterval         666666
        bFrameIntervalType                  1
        dwFrameInterval( 0)            666666
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         3
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            176
        wHeight                           144
        dwMinBitRate                 12165120
        dwMaxBitRate                 12165120
        dwMaxVideoFrameBufferSize       50688
        dwDefaultFrameInterval         666666
        bFrameIntervalType                  1
        dwFrameInterval( 0)            666666
      VideoStreaming Interface Descriptor:
        bLength                            30
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         4
        bmCapabilities                   0x00
          Still image unsupported
        wWidth                            160
        wHeight                           120
        dwMinBitRate                  9216000
        dwMaxBitRate                  9216000
        dwMaxVideoFrameBufferSize       38400
        dwDefaultFrameInterval         666666
        bFrameIntervalType                  1
        dwFrameInterval( 0)            666666
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x13d4  3x 980 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0364  1x 868 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0278  1x 632 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x0320  1x 800 bytes
        bInterval               1
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)[/SIZE]

---

### Post by charlemagne86 on 2008-05-23
HEY EVERYONE

for all those people who have got their webcams working on ekiga but after a sec or so they begin showing distortions with funny black/red/pink/green colors.....i found a sollution:

when you start ekiga webcam, when this distortion happens....just clik on the brightness slider in the video tab (even the minutest adjustment will do) and the distortions are all gone...even after you restart ekiga again....However you have to do this after each reboot.

---

### Post by lotrnew on 2008-05-26
i got cheese working on my vaio FZ 
just create file
nano /usr/share/hal/fdi/information/20thirdparty/10-r5u870-webcam.fdi

paste this
> 
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
    <match key="info.subsystem" string="usb">
      <match key="usb.interface.class" int="0x0e">
        <match key="usb.interface.subclass" int="0x02">
          <match key="usb.interface.protocol" int="0x00">
            <merge key="info.category" type="string">video4linux</merge>
	    <append key="info.capabilities" type="strlist">video4linux</append>
            <merge key="linux.subsystem" type="string">video4linux</merge>
            <merge key="video4linux.device" type="string">/dev/video0</merge>
            <merge key="video4linux.version" type="string">2</merge>
          </match>
        </match>
      </match>
    </match>
  </device>
</deviceinfo>

then /etc/init.d/hal restart


but image from cam is duplicated and also i got a big green plague, so what should i do to fix that
i attached my picture from webcam as example

---

### Post by LadyTeacher on 2008-05-27
Hello! Im a very "new" ubuntu-user. (I have moved from Apple). I've had hardy heron on my sony vaio in about one week. Everything (almost) works fantastic. Exept my webcam... Ive tried to use all the solutions I've seen on this forum... I have installed the r5u870 installed...the lamp beside the camera eye is blinking...but no picture at all. But the system can not find the camera when I like to use it in any probram..... I get the error message "could not connect to video device (/dev/video0). Please check connection." Please....HELP!:confused:

---

### Post by LadyTeacher on 2008-05-27
Me again... Downloaded Ekiga! Ekiga detected the camera but cant get any picture out of it. Cheese and Camorama does not connect to the camera at all :?:? Oh how very very very nice it would be to get it work. I really like this OS (Hardy Heron). It works perfect on my Sony Waio...the only thing that is missing is to get the webcam function.

---

### Post by edgesgeno on 2008-06-04
are there any drivers for the VGN-FE890 motion eye?

---

### Post by Sealbhach on 2008-06-05
Hi Just found this thread. Here is my lsusb:

```
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 05ca:183b Ricoh Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c047 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

Is my webcam the Ricoh Co.?

I have got test calls working in skype but would like to have the webcam working.

Skype can't find a device, neither can Ekiga.




.

---

### Post by oooh on 2008-06-06
you have a ricoh model  183b, the same as me 

05ca:183b Ricoh Co., Ltd 

you can make it run like this:
[http://ubuntuforums.org/showthread.php?t=289836&page=19](http://ubuntuforums.org/showthread.php?t=289836&page=19) same thread as this, just same pages ago !

good luck !

---

### Post by tempaznx on 2008-06-11
Hey guys, I'm new to linux, but I've picked it up sorta quickly.

I have the fz140E, with the 1837 RICOH camera (>__<)
I used this website

[http://ubuntuforums.org/showthread.php?t=486861&highlight=1837&page=2]("http://ubuntuforums.org/showthread.php?t=486861&highlight=1837&page=2")  Instructions are on the sept 10th post.

And ended up with these errors. 

> 

sanvichithj@sanvichithj-laptop:~/Documents/r5u870-0.10.0$ sudo make
make -C /lib/modules/2.6.24-18-generic/build M=/home/sanvichithj/Documents/r5u870-0.10.0 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  CC [M]  /home/sanvichithj/Documents/r5u870-0.10.0/r5u870_md.o
In file included from /home/sanvichithj/Documents/r5u870-0.10.0/r5u870_md.c:55:
/home/sanvichithj/Documents/r5u870-0.10.0/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/sanvichithj/Documents/r5u870-0.10.0/r5u870_md.o] Error 1
make[1]: *** [_module_/home/sanvichithj/Documents/r5u870-0.10.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [all] Error 2
sanvichithj@sanvichithj-laptop:~/Documents/r5u870-0.10.0$ sudo make install
make -C /lib/modules/2.6.24-18-generic/build M=/home/sanvichithj/Documents/r5u870-0.10.0 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  CC [M]  /home/sanvichithj/Documents/r5u870-0.10.0/r5u870_md.o
In file included from /home/sanvichithj/Documents/r5u870-0.10.0/r5u870_md.c:55:
/home/sanvichithj/Documents/r5u870-0.10.0/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/sanvichithj/Documents/r5u870-0.10.0/r5u870_md.o] Error 1
make[1]: *** [_module_/home/sanvichithj/Documents/r5u870-0.10.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [all] Error 2


---

### Post by rafttrip on 2008-06-24
I got my webcam working in hardy (8.04) with thease 2

ricoh-webcam-r5u870-2.6.24-19-generic_0.11.0-2arakhne1_i386.deb

ricoh-webcam-r5u870_0.11.0-2arakhne1_i386.deb packages

 I got from this sight.

[http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/](http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/)

I'm not sure how I found it the firs time but it is working now in XawTV any way. I have not tryed in aMSN yet.

I have a VAIO VGN-CR125E

with a 05ca:1839 Ricoh Co., Ltd
webcam

hope this healped.

---

### Post by napalm brain on 2008-06-28
I installed the driver and it now works but it's inverted. Any one have any advice on what to do?

---

### Post by borgrodrick on 2008-07-13
Hey Thanks for whoever put this post 
[http://www.palmix.org/r5u870-en.html](http://www.palmix.org/r5u870-en.html)

It worked for me. 

The only problem is that it works perfectly with Ekiga but does not work with Cheese or camorama.. is there a setting or something in these programs??

Regards 
Rodrick

---

### Post by Arschbohrung on 2008-07-15
Hi rafttrip

i have the same webcam in my sony vaio vgn-ar31s desktop replacement and i am running hardy 8.04 (2.6.24-19-generic) but when i tried to install the drivers from the above sites, i get an error saying "wrong architecture" this driver is compiled for 2.6.24-19-generic and i have (uname -r) confirmed my version to be the same but still the message - left me bewildered.

any help will be appreciated. thanks

p.s screenshot attached

---

### Post by aliwery on 2008-07-19
Any simpletons out there??

Just got a VGN-SZ76 - with 64bit..& you've guessed it, motion eye doesn't work.   Aghhhhhhhhhh!

I've read this thread (& searched many others!), but it's way over my head - anyone know of an idiots guide / link to get this working?

Thanks

---

### Post by Arschbohrung on 2008-07-21
Hi Aliwery

As far as I know (or I didn't bother to explore enough into 64 bit architecture) there are no drivers available for vaio motion eye. Apparently, there are drivers for 32 bit, but it still brings an error of architecture and not advisable to test these drivers for 64 bit. 

What I am trying to say is, keep looking mate. I am looking as well. will post in forum once resolved. 

cheers

---

### Post by IntuitiveNipple on 2008-07-22
I've created a DKMS (Dynamic Kernel Module Support) kernel-module package for the Motion Eye driver to make it easier to install for **Gutsy**, **Hardy**, and **Intrepid**.

To use it, first add my Ubuntu PPA (Personal Package Archive) to the apt sources list, update:
```

$ sudo sh -c "echo 'deb http://ppa.launchpad.net/intuitivenipple/ubuntu $(lsb_release -sc) main' >/etc/apt/sources.list.d/intuitivenipple.list"
$ sudo apt-get update

```
Use Synaptic, aptitude or apt-get to install:
```

$ sudo apt-get install r5u870-kernel-source

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  r5u870-kernel-source
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 158kB of archives.
After this operation, 0B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  r5u870-kernel-source
Install these packages without verification [y/N]? y
Get: 1 http://ppa.launchpad.net hardy/main r5u870-kernel-source 0.11.1-0ubuntu1~ppa5h [158kB]
Fetched 158kB in 0s (400kB/s)            
(Reading database ... 155123 files and directories currently installed.)
Preparing to replace r5u870-kernel-source 0.11.1-0ubuntu1~ppa1h (using .../r5u870-kernel-source_0.11.1-0ubuntu1~ppa5h_all.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement r5u870-kernel-source ...
Setting up r5u870-kernel-source (0.11.1-0ubuntu1~ppa5h) ...
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.

```
Load the driver:
```

$ sudo modprobe r5u870

```

---

