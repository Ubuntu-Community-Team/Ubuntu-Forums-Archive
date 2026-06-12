---
title: "Black screen"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by young-dragon on 2009-10-19
Hi,

I am a beginner that I am very new to Linux, I am already familiar with Windows (whole family) and Apple Mac OS X, therefore I am very interesting to install Linux Ubuntu on my pc however, before I start explain what wrong with it, I will put my oc specification to ensure you know what wrong with it.

CPU: Intel Pentium 4 2.93GHz
RAM: 512MB
Graphic Card: Intel 82915G/GV/ 910GL Express Chipset Family

So, when I run the boot with Ubuntu, the logo and list of stuff for install, i select either "Try Ubuntu without any change to your computer" or "Install Ubuntu". After that, it come up like windows loading which are Ubuntu so I just waiting for install or desktop however, after Ubuntu loading done, it gone to black screen... I cant even see anything from error or white mouse thing.

So how can I resolve the problem?
Sorry for my english as it's not my first language. I am deaf.

Thanks
young-dragon

---

### Post by stlsaint on 2009-10-19
sounds like you have a faulty iso download. try redownloading the iso again and burn to disc at slowest speed possible and check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") of the iso before burning to disc.

---

### Post by p0cky84 on 2009-10-19
> **young-dragon said:**
>  Sorry for my english as it's not my first language. I am **deaf.**

Kinda off-topic... but I don't see how you being deaf has anything to do with that o_O
Was it a joke of some sort?

---

### Post by young-dragon on 2009-10-20
> **p0cky84 said:**
> Kinda off-topic... but I don't see how you being deaf has anything to do with that o_O
Was it a joke of some sort?

Nah, it no joke, because english is hard for deaf and their grammar  is not correct for their sentence and ittake long time to improve their english structure. :-)

---

### Post by young-dragon on 2009-10-20
> **stlsaint said:**
> sounds like you have a faulty iso download. try redownloading the iso again and burn to disc at slowest speed possible and check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") of the iso before burning to disc.

Well, I already check other computer, windows xp and vista on the laptop, to run Ubuntu and it seem nothing wrong with it, it just prefect. It seem my old PC cant run with it.
Do I have to use MD5sum to check it? I am no knowledge of code language.

i think i burned the iso as 24 times speed, not 52 times.

---

### Post by young-dragon on 2009-10-21
> **stlsaint said:**
> sounds like you have a faulty iso download. try redownloading the iso again and burn to disc at slowest speed possible and check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") of the iso before burning to disc.

Hi,

I tried to following what you said to me about md5sum, it work well unfortunately, it still same result! I really need it as soon as possible before 28 days left for activation (crap windows damn xp)

Thanks

---

### Post by young-dragon on 2009-10-21
I forgot to add something.

My hard drive is 500GB!

---

### Post by Sylslay on 2009-10-21
Yours problem is here Graphic Card: Intel 82915G/GV/ 910GL Express Chipset Family 
and here Xorg ,, 
Graphic card can't find proper resolution of screen!!
Try run in vesa mode (is that F4)
or before you boot just press "tab or e"
and go to command line of grub,
and now delete splash and quite and add line to grub:
vga= 773 ??? 

depend on screensize :
VGA Resolution Codes for GRUB & Lilo
--- Depth --
Colors  bits [ 640x480]  [800×600] [1024×768]  1152×864] 1280×1024]  1600×1200]
   256    8   vga=769 ] vga=771 ]  vga=773]    vga=353 ]  vga=775 ]  vga=796 ]
 32000    ?   vga=784 ] vga=787 ]  vga=790]    vga= ?]    vga=793]    vga= ? ]
 65000   16   vga=785 ] vga=788 ]  vga=791]    vga=355 ]   vga=794]    vga=798 ]
 16.7M   24   vga=786 ] vga=789 ]  vga=792   vga=795 ]  vga=799 ]

:P

and you can rest () to deflaut setting:

sudo dpkg-reconfigure -phigh xserver-xorg

my intell and my ubuntu worked great since:

8.04 good
8.10 bad - balck screen
9.04 - good
9.10   very good, 
so try difren version of install cd and than upgrade to latest:
update-manager 
or to karmic 9.10 , it use new intel driver xorg 1.7 with UXA.
 PRESS alt+F2 TYPE update-manager -d

---

### Post by young-dragon on 2009-10-22
> **Sylslay said:**
> Yours problem is here Graphic Card: Intel 82915G/GV/ 910GL Express Chipset Family 
and here Xorg ,, 
Graphic card can't find proper resolution of screen!!
Try run in vesa mode (is that F4)
or before you boot just press "tab or e"
and go to command line of grub,
and now delete splash and quite and add line to grub:
vga= 773 ??? 

depend on screensize :
VGA Resolution Codes for GRUB & Lilo
--- Depth --
Colors  bits [ 640x480]  [800×600] [1024×768]  1152×864] 1280×1024]  1600×1200]
   256    8   vga=769 ] vga=771 ]  vga=773]    vga=353 ]  vga=775 ]  vga=796 ]
 32000    ?   vga=784 ] vga=787 ]  vga=790]    vga= ?]    vga=793]    vga= ? ]
 65000   16   vga=785 ] vga=788 ]  vga=791]    vga=355 ]   vga=794]    vga=798 ]
 16.7M   24   vga=786 ] vga=789 ]  vga=792   vga=795 ]  vga=799 ]

:P

and you can rest () to deflaut setting:

sudo dpkg-reconfigure -phigh xserver-xorg

my intell and my ubuntu worked great since:

8.04 good
8.10 bad - balck screen
9.04 - good
9.10   very good, 
so try difren version of install cd and than upgrade to latest:
update-manager 
or to karmic 9.10 , it use new intel driver xorg 1.7 with UXA.
 PRESS alt+F2 TYPE update-manager -d

Hi,

I just testing now but i am not very sure about grub line...
What i wrote is here

file=cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz grub:vga= 791

and it just list of programming so some of them are failed!

i am not sure if i did right way what you told me to do...

Should I have to add the line like this?

file=cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz grub:vga= 791 sudo dpkg-reconfigure -phigh xserver-xorg

Explain to me. I am new to use Ubuntu :-)

---

### Post by young-dragon on 2009-10-22
I am going to downloading ubuntu 8.04 desktop to see if it work.

I will let you know the result in few hour

---

### Post by Sylslay on 2009-10-22
yes
this command 
Should I have to add the line like this?

Just Prss Tab/ or e letter , than chanege booting line, delete other parametrs and add 2 parametrs

it's from my grub:
linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=db96d726-e57f-44b8-af35-279408553c8b ro vga=792,

last 2 praramets
ro -mount read onyly,file sysytem
vga=792 type of graphic mode,

You mays use insted vga=792, command gfxpayload=1024x768,

And about this command : use to rest seting, after somthing go wrong with yours ubuntu on harddrive, than use that

sudo dpkg-reconfigure -phigh xserver-xorg, 

PS. ubuntu 8.04 is LTS, long term support

---

### Post by young-dragon on 2009-10-23
Right... I will tell you what I done so far..

I press F6 for edit=on (is that grub command?)
then i use ro vga=792, command gfxpayload=1024x768 and den run the grub and it nothing happened... it just command run and that it... i cant see anything happened next.

And then, i read again what other guy said about MD5SUM so I use cd to run check for defects (the picture look different from my linux OS) and it says 2 files is error... Does it mean I have to downloading again?

---

### Post by Sylslay on 2009-10-23
after You edit grub ,
add only 2 parametrs : in end off line  ,delete only command "splash"
add: ro vga=792

and then press
ctrl+x to run grub.(with modifcation)

---

### Post by young-dragon on 2009-10-24
Finally you explain to me much clear unfortunately last part is madifcation... It does not work, when I press control + x and it didnt run... it just stay... :-S

Any suggestion?[FONT=&quot] [/FONT]

---

### Post by Sylslay on 2009-10-24
before changing boot option for grub

prsss F6 and mark acpi=off and other box's in this menu

acpi - menagmet of power somtimes not working properly from BIOS.

And if yua able to hear any sound from speakers, 
try swietch defoult console from 
ctlr+alt+F1 too ctrl+alt+f12

Gnome/xorg windows is on ctr+alt+F7 in ubuntu - ususaly

---

### Post by young-dragon on 2009-10-26
Unfortunately it doesn't work. Do you think it something wrong with graphic card?

---

### Post by Sylslay on 2009-10-27
I think that, some disto-linux work on some pc and some disto , DOES NOT...
I lern so far , very litle.
On my pc full installed and worked where:
Debian, Ubuntu, Knoppix, Mandriva

other disto seems to be to complicated, for convinient use.

PS. Download Debian network install, connect pc to router/modem  with network cable - lan,
and install in 2hr.

[http://cdimage.debian.org/debian-cd/5.0.3/i386/bt-cd/debian-503-i386-netinst.iso.torrent](http://cdimage.debian.org/debian-cd/5.0.3/i386/bt-cd/debian-503-i386-netinst.iso.torrent)

GUI installer

Ubuntu way:
You could try downloading 'Ubuntu Netbook Remix' from bottom of this page:
[http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr)

Alternate install CD

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installs on systems with less than about 256MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably). 

[http://releases.ubuntu.com/jaunty/](http://releases.ubuntu.com/jaunty/)

[http://www.geteasypeasy.com/](http://www.geteasypeasy.com/)

---

### Post by young-dragon on 2009-10-30
Right,

I have learnt a lot about Ubuntu Desktop and Ubuntu Alternate however, I tried to use 9.04 and 9.10 Ubuntu Alternate version.
Alternate did work but it cant found some thing on the cd so, Here what is say... Both of them did not work well.

Alternate 9.04 and 9.10

9.04-
.dists/jaunty/main/binary-i386/Pakages.gz

9.10
.dists/karmic/main/binary-i386/Pakages.gz

So what can I do? I think Alternate version MIGHT work on my pc if we can sort it out!

---

### Post by young-dragon on 2009-11-02
OR shall I try to install Netbook remix?
I dont really like Netbook remix layout as I prefer to use desktop or alternate (it look same style as desktop)

---

### Post by young-dragon on 2009-11-09
I have resolve the problem, the main problem is DVD drive that it can't read full disc so I replaced old DVD drive so it now WORK!... Whoa hoo... I can now able to playing with Linux!

---

