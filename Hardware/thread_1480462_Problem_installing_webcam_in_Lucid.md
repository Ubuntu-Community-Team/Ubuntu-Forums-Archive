---
title: "Problem installing webcam in Lucid"
date: 2010-05-11
forum: Hardware
---

### Post by rrc21 on 2010-05-11
Hi Ubuntu Forum Community,

I've spent 5 hours googling and searching the forums of no avail for help on how to install my webcam (an Intel Easy PC CS120) with Ubuntu Desktop Lucid 10.04.

As far as I've understood, all I need to do is install GSPCA. I've downloaded it and I've tried following every guide that I've found and nothing works - well 'lsmod' lists the webcam so it's detected at least.

All I really want is to use my webcam with skype and I really hope that's not too much to ask from the ubuntu community or overlords.

Could some kind soul please help me with the commands that I need to  use.

---

### Post by prj44 on 2010-05-12
Good luck!

For me, a fan of Ubuntu, THE most disappointing thing  -- all versions back to 7 -- has involved my inability to get ANY webcam to work properly.  It simply doesn't happen and getting meaningful instruction or properly composed help material is not likely.

It is frustrating to see the OS develop so nicely, to be so easy and yet to not have my cam working.  It's what keeps me using Windows, frankly.

I hope your experience is different.
:(

---

### Post by rrc21 on 2010-05-13
Thank prj44 for the reply, although it wasn't really what I was hoping for.

I love Ubuntu and use it as my primary os, but I'd agree with you that my experience thus far hasn't been the best wrt webcam support.

For the sake of my life, I don't know how to decompile the kernal. Still, I hope that it isn't that difficult to direct new users on how to install the GSPCA.

:confused:

---

### Post by kyphi on 2010-05-13
Now calm down folks.

Gspca? I assume that you mean the file from Michel Xhaard who has tested a great many webcams and has written drivers for them.

The file is called:  gspcav1-20071224.tar.gz

To open it, open a terminal and change directory to where you have downloaded the file (if the file has been downloaded to your Desktop, type cd Desktop) and then type:

tar xvf gspcav1-20071224.tar.gz

then press Enter.

You will find instructions in there on what to do next.

I have not checked if your webcam is supported by this driver - there are just too many webcams in this world.

I use a Logitech Quickcam Pro 9000, a fine webcam,  Plug it in and it works straightaway.  Recommended by Skype too,

---

### Post by IcarusR on 2010-05-13
prj44 may I suggest you read this article ??

[http://linux.oneandoneis2.org/LNW.htm]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by oldsoundguy on 2010-05-14
> **kyphi said:**
> Now calm down folks.

Gspca? I assume that you mean the file from Michel Xhaard who has tested a great many webcams and has written drivers for them.

The file is called:  gspcav1-20071224.tar.gz

To open it, open a terminal and change directory to where you have downloaded the file (if the file has been downloaded to your Desktop, type cd Desktop) and then type:

                                   
tar xvf gspcav1-20071224.tar.gz

then press Enter.

You will find instructions in there on what to do next.

I have not checked if your webcam is supported by this driver - there are just too many webcams in this world.

I use a Logitech Quickcam Pro 9000, a fine webcam,  Plug it in and it works straightaway.  Recommended by Skype too,

Same make and model using 10.04 and no joy on Skype.  Camera works in Cheese (and love the ability to dial down the contrast and the resolution .. really speeds up the frame rate!) and the audio works when I test it in another program.

Just that in Skype neither the camera nor the audio will come on and no contact can be made to the audio test site.

Have un-installed and re-installed the beta to no avail.  It did work before I updated from 8.10.

---

### Post by kyphi on 2010-05-15
I am in the process of writing up a HowTo after getting Skype to play nice with a Logitech QC IM which used to work in Hardy but not in Lucid.
Help is on its way.

---

### Post by oldsoundguy on 2010-05-15
Not impatient at all and await the info.  I only use Skype to contact 4 relatives and to share personal files with a couple of friends.

But the idea is IF it is hooked up, it should work!! LOL  This is, as I have mentioned the only REAL issue in my total upgrade 
(did have a video problem but UPGRADING (not a new install) drags a lot of garbage along in xorg.config.. simply doing a sudo rm and re-booting solved ALL display problems.  Such a simple fix, but it took this forum to jog my slow brain.  I had multiple PAGES of xorg.conf.. all conflicting!!)

---

### Post by kyphi on 2010-05-16
It seems that there are a number of issues here so the following may help only some of you.

If your webcam works in Cheese then your webcam works.  It is just Skype where it fails.

There is no need to download gspca, it is already in the kernel as is the universal video device class UVC driver.  Next time that you are ready to buy a new webcam, buy a UVC compliant webcam.  In time all webcams will be UVC.

So here it is:

1.  Shut down Skype.
2.  Open a Terminal window and type:
```
gksudo nautilus
```
    followed by your password
3.  Click on "File System" in the left part of the screen and then go to /usr/local/bin in the right part of the screen.
4.  Click on "File" and select "Create Document".
5.  Give the new document the name "skype" and leave the document empty.
6.  Close the screen and return to the Terminal window and type:
```
sudo gedit /usr/local/bin/skype
```
that will take you to the new skype document.
7.  Copy and paste the following two lines into the document:
> #!bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
8.  Click on "Save" then close the document to return to the Terminal    window and type:
```
sudo chmod a+x /usr/local/bin/skype
```
    to make the file executable.
9.  Press Ctrl+d to close the Terminal.
10. Start Skype and select your webcam (in Skype) under Options, Video Settings.

Good Luck!

Acknowledgement: Eldragon's post of 30th October, 2008 on this Forum.  I only experimented and elaborated his work.

---

### Post by oldsoundguy on 2010-05-16
kyphi.. thanks for the effort .. but when I go to Skype .. no camera no sound still.

---

### Post by oldsoundguy on 2010-05-18
still working on this off an on to no avail.

---

### Post by oldsoundguy on 2010-05-21
3 days later .. this problem still exists.

---

### Post by dr_bovine on 2010-05-23
> **kyphi said:**
> It seems that there are a number of issues here so the following may help only some of you.

I was having the same problem and kyphi's method worked for me. Thanks!!

However, I should point out that there is a small (but crucial) typo in the shell script code in his post.  It should read:

```
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype 
``` 

Just missing a slash between the exclamation point and "bin". :)

---

### Post by oldsoundguy on 2010-05-24
fixed the typo .. still no joy!! LOL

---

### Post by rrc21 on 2010-05-25
> **kyphi said:**
> Now calm down folks.

Gspca? I assume that you mean the file from Michel Xhaard who has tested a great many webcams and has written drivers for them.

The file is called:  gspcav1-20071224.tar.gz

To open it, open a terminal and change directory to where you have downloaded the file (if the file has been downloaded to your Desktop, type cd Desktop) and then type:

tar xvf gspcav1-20071224.tar.gz

then press Enter.

You will find instructions in there on what to do next.

I have not checked if your webcam is supported by this driver - there are just too many webcams in this world.

I use a Logitech Quickcam Pro 9000, a fine webcam,  Plug it in and it works straightaway.  Recommended by Skype too,


Hi kyphi, Yes I've downloaded the file, and tried to follow the instructions in the readme, but it doesn't work unfortunately. I keep getting errors in the terminal.
Now I don't know if I am doing it wrong or what, which is why I started this thread.

My Intel webcam is stated to be supported by GSPCAV1 so I know that there is hope!
Still, neither Skype nor Cheese recognises it.

But I don't understand when you wrote that there is "no need to download gspca, as it's already in the kernel as is  the universal video device class UVC driver."
If that were the case, my webcam would work (?)

Would really appreciate some help with the correct commands to install gspcav1.

---

### Post by oldsoundguy on 2010-05-28
bump for two people.

---

### Post by labinnsw on 2010-05-30
> **oldsoundguy said:**
> fixed the typo .. still no joy!! LOL
Bump

---

### Post by labinnsw on 2010-06-05
[I finally found something that worked for me.]("http://ubuntuforums.org/showpost.php?p=9419207&postcount=50")

---

### Post by aitana.asdef on 2010-09-30
1. make skype-wrapper

#!/bin/sh

if [ ! -e ~/.Skype/shared.xml ]; then
  mkdir -p ~/.Skype
  cp /usr/share/skype/shared.xml ~/.Skype/shared.xml
fi

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so QT_PLUGIN_PATH=/usr/lib32/qt4/plugins /usr/bin/skype "$@"

2. copy it to /usr/bin/
3.start "Skype" typing skype-wrapper

---

### Post by ka11u_2305 on 2011-01-03
> **dr_bovine said:**
> I was having the same problem and kyphi's method worked for me. Thanks!!

However, I should point out that there is a small (but crucial) typo in the shell script code in his post.  It should read:

```
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype 
``` 

Just missing a slash between the exclamation point and "bin". :)
that was the mistake... thank you !!!

---

### Post by Chogsed10 on 2011-01-23
> **kyphi said:**
> Now calm down folks.

Gspca? I assume that you mean the file from Michel Xhaard who has tested a great many webcams and has written drivers for them.

The file is called:  gspcav1-20071224.tar.gz

To open it, open a terminal and change directory to where you have downloaded the file (if the file has been downloaded to your Desktop, type cd Desktop) and then type:

tar xvf gspcav1-20071224.tar.gz

then press Enter.

You will find instructions in there on what to do next.

I have not checked if your webcam is supported by this driver - there are just too many webcams in this world.

I use a Logitech Quickcam Pro 9000, a fine webcam,  Plug it in and it works straightaway.  Recommended by Skype too,


I have a logitech c500 webcam, and it works with skype and cheese, but i cant get it to work within firefox....any suggestions?

---

