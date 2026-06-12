---
title: "Touchpad of asus notebook e202sa does not work at ubuntu 14.04"
date: 2016-04-17
forum: Hardware
---

### Post by Jongtaek_Choi on 2016-04-17
Hi.
Sorry for my bad English. I'm not native at English. 
Some days ago, I bought an asus notebook(e202sa) and installed ubuntu 14.04 LTS  version.
When I was installing the ubuntu, my touchpad worked well like below.
[IMG]https://www.dropbox.com/s/bky2qto6v36w90r/Screenshot%20from%202016-04-19%2008%3A50%3A56.png?dl=0[/IMG]
But after I finished installing and reboot It does not work.
I searched some tips but all does not work. 
Here's what I've tried to solve the problem.

1. I pressed fn key and f9 key simultaneously. It is combination to toggle activation the touchpad.

2. I have followed as outlined in the link below.
[http://askubuntu.com/questions/506826/asus-laptop-touchpad-not-working](http://askubuntu.com/questions/506826/asus-laptop-touchpad-not-working)

but, It did not work. Followings are error message at install focaltech-dkms[INDENT]Selecting previously unselected package focaltech-dkms.
(&#45936;&#51060;&#53552;&#48288;&#51060;&#49828; &#51069;&#45716;&#51473; ...&#54788;&#51116; 197295&#44060;&#51032; &#54028;&#51068;&#44284; &#46356;&#47113;&#53552;&#47532;&#44032; &#49444;&#52824;&#46104;&#50612; &#51080;&#49845;&#45768;&#45796;.)
Preparing to unpack .../focaltech-dkms_1.5~trusty1_all.deb ...
Unpacking focaltech-dkms (1.5~trusty1) ...
focaltech-dkms (1.5~trusty1) &#49444;&#51221;&#54616;&#45716; &#51473;&#51077;&#45768;&#45796; ...
Loading new focaltech-1.5~trusty1 DKMS files...
First Installation: checking all kernels...
Building only for 4.2.0-35-generic
Building for architecture x86_64
Building initial module for 4.2.0-35-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/focaltech-dkms.0.crash'
Error! Bad return status for module build on kernel: 4.2.0-35-generic (x86_64)
Consult /var/lib/dkms/focaltech/1.5~trusty1/build/make.log for more information.
jtchoi@jtchoi-E202SA:~/&#45796;&#50868;&#47196;&#46300;$ 
[/INDENT]


3. I tried to install xserver-xorg-input-synaptics but I couldn't install it.

Followings are some of the error msg.
 xserver-xorg-input-synaptics : &#51032;&#51316;: xorg-input-abi-20
                                &#51032;&#51316;: xserver-xorg-core (>= 2:1.14.99.902)

It may be caused by dependency problem. 

Followings are some information about my problem. 

jtchoi@jtchoi-E202SA:~/&#45796;&#50868;&#47196;&#46300;$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse                  id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; USB2.0 VGA UVC WebCam                       id=10    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
jtchoi@jtchoi-E202SA:~/&#45796;&#50868;&#47196;&#46300;$ uname -a
Linux jtchoi-E202SA 4.2.0-35-generic #40~14.04.1-Ubuntu SMP Fri Mar 18 16:37:35 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

If there's some one know about it, please help me. 
Thanks for reading.

---

