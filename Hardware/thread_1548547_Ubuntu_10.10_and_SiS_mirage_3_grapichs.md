---
title: "Ubuntu 10.10 and SiS mirage 3 grapichs"
date: 2010-08-08
forum: Hardware
---

### Post by 19rocker85 on 2010-08-08
Hi everyone


I've just installed version alpha 3 of ubuntu 10.10.....

but the screen has a resolution 800x600.......any solution???

---

### Post by Shtrk on 2010-08-11
> **19rocker85 said:**
> Hi everyone


I've just installed version alpha 3 of ubuntu 10.10.....

but the screen has a resolution 800x600.......any solution???

Same problem here.... sis mirage 3+ m671
I noticed that in each next edition of ubuntu is more and more difficult to setup sis grapichs. 9.04 work best. Please make deb for 10.10. I try mandriva 2010 spring live CD - work out of the box. Can that be posible in ubuntu?

---

### Post by 19rocker85 on 2010-08-20
pleaseeeeeeeeeeeeeeeeeeeeeeeeeeee help meeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee

---

### Post by NHaGa on 2010-10-07
Any news on this??

---

### Post by NHaGa on 2010-10-07
I got this working thanks to a guy commenting this blog:

[http://diversosassuntosbrasil.blogspot.com/2010/09/driver-mandriva-2011-0-para-uso-em-sis.html](http://diversosassuntosbrasil.blogspot.com/2010/09/driver-mandriva-2011-0-para-uso-em-sis.html)

Just extract and copy the driver to /usr/lib/xorg/modules/drivers
Then use the Device setting from the attached xorg.conf

---

### Post by Dark_Stang on 2010-10-08
In the future, stay away from anything with SiS graphics. Just stick with nVidia, AMD/ATI, and Intel.

---

### Post by jglori on 2010-10-11
@NHaGa

Thanks for this info but, is there an English version of the blog? (sorry, I don't speak Portuguese) And also, I'm not that adept yet with Linux so, can you likewise give a more detailed, step-by-step procedure on how to install the sis driver? Oh, and by the way, does this driver have 3d acceleration support? Thanks!

@Dark_Stang

That would be the ideal. However, in my case, I don't have any choice. My laptop came with an Sis mirage video card. If it was a desktop PC, it would have been easy to replace the video card and I wouldn't have this problem.

---

### Post by NHaGa on 2010-10-11
Just move the contents of the file **sisimedia_drv.so.zip** to /usr/lib/xorg/modules/drivers

Then edit the the file /etc/X11/xorg.conf, go to the Section "Device" and change the Driver to "sisimedia"

Reboot and that should do it...

And this is just a 2d driver

---

### Post by stuarttanner on 2010-10-11
i am having the same problems with my v5535 i have done what has been said but it wont let me change file permissions for the drivers folder so i can tranfer file into folder.
i could do with a step by step guide for idiots lol.
anyone up to the challenge???


stu

---

### Post by zuraw on 2010-10-11
Just move the contents of the file sisimedia_drv.so.zip to /usr/lib/xorg/modules/drivers
  
no possible to do Permission denied  F..K! 800X600 resolution kill me ubuntu 10.10 how to make it in console? [email]zuraw73@gmail.com[/email] THX 
esprimo mobile V5535 f...ing sis

---

### Post by stuarttanner on 2010-10-11
i must admit sis media will drive you mad eventually some days i feel like ramming my v5535 straight up fujitsu's a***se lol

---

### Post by msmx5s on 2010-10-11
> **NHaGa said:**
> I got this working thanks to a guy commenting this blog:

[http://diversosassuntosbrasil.blogspot.com/2010/09/driver-mandriva-2011-0-para-uso-em-sis.html](http://diversosassuntosbrasil.blogspot.com/2010/09/driver-mandriva-2011-0-para-uso-em-sis.html)

Just extract and copy the driver to /usr/lib/xorg/modules/drivers
Then use the Device setting from the attached xorg.conf

ABSOLUTLEY F***ING SPECTACULAR!!!!!! 

I had previously altered the xorg.conf file to allow the 1280x800 resolution on my Fujitsu-Seimens V5515, but that had left the screen looking fuzzy. I nearly resigned myself to thinking that was the best I would get.

Works like a dream! I am no Linux/Ubuntu expert by any means, but this was easy enough! See the post on 1st page of this thread for the files.

Just a few more comments to make it easier... 

0. Backup your xorg.conf 

1. Open Nautilus in Root so you can paste in the directories required, by typing in "sudo nautilus" in the Terminal.

2. Copy the sismedia_drv.so file in first download, then paste into /usr/lib/xorg/modules/drivers

3. Copy the contents of the xorg.conf in the other download and open your xorg.conf in /etc/x11. Delete the old data, paste the new data you copied, then save and close. (Alternately, copy the xorg.conf file and paste in /etc/x11)

4. Restart computer.

Simples! :)

---

### Post by kurtzou on 2010-10-11
But I failed.
Do same things.
But after boot the whole screen is black...I can't login to system.
so I can only del     "driver "sisimedia" "
please help me...
Sorry for my poor English

My Computer is HP Compaq DX2130 MT

---

### Post by zuraw on 2010-10-12
msmx5s  thx work perfekt :guitar:

---

### Post by Peter09 on 2010-10-12
Deleted - wrong thread

---

### Post by stuarttanner on 2010-10-12
Can i just say a big thank you to all that have helped on this thread.. IT REALLY WORKS!!!!!!!
i have been trying to get the correct resolution on my v5535 for 2 years with lots and lots of fails but this was simples in the end.
I now have 1280 x 800 resolution and is pin sharp!

again a massive thank you

Stu   :)

---

### Post by metallus on 2010-10-12
> **zuraw said:**
> Just move the contents of the file sisimedia_drv.so.zip to /usr/lib/xorg/modules/drivers
  
no possible to do Permission denied  F..K! 800X600 resolution kill me ubuntu 10.10 how to make it in console? [EMAIL="zuraw73@gmail.com"]zuraw73@gmail.com[/EMAIL] THX 
esprimo mobile V5535 f...ing sis

zuraw please calm yourself.
you have do use sudo to move the files. first you have to unpack the zip archive containing the driver. then: sudo mv sisimedia_drv.so /usr/lib/xorg/modules/drivers .
Do the same with the xorg.conf: sudo mv xorg.conf /etc/X11/
Reboot and you're done.

Anyway, the driver works. I tested it. This is great :D
Good luck.

---

### Post by stuarttanner on 2010-10-12
> **msmx5s said:**
> ABSOLUTLEY F***ING SPECTACULAR!!!!!! 

I had previously altered the xorg.conf file to allow the 1280x800 resolution on my Fujitsu-Seimens V5515, but that had left the screen looking fuzzy. I nearly resigned myself to thinking that was the best I would get.

Works like a dream! I am no Linux/Ubuntu expert by any means, but this was easy enough! See the post on 1st page of this thread for the files.

Just a few more comments to make it easier... 

1. Open Nautilus in Root so you can paste in the directories required, by typing in "sudo nautilus" in the Terminal.

2. Copy the sismedia_drv.so file in first download, then paste into /usr/lib/xorg/modules/drivers


3. Copy the contents of the xorg.conf in the other download and open your xorg.conf in /etc/x11. Delete the old data, paste the new data you copied, then save and close. (Alternately, copy the xorg.conf file and paste in /etc/x11)

4. Restart computer.

Simples! :)

you need to follow this the cream is the "sudo nautilus" in your  terminal this will allow you to change files and add files i managed to  do it in the end. Also i found i had to just paste the xorg.conf file into my x11 file as there was no xorg.conf file there ????

stuart

---

### Post by msmx5s on 2010-10-12
> **stuarttanner said:**
> you need to follow this the cream is the "sudo nautilus" in your  terminal this will allow you to change files and add files i managed to  do it in the end. Also i found i had to just paste the xorg.conf file into my x11 file as there was no xorg.conf file there ????

stuart

I didn't have the xorg.conf file in there originally either! It was there in 10.4, but not on a fresh install of 10.10. I saved my old one using ubuntu one, but a direct copy into 10.10 made the screen look all fuzzy. 

This solution worked perfect for me and is still looking good! :-)

---

### Post by msmx5s on 2010-10-12
> **kurtzou said:**
> But I failed.
Do same things.
But after boot the whole screen is black...I can't login to system.
so I can only del     "driver "sisimedia" "
please help me...
Sorry for my poor English

My Computer is HP Compaq DX2130 MT

kurtzou, have you tried holding the left shift key down on startup, then booting in low graphics mode? Do that, and try again...

---

### Post by stuarttanner on 2010-10-12
> **msmx5s said:**
> I didn't have the xorg.conf file in there originally either! It was there in 10.4, but not on a fresh install of 10.10. I saved my old one using ubuntu one, but a direct copy into 10.10 made the screen look all fuzzy. 

This solution worked perfect for me and is still looking good! :-)

had me confused for a bit [msmx5s]("http://ubuntuforums.org/member.php?u=746811") but soon worked it out lol

---

### Post by m.hAMDy on 2010-10-12
thanks a lot NHaGa @ post 3. 
this worked perfect for me.i'll take the time adjust to the new screen resolution.:)

---

### Post by msmx5s on 2010-10-12
> **m.hAMDy said:**
> thanks a lot NHaGa @ post 3. 
this worked perfect for me.i'll take the time adjust to the new screen resolution.:)

Just to correct (as it confused me lol) It's post 5 :P

---

### Post by stuarttanner on 2010-10-13
i must admit the number 1 test of these drivers was what i call the over night test lol, if i installed drivers before even with dare i say it Mandriva they would work all the time i had the computer on and even if i turned off for about a hour.
but if left over night i would be welcomed by a black screen on boot the next morning making it impossible to rectifier the problem.
the only way out would be to do a reinstall :(
these drivers do work the next day so a very happy bunny:P

stu

---

### Post by ywgx on 2010-10-13
> **NHaGa said:**
> I got this working thanks to a guy commenting this blog:
 
[http://diversosassuntosbrasil.blogspot.com/2010/09/driver-mandriva-2011-0-para-uso-em-sis.html](http://diversosassuntosbrasil.blogspot.com/2010/09/driver-mandriva-2011-0-para-uso-em-sis.html)
 
Just extract and copy the driver to /usr/lib/xorg/modules/drivers
Then use the Device setting from the attached xorg.conf
  
 
 
 
help,help !I have not  permission to access this page . Do not download  2  sis  file.
 
please  gave me   [EMAIL="ywgxjxh@163.com"]ywgxjxh@163.com[/EMAIL]
 
thanks,thanks ,thanks,thanks!

---

### Post by msmx5s on 2010-10-13
> **ywgx said:**
> help,help !I have not  permission to access this page . Do not download  2  sis  file.
 
please  gave me   [EMAIL="ywgxjxh@163.com"]ywgxjxh@163.com[/EMAIL]
 
thanks,thanks ,thanks,thanks!

ywgx, you don't need access to the page (although I don't understand why you don't!), as the drivers and instructions are on this thread.

Why did you say don't download the file? It has worked for lots of people, including me :)

---

### Post by ywgx on 2010-10-13
> **19rocker85 said:**
> Hi everyone
 
 
I've just installed version alpha 3 of ubuntu 10.10.....
 
but the screen has a resolution 800x600.......any solution???
 Can you give me  that  2 sis  file  !  I can not download!
 
[EMAIL="ywgxjxh@163.com"]ywgxjxh@163.com[/EMAIL]
 
 
thanks ,thanks .thanks

---

### Post by msmx5s on 2010-10-13
> **ywgx said:**
> Can you give me  that  2 sis  file  !  I can not download!
 
[EMAIL="ywgxjxh@163.com"]ywgxjxh@163.com[/EMAIL]
 
 
thanks ,thanks .thanks

Can you not download the file from this thread in post #5, or from the link [http://diversosassuntosbrasil.blogsp...so-em-sis.html?](http://diversosassuntosbrasil.blogsp...so-em-sis.html?)

They are the same drivers.

---

### Post by msmx5s on 2010-10-13
[http://ubuntuforums.org/attachment.php?attachmentid=171588&d=1286496002]("http://ubuntuforums.org/attachment.php?attachmentid=171588&d=1286496002")

[http://ubuntuforums.org/attachment.php?attachmentid=171587&d=1286495857]("http://ubuntuforums.org/attachment.php?attachmentid=171587&d=1286495857")

You need the driver file, and the xorg.conf file. Then, follow my instructions on page 2 of this thread.

---

### Post by lisiren on 2010-10-14
Ty for drivers :popcorn:

---

### Post by ajoliveira on 2010-10-15
Hi. I have posted native 32 and 64 bit Maverick drivers [here]("http://ajoliveira.com/ajoliveira/uk/software/xorg.php").

There is a step-by-step guide at the end, which should help you to install other drivers as well, if you wish.

I will try to improve that with a script soon.

---

### Post by hellnest on 2010-10-15
Well do anyone here know that if M672 chipset can't be working if we use M671 Driver?

---

### Post by ajoliveira on 2010-10-15
-

---

### Post by ajoliveira on 2010-10-15
I just put an experimental install script on my [page]("http://ajoliveira.com/ajoliveira/uk/software/xorg.php"), hope it will help.

---

### Post by hellnest on 2010-10-15
> **ajoliveira said:**
> I just put an experimental install script on my [page]("http://ajoliveira.com/ajoliveira/uk/software/xorg.php"), hope it will help.

Hmm you told me to done it in su mode... what if i'm do it with sudo nautilus mode? because much more easy for me.

---

### Post by CesarDuarte on 2010-10-15
> **NHaGa said:**
> Just move the contents of the file **sisimedia_drv.so.zip** to /usr/lib/xorg/modules/drivers

Then edit the the file /etc/X11/xorg.conf, go to the Section "Device" and change the Driver to "sisimedia"

Reboot and that should do it...

And this is just a 2d driver

It tells me that i dont have permissions to do that move of the contents

---

### Post by hellnest on 2010-10-15
> **CesarDuarte said:**
> It tells me that i dont have permissions to do that move of the contents

For the easy way just type in your terminal
>sudo nautilus
(your_password)

and then leave the terminal open, in a second you will got a pop up of explorer and then you can get full access to do copy / paste / editing without do any command in terminal again.

But becarefull.. remember to always let the terminal windows open when using nautilus

after finish just return to terminal and then press "ctrl+c"

CMIIW:)

---

### Post by CesarDuarte on 2010-10-15
This isnt working for me :(

---

### Post by Deviling Master on 2010-10-15
Hi, i have an Asus X5DC Series (model should be K50C). I've installed Ubuntu 10.10 i386 version.

The problem: In monitor options i have only 800x600 resolution and i can't work like this....

I've tried lots of xorg.cong without success.....
At the reboot i get a very strange resolution/colors window and after few seconds start the text mode with command line.
To get back work again i have to delete xorg.conf with
```
sudo rm /etc/X11/xorg.conf
```After this delete if i reboot Ubuntu works again....

Under Windows 7 i have 1366x768 resolution, so if is possibile i wanto to set this one in Ubuntu too.

The VGA controller is:
```
VGA Compatibile Controller: Silicon Integrated Systems [SiS]  771/671 PCIE VGA Display Adapter (rev 10)
```Thanks for your help....  i really can't work with 800x600 resolution....

---

### Post by hellnest on 2010-10-15
> **Deviling Master said:**
> Hi, i have an Asus X5DC Series (model should be K50C). I've installed Ubuntu 10.10 i386 version.

The problem: In monitor options i have only 800x600 resolution and i can't work like this....

I've tried lots of xorg.cong without success.....
At the reboot i get a very strange resolution/colors window and after few seconds start the text mode with command line.
To get back work again i have to delete xorg.conf with
```
sudo rm /etc/X11/xorg.conf
```After this delete if i reboot Ubuntu works again....

Under Windows 7 i have 1366x768 resolution, so if is possibile i wanto to set this one in Ubuntu too.

The VGA controller is:
```
VGA Compatibile Controller: Silicon Integrated Systems [SiS]  771/671 PCIE VGA Display Adapter (rev 10)
```Thanks for your help....  i really can't work with 800x600 resolution....

Ok, i'm trying to help. Actually if you do a search before you posting is much better

Someone in this forum already finally get rid of that resolution problem with Asus and i think it's gonna be not too much different

[***Visit his blogsite for information and download link.***]("http://tpurch-blog.blogspot.com/2010/05/sis67x-driver-for-ubuntu-1004.html")

[COLOR="Red"]That one is run for 10.04 But give it a try[/COLOR]

---

### Post by Deviling Master on 2010-10-15
> **hellnest said:**
> Ok, i'm trying to help. Actually if you do a search before you posting is much better

Someone in this forum already finally get rid of that resolution problem with Asus and i think it's gonna be not too much different

[***Visit his blogsite for information and download link.***]("http://tpurch-blog.blogspot.com/2010/05/sis67x-driver-for-ubuntu-1004.html")

[COLOR=Red]That one is run for 10.04 But give it a try[/COLOR]
I've already follow this guide.... without success....

I've already read all this....

I've already read:
- [http://forum.ubuntu-it.org/index.php/topic,415013.0.html](http://forum.ubuntu-it.org/index.php/topic,415013.0.html)
- [http://forum.ubuntu-it.org/index.php?topic=349921.0](http://forum.ubuntu-it.org/index.php?topic=349921.0)
- [http://wiki.ubuntu-it.org/Hardware/Video/SisXgiVolari/Sis771-671?highlight=%28sis%29]("http://wiki.ubuntu-it.org/Hardware/Video/SisXgiVolari/Sis771-671?highlight=%28sis%29")
- [http://ubuntuforums.org/showthread.php?t=1548547](http://ubuntuforums.org/showthread.php?t=1548547)
- [http://diversosassuntosbrasil.blogspot.com/2010/10/sis-671-no-ubuntu-maverick-1010-32-bits.html](http://diversosassuntosbrasil.blogspot.com/2010/10/sis-671-no-ubuntu-maverick-1010-32-bits.html)
- [http://tpurch-blog.blogspot.com/2010/05/sis67x-driver-for-ubuntu-1004.html](http://tpurch-blog.blogspot.com/2010/05/sis67x-driver-for-ubuntu-1004.html)
- [http://ajoliveira.com/ajoliveira/uk/software/xorg.php](http://ajoliveira.com/ajoliveira/uk/software/xorg.php)
but i can't fix the problem

---

### Post by hellnest on 2010-10-15
> **Deviling Master said:**
> I've already follow this guide.... without success....

I've already read all this....

I've already read:
- [http://forum.ubuntu-it.org/index.php/topic,415013.0.html](http://forum.ubuntu-it.org/index.php/topic,415013.0.html)
- [http://forum.ubuntu-it.org/index.php?topic=349921.0](http://forum.ubuntu-it.org/index.php?topic=349921.0)
- [http://wiki.ubuntu-it.org/Hardware/Video/SisXgiVolari/Sis771-671?highlight=%28sis%29]("http://wiki.ubuntu-it.org/Hardware/Video/SisXgiVolari/Sis771-671?highlight=%28sis%29")
- [http://ubuntuforums.org/showthread.php?t=1548547](http://ubuntuforums.org/showthread.php?t=1548547)
- [http://diversosassuntosbrasil.blogspot.com/2010/10/sis-671-no-ubuntu-maverick-1010-32-bits.html](http://diversosassuntosbrasil.blogspot.com/2010/10/sis-671-no-ubuntu-maverick-1010-32-bits.html)
- [http://tpurch-blog.blogspot.com/2010/05/sis67x-driver-for-ubuntu-1004.html](http://tpurch-blog.blogspot.com/2010/05/sis67x-driver-for-ubuntu-1004.html)
- [http://ajoliveira.com/ajoliveira/uk/software/xorg.php](http://ajoliveira.com/ajoliveira/uk/software/xorg.php)
but i can't fix the problem

Try to post your Chipset specification and your xorg.log maybe someone here can help

---

### Post by Deviling Master on 2010-10-15
> **hellnest said:**
> Try to post your Chipset specification and your xorg.log maybe someone here can help

I've formatted all system with 10.04.1.

Now this guide works
[http://tpurch-blog.blogspot.com/2010/05/sis67x-driver-for-ubuntu-1004.html](http://tpurch-blog.blogspot.com/2010/05/sis67x-driver-for-ubuntu-1004.html)

Thanks for help

---

### Post by hellnest on 2010-10-16
> **Deviling Master said:**
> I've formatted all system with 10.04.1.

Now this guide works
[http://tpurch-blog.blogspot.com/2010/05/sis67x-driver-for-ubuntu-1004.html](http://tpurch-blog.blogspot.com/2010/05/sis67x-driver-for-ubuntu-1004.html)

Thanks for help

Well glad to hear that...

---

### Post by ajoliveira on 2010-10-17
Mmmm...It seems you people need a recompile of a patched driver just for a specific resolution that "my" driver does not support...I will try to come back with it very soon...no warranties...

---

### Post by hellnest on 2010-10-17
> **ajoliveira said:**
> Mmmm...It seems you people need a recompile of a patched driver just for a specific resolution that "my" driver does not support...I will try to come back with it very soon...no warranties...

Yup you right, muse use a different driver for each resolution. My monitor also still detected as unknown even it's running in native resolution. Btw, would be glad if you help to recompile for 10.10 (1336x768) i would very appreciate that :popcorn:

---

### Post by kurtzou on 2010-10-17
> **ajoliveira said:**
> Hi. I have posted native 32 and 64 bit Maverick drivers [here]("http://ajoliveira.com/ajoliveira/uk/software/xorg.php").

There is a step-by-step guide at the end, which should help you to install other drivers as well, if you wish.

I will try to improve that with a script soon.

Oh!It works!Thank you very much!

---

### Post by hellnest on 2010-10-18
I just wondering... if you do all the major upgrade in Sypnastic package manager will it automaticly upgrade my OS to Maverick? and also the X-server will be upgraded to 7.3 i guess.
I want to update my lucid but don't want to upgrade it to maverick coz still no solution for my resolution in Maverick :)

---

### Post by hBeeb on 2010-10-20
Thanks to NHaGa and everyone else who helped me with this problem. A satisfied user here.

Thanks again for the support!!

---

### Post by petaramesh on 2010-10-22
Hi,

Just for a big thanks, for info:

- A Fujitsu-Siemens Esprimo V5535 with standard clean install of Ubuntu 10.10 Maverick would just do 800x600 in X11 ;
- Using the "sisismedia" driver and xorg.conf from [files given in page 1 of this thread]("http://ubuntuforums.org/showthread.php?t=1548547&page=1#5"), machine automagically gives a perfect 1280x800 @75 Hz !

=> I just notice that during X startup, LCD screen gets "blurred" for a couple seconds like when overdriving an LCD screen (sync too fast etc.) but then the X screen comes up with perfect resolution.

=> lspci identifies the video device as:

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

---

### Post by stuarttanner on 2010-10-22
> **petaramesh said:**
> Hi,

Just for a big thanks, for info:

- A Fujitsu-Siemens Esprimo V5535 with standard clean install of Ubuntu 10.10 Maverick would just do 800x600 in X11 ;
- Using the "sisismedia" driver and xorg.conf from [files given in page 1 of this thread]("http://ubuntuforums.org/showthread.php?t=1548547&page=1#5"), machine automagically gives a perfect 1280x800 @75 Hz !

=> I just notice that during X startup, LCD screen gets "blurred" for a couple seconds like when overdriving an LCD screen (sync too fast etc.) but then the X screen comes up with perfect resolution.

=> lspci identifies the video device as:

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)


this is exactly the same on my v5535 but must admit its the best fix i have seen in 3 years.
2 weeks in now and still perfect!

stu

---

### Post by hellnest on 2010-10-22
Can't wait for 1366x768 Resolution.... :( can't use a driver and configuration from 1280x800 :(

---

### Post by G8HAV on 2010-10-22
> **NHaGa said:**
> Just move the contents of the file **sisimedia_drv.so.zip** to /usr/lib/xorg/modules/drivers

Then edit the the file /etc/X11/xorg.conf, go to the Section "Device" and change the Driver to "sisimedia"

Reboot and that should do it...

And this is just a 2d driver
  

Hi,
Extracted the contents of the zip file but I am not allowed to move it into the driver folder; only allowed to move to'Home' or 'Desktop' folder.

I am very new to ubuntu and I have tried other flavours of linux without much satisfaction but been slightly impressed with ubuntu as it got on with the job. However this screen resolution problem is painful; seems the hardware SIS video is a problem. May try another video card before consigning ubuntu to the bin along with the six previous attempts.

---

### Post by hellnest on 2010-10-23
> **G8HAV said:**
> Hi,
Extracted the contents of the zip file but I am not allowed to move it into the driver folder; only allowed to move to'Home' or 'Desktop' folder.

I am very new to ubuntu and I have tried other flavours of linux without much satisfaction but been slightly impressed with ubuntu as it got on with the job. However this screen resolution problem is painful; seems the hardware SIS video is a problem. May try another video card before consigning ubuntu to the bin along with the six previous attempts.

You must use Root Access to do that operation, here's the step

1. Open your terminal, type
```
sudo nautilus
```
2. Enter and then put your password, in a sec a file explorer will open and then you can easily move and copy the file anywhere you want.
*Don't close the terminal window when you do this progress, when you finished copy / move the file, just go back to terminal windows and press CTRL+C*

---

### Post by afeasfaerw23231233 on 2010-10-25
Thanks you guys for the instructions! But is there a 3D driver available for 32/64-bit?

I think we all hate SiS's products. If it was a Desktop I would certainly buy another graphic card / motherboard to replace this SiS 671/672(D/MX) chipsets/ Mirage3(+) IGP. However this is a laptop. Replacement is not possible. I am glad that SiS already quitted the chipsets manufacturing business!

---

### Post by DooM55 on 2010-10-25
tnx it's work and im very happe 
:P


but Desktop effect could not be enabled 

why??
:popcorn:

:KS

---

### Post by hellnest on 2010-10-26
> **DooM55 said:**
> tnx it's work and im very happe 
:P


but Desktop effect could not be enabled 

why??
:popcorn:

:KS
It's because compiz need to have 3D accleration enabled. And the driver only support 2D :) if you want to see a little effect like shade / transparacy / etc you can try to use KDE based instead  Gnome :)

---

### Post by Buckethead90 on 2010-10-27
Fantastic resolution fix. MANY THANKS to the genius who made this fix.

---

### Post by ax8l on 2010-10-28
So, is it possible to ever enable (some to write) a 3D enabled driver ? :D
Btw, first time when I installed this driver I used the ui to copy the driver. yeah big mistake. Use the command line dudes!

---

### Post by hellnest on 2010-10-28
> **ax8l said:**
> So, is it possible to ever enable (some to write) a 3D enabled driver ? :D
Btw, first time when I installed this driver I used the ui to copy the driver. yeah big mistake. Use the command line dudes!

Command line is fun :) but sometimes people can get typo so if you can't type really well it's better using **sudo nautilus** it's a GUI with a Root access... Of course to do that you must type that command in command line ^^

---

### Post by japetonida on 2010-10-29
Thank you so much! I downloaded these two files and it worked perfectly.

However, in my Ubuntu 10.10 (fresh install from latest version on an USB) folder etc/X11/ I could not found xorg.conf as previous people have noticed, so I had to read around to know what to do next. I came across this thread [http://ubuntuforums.org/showpost.php?p=9778241&postcount=546](http://ubuntuforums.org/showpost.php?p=9778241&postcount=546) where they mentioned a website of a portuguese guy that mentioned** that you dont need to have the xorg.conf file on your **etc/x11/ to make it work (for those who don't know!)

I just copy-pasted it and it worked perfectly!

---

### Post by CesarDuarte on 2010-10-29
> **japetonida said:**
> Thank you so much! I downloaded these two files and it worked perfectly.

However, in my Ubuntu 10.10 (fresh install from latest version on an USB) folder etc/X11/ I could not found xorg.conf as previous people have noticed, so I had to read around to know what to do next. I came across this thread [http://ubuntuforums.org/showpost.php?p=9778241&postcount=546](http://ubuntuforums.org/showpost.php?p=9778241&postcount=546) where they mentioned a website of a portuguese guy that mentioned** that you dont need to have the xorg.conf file on your **etc/x11/ to make it work (for those who don't know!)

I just copy-pasted it and it worked perfectly!

sorry but where is that etc folder?

---

### Post by CesarDuarte on 2010-10-29
God i feel like a noob! It worked so fine +.+ thanks for the help!

---

### Post by BenettFreeman on 2010-10-31
Well the suggestions posted on this thread didn't work for me at all, and I'm very disappointed - since I have the same laptop as others have (Fujitsu-Siemens V5535) and am running Ubuntu 10.10, which others are

Copied the drivers in, edited xorg.conf (which didn't exist before), restarted, and 

NO X SERVER

just command prompt to login

I'm getting to the point of despair, I really am. I love Linux, it works fine on my desktop, but the way Ubuntu deals with my (admittedly sh*t) graphics card just gets worse and worse.

9.04 works if I edit xorg.conf Monitor section
9.10 and 10.04 don't work at all - can't even see the install screen
10.10 installs fine but then no configuration appears possible

HELP HELP HELP

If anyone is willing to help me, I'd really appreciate it.

Thanks

---

### Post by haha100 on 2010-10-31
have you a simple solution for the  simens v5535
graphic  card sis
like a .deb paquage

---

### Post by haha100 on 2010-10-31
> **msmx5s said:**
> ABSOLUTLEY F***ING SPECTACULAR!!!!!! 

I had previously altered the xorg.conf file to allow the 1280x800 resolution on my Fujitsu-Seimens V5515, but that had left the screen looking fuzzy. I nearly resigned myself to thinking that was the best I would get.

Works like a dream! I am no Linux/Ubuntu expert by any means, but this was easy enough! See the post on 1st page of this thread for the files.

Just a few more comments to make it easier... 

0. Backup your xorg.conf 

1. Open Nautilus in Root so you can paste in the directories required, by typing in "sudo nautilus" in the Terminal.

2. Copy the sismedia_drv.so file in first download, then paste into /usr/lib/xorg/modules/drivers

3. Copy the contents of the xorg.conf in the other download and open your xorg.conf in /etc/x11. Delete the old data, paste the new data you copied, then save and close. (Alternately, copy the xorg.conf file and paste in /etc/x11)

4. Restart computer.

Simples! :)

THINKS THINKS THIKS 
:) :D) :P
IT is OK now

---

### Post by BenettFreeman on 2010-11-02
I managed to find a solution.

I followed THIS WALKTHROUGH

[http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html)

and the comment posted in response by Pablo Ignacio

and VOILA

The first working driver for my laptop in 2 years!

Hope this helps others

---

### Post by davagni on 2010-11-05
Ty! It's my third time i use Ubuntu and I'm really happy with it, When i first install it, I thought that i wont be able to configure the video (sis) but i follow the steps with the archives and it works! now i can have the screen on 1280x800 :)

Really thanks!

---

### Post by temporalshift on 2010-11-09
Thanks to all involved. I had backed away from 10.10 because of the graphics problem. Herein lies the strength of Ubuntu... its users.

---

### Post by coolbudy on 2010-11-17
> **NHaGa said:**
> I got this working thanks to a guy commenting this blog:

[http://diversosassuntosbrasil.blogspot.com/2010/09/driver-mandriva-2011-0-para-uso-em-sis.html](http://diversosassuntosbrasil.blogspot.com/2010/09/driver-mandriva-2011-0-para-uso-em-sis.html)

Just extract and copy the driver to /usr/lib/xorg/modules/drivers
Then use the Device setting from the attached xorg.conf

Thank you very much. It really helped me. I was really frustrated with how to fix the graphics(800x600). Installing this driver, just worked wonder.:)

---

### Post by Spam1k on 2010-11-19
Good day, somebody has successfully raised the driver on this card under ubuntu 10.10?
With just have not tried, without success.
And visited all  http: / / ubuntuforums.org / showthread.php? T = 1548547 here
and  here  [http://translate.googleusercontent.com/translate_c?hl=ru&ie=UTF-8&sl=en&tl=ru&u=http://ajoliveira.com/ajoliveira/uk/software/xorg.php&prev=_t&rurl=translate.google](http://translate.googleusercontent.com/translate_c?hl=ru&ie=UTF-8&sl=en&tl=ru&u=http://ajoliveira.com/ajoliveira/uk/software/xorg.php&prev=_t&rurl=translate.google).  com & usg = ALkJrhgV1TnkQMHRvbaryp_qYt87 - and here
and here [http://forum.ubuntu.ru/index.php?topic=97439.30](http://forum.ubuntu.ru/index.php?topic=97439.30)
and much more.
what will be a proposal? maybe something overlooked?
It makes sense to revert to previous versions of Ubuntu?
Please help, I'll be in much grateful for any delny new board.

---

### Post by hellnest on 2010-11-19
> **Spam1k said:**
> Good day, somebody has successfully raised the driver on this card under ubuntu 10.10?
With just have not tried, without success.
And visited all  http: / / ubuntuforums.org / showthread.php? T = 1548547 here
and  here  [http://translate.googleusercontent.com/translate_c?hl=ru&ie=UTF-8&sl=en&tl=ru&u=http://ajoliveira.com/ajoliveira/uk/software/xorg.php&prev=_t&rurl=translate.google](http://translate.googleusercontent.com/translate_c?hl=ru&ie=UTF-8&sl=en&tl=ru&u=http://ajoliveira.com/ajoliveira/uk/software/xorg.php&prev=_t&rurl=translate.google).  com & usg = ALkJrhgV1TnkQMHRvbaryp_qYt87 - and here
and here [http://forum.ubuntu.ru/index.php?topic=97439.30](http://forum.ubuntu.ru/index.php?topic=97439.30)
and much more.
what will be a proposal? maybe something overlooked?
It makes sense to revert to previous versions of Ubuntu?
Please help, I'll be in much grateful for any delny new board.

I don't understand what you mean >.<" what help do you want? What version of ubuntu that run inside ur machine right now?:D

---

### Post by Sjooop on 2010-11-20
Thanks, this worked for me I have a resolution now from 1440x900 (16:10) great!!!

---

### Post by Spam1k on 2010-11-20
I have a notebook asus k50c
video card sis 671
os ubuntu 10,10
I can not put a driver
tried different. :o


I beg pardon for my English, I use a dictionary.

---

### Post by balram38 on 2010-11-21
i want to express hearty thanks to u.

---

### Post by larryni on 2010-11-26
> **NHaGa said:**
> I got this working thanks to a guy commenting this blog:

[http://diversosassuntosbrasil.blogspot.com/2010/09/driver-mandriva-2011-0-para-uso-em-sis.html](http://diversosassuntosbrasil.blogspot.com/2010/09/driver-mandriva-2011-0-para-uso-em-sis.html)

Just extract and copy the driver to /usr/lib/xorg/modules/drivers
Then use the Device setting from the attached xorg.conf

Finally a solution that worked. This started driving me nuts!

Thanks very much :)

---

### Post by Shtrk on 2010-11-28
Tipe sudo nautilus and then enter password. Now copy the driver. Good luck!

---

### Post by alexdavisbooth on 2010-11-28
Thank you [msmx5s]("http://ubuntuforums.org/member.php?u=746811")!! That worked perfectly. I have been trying to get this figured out for days now. Worked like a dream, thank you for the relatively simple language.
I am new to Ubuntu and want to make this work for me.

---

### Post by Takki2010 on 2010-12-01
Hi all, 

I have a nettop PC with a sis mirage on board graphic and try to use linux mint 10 (Julia) instead of win7. At the begining I had only 800*600 resolution but after studying this thread and using the mentioned sis drivers and xorg.info I was able to change resolution to 1400*1050. This is better than before but still not perfect because I use a 22inch with native 1680*1050 resolution.
So I tried to enter this resolution in the xorg.info but it didn't help at all. 

Right now I do not have any idea what else to do, any ideas from your side?

thanks and best regards from germany

Takki2010

---

### Post by hellnest on 2010-12-03
> **Takki2010 said:**
> Hi all, 

I have a nettop PC with a sis mirage on board graphic and try to use linux mint 10 (Julia) instead of win7. At the begining I had only 800*600 resolution but after studying this thread and using the mentioned sis drivers and xorg.info I was able to change resolution to 1400*1050. This is better than before but still not perfect because I use a 22inch with native 1680*1050 resolution.
So I tried to enter this resolution in the xorg.info but it didn't help at all. 

Right now I do not have any idea what else to do, any ideas from your side?

thanks and best regards from germany

Takki2010

copy ur xorg.conf here maybe i can help

---

### Post by Takki2010 on 2010-12-04
Dear hellnest, 

here is my xorg.info:

# (xorg.conf para Ubuntu 10.10) 
#
# SÃ³ altere as configuraÃ§Ãµes abaixo se apenas souber o que estÃ¡ fazendo 

Section "Device"
        Identifier "device1"
        Driver "sisimedia"
        Option "DPMS"
        Option "EnableSiSCtrl" "yes"
        Option "useROMData " "False"
	Option "ForceCRT1Type" "NONE"
	Option "ForceCRT2Type" "LCD"
	Option "CRT1Gamma" "on"
        Option "CRT2Gamma" "on"
	Option "Brightness" "0.000 0.000 0.000"
	Option "Contrast" "0.000 0.000 0.000"
	Option "CRT1Saturation" "1"
	Option "XvOnCRT2" "yes"
	Option "XvDefaultContrast" "64"
	Option "XvDefaultBrightness" "10"
	Option "XvDefaultHue" "1"
	Option "XvDefaultSaturation" "1"
	Option "XvDefaultDisableGfxLR" "no"
	Option "XvGamma" "on"
        VideoRam 262016
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
        Option "DPMS"
        HorizSync 30 - 63
        VertRefresh 50 - 75
	Gamma 1.000 1.000 1.000
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
        DefaultDepth	24
SubSection "Display"
        Depth   24
                Modes           "1280x800@75"   "1280x800@60"   "1280x720@60"   "1280x768@60"   "800x600@60"    "1680x1050@60"
        EndSubSection
	Device		"Configured Video Device"
EndSection

Section "Module"
    Disable "dri"
    Load "dbe" 
    Load "v4l" 
    Load "extmod"
    Load "type1"
    Load "freetype"
    Load "glx" 
    Load "GLcore"
EndSection

Section "DRI"
        Mode 0666
EndSection

br

Takki2010

---

### Post by Shazza6969 on 2010-12-05
> **petaramesh said:**
> Hi,

Just for a big thanks, for info:

- A Fujitsu-Siemens Esprimo V5535 with standard clean install of Ubuntu 10.10 Maverick would just do 800x600 in X11 ;
- Using the "sisismedia" driver and xorg.conf from [files given in page 1 of this thread]("http://ubuntuforums.org/showthread.php?t=1548547&page=1#5"), machine automagically gives a perfect 1280x800 @75 Hz !

=> I just notice that during X startup, LCD screen gets "blurred" for a couple seconds like when overdriving an LCD screen (sync too fast etc.) but then the X screen comes up with perfect resolution.

=> lspci identifies the video device as:

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

I had exactly the same issue with my V5535 and was losing the will to live - thanks to all for the help - it works!!!!!!!!!

---

### Post by hellnest on 2010-12-08
> **Takki2010 said:**
> Dear hellnest, 

here is my xorg.info:

# (xorg.conf para Ubuntu 10.10) 
#
# SÃ³ altere as configuraÃ§Ãµes abaixo se apenas souber o que estÃ¡ fazendo 

Section "Device"
        Identifier "device1"
        Driver "sisimedia"
        Option "DPMS"
        Option "EnableSiSCtrl" "yes"
        Option "useROMData " "False"
	Option "ForceCRT1Type" "NONE"
	Option "ForceCRT2Type" "LCD"
	Option "CRT1Gamma" "on"
        Option "CRT2Gamma" "on"
	Option "Brightness" "0.000 0.000 0.000"
	Option "Contrast" "0.000 0.000 0.000"
	Option "CRT1Saturation" "1"
	Option "XvOnCRT2" "yes"
	Option "XvDefaultContrast" "64"
	Option "XvDefaultBrightness" "10"
	Option "XvDefaultHue" "1"
	Option "XvDefaultSaturation" "1"
	Option "XvDefaultDisableGfxLR" "no"
	Option "XvGamma" "on"
        VideoRam 262016
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
        Option "DPMS"
        HorizSync 30 - 63
        VertRefresh 50 - 75
	Gamma 1.000 1.000 1.000
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
        DefaultDepth	24
SubSection "Display"
        Depth   24
                Modes           "1280x800@75"   "1280x800@60"   "1280x720@60"   "1280x768@60"   "800x600@60"    "1680x1050@60"
        EndSubSection
	Device		"Configured Video Device"
EndSection

Section "Module"
    Disable "dri"
    Load "dbe" 
    Load "v4l" 
    Load "extmod"
    Load "type1"
    Load "freetype"
    Load "glx" 
    Load "GLcore"
EndSection

Section "DRI"
        Mode 0666
EndSection

br

Takki2010

Hi Takki,

sorry for the late response. Are you trying to configure for 2 Monitor or single one? I guees you put too many option inside your xorg.conf files. Sisimedia will automaticly detect which Modules is supported by the card and will enabled it by default. For example like "AIGLX", even it will be fail and go back to software rendering..

I will point you to my blog which is have a guide to configure the xorg.conf also include the files. My internet connection now is a crap >.<" very slow.

[http://hellbunker.blogspot.com/2010/11/sis-m671-on-linux.html](http://hellbunker.blogspot.com/2010/11/sis-m671-on-linux.html)

---

### Post by philcarao88 on 2010-12-27
> **NHaGa said:**
> I got this working thanks to a guy commenting this blog:

[http://diversosassuntosbrasil.blogspot.com/2010/09/driver-mandriva-2011-0-para-uso-em-sis.html](http://diversosassuntosbrasil.blogspot.com/2010/09/driver-mandriva-2011-0-para-uso-em-sis.html)

Just extract and copy the driver to /usr/lib/xorg/modules/drivers
Then use the Device setting from the attached xorg.conf





yeah, it worked.. i had tried also instead of using sisimedia driver, i used vesa. i just used the xorg.conf then replaced "sisimedia" w/ "vesa"

---

### Post by pennypecker on 2011-01-08
> **NHaGa said:**
> I got this working thanks to a guy commenting this blog:

[http://diversosassuntosbrasil.blogspot.com/2010/09/driver-mandriva-2011-0-para-uso-em-sis.html](http://diversosassuntosbrasil.blogspot.com/2010/09/driver-mandriva-2011-0-para-uso-em-sis.html)

Just extract and copy the driver to /usr/lib/xorg/modules/drivers
Then use the Device setting from the attached xorg.conf

I got working my SiS 771 graphic card on a Fujitsu Siemens Esprimo Mobile V5335. Thanks a lot. A future warning:
After using the same refresh rate as in the xorg.conf file in the archive, after 30 minutes of running the screen started to flicker. Even after changing to a lower refresh rate I still had that flicker. I verified the specifications for the monitor and I think the refresh rate was too high, and I modified like below in the "Monitor" section of xorg.conf: 
#        HorizSync 30-63
#        VertRefresh 50-75
        HorizSync 28-72
        VertRefresh 43-60

In the manual it says that it's possible to damage your monitor if you use incorrect values. Now I use 60 Hz.
I got a little scared, but fortunately after I turned off the laptop for 15 minutes now it's OK, no more flickering.

---

### Post by pennypecker on 2011-01-08
> **Shazza6969 said:**
> I had exactly the same issue with my V5535 and was losing the will to live - thanks to all for the help - it works!!!!!!!!!

I also had this issue with my V5535 but I had to correct the refresh rate, because after 30 minutes of running at 75Hz the screen started to flicker. I supposed the value was too high.

Later edit: I get this flicker every time I resume from screen saver or from monitor sleep. Discussed in [this]("http://ubuntuforums.org/showthread.php?p=10334601") thread.

---

### Post by NicoleSigaud on 2011-01-14
> **stuarttanner said:**
> i am having the same problems with my v5535 i have done what has been said but it wont let me change file permissions for the drivers folder so i can tranfer file into folder.
i could do with a step by step guide for idiots lol.
anyone up to the challenge???


stu

Well, I assume you tried to put your username as Administrator. In case you did not, try this first.

- After having the status of Administrator (for ROOT), _copy_ the file **sisimedia_drv.so** to Home Folder.

- Open TERMINAL and paste this line (using the right mouse button):
[COLOR=SeaGreen]**sudo mv sisimedia_drv.so /usr/lib/xorg/modules/drivers**[/COLOR]

- Now your file in in the right folder.Next step: edit your **xorg.conf** file with this line in TERMINAL:
**[COLOR=SeaGreen]sudo gedit /etc/X11/xorg.conf[/COLOR]**

- Copy all the contents of the xorg.conf file included into the downloadable file I enclosed here.

- Reboot system

- Open menu SYSTEM > PREFERENCES > MONITORS and choose the right resolution for you.

- Yes, keep those two files safe in case you need to reinstall UBUNTU 10.10

---

### Post by djkrisx on 2011-01-21
mate it works you just need to use sudo command when you edit the file

---

### Post by midhuno on 2011-01-29
I did all described in this form........now i get 1280x800 screen resolution.....thanks 2 all....but now i have a problem......when i open any video file in default movie player it is blurred and shows only some oscillating colours..........i then downloaded the vlc player it shows the following error message
"  p, li { white-space: pre-wrap; } Your video output acceleration driver does not support the required resolution: 672x288 pixels. The maximum supported resolution is 704x288.
 Video output acceleration will be disabled. However, rendering videos with overly large resolution may cause severe performance degration."


and the video is stretched and unclear....please help me...........


i am using Wipro notebook 7B1611 with sis mirage m672
:(

---

### Post by NicoleSigaud on 2011-01-29
Midhuno, I am using VLC 1.1.4, which is behaving marvelously so far. Maybe it's the case to upgrade yours via Synaptic? I am sorry if it doesn't work for you; my humble knowledge stucks here... hope someone more seasoned can help you out.

---

### Post by midhuno on 2011-01-29
> **NicoleSigaud said:**
> Midhuno, I am using VLC 1.1.4, which is behaving marvelously so far. Maybe it's the case to upgrade yours via Synaptic? I am sorry if it doesn't work for you; my humble knowledge stucks here... hope someone more seasoned can help you out.


I am using the VLC 1.1.4 friend...........but no use

---

### Post by octatone on 2011-02-02
Hello,

I've tried all the different instructions and download and in 32bit 10.10 it always goes to a black screen.

I guess I'm stuck with vesa.

---

### Post by hellnest on 2011-02-04
Ok let's take it straight for this issue regarding SIS / VESA.

_1280x800 VS 1366x768_
There are 2 Different xorg.configuration. If you have A display with 1280x800 Resolution so it's don't need to "tweak" xorg.conf. Just replace vesa with sisimedia and eveything will go well. In other hand, if you have 1366x768 Resolution you need to add an extra option you can take a look inside this file which is have a config for 1366x768 resolution 
[http://db.tt/vH7GMYP](http://db.tt/vH7GMYP)

*VIDEO PLAYBACK ISSUE*
First there's nothing wrong with your VLC or Mplayer or other video player you use. First you must change the video output in VLC prefences to "XV" and everything will go fine. For global you you can use this step,
a. open your terminal
```

$ gstreamer-properties

```
b. Go to video properties and change the output to "XV"
So you will enjoy your video with full screen without any gaps or flickering.

_TERMINAL??_
Ubuntu is make or created for user to be eaasy to use and easy to manage. But don't forget the important things that you can't leave "terminal" behind. Many stuff will easy to be done from terminal. Ok, here's the point.
If you lazy to use "cp" or "mv" command to copy the driver, just open terminal and use this
```

$ gksu nautilus

```
it will open terminal with root previlege and give all access. So you can use GUI to copy paste the file into the right direction. '


Note : 
Follow the step one by one and take a look closely in all guide. You can refer to my blog. I already explained this, I'm not using ubuntu anymore but i can't leave this community because this is where i start using linux :)

Regards,

You can contact me throught email if you facing any problem. I just don't want anyone have a difficult experience installing this driver

---

### Post by midhuno on 2011-02-07
@hellnest
i changed the video output into x windows system(x11/xshm,xv) but the problem when playing videos in Mplayer still remains...video appear as a group of horizontal coloured bands..audio is clear....pls help me...i dont find a video output option in vlc...i am a beginner in linux so help me

thanks in advance

---

### Post by hellnest on 2011-02-07
> **midhuno said:**
> @hellnest
i changed the video output into x windows system(x11/xshm,xv) but the problem when playing videos in Mplayer still remains...video appear as a group of horizontal coloured bands..audio is clear....pls help me...i dont find a video output option in vlc...i am a beginner in linux so help me

thanks in advance

Ok i don't get it know. First in your PM, you told me that you were try to play it on VLC. When you change the output on gstreamer-properties, there are "test" button. Do you already test it when you change the output?

---

### Post by rizwanmumtaz on 2011-02-08
hats off to you guys. I was trying to solve this stupid graphics problem for the last whole week. But only this one solved the trouble. Bundle of thanks :)

Not to forget mentioning that SIS stuff really sucks!

Cheers!
Rizwan

---

### Post by hellnest on 2011-02-09
> **rizwanmumtaz said:**
> hats off to you guys. I was trying to solve this stupid graphics problem for the last whole week. But only this one solved the trouble. Bundle of thanks :)

Not to forget mentioning that SIS stuff really sucks!

Cheers!
Rizwan

Glad you solve it dude... Where you come from? Indonesia? Well actually we still must face the reality that current driver will not compatible on Natty.. :)

---

### Post by sephiroth_slash on 2011-03-02
Hi guys

I installed Ubuntu 10.10 amd64 ( 64 bit ) for a friend who had Fujitsu Siemens Esprimo v5535, I had a problem with the resolution ( 800x600 ) , I downloaded the sis driver ( attachment )

and did the following commands : 

- Extract the content of the archive to home directory
- $ sudo cp 64-bit/xorg.conf /etc/X11
- $ sudo cp 64bit/sis671_drv.so /usr/lib/xorg/modules/drivers
- reboot

then it worked !! the resolution now is : 1280x800 !! thank you very much ajoliveira !

Guys who have Ubuntu 10.10 amd64 ( 64 bits ) , you have to follow these instructions, the previous posts are about Ubuntu 10.10 i386, and the driver is sensitive to the CPU architecture .

Hope it helps someone !!

---

### Post by hellnest on 2011-03-05
Go to my blog, i already put an update from Paulo Zaunoni for this driver so it can use in Natty

---

### Post by Alexvc2400 on 2011-03-08
THanks for the advice in this thread.

Copied the driver, copied the xorg.congn restarted.
And was happy to see my fujitsu 5535 boot into 1280 x 800.

Goodbye 800 x 600 :)

---

### Post by vikziee on 2011-04-01
i need your help guys :'(
today is my first day to linux ubuntu and i have been scratching my head and visiting website for my graphics solution for sis mirage 3.
The problem is i get a Command line interface after i restart my computer.
I do all the things according to instructions but still a Command Line Interface after the computer is restarted.
i tried 5 -6 times but no results.

help me please what should i do ??

---

### Post by DrSeemann on 2011-04-05
> **vikziee said:**
> i need your help guys :'(
today is my first day to linux ubuntu and i have been scratching my head and visiting website for my graphics solution for sis mirage 3.
The problem is i get a Command line interface after i restart my computer.
I do all the things according to instructions but still a Command Line Interface after the computer is restarted.
i tried 5 -6 times but no results.

help me please what should i do ??

Hi vik, im new at ubuntu too. This is my first post and what a better way for starting than helping some guy :P .
I had exactly the same problem, this is the way i solved it::

I did read [this entire post. ]("http://ubuntuforums.org/showthread.php?t=958967&page=71&highlight=sis+mirage")
I hope you read it too. I even had same problem, following a guide (blindly) i got to a part where i needed to (i really dunno exactly) close the OS GUI and continue by console commands. Well i didn't understood at that moment, and found my self reinstalling OS.
I really don't have time to "write" a guide for you. Just some council, based on my experience.
Get sisimedia driver, wich is linked on the post i linked you to.
Copy it to the indicated folder (there are a lot of guides), u'll have to use terminal with sudo prefix.
Then edit the xorg.conf file (you can do it, without closing OS GUI) as indicated on the guides. Reboot and you will have it all done.

PS: There's no 3d driver for sis mirage 3. If you still can't solve it, PM me and i'll gather you all information i used. And some advice, try to understand the guides you are following.

I hope it works for you, as it worked 100% fine for me.

---

### Post by Giaco_Luigi on 2011-05-22
I have the same problem but with Ubuntu 11.04, I'm new in this S.O., I try with the solutions proposed for previous versions but didn't work. There is any solution for it?

---

### Post by Zli Zeka on 2011-07-02
How to set up a dual display and extended desktop?

esprimo mobile v5535, sis mirage 3, 10.10

---

### Post by d.vanheeckeren on 2011-07-03
hmm, evidently I can't delete my own posts, so this [EDIT] is the result of my deletion attempt.

---

### Post by Zli Zeka on 2011-07-19
> **sephiroth_slash said:**
> hi guys

i installed ubuntu 10.10 amd64 ( 64 bit ) for a friend who had fujitsu siemens esprimo v5535, i had a problem with the resolution ( 800x600 ) , i downloaded the sis driver ( attachment )

and did the following commands : 

- extract the content of the archive to home directory
- $ sudo cp 64-bit/xorg.conf /etc/x11
- $ sudo cp 64bit/sis671_drv.so /usr/lib/xorg/modules/drivers
- reboot

then it worked !! The resolution now is : 1280x800 !! Thank you very much ajoliveira !

Guys who have ubuntu 10.10 amd64 ( 64 bits ) , you have to follow these instructions, the previous posts are about ubuntu 10.10 i386, and the driver is sensitive to the cpu architecture .

Hope it helps someone !!

tnx !

---

### Post by lin9 on 2012-11-06
uhhm guys,

I did everything as written here - but I just can choose 1280 x 768 resolution ???

- in the xorg.conf the 1280x800 mode is listed...I didn't change anything....

what happened? why I can't choose 1280 x 800 ??

please help..also sufferd since serveral years on that dumb 1024 resolution..now so close to a real solution....just 32 tiny pixels away from it ....are missing :(

please help!

edit: my xrandr -q gives:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 768, maximum 1280 x 768
default connected 1280x768+0+0 0mm x 0mm
   1280x768        0.0* 
   1024x768       76.0  
   800x600        73.0  
   640x480        73.0 

thanks,

...just another desperate fujitsu V5535 user

---

