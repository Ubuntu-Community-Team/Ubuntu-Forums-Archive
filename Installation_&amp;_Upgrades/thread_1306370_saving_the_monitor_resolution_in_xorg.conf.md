---
title: "saving the monitor resolution in xorg.conf"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by JKH Designs on 2009-10-30
Hello,

I've been having a little trouble with my 8.04 LTS server/Kubuntu 3.5.10 installation.  I had this posted on the Kubuntu forurms and got the following results but is still unsolved thought I would see if anyone on here has had a similar.

Hope this is OK to do, please start at bottom and read to the top.

Thanks in advance,

James



Posted by: lmilano  Posted on: October 28, 2009, 07:18:43 am  
Insert Quote  
Mmm, it is there in Jaunty. Is anyone else running 8.04 and able to help with this? Thanks! 

Posted by: JKH Designs  Posted on: October 28, 2009, 07:01:41 am  
Insert Quote  
Imilano,

This fix DPI in system settings display sounds like it might do the trick if I could just find it now, sorry about being a little slow you know.  Under System settings I found the Monitor & Display thats where I've been adjusting the resolution when it will let me that is.  I've gone in to admin and logged in then monitor size,orientation & positioning tab, color & gamma tab, the hardware tab has 2 configure buttons but no fix DPI.  Am I in the right ballpark or are you talking about another spot that I haven't found yet?  I am running Ubuntu 8.04 LTS server with KDE release 3.5.10 

Thank yall for being patient,


James 

Posted by: lmilano  Posted on: October 27, 2009, 08:30:30 pm  
Insert Quote  
Another thing that might help in your cse is to try to choose a fix DPI in System Settings -> Display 

Posted by: GreyGeek  Posted on: October 27, 2009, 08:19:28 pm  
Insert Quote  
Quote from: JKH Designs on October 27, 2009, 09:24:54 am
......

I found this command in the xorg.conf file but have not tried it, kinda gunshy after messing around with it yesterday.

sudo dpkg-reconfigure - phigh xserver-xorg

.....



James, that command is why I asked my question above.  The "-phigh" parameter USED to create an xorg.conf file, but it is no longer functional.  Only the "-plow" parameter for configuring the keyboard, etc, works.   

So, I was wondering how those folks who created their xorg.conf file, since HAL no longer creates it, did that.    It looks like 
Xorg -configure
is it.  That's nice to know.  (Odd that that command starts with a capital X). 

Posted by: JKH Designs  Posted on: October 27, 2009, 09:24:54 am  
Insert Quote  
Snowdog,Imilano and all,

I thought we had this problem solved.  I rebooted my system this morning and it came back up to the oversized resolution.  I went through the steps ya'll recommended yesterday and I'm back to an adjustable resolution again.

My question is what do I need to do to save these settings permanently?

I found this command in the xorg.conf file but have not tried it, kinda gunshy after messing around with it yesterday.

sudo dpkg-reconfigure - phigh xserver-xorg

Any suggestions?


Thanks again in advance

James


 
Posted by: JKH Designs  Posted on: October 27, 2009, 06:54:42 am  
Insert Quote  
Hey Snowhog,

Yes I have a grub menu that comes up very briefly.  I only have the one os on this system so it does not stay on but a second or 2.  I have several other systems that give you a choice at start of which os you need to boot into.

Thnaks again for ya'lls help. ;  

Posted by: lmilano  Posted on: October 26, 2009, 06:20:57 pm  
Insert Quote  
Quote from: GreyGeek on October 26, 2009, 04:16:04 pm
Hey, guys, the visual impaired GreyGeek has a question:

I thought that HAL no longer uses xorg.conf and identifies and configures the video device each time it boots?  Yes?  No?


Hi GreyGeek,

Yes and no. It is not needed by default in Karmic. If it's not present, it's not used, and everything works automagically. If it is present, it is used. 

[http://ubuntuforums.org/showthread.php?p=8051823](http://ubuntuforums.org/showthread.php?p=8051823)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1221226](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1221226)

Apparently, "sudo Xorg -configure" regenerates one. 

Posted by: Snowhog  Posted on: October 26, 2009, 04:19:29 pm  
Insert Quote  
Not in Hardy IIUC. 


Posted by: GreyGeek  Posted on: October 26, 2009, 04:16:04 pm  
Insert Quote  
Hey, guys, the visual impaired GreyGeek has a question:

I thought that HAL no longer uses xorg.conf and identifies and configures the video device each time it boots?  Yes?  No? 
Posted by: Snowhog  Posted on: October 26, 2009, 02:54:41 pm  
Insert Quote  
Glad we could help. 

Do you even see your Grub menu? If 'no,' then it's hidden, and if you don't want that, it can be 'unhidden' so you can see all the kernel boot options available to you. 


Posted by: JKH Designs  Posted on: October 26, 2009, 02:47:40 pm  
Insert Quote  
Thank you both Imilano & Snowhog very much for the input.

I did not have a recovery mode already in the Grub.

Pressed esc. key at boot up and went to the newest kernal Recovery mode.
first loaded any new dpkg,  rebooted and then went in to x file server recover and rebooted into a kubuntu o.s.  

Couldn't have done it without your input, thanks so much thought I had lost everything.


James 


Posted by: lmilano  Posted on: October 26, 2009, 12:38:31 pm  
Insert Quote  
Right. There is also an option to "repair graphics" usually in the Rescue Mode. That might work. 
Posted by: Snowhog  Posted on: October 26, 2009, 12:34:25 pm  
Insert Quote  
Do you have a (recovery mode) boot entry in your Grub menu when you boot? If you do, select it. That gets you to a command line 'as root.' If you don't, then when you see the Grub menu, press 'e' to edit. Select the kernel line and arrow to the end and then backspace to erase the items after ro and then type single so that the end of the kernel line you have so single

Tthis is what mine looks like:

Quote
kernel          /boot/vmlinuz-2.6.28-16-generic root=UUID=8c01fe0c-a60f-4921-94d6-cabbfff0a699 ro single


Then press 'b' to boot. You will end up at the command line 'as root.' 


Posted by: JKH Designs  Posted on: October 26, 2009, 11:41:38 am  
Insert Quote  
I am new to 8.04 Hardy and Kubuntu been using it about a year. I really like it and have a lot of software loaded.  I came in this morning and at startup my monitor resolution was very large. I could not increase the resolution through the settings monitor desktop menu.   I found a message about editing the xorg.conf file which I tried, rebooted and now I have a black screen.  How do I boot into a console or bare bones os to try to restore the original xorg.conf file?

Thanks in advance

James

---

### Post by phillw on 2009-10-30
> **JKH Designs said:**
> Hello,

I've been having a little trouble with my 8.04 LTS server/Kubuntu 3.5.10 installation.  I had this posted on the Kubuntu forurms and got the following results but is still unsolved thought I would see if anyone on here has had a similar.

Hope this is OK to do, please start at bottom and read to the top.

Thanks in advance,

James



Posted by: lmilano  Posted on: October 28, 2009, 07:18:43 am  
Insert Quote  
Mmm, it is there in Jaunty. Is anyone else running 8.04 and able to help with this? Thanks! 

Posted by: JKH Designs  Posted on: October 28, 2009, 07:01:41 am  
Insert Quote  
Imilano,

This fix DPI in system settings display sounds like it might do the trick if I could just find it now, sorry about being a little slow you know.  Under System settings I found the Monitor & Display thats where I've been adjusting the resolution when it will let me that is.  I've gone in to admin and logged in then monitor size,orientation & positioning tab, color & gamma tab, the hardware tab has 2 configure buttons but no fix DPI.  Am I in the right ballpark or are you talking about another spot that I haven't found yet?  I am running Ubuntu 8.04 LTS server with KDE release 3.5.10 

Thank yall for being patient,


James 

Posted by: lmilano  Posted on: October 27, 2009, 08:30:30 pm  
Insert Quote  
Another thing that might help in your cse is to try to choose a fix DPI in System Settings -> Display 

Posted by: GreyGeek  Posted on: October 27, 2009, 08:19:28 pm  
Insert Quote  
Quote from: JKH Designs on October 27, 2009, 09:24:54 am
......

I found this command in the xorg.conf file but have not tried it, kinda gunshy after messing around with it yesterday.

sudo dpkg-reconfigure - phigh xserver-xorg

.....



James, that command is why I asked my question above.  The "-phigh" parameter USED to create an xorg.conf file, but it is no longer functional.  Only the "-plow" parameter for configuring the keyboard, etc, works.   

So, I was wondering how those folks who created their xorg.conf file, since HAL no longer creates it, did that.    It looks like 
Xorg -configure
is it.  That's nice to know.  (Odd that that command starts with a capital X). 

Posted by: JKH Designs  Posted on: October 27, 2009, 09:24:54 am  
Insert Quote  
Snowdog,Imilano and all,

I thought we had this problem solved.  I rebooted my system this morning and it came back up to the oversized resolution.  I went through the steps ya'll recommended yesterday and I'm back to an adjustable resolution again.

My question is what do I need to do to save these settings permanently?

I found this command in the xorg.conf file but have not tried it, kinda gunshy after messing around with it yesterday.

sudo dpkg-reconfigure - phigh xserver-xorg

Any suggestions?


Thanks again in advance

James


 
Posted by: JKH Designs  Posted on: October 27, 2009, 06:54:42 am  
Insert Quote  
Hey Snowhog,

Yes I have a grub menu that comes up very briefly.  I only have the one os on this system so it does not stay on but a second or 2.  I have several other systems that give you a choice at start of which os you need to boot into.

Thnaks again for ya'lls help. ;  

Posted by: lmilano  Posted on: October 26, 2009, 06:20:57 pm  
Insert Quote  
Quote from: GreyGeek on October 26, 2009, 04:16:04 pm
Hey, guys, the visual impaired GreyGeek has a question:

I thought that HAL no longer uses xorg.conf and identifies and configures the video device each time it boots?  Yes?  No?


Hi GreyGeek,

Yes and no. It is not needed by default in Karmic. If it's not present, it's not used, and everything works automagically. If it is present, it is used. 

[http://ubuntuforums.org/showthread.php?p=8051823](http://ubuntuforums.org/showthread.php?p=8051823)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1221226](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1221226)

Apparently, "sudo Xorg -configure" regenerates one. 

Posted by: Snowhog  Posted on: October 26, 2009, 04:19:29 pm  
Insert Quote  
Not in Hardy IIUC. 


Posted by: GreyGeek  Posted on: October 26, 2009, 04:16:04 pm  
Insert Quote  
Hey, guys, the visual impaired GreyGeek has a question:

I thought that HAL no longer uses xorg.conf and identifies and configures the video device each time it boots?  Yes?  No? 
Posted by: Snowhog  Posted on: October 26, 2009, 02:54:41 pm  
Insert Quote  
Glad we could help. 

Do you even see your Grub menu? If 'no,' then it's hidden, and if you don't want that, it can be 'unhidden' so you can see all the kernel boot options available to you. 


Posted by: JKH Designs  Posted on: October 26, 2009, 02:47:40 pm  
Insert Quote  
Thank you both Imilano & Snowhog very much for the input.

I did not have a recovery mode already in the Grub.

Pressed esc. key at boot up and went to the newest kernal Recovery mode.
first loaded any new dpkg,  rebooted and then went in to x file server recover and rebooted into a kubuntu o.s.  

Couldn't have done it without your input, thanks so much thought I had lost everything.


James 


Posted by: lmilano  Posted on: October 26, 2009, 12:38:31 pm  
Insert Quote  
Right. There is also an option to "repair graphics" usually in the Rescue Mode. That might work. 
Posted by: Snowhog  Posted on: October 26, 2009, 12:34:25 pm  
Insert Quote  
Do you have a (recovery mode) boot entry in your Grub menu when you boot? If you do, select it. That gets you to a command line 'as root.' If you don't, then when you see the Grub menu, press 'e' to edit. Select the kernel line and arrow to the end and then backspace to erase the items after ro and then type single so that the end of the kernel line you have so single

Tthis is what mine looks like:

Quote
kernel          /boot/vmlinuz-2.6.28-16-generic root=UUID=8c01fe0c-a60f-4921-94d6-cabbfff0a699 ro single


Then press 'b' to boot. You will end up at the command line 'as root.' 


Posted by: JKH Designs  Posted on: October 26, 2009, 11:41:38 am  
Insert Quote  
I am new to 8.04 Hardy and Kubuntu been using it about a year. I really like it and have a lot of software loaded.  I came in this morning and at startup my monitor resolution was very large. I could not increase the resolution through the settings monitor desktop menu.   I found a message about editing the xorg.conf file which I tried, rebooted and now I have a black screen.  How do I boot into a console or bare bones os to try to restore the original xorg.conf file?

Thanks in advance

James

Hi James,

I've tried to read the thread .... :(

So, do you have the Server version of 8.04 ?
Have you then added the kubuntu 3.5.10 as a desktop environment ?

As Johnny5 famously said "I need input" ... Rebuilding your xorg is not unsurmountable problem, but some more details of what you have, and how you installed stuff / upgraded versions etc. would sure be a help !!

Phill.

---

### Post by JKH Designs on 2009-10-30
Hey Phill,

Thanks for responding. sorry about the long initial post was trying to let ya&#314;l know where I was at with my problem.   

Yes I have been running Hardy 8.04 LTS server with Kubuntu KDE 3.5.10 desktop for about a year now.  I have always kept it updated.  The last update I received was a week ago today I clicked to let adept install and it said for me to restart the system to finish the upgrade. When it rebooted I came up to a oversized resolution and the system settings would not let me go to anything different.  It was locked on 640x480.  I then found a post that told me to edit the xorg.conf file which I did and saved and rebooted.  Well this time I came up to a black screen.  I then rebooted waited for GRUB hit the esc key and then went to the recovery mode kernel and hit enter. I came to the recovery menu and first run dpkg to repair any broken packages, then it came back to the recovery menu and I ran xserver repair to fix xorg.conf  then rebooted.  This time it was a very tiny resolution but systems settings would let me reduce it down to the 1024x768 correct setting.  Everything is fine from this point until I have to reboot then it comes back to the oversized resolution and I have to repeat the above procedure to correct.  I am trying to get the screen settings to save as default the 1024x768 setting.  I have tried comparing and editing the xorg.conf file to 3 other systems that I am running this same Kubuntu 3.5.10 Hardy server on not changing the video card section because they differ from on system to the other,  It always comes back to the 640x480 resoltion unless I have just run the xserver repair program.  I also noticed that it sets the modeline to 640x480 in the xorg.conf file.  That is what I have been editing out but it always reboots back to a black screen after I edit.

I hope this the info you need to help but if its not please let me know.

Thanks for your help,

James

---

