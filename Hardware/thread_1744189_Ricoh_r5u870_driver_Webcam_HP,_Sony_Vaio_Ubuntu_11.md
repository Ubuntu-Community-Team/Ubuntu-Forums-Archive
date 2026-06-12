---
title: "Ricoh r5u870 driver Webcam HP, Sony Vaio Ubuntu 11.04"
date: 2011-04-30
forum: Hardware
---

### Post by novatillasku on 2011-04-30
Hi all, i have a webcam with ricoh r5u870 driver in a HP Pavilion dv1000
In maverick i configure with this link: [http://code.google.com/p/r5u870/]("http://code.google.com/p/r5u870/") but now don't work.

Googled i found new packages [here]("http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/").I install two .deb ([http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870-firmware_0.11.6-0arakhne0_i386.deb]("http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870-firmware_0.11.6-0arakhne0_i386.deb")) and ([ricoh-webcam-r5u870_0.11.6-0arakhne0_i386.deb]("ricoh-webcam-r5u870_0.11.6-0arakhne0_i386.deb")) but my webcam dont't work.

Can you tell me how is configuration? (sorry for my english)

---

### Post by nikunjbadjatya on 2011-04-30
Hi Members,

Even I am facing the same problem with my "HP Pavillion DV6000 laptop".
Previously I configured the webcam with same link as given by novatillasku.
But after updating to "Ubuntu11.04" from 10.10 . The webcam seems to not working.
It gives the following error msg on recompiling the [http://code.google.com/p/r5u870/](http://code.google.com/p/r5u870/) 

```

$ uname -a
$ Linux explorer 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

``````

$pwd
~/r5u870

$ make
make -C /lib/modules/2.6.38-8-generic/build M=/home/niks/Downloads/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/niks/Downloads/r5u870/r5u870.o
In file included from /home/niks/Downloads/r5u870/r5u870.c:59:0:
/home/niks/Downloads/r5u870/usbcam/usbcam.h:38:28: fatal error: linux/videodev.h: No such file or directory
compilation terminated.
make[2]: *** [/home/niks/Downloads/r5u870/r5u870.o] Error 1
make[1]: *** [_module_/home/niks/Downloads/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [all] Error 2

```On further investigation I found that in 38 kernel, videodev.h has been removed/changed . 

I checked with webcam softwares such as "gucview" also..But they are also not able to start/open webcam.

Please help us with this.!! 

Thanks,
Nikunj
Bangalore , India

---

### Post by siabost on 2011-04-30
I have exactly the same problem.
Seems support for videodev.h has been dropped - see this in the Kubuntu Forums [http://kubuntuforums.net/forums/index.php?topic=3115676.0]("http://kubuntuforums.net/forums/index.php?topic=3115676.0")

SOLVED (for me anyway):
[http://ubuntuforums.org/showthread.php?t=1544564&highlight=videodev.h&page=3]("http://ubuntuforums.org/showthread.php?t=1544564&highlight=videodev.h&page=3")
I'm running Ubuntu 11.04, kernel 2.6.38-8-generic & works splendidly

Enter the following lines (one at a time) in the terminal - you will be asked your password after entering the first line (the password entry will not show in the terminal but it is being registered).

> sudo add-apt-repository ppa:r5u87x-loader/ppa
sudo apt-get update
sudo apt-get install r5u87x
sudo /usr/share/r5u87x/r5u87x-download-firmware.sh 

You'll get a GPG authentication warning but ignore that & also a y/n warning (enter y) after the last line shown above.

Good Luck :-)

---

### Post by nikunjbadjatya on 2011-05-01
Thanks siabost for your useful post.

It did work for me too. :)
[B]But the mic has stopped working now..!! :( 
[/B]
I am not sure whether it was working before installing this new firmware or not. !! But it is sure working in Windows ( dual boot ).  

Any ideas.?

---

### Post by samcompton on 2011-05-01
Does not work for HP dv6000 webcam.   

Bus 001 Device 002: ID 05ca:1870 Ricoh Co., Ltd Webcam 1000

Any ideas?

---

### Post by tfotherby on 2011-05-02
Thanks siabost - your instructions fixed the webcam on my Sony Vaio VGN-AR51 laptop after upgrading to Ubuntu 11.04.

---

### Post by Doctor_Pain on 2011-05-03
Doesn't work for Bus 001 Device 004: ID 05ca:1830 Ricoh Co., Ltd Visual Communication Camera VGP-VCC2 in a sony vaio vgn-sz3xwp/c.

---

### Post by nikunjbadjatya on 2011-05-04
Hi,

I followed the link  [http://ubuntuforums.org/showthread.php?t=1744751](http://ubuntuforums.org/showthread.php?t=1744751)
and mic was back into action. !!

Thanks All.
Nikunj
Bangalore, India

---

### Post by grampe on 2011-05-06
it doesn't work with any WDM cameras, only with UVC.
the [list]("https://bitbucket.org/ahixon/r5u87x/src/881dbd07a263/docs/model_matrix.txt") of r5u87x cameras.
Only R5U870 works with WDMs but there is not version for >=2.6.38 kernel yet.

---

### Post by Tiko on 2011-05-20
Thanks, solved my sony vaio VGN-SZ55GN webcam.

Not sure about the mic problem though.

---

### Post by Stormsight on 2011-05-20
i cannot use the r5u87x driver with my hp pavillion dv6000 because it doesnt work with skype. So i came up with a partial fix for r5u870 (on ubuntu 11.04), which however doesnt solve the compilation problem. here it is:

sudo apt-get install libv4l-dev

sudo ln -s '/usr/include/libv4l1-videodev.h' '/usr/src/linux-headers-2.6.38-8-generic/include/linux/libv4l1-videodev.h' 


modify usbcam.h and usbcam_priv.h to point at libv4l1-videodev.h

but i still got some errors dont know how to fix those

make:

make -C /lib/modules/2.6.38-8-generic/build M=/home/francy/Downloads/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/francy/Downloads/r5u870/r5u870.o
In file included from /usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/include/stdint.h:5:0,
                 from include/linux/libv4l1-videodev.h:6,
                 from /home/francy/Downloads/r5u870/usbcam/usbcam.h:38,
                 from /home/francy/Downloads/r5u870/r5u870.c:59:
/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/include/stdint-gcc.h:86:26: error: conflicting types for &#8216;uintptr_t&#8217;
include/linux/types.h:44:24: note: previous declaration of &#8216;uintptr_t&#8217; was here
make[2]: *** [/home/francy/Downloads/r5u870/r5u870.o] Error 1
make[1]: *** [_module_/home/francy/Downloads/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [all] Error 2

my programming knowledge is limited so if any one understands these errors please help me make this work

before in ubuntu 10 i was using this driver and everything worked just fine.

---

### Post by padonok600 on 2011-07-01
Try to install old 2.6.35 kernel and headers

Ether from ubuntu 10.10 or like I did from here: [http://ck.kolivas.org/patches/Ubuntu%20Packages/](http://ck.kolivas.org/patches/Ubuntu%20Packages/) (they only have 64bit packages)
reboot pick Try older kernel (or something like that, don't quite remember)

Make sure /lib/modules/{your kernel}/build points to /usr/src/{your kernel}
ln -s /usr/src/{your kernel} /lib/modules/{your kernel}/build

install dkms and libusb-dev

download r5u870 packages (ver 0.11.6 updated for 2.6.35 kernel) from here : [http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/](http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/)

install both, firmware first

---

### Post by MotherMonster on 2011-07-01
Hi :( I sound like such an idiot and I'm very sorry for your predicament, but I'm really desperate for help... If anyone could take a look at my thread [http://ubuntuforums.org/showthread.php?t=1794403](http://ubuntuforums.org/showthread.php?t=1794403) and see if they could help out I would be thrilled. Once again I'm sorry for looking like such an idiot. I hope you solve your problem too!

---

### Post by iceguitar on 2011-07-15
Siabost,
Thanks for sharing this mate, fixed my long pesking issue with the Ricoh webcam on a VAIO CR series laptop:popcorn:

---

### Post by hosami on 2011-08-09
Thanks dude, It also worked for me:

Vaio VGN SZ430N webcam

---

### Post by dpilgrim on 2011-08-24
> **siabost said:**
> Enter the following lines (one at a time) in the terminal - you will be asked your password after entering the first line (the password entry will not show in the terminal but it is being registered).



You'll get a GPG authentication warning but ignore that & also a y/n warning (enter y) after the last line shown above.

Good Luck :-)

I have a Sony Vaio SZ series, and my Ricoh webcam is on the list of [supported devices]("https://bitbucket.org/ahixon/r5u87x/src/881dbd07a263/docs/model_matrix.txt") (VID 0x05CA, PID 0x1830), but these steps do not appear to work for me. Package installation went smoothly, but Cheese still reports "no device found".

---

### Post by fayeav on 2011-09-04
> **siabost said:**
> I have exactly the same problem.
Seems support for videodev.h has been dropped - see this in the Kubuntu Forums [http://kubuntuforums.net/forums/index.php?topic=3115676.0]("http://kubuntuforums.net/forums/index.php?topic=3115676.0")

SOLVED (for me anyway):
[http://ubuntuforums.org/showthread.php?t=1544564&highlight=videodev.h&page=3]("http://ubuntuforums.org/showthread.php?t=1544564&highlight=videodev.h&page=3")
I'm running Ubuntu 11.04, kernel 2.6.38-8-generic & works splendidly

Enter the following lines (one at a time) in the terminal - you will be asked your password after entering the first line (the password entry will not show in the terminal but it is being registered).



You'll get a GPG authentication warning but ignore that & also a y/n warning (enter y) after the last line shown above.

Good Luck :-)

Thank you so much!! I can believe that I finally have my camera work in my dv6000. I was about to buy a seperate one!!! :)

---

### Post by Stormsight on 2011-10-30
ok so the dude who makes the driver which this thread is about updated it for 3.x kernels, check out if it works [http://code.google.com/p/r5u870/](http://code.google.com/p/r5u870/)
 also (im using 10.04) i couldnt make the webcam work with skype, i tryed everything, and today after installing compiz my webcam is magically working!! i would love to tell you how but i've no idea!!!

---

### Post by lfmiller on 2012-12-29
> **siabost said:**
> I have exactly the same problem.
Seems support for videodev.h has been dropped - see this in the Kubuntu Forums [http://kubuntuforums.net/forums/index.php?topic=3115676.0]("http://kubuntuforums.net/forums/index.php?topic=3115676.0")

SOLVED (for me anyway):
[http://ubuntuforums.org/showthread.php?t=1544564&highlight=videodev.h&page=3]("http://ubuntuforums.org/showthread.php?t=1544564&highlight=videodev.h&page=3")
I'm running Ubuntu 11.04, kernel 2.6.38-8-generic & works splendidly

Enter the following lines (one at a time) in the terminal - you will be asked your password after entering the first line (the password entry will not show in the terminal but it is being registered).



You'll get a GPG authentication warning but ignore that & also a y/n warning (enter y) after the last line shown above.

Good Luck :-)

This worked for me using a HP Pavillon DV6000, thou I seem to have audio issues with recordings, doubt that has anything to do with the camera! :-) Glad I came across this posting, it was frusting up till now!
Thanks

---

### Post by Mugen Kurohachi on 2013-05-15
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mugen@ROG-MUG-002 ~ $ sudo apt-get install r5u87x
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

HELP???

---

