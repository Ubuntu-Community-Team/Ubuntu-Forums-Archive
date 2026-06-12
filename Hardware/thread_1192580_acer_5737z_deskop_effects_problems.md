---
title: "acer 5737z deskop effects problems"
date: 2009-06-20
forum: Hardware
---

### Post by Zoyberk on 2009-06-20
hello,just got acer laptop, installed kubuntu, tried to enable desktop effects and i get this(look sreen shoot)
any idea how can i fix that xD

oh and i have nvidia 9400M G graphich card, and I'm quite a newbie in kubuntu xD

---

### Post by overdrank on 2009-06-20
Hi and this may help     [BinaryDriverHowto Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?action=show&redirect=RestrictedDrivers%2FNVIDIA")

---

### Post by jerrrys on 2009-06-20
this may give you a better idea of whats going on

[http://ubuntuforums.org/showthread.php?t=799070&highlight=compiz-check](http://ubuntuforums.org/showthread.php?t=799070&highlight=compiz-check)

---

### Post by Zoyberk on 2009-06-20
> **jerrrys said:**
> this may give you a better idea of whats going on

[http://ubuntuforums.org/showthread.php?t=799070&highlight=compiz-check](http://ubuntuforums.org/showthread.php?t=799070&highlight=compiz-check)

did that and got this:

```
zoyberk@utopija:~$ chmod +x compiz-check
zoyberk@utopija:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   KDE4
 Graphics chip:         nVidia Corporation GeForce 9400M G (rev b1)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card.

```

---

### Post by Zoyberk on 2009-06-20
I went and cheched if there are any drivers avilible for my Graphic card. and there were. I instaled recommendet one, but when i try enable desktop effect screan just goes werid and lagg a litle. If i try enable them agen i get error that desktop effet couldnt be enabled, and that i should chech X settings or something like that.
If i reboot sistem all isok, and desktop effect arent enabbled.

---

### Post by jerrrys on 2009-06-20
run the test again, it should tell you about xorg

---

### Post by overdrank on 2009-06-20
Hi and I have seen many threads where kwin and compiz do not play well together.

---

### Post by Zoyberk on 2009-06-20
> **overdrank said:**
> Hi and I have seen many threads where kwin and compiz do not play well together.

emmm how can i fix that Xd ...i'm kinda noob

and runned test agen and got this:

```
zoyberk@utopija:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   KDE4       
 Graphics chip:         nVidia Corporation GeForce 9400M G (rev b1)
 Driver in use:         nvidia                                     
 Rendering method:      Nvidia                                     

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


```

---

### Post by olalaaa on 2009-08-28
I have some bad troubles with my Aspire 5737z, too (running Ubuntu 8.04).

Maybe I had to post in a different topic, but I feel that here is the place though where this issue should be discussed.

My Aspire 5737z has a Intel Dual Core T4200 (low voltage last generation 64bit processor).

I thought to install a 64bit flavor in my laptop, but I saw there in Ubuntu download page that it was nothing about i386-64 ( they told there only about AMD64 download version - fact which I consider some kind of bug : if I install AMD source in an Intel processor, with different architecture, I don't want to take some risk from doing that :confused: :confused: :confused:   ).

Also, I have read about some debates 32bit - vs 64bit which confused me even more, so I decided to install for the start the 32 bits, for being in the safe side... Anyway.

My videocard is GeForce 9400M G, but the main trouble is the widescreen display ( 1366 x 768 ).

The fact that my laptop is one of the 6 best laptops under 1000 Euros is of no help for me in the following circumstances :
neither (1) NVIDIA released any Linux driver to support that resolution,
(2) nor Ubuntu recognizes such resolution or allow me to chose at start NVIDIA driver or even "vesa" in order to see such HD image on my monitor
(3) I always am stuck with 800x600 even if I try to run nvidia-xconfig or to look after xorg.conf and add there the resolution supported by my display ...

Each single time the menu in Screen Resolution stay at 800x600 or 640x480. Why ??? :x .... **Why is not possible to upgrade anything in Ubuntu at least to recognize the native resolution of my display ?? Then how is possible that the 800x600 image to fill even the last pixel of my monitor ??? Isn't that a proof that Ubuntu actually *DOES recognize* my display resolution ??????????** Then why I am not allowed to use my graphic driver in order to fill that same display with 1366x768 content instead of 800x600 images ??

So, the problem is that with last generation video card and last generation display I am not able at least to see a single image in that native resolution of my display :confused: ( not to say about desktop visual effects or compiz .... I even don't know if I have installed or not compiz in my laptop ... :cry: ... When I look at youtube videos with Ubuntu desktop effects, this makes me cry ... :( ...

I tried to add some own "monitor driver" when the initial menu saying {Configure / Run Always Low Res / Continue} was presented to me ("Your monitor could not be identified, etc etc"), but there are NO laptop display drivers ( **.inf** files ), nothing !! ....

Despite of setting some similar resolution ( as generic LCD display 1320 x 7** ) , I am not able, again to pass the Test and to set the resolution as it should be....

What to do ? ( Because I hate going back at Windows, even a Win7 one .... :confused: ... ) I must mention that in Windows I am pretty good ... but these Ubuntu display issues makes me crazy .... 

Anyone could help ? ...

---

### Post by olalaaa on 2009-08-28
**Zoyberk**, has your laptop also widescreen, too ?

By the way, I'm not going to upgrade at different Ubuntu version !! If you look carefully, Ubuntu 8.04 is the only Long Term Support, right ??

( Despite that, I find it difficult to believe that even until now the Firefox 3.5.2 was not included yet by default in repositories of Ubuntu 8.04 ..... :evil: .... ) I don't want to upgrade each 6 months or so and find new drivers for my laptop or reinstall anything :( ....

---

### Post by Zoyberk on 2009-08-28
Hello,

I have wide screen too and I'm using ubuntu 9.04 
When i was using kubuntu i had those effect problems... but then i installed gnome and removed KDE and all work fine.
All worked out of box and if i go to system>adminsitrator>hardware drivers i have the my geforce 9400M G available (version 180)

all worket out of box except i cant get suspend to work, whats making it weird is that when i first installed kubuntu suspend was working and then some day just stoped =)
so your suspend/sleep work? XD

---

### Post by olalaaa on 2009-08-28
What do you mean of "installing gnome" ??? Gnome is installed by default with Ubuntu, right ? I never heard of any linux distro that to not have "inside" it the Gnome ...

Do you mean the Gnome part that handle the display ( "Gdm" ), maybe ?

About the suspend / sleep, I will check then tell you ( I now write from my PC, not my laptop ). I prefer to not use so much such functions sleep / suspend ( I never did ), especially not like to let the laptop powered ( even if only with battery ) because either battery can be damaged if stays too much connected with AC power charger or its lifetime can be decreased if it is discharged very slowly ( during the sleep ). On the laptop handbook it says that it can be about 300 times recharged before its performance decreases. First week since I bought the laptop I used it 10 hours per day so it is already now at 97% from battery capacity ( even fully charged ) .

Is that driver NVIDIA downloaded from Ubuntu repositories ? ( is it installed by default ?? )

---

### Post by Zoyberk on 2009-08-29
sorry for late response... XD

well first thanks for that sleep on laptops info =)
and about gnome i used this guide: [http://psychocats.net/ubuntu/gnome]("http://psychocats.net/ubuntu/gnome")
hope that tells you what i mean.

And for graphic card drivers, ubuntu suggested me to install them, so i guess they are default ones and installed from ubuntu repos.

---

### Post by olalaaa on 2009-08-31
You're right, KDE and Gnome are different graphical/command interfaces. Gnome is the default interface to most Linux distributions.

I solved my issue  with NVIDIA driver so I can enjoy now all the beautiful visual effects of Ubuntu.

Here's what I did, step by step ( or alike, main steps :P... ) :

( => Don't forget to have the internet connection enabled because sometimes the driver installation requires internet access to ftp.nvidia.com in order to download and install updates of kernel modules for NVIDIA )

for NVIDIA Geforce 9400M G it is necessary to download first the driver from here :

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
click
"**Beta and Archived Drivers**"
because the _stable/certified releases DON'T support yet 9400M G card_, only 9400 and older versions, so we need latest beta driver for Linux created for 9400M G .

We use that search page that opens there just to be allowed to chose from Recommended/Certified, BETA ,and ALL drivers. The default option does not give us access to ALL driver (but only to Recommended/Certified ones instead).

I had a lot of trouble until finding this workaround. Even version 180 seemed not to be the exact fit for my 9400M G ( which is not the same card as other 9400 cards or 9x00 cards :) ).

OK. From that menu, you chose Product Series - GeForce 9M Series ( Notebooks ), Product - GeForce 9400M G, and then Recommended/Certified - ALL, so you will find the driver that you need : **Linux Display Driver Version 190.18 Beta** ( Release date 23 July, 2009 ).

Download the driver on the Desktop ( as I did ) to be easier to find it when you install it.

In Ubuntu 8.04 the steps are those :

Stop the X server :

1). **CTRL+ALT+F1**
2). **sudo /etc/init.d/gdm stop**

somewhere at steps 1 or 2 you are asked to insert again username + password in order to continue to insert command lines in terminal.

3). **cd Desktop**
4). **sudo sh ./NVIDIA-Linux-x86-190.18-pkg1.run**

As you can see, the driver version is 190 ( BETA version ), and I used the 32-bit but I think for 64 bit is the same, just check the name for yourself when downloading the driver and insert it correctly when you install it as above.

The installer opens a red-blue window, you just must choose "Accept" the license, then "OK" at each question (including that about running **nvidia-xconfig** utility which will reconfigure the **xorg.conf** file ).

After you are done, you must restart the X server :

**sudo /etc/init.d/gdm start**
and you can enjoy your new display :popcorn:

---

### Post by olalaaa on 2009-08-31
Very useful commands just to check your video card

```
lspci | grep VGA
```

or, even a better one

```
sudo lshw -C video
```

With this second one, you can see a lot of details :guitar:

---

### Post by olalaaa on 2009-10-22
latest NVidia driver is now 
**190.32**

---

