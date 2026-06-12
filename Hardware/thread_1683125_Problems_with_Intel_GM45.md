---
title: "Problems with Intel GM45"
date: 2011-02-07
forum: Hardware
---

### Post by ztotz_pc on 2011-02-07
Hello!^_^
I have a problem with my xorg.conf file. It has detected my Intel GM45 Express but it has a problem with the resolution....Its always on the 1024x768 resolution and not in full screen resolution( 1366x768 ).....How do I do it?

NOTE: I'm new to Ubuntu I have just installed it     Jan. 4, 2011

---

### Post by sam1948 on 2011-02-07
hi,
u can try this:
[http://www.liberiangeek.net/2010/12/change-screen-resolutions-ubuntu-10-10-maverick-meerkat-arandr/](http://www.liberiangeek.net/2010/12/change-screen-resolutions-ubuntu-10-10-maverick-meerkat-arandr/)

or more complex way:
please run the following and upload the output.
```
uname -a
```
and 
```
lspci -v
```

and we will try to solve it.

---

### Post by ztotz_pc on 2011-02-07
> **sam1948 said:**
> hi,
u can try this:
[http://www.liberiangeek.net/2010/12/change-screen-resolutions-ubuntu-10-10-maverick-meerkat-arandr/](http://www.liberiangeek.net/2010/12/change-screen-resolutions-ubuntu-10-10-maverick-meerkat-arandr/)

or more complex way:
please run the following and upload the output.
```
uname -a
```
and 
```
lspci -v
```

and we will try to solve it.

yehey!!!!! \\:D/
thanks for the help my display is totally ok(atleast).
Thanks Very much..........

---

### Post by ketanmalvankar on 2011-07-31
I am having same problem, however xrandr also shows only one resolution(1024x768). I am using ubuntu 11.04. 
pls provide me solution for this.

---

### Post by sam1948 on 2011-08-01
hi,

it is a bit long but if xrender didnt work we must go the long way.

please avoid uploading so much text this way. it is hard to follow.
instead paste the text in file and upload it (give the file proper name)
(it would be very kind of you also to delete the log file text from the message(: )

in addition please upload the data requested in the previous messages (also...if its too long, put it in a file)

you can copy paste the output from the terminal 
OR use this way:
```
lspci -v > lspci_out
```
which will directly put the commands output into a file called "lspci_out"

additional useful info is technical details about your computer (brand and model/type/name)
or/and the output of:
```
sudo lshw > lshw_out
```

BR

---

### Post by ketanmalvankar on 2011-08-02
Thanks for ur input :)
As requested I have attached my log file in previous reply.As far as my understanding in log file it shows it has loaded Vesa driver instead of intel. I have installed xorg-video-intel.
driver files,and I have intel cantiga graphics controller. 
Since I am not at home I'll provide u output of those command once I reach home. My doubt is does Vesa supports 1366x768 resolution?

---

### Post by ketanmalvankar on 2011-08-04
Output of uname -a is follows
Linux ketan-Aspire-4736Z 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
I am using Ubuntu 11.04
I have attached my output in following files..pls suggest me what to do.

---

### Post by sam1948 on 2011-08-09
hi,
sorry for the delay.
I hope we will find something.
1. does 3d effects works?
2. please upload the file /etc/X11/xorg.conf

this is an example of my xorg.conf:
```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	SubSection "Display"
        Depth        24
        Modes      "1920x1080_60.00"
    EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

**backup this file** 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkup
```
**if you'r not sure how don't change it yet**

step 1: if you can see in your xorg.conf file the resolution which you r stuck with, try to change the width and height to those you want (and your screen is capable) 

now before we continue try restart and see if there is any change.

if there is then we done, if not check the this 

your xorg should looks somewhat similar to mine but instead of "nvidia" it should have "intel"

run and upload the output:
```
lsmod | grep intel
```
```
lsmod | grep i915
```

was there any other distro that worked?

when trying ARandR, do you see only one resolution or the other just wont work?

do you use vga cable? try dvi and restart
do you use dvi cable? try vga and restart (:

i hope one of these will solve it.
if not consider other distros which you can try the live-cd first.

this guy [_here_]("http://www.h-node.com/notebooks/view/en/305/Aspire-5742-6430") says that [_this_]("http://trisquel.info/en") distro worked for with the same vga card.
you can try it.

i know it looks a lot, try to follow and reply with some results.

good luck.

---

