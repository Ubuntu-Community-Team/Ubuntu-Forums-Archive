---
title: "Built-In Webcam Problems"
date: 2008-05-07
forum: Hardware
---

### Post by zambiandreams on 2008-05-07
I have a Sager NP6690 laptop with a built in webcam that I have not yet been able to get functioning.

I am running Ubuntu 8.04.

Cheese did not detect the camera, and Camorama diplays the message "Could not connect to video device (/dev/video0) when I try and launch it.

I ran EasyCam in an attempt to install the correct driver, but that too was unsuccessful.

The output when I run lsusb is 

Bus 005 Device 003: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Am I missing something? Thanks in advance!

---

### Post by linuxwizard on 2008-05-07
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by zambiandreams on 2008-05-07
In Ekiga, under Edit>Preferences>Video Devices>Input Device no devices appear to be found; the only option listed is 'No Device Found.'  The same thing happened when I completed the 'First Time Configuration' for Ekiga.  The 'Detect Devices' button under the same menu also is unable to locate the camera. 

Changing the video plugin was also obviously unfruitful.

Is there a standard procedure for making Ubuntu recognize hardware?  My every other experience with hardware has been seamless.

---

### Post by linuxwizard on 2008-05-07
After doing some searching on your webcam >Bus 006 Device 002: ID 0402:5602 ALi Corp. Video Camera Controller > it is not supported in Linux no driver. Maybe in the future their will be a driver that supports your webcam. Good Luck

---

### Post by zambiandreams on 2008-05-07
Well, that would certainly explain why EasyCam could not find a driver.

Thank you for the very quick responses.  I would be lost without people so dedicated to the Ubuntu community.

---

### Post by AbtZ on 2008-05-27
[COLOR="Red"]EDIT: [/COLOR]The information below is quite old,  and as such you cannot follow the guide exactly. As of 9.04, my webcam works out of the box, so I see no reason to update it. I will leave it as reference, though.


> **linuxwizard said:**
> After doing some searching on your webcam >Bus 006 Device 002: ID 0402:5602 ALi Corp. Video Camera Controller > it is not supported in Linux no driver.

Actually, I got my ALi Corp webcam working, with some help from the place I bought the computer from. Here's how:


1. Make sure you have the  ALi Corp webcam installed. Activate it (for me I do so by pressing Fn+F10), then run
```
lsusb | grep ALi
```

I get 
```
Bus 003 Device 004: ID 0402:5602 ALi Corp. Video Camera Controller
```
which means I have the correct webcam.

2. Install subversion
```
sudo apt-get install subversion
```

3.  Pull the required files via subversion

```
svn co https://m560x-driver.svn.sourceforge.net/svnroot/m560x-driver/m560x/branches/m5602-ov9650
```

[COLOR="Red"]EDIT[/COLOR]: As it seems they have made an update, I have not tested this version of the driver myself, and cannot answer for whether it works or not. Perhaps a different branch is better for your computer.

This will give you all the different branches, as well as some other stuff, from their subversion repo:
```
svn co https://m560x-driver.svn.sourceforge.net/svnroot/m560x-driver
```

Check out the link at the bottom of this post to find the project page at sourceforge.

4. ```
cd m5602-ov9650/
```

5. You need the proper packages so you can compile code
```
sudo apt-get install build-essential
```

Then you can compile by simply running
```
make
```

in the folder you downloaded the files to.

6. ```
sudo mkdir /lib/modules/`uname -r`/kernel/drivers/usb/media
sudo cp m5602.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
sudo depmod -a
sudo modprobe m5602
```

7. The camera should now work. You can try it out with xawtv. If you want it to work with cheese you need to install a script -- go here to download it:

[http://sourceforge.net/mailarchive/forum.php?thread_name=481DA244.8010200%40gmail.com&forum_name=m560x-driver-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=481DA244.8010200%40gmail.com&forum_name=m560x-driver-devel)

It is the .fdi file attached at the top of his post.

Then go to the folder where you downloaded the file and do

```
sudo cp 10-m5602-webcam.fdi /usr/share/hal/fdi/information/20thirdparty/
```

After this, reboot and everything should now work. :)

I first tried this with the 64-bit version of Ubuntu, and it worked with cheese but not xawtv. There were also some other bugs such as the computer hard freezing when trying to exit one of the programs or trying to add different effects in Cheese, and sometimes it also refused to resume after suspending.

I have just reinstalled Ubuntu (Mint) 32-bit version, and I followed my own guide to activate the cam while writing it. So far everything seems to work smoothly.

More info can be found here:
[http://sourceforge.net/projects/m560x-driver](http://sourceforge.net/projects/m560x-driver)

Or at their mailing list:
[http://sourceforge.net/mailarchive/forum.php?forum_name=m560x-driver-devel](http://sourceforge.net/mailarchive/forum.php?forum_name=m560x-driver-devel)

---

### Post by zambiandreams on 2008-05-27
AbtZ, everything went smooth until I hit the final command of step 6.  When I entered: 

sudo modprobe m5602

it returned:

FATAL: Module m5602 not found.

So close!  Could I have not obtained the correct packages?

---

### Post by AbtZ on 2008-05-27
IIRC, I got the same problem when the "depmod -a" command failed to run properly.

Do this:
```
ls /lib/modules/2.6.24-16-generic/kernel/drivers/usb/media/
```

It should tell you whether the m5602.ko is in the folder or not. If it's not,  move it there and try 
```
sudo depmod -a
``` 
and
```
sudo modprobe m5602
```

again. If it is already there, reboot your computer before running those two commands. Dunno why, but it worked for me.

---

### Post by zambiandreams on 2008-05-27
The ls command shows that m5602.ko is present, and the depmod -a command also seems to work fine, but modprobe still returns:

FATAL: Module m5602 not found.


Same results before and after the restart.

---

### Post by AbtZ on 2008-05-27
I went through my how to again, thinking there might be a typo somewhere, but I cannot reproduce your error. I'm sorry, I do not know why it doesn't work for you.

EDIT: Perhaps your kernel version is different from mine?
Try
```
uname -r
```
and see what you get.

---

### Post by CryptiniteDemon on 2008-05-31
I followed your guide exactly and I get no errors in compiling or any of the bash commands.  However, it still refuses to open the camera in ekiga dn xawtv never starts fo rme.

---

### Post by AbtZ on 2008-05-31
When on 64bit xawtv didn't work for me either, but cheese did. Do that extra stuff in the guide to get cheese enabled, then try again.

---

### Post by Fizz.LeChat on 2008-06-15
Thanks for your help. But I followed your tutorial (Eurocom with ALi 402:5602) and at #3 I get file doesn't exist on Sourceforge... I tried to substitute another file on the branch but it didn't work...

---

### Post by causeitsme on 2008-06-17
> **Fizz.LeChat said:**
> Thanks for your help. But I followed your tutorial (Eurocom with ALi 402:5602) and at #3 I get file doesn't exist on Sourceforge... I tried to substitute another file on the branch but it didn't work...

What he said, 'file doesn't exist'. Any ideas where it can be gotten?

---

### Post by AbtZ on 2008-06-24
[http://sourceforge.net/svn/?group_id=185953](http://sourceforge.net/svn/?group_id=185953)

Here's how to get their whole subversion directory:
```
svn co https://m560x-driver.svn.sourceforge.net/svnroot/m560x-driver
```

This means you will get everything -- all different branches and testprograms and documentation and whathaveyou that they have put in the svn directory.

To download the branch I used in my original post type
```
svn co https://m560x-driver.svn.sourceforge.net/svnroot/m560x-driver/m560x/branches/m5602-ov9650
```

As I think I have said before this driver is kinda buggy, and stops my laptop from resuming from suspend if the webcam is active. As such, you might want to check out another branch, and see if it works better.

I put the link in my original post, but perhaps you missed it. [Here's the address for the projects homepage at sourceforge]("http://sourceforge.net/projects/m560x-driver"). If you want more info, or if the change the names of the svn directories again, I suggest you check it out.

Good luck. :)

---

### Post by Zipolite on 2008-07-11
The second part of step six doesn't work for me I'm a noob any help???

root@HAL:/home/zip/m5602-ov9650# sudo cp m5602.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
cp: cannot stat `m5602.ko': No such file or directory

---

### Post by nbppp2 on 2008-07-25
> **Zipolite said:**
> The second part of step six doesn't work for me I'm a noob any help???

root@HAL:/home/zip/m5602-ov9650# sudo cp m5602.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
cp: cannot stat `m5602.ko': No such file or directory

The name of the file has been changed in the latest version of the driver.  

Try this instead  

```
sudo mkdir /lib/modules/`uname -r`/kernel/drivers/usb/media
sudo cp m560x.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
sudo depmod -a
sudo modprobe m560x
```

---

### Post by nbppp2 on 2008-07-25
After getting my webcam working via this thread, I have started to notice that my webcam light is now always on.  I don't care if it is on, my concern is that my webcam may be on and always broadcasting.  

I'm not a noob, but I'm also not a expert in inner workings of the kernel or how the hald works. 

I'm pretty sure that the HAL (that would be **H**ardware **A**bstraction **L**ayer for you noobs) has a process that controls this, I'm just not sure what it is, or what command I could run to turn off my camera.

If I knew what command I could run to turn an/off my webcam, I could write a small shell script that would handle it for me.  

Any help would be appreciated.  I run ubuntu 8.04.1 AMD64.

---

### Post by cruzcarneiro on 2008-07-27
After o make :
[quote]make -C /lib/modules/2.6.26-4-generic/build SUBDIRS=/home/gabriel/m5602-ov9650 modules
make[1]: Entrando no diretório `/usr/src/linux-headers-2.6.26-4-generic'
  CC [M]  /home/gabriel/m5602-ov9650/m560x_core.o
/home/gabriel/m5602-ov9650/m560x_core.c:1570: warning: ‘struct class_device’ declared inside parameter list
/home/gabriel/m5602-ov9650/m560x_core.c:1570: warning: its scope is only this definition or declaration, which is probably not what you want
/home/gabriel/m5602-ov9650/m560x_core.c: In function ‘show_model’:
/home/gabriel/m5602-ov9650/m560x_core.c:1570: warning: initialization from incompatible pointer type
/home/gabriel/m5602-ov9650/m560x_core.c: At top level:
/home/gabriel/m5602-ov9650/m560x_core.c:1570: error: expected ‘)’ before ‘(’ token
/home/gabriel/m5602-ov9650/m560x_core.c:1571: warning: ‘struct class_device’ declared inside parameter list
/home/gabriel/m5602-ov9650/m560x_core.c: In function ‘show_in_use’:
/home/gabriel/m5602-ov9650/m560x_core.c:1571: warning: initialization from incompatible pointer type
/home/gabriel/m5602-ov9650/m560x_core.c: At top level:
/home/gabriel/m5602-ov9650/m560x_core.c:1571: error: expected ‘)’ before ‘(’ token
/home/gabriel/m5602-ov9650/m560x_core.c:1572: warning: ‘struct class_device’ declared inside parameter list
/home/gabriel/m5602-ov9650/m560x_core.c: In function ‘show_streaming’:
/home/gabriel/m5602-ov9650/m560x_core.c:1572: warning: initialization from incompatible pointer type
/home/gabriel/m5602-ov9650/m560x_core.c: At top level:
/home/gabriel/m5602-ov9650/m560x_core.c:1572: error: expected ‘)’ before ‘(’ token
/home/gabriel/m5602-ov9650/m560x_core.c:1573: warning: ‘struct class_device’ declared inside parameter list
/home/gabriel/m5602-ov9650/m560x_core.c: In function ‘show_palette’:
/home/gabriel/m5602-ov9650/m560x_core.c:1573: warning: initialization from incompatible pointer type
/home/gabriel/m5602-ov9650/m560x_core.c: At top level:
/home/gabriel/m5602-ov9650/m560x_core.c:1573: error: expected ‘)’ before ‘(’ token
/home/gabriel/m5602-ov9650/m560x_core.c:1574: warning: ‘struct class_device’ declared inside parameter list
/home/gabriel/m5602-ov9650/m560x_core.c: In function ‘show_frames_total’:
/home/gabriel/m5602-ov9650/m560x_core.c:1574: warning: initialization from incompatible pointer type
/home/gabriel/m5602-ov9650/m560x_core.c: At top level:
/home/gabriel/m5602-ov9650/m560x_core.c:1574: error: expected ‘)’ before ‘(’ token
/home/gabriel/m5602-ov9650/m560x_core.c:1575: warning: ‘struct class_device’ declared inside parameter list
/home/gabriel/m5602-ov9650/m560x_core.c: In function ‘show_frames_read’:
/home/gabriel/m5602-ov9650/m560x_core.c:1575: warning: initialization from incompatible pointer type
/home/gabriel/m5602-ov9650/m560x_core.c: At top level:
/home/gabriel/m5602-ov9650/m560x_core.c:1575: error: expected ‘)’ before ‘(’ token
/home/gabriel/m5602-ov9650/m560x_core.c:1576: warning: ‘struct class_device’ declared inside parameter list
/home/gabriel/m5602-ov9650/m560x_core.c: In function ‘show_packets_dropped’:
/home/gabriel/m5602-ov9650/m560x_core.c:1576: warning: initialization from incompatible pointer type
/home/gabriel/m5602-ov9650/m560x_core.c: At top level:
/home/gabriel/m5602-ov9650/m560x_core.c:1576: error: expected ‘)’ before ‘(’ token
/home/gabriel/m5602-ov9650/m560x_core.c:1577: warning: ‘struct class_device’ declared inside parameter list
/home/gabriel/m5602-ov9650/m560x_core.c: In function ‘show_decoding_errors’:
/home/gabriel/m5602-ov9650/m560x_core.c:1577: warning: initialization from incompatible pointer type
/home/gabriel/m5602-ov9650/m560x_core.c: At top level:
/home/gabriel/m5602-ov9650/m560x_core.c:1577: error: expected ‘)’ before ‘(’ token
/home/gabriel/m5602-ov9650/m560x_core.c: In function ‘m560x_create_sysfs_files’:
/home/gabriel/m5602-ov9650/m560x_core.c:1581: error: ‘class_device_attr_model’ undeclared (first use in this function)
/home/gabriel/m5602-ov9650/m560x_core.c:1581: error: (Each undeclared identifier is reported only once
/home/gabriel/m5602-ov9650/m560x_core.c:1581: error: for each function it appears in.)
/home/gabriel/m5602-ov9650/m560x_core.c:1582: error: ‘class_device_attr_in_use’ undeclared (first use in this function)
/home/gabriel/m5602-ov9650/m560x_core.c:1583: error: ‘class_device_attr_streaming’ undeclared (first use in this function)
/home/gabriel/m5602-ov9650/m560x_core.c:1584: error: ‘class_device_attr_palette’ undeclared (first use in this function)
/home/gabriel/m5602-ov9650/m560x_core.c:1585: error: ‘class_device_attr_frames_total’ undeclared (first use in this function)
/home/gabriel/m5602-ov9650/m560x_core.c:1586: error: ‘class_device_attr_frames_read’ undeclared (first use in this function)
/home/gabriel/m5602-ov9650/m560x_core.c:1587: error: ‘class_device_attr_packets_dropped’ undeclared (first use in this function)
/home/gabriel/m5602-ov9650/m560x_core.c:1588: error: ‘class_device_attr_decoding_errors’ undeclared (first use in this function)
/home/gabriel/m5602-ov9650/m560x_core.c: In function ‘m560x_remove_sysfs_files’:
/home/gabriel/m5602-ov9650/m560x_core.c:1593: error: ‘class_device_attr_model’ undeclared (first use in this function)
/home/gabriel/m5602-ov9650/m560x_core.c:1594: error: ‘class_device_attr_in_use’ undeclared (first use in this function)
/home/gabriel/m5602-ov9650/m560x_core.c:1595: error: ‘class_device_attr_streaming’ undeclared (first use in this function)
/home/gabriel/m5602-ov9650/m560x_core.c:1596: error: ‘class_device_attr_palette’ undeclared (first use in this function)
/home/gabriel/m5602-ov9650/m560x_core.c:1597: error: ‘class_device_attr_frames_total’ undeclared (first use in this function)
/home/gabriel/m5602-ov9650/m560x_core.c:1598: error: ‘class_device_attr_frames_read’ undeclared (first use in this function)
/home/gabriel/m5602-ov9650/m560x_core.c:1599: error: ‘class_device_attr_packets_dropped’ undeclared (first use in this function)
/home/gabriel/m5602-ov9650/m560x_core.c:1600: error: ‘class_device_attr_decoding_errors’ undeclared (first use in this function)
make[2]: ** [/home/gabriel/m5602-ov9650/m560x_core.o] Erro 1
make[1]: ** [_module_/home/gabriel/m5602-ov9650] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-2.6.26-4-generic'
make: ** [all] Erro 2
[quote/]

I have instaled build-essencial linux-source bin86... all and don't work!!!!!!!

---

### Post by EmilM on 2008-08-04
i'm not getting any response from "lsusb | grep ALi" :(

---

### Post by marlon89br on 2008-08-17
I've compiled three versions: the first 5602 only, the 5602 from the SVN repository, and m5602-ov9650 from SVN. Either I get segmentation fault when modprobbing the module, or I get my webcam recognized in skype but with a black image... Is there something I can do?

Thanks for helping :)

---

### Post by rajan dhir on 2008-09-09
> **nbppp2 said:**
> The name of the file has been changed in the latest version of the driver.  

Try this instead  

```
sudo mkdir /lib/modules/`uname -r`/kernel/drivers/usb/media
sudo cp m560x.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
sudo depmod -a
sudo modprobe m560x
```
err hi 
i am very new(2 days to be exact) to linux
i followed your guide fully
but at step 6
rd@rd-laptop:~/m5602-ov9650$ sudo mkdir /lib/modules/'uname -r'/kernel/drivers/usb/media
mkdir: cannot create directory `/lib/modules/uname -r/kernel/drivers/usb/media': No such file or directory

this message comes up
what am i doing wrong??
please help this noob
thks

---

### Post by AbtZ on 2008-09-09
Hey, all. I'm sorry, but a lot of your questions I don't know the answer to, and I'm sure your google fu is as powerful as mine. :)

rajan dhir, your problem seems to lie in the stupid syntaxes of bash (terminal). See, ```
'
``` is not the same as ```
`
```. Therefore, in order to create that directory you must enter the code exactly as shown:
```
sudo mkdir /lib/modules/`uname -r`/kernel/drivers/usb/media
```
Try copy/pasting, it's easier than writing the `-symbol on a non-American keyboard.

---

### Post by rajan dhir on 2008-09-10
> **AbtZ said:**
> Hey, all. I'm sorry, but a lot of your questions I don't know the answer to, and I'm sure your google fu is as powerful as mine. :)

rajan dhir, your problem seems to lie in the stupid syntaxes of bash (terminal). See, ```
'
``` is not the same as ```
`
```. Therefore, in order to create that directory you must enter the code exactly as shown:
```
sudo mkdir /lib/modules/`uname -r`/kernel/drivers/usb/media
```
Try copy/pasting, it's easier than writing the `-symbol on a non-American keyboard.
hey thanks a lot!!!
but after the restart cheese still does not work :(
anyway thks again for helping

---

### Post by rajan dhir on 2008-09-10
> **AbtZ said:**
> Hey, all. I'm sorry, but a lot of your questions I don't know the answer to, and I'm sure your google fu is as powerful as mine. :)

rajan dhir, your problem seems to lie in the stupid syntaxes of bash (terminal). See, ```
'
``` is not the same as ```
`
```. Therefore, in order to create that directory you must enter the code exactly as shown:
```
sudo mkdir /lib/modules/`uname -r`/kernel/drivers/usb/media
```
Try copy/pasting, it's easier than writing the `-symbol on a non-American keyboard.
hey thanks a lot!!!
but after the restart cheese still does not work :(
anyway thks again for helping

---

### Post by k00t on 2008-09-23
My terminal doesn't respond when i enter lsusb | grep ALi or when I enter sudo modprobe m560x. Everything else worked perfectly.

My kernel is: uname -r
2.6.24-19-generic

Thanks,
     k00t

---

### Post by theDaveTheRave on 2008-10-18
Hello Guys,

I was folowing the instructions and I was all prepared to give a realy huge THANKS to ALL when I was right at the the end with the command 

> 
sudo modprobe m560x
FATAL: Module m560x not found.


So after a bit of hunting into what may be the problem I descovered the folowing...
>  
davem@Dartagnon:~/m5602-ov9650$ ls /lib/modules/2.6.24-19-generic/kernel/drivers/usb/media
[COLOR="Red"]ls: cannot access /lib/modules/2.6.24-19-generic/kernel/drivers/usb/media/: Not a directory[/COLOR]
davem@Dartagnon:~/m5602-ov9650$ ls -l  /lib/modules/2.6.24-19-generic/kernel/drivers/usb
total 864
drwxr-xr-x 2 root root   4096 2008-09-30 11:33 atm
drwxr-xr-x 2 root root   4096 2008-09-30 11:33 class
drwxr-xr-x 2 root root   4096 2008-09-30 11:33 core
drwxr-xr-x 2 root root   4096 2008-09-30 11:33 gadget
drwxr-xr-x 2 root root   4096 2008-09-30 11:33 host
drwxr-xr-x 2 root root   4096 2008-09-30 11:33 image
[COLOR="Red"][COLOR="Blue"]-[/COLOR]rw-r--r-- 1 root root 838618 2008-10-18 16:48 media[/COLOR]
drwxr-xr-x 3 root root   4096 2008-09-30 11:33 misc
drwxr-xr-x 2 root root   4096 2008-09-30 11:33 mon
drwxr-xr-x 2 root root   4096 2008-09-30 11:33 serial
drwxr-xr-x 2 root root   4096 2008-09-30 11:33 storage
davem@Dartagnon:~/m5602-ov9650$ 


which certainly seems to confirm that problem, so I decided to see what was in this file... 
> 
davem@Dartagnon:~/m5602-ov9650$ more /lib/modules/2.6.24-19-generic/kernel/drivers/usb/media

******** /lib/modules/2.6.24-19-generic/kernel/drivers/usb/media: Not a text file ********

davem@Dartagnon:~/m5602-ov9650$ 


I'm not a newb, but I aint no guru.... Am I safe to "delete" this not a text file or something and if I do...what am I going to break? I'm guessing that it holds the details of the files that are loaded at start up for all the media stuff to work... or is a script that points to them?

anyone got any ideas of what I should do next??

oh by the way... I also rapidly descovered the issue of the module having changed name not very helpful!

also I've been reading that some of you have been having problems with the <lsusb> command, and "grep" the line that you are after.

If your camera is internal it may or may not be connected to a USB port.

to see if it is do this...

> 
davem@Dartagnon:~/m5602-ov9650$ lsusb
Bus 005 Device 002: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
davem@Dartagnon:~/m5602-ov9650$ 


and it will show up the ALi video controller if it is conected via that route.

OTHER wise try :lolflag::lolflag: <lshw |grep ALi> or just plain simple lshw to see if it is there anywhere? it may be it is turned off.... in which case I can't help! sorry..

sorry if there are any funny typo's in this message, my friends young daughter is saying hi.... her first taste of Ubuntu happiness! I think I should lend her to Bill gates, so as she can prove how problematic it is having all users as default admins.... she would have destroyed my long since gone Vista partition by now:lolflag:

anyway I hope the above helps somewhat.

Dave

---

### Post by 666porcondissaum on 2008-11-16
Got some trouble...

First, tanks a lot... because you've ressurrected the cam hope in my heart, also, gave me wings to fly to the solution and... but... actually stucked in the terminal after the mobprobe... oh gosh...


Seems to be the time to call it "crack in terminal"... no response...

---

### Post by 666porcondissaum on 2008-12-02
Is there anybody built-in there!?):P

---

### Post by paechan on 2008-12-03
I have been trying to get my Ali 5602 cam to work these past couple of days but it just wont.

I am using ubuntu 8.10 32-bit and that may be the root of my troubles. 

lsusb gives the following:

```
johannes@johannes-laptop:~$ lsusb | grep ALi
Bus 005 Device 002: ID 0402:5602 ALi Corp. Video Camera Controller

```

So I know that the cam is there and that I am using the right approach. I have tried using the approach from the original post with instructions. I have also tried to use the guide posted on the sourceforge page for the driver, but with no luck either. I have figured out that I am supposed to use the gspca_m5602 driver instead of the ov9655 one. This is easily done by replacing m5602.ko with gspc_m5602.ko in the original instructions. Everything seems to work until I hit the modprobe step.

```
johannes@johannes-laptop:~$ sudo modprobe gspca_m5602 
[sudo] password for johannes: 
FATAL: Error inserting gspca_m5602 (/lib/modules/2.6.27-9-generic/kernel/drivers/usb/media/gspca_m5602.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

dmesg gives this in regard to gspca_m5602

```
[  188.411542] gspca_m5602: disagrees about version of symbol gspca_frame_add
[  188.411563] gspca_m5602: Unknown symbol gspca_frame_add
[  188.412807] gspca_m5602: disagrees about version of symbol gspca_dev_probe
[  188.412812] gspca_m5602: Unknown symbol gspca_dev_probe
[  213.787517] gspca_m5602: disagrees about version of symbol gspca_frame_add
[  213.787534] gspca_m5602: Unknown symbol gspca_frame_add
[  213.788772] gspca_m5602: disagrees about version of symbol gspca_dev_probe
[  213.788777] gspca_m5602: Unknown symbol gspca_dev_probe

```

I cant get any of this to make sense because according to the sourceforge instructions, none of this is needed. 

[http://m560x-driver.wiki.sourceforge.net/install_m560x_driver](http://m560x-driver.wiki.sourceforge.net/install_m560x_driver)

It tells me that I need livecam to get the 5602 branch to work and that is a whole different chapter.

I hope that someone out there knows what is going on and if it is even possible to get this ALi m5602 cam to work in ubuntu 8.10.

---

### Post by paechan on 2008-12-04
So I toyed around a bit more with the driver and now it seems that I have compiled it right. I used the m5602 instead of the gspca one. It says on sourceforge that it is for older kernels than what I am currently using, but it gave me no rouble at all. The trouble now is just getting it to work. vlc v4l2: doesnt work and I cant compile livecam. How do I see if this actually works?

---

### Post by paechan on 2008-12-04
It seems that ekiga was somehow able to get through. First time I started it up, I could actually see myself. That was pretty sweet, but then I closed it and when I tried again, the picture was all messed up. I think it is possible to get it working by using the 5602 branch instead of the newest one and Ekiga, but it definetly takes a lot of hairpulling and it is not really worth it. We must hope that it will be integrated into ubuntu soon so that we can use cheese.

---

### Post by AbtZ on 2008-12-04
I see this thread is still active. I'm sad to see that this still isn't fixed in 8.10.

---

### Post by paechan on 2008-12-05
Yeah it is really annoying. Your original post really has helped many people, including myself, but a stable integrated solution is really needed. We want to use cheese and make stupid pictures like our smug mac-brothers!

Since the webcam is now working in both gstreamer-properties and ekiga, I guess all there is left to do is file a bugreport for the cheese developers.

[http://bugzilla.gnome.org/show_bug.cgi?id=563325](http://bugzilla.gnome.org/show_bug.cgi?id=563325)

SO thats what I did and I dont think it will be long before someone fixes this. It must be a very small patch that is needed to make this webcam work in cheese, so it probably wont be long now.

---

### Post by 666porcondissaum on 2008-12-09
Yeah me too.:KS

---

### Post by paechan on 2008-12-10
I think that a developer is getting interested in our problems now, at least when you read his comments on bugzilla it seems that way. I will try and provide him with everything so that he can get it working. Would really love to try cheese out.

---

### Post by barbedsaber on 2009-01-16
I got an error while compiling (or failing to compile as the case was.)
```
harry@neo:~/m5602-ov9650$ make
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/harry/m5602-ov9650 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/harry/m5602-ov9650/m560x_core.o
/home/harry/m5602-ov9650/m560x_core.c: In function ‘rvmalloc’:
/home/harry/m5602-ov9650/m560x_core.c:66: error: implicit declaration of function ‘PAGE_ALIGN’
/home/harry/m5602-ov9650/m560x_core.c:74: error: implicit declaration of function ‘SetPageReserved’
/home/harry/m5602-ov9650/m560x_core.c:74: error: implicit declaration of function ‘vmalloc_to_page’
/home/harry/m5602-ov9650/m560x_core.c: In function ‘rvfree’:
/home/harry/m5602-ov9650/m560x_core.c:91: error: implicit declaration of function ‘ClearPageReserved’
/home/harry/m5602-ov9650/m560x_core.c: In function ‘m5602_init_from_script’:
/home/harry/m5602-ov9650/m560x_core.c:337: warning: assignment discards qualifiers from pointer target type
/home/harry/m5602-ov9650/m560x_core.c:352: warning: assignment discards qualifiers from pointer target type
/home/harry/m5602-ov9650/m560x_core.c:420: warning: assignment discards qualifiers from pointer target type
/home/harry/m5602-ov9650/m560x_core.c: In function ‘init_from_script’:
/home/harry/m5602-ov9650/m560x_core.c:589: warning: assignment discards qualifiers from pointer target type
/home/harry/m5602-ov9650/m560x_core.c:604: warning: assignment discards qualifiers from pointer target type
/home/harry/m5602-ov9650/m560x_core.c:673: warning: assignment discards qualifiers from pointer target type
/home/harry/m5602-ov9650/m560x_core.c: In function ‘init_hashtab’:
/home/harry/m5602-ov9650/m560x_core.c:812: warning: assignment discards qualifiers from pointer target type
/home/harry/m5602-ov9650/m560x_core.c:827: warning: assignment discards qualifiers from pointer target type
/home/harry/m5602-ov9650/m560x_core.c:851: warning: assignment discards qualifiers from pointer target type
/home/harry/m5602-ov9650/m560x_core.c: At top level:
/home/harry/m5602-ov9650/m560x_core.c:1572: warning: ‘struct class_device’ declared inside parameter list
/home/harry/m5602-ov9650/m560x_core.c:1572: warning: its scope is only this definition or declaration, which is probably not what you want
/home/harry/m5602-ov9650/m560x_core.c: In function ‘show_model’:
/home/harry/m5602-ov9650/m560x_core.c:1572: warning: initialization from incompatible pointer type
/home/harry/m5602-ov9650/m560x_core.c: At top level:
/home/harry/m5602-ov9650/m560x_core.c:1572: error: expected ‘)’ before ‘(’ token
/home/harry/m5602-ov9650/m560x_core.c:1573: warning: ‘struct class_device’ declared inside parameter list
/home/harry/m5602-ov9650/m560x_core.c: In function ‘show_in_use’:
/home/harry/m5602-ov9650/m560x_core.c:1573: warning: initialization from incompatible pointer type
/home/harry/m5602-ov9650/m560x_core.c: At top level:
/home/harry/m5602-ov9650/m560x_core.c:1573: error: expected ‘)’ before ‘(’ token
/home/harry/m5602-ov9650/m560x_core.c:1574: warning: ‘struct class_device’ declared inside parameter list
/home/harry/m5602-ov9650/m560x_core.c: In function ‘show_streaming’:
/home/harry/m5602-ov9650/m560x_core.c:1574: warning: initialization from incompatible pointer type
/home/harry/m5602-ov9650/m560x_core.c: At top level:
/home/harry/m5602-ov9650/m560x_core.c:1574: error: expected ‘)’ before ‘(’ token
/home/harry/m5602-ov9650/m560x_core.c:1575: warning: ‘struct class_device’ declared inside parameter list
/home/harry/m5602-ov9650/m560x_core.c: In function ‘show_palette’:
/home/harry/m5602-ov9650/m560x_core.c:1575: warning: initialization from incompatible pointer type
/home/harry/m5602-ov9650/m560x_core.c: At top level:
/home/harry/m5602-ov9650/m560x_core.c:1575: error: expected ‘)’ before ‘(’ token
/home/harry/m5602-ov9650/m560x_core.c:1576: warning: ‘struct class_device’ declared inside parameter list
/home/harry/m5602-ov9650/m560x_core.c: In function ‘show_frames_total’:
/home/harry/m5602-ov9650/m560x_core.c:1576: warning: initialization from incompatible pointer type
/home/harry/m5602-ov9650/m560x_core.c: At top level:
/home/harry/m5602-ov9650/m560x_core.c:1576: error: expected ‘)’ before ‘(’ token
/home/harry/m5602-ov9650/m560x_core.c:1577: warning: ‘struct class_device’ declared inside parameter list
/home/harry/m5602-ov9650/m560x_core.c: In function ‘show_frames_read’:
/home/harry/m5602-ov9650/m560x_core.c:1577: warning: initialization from incompatible pointer type
/home/harry/m5602-ov9650/m560x_core.c: At top level:
/home/harry/m5602-ov9650/m560x_core.c:1577: error: expected ‘)’ before ‘(’ token
/home/harry/m5602-ov9650/m560x_core.c:1578: warning: ‘struct class_device’ declared inside parameter list
/home/harry/m5602-ov9650/m560x_core.c: In function ‘show_packets_dropped’:
/home/harry/m5602-ov9650/m560x_core.c:1578: warning: initialization from incompatible pointer type
/home/harry/m5602-ov9650/m560x_core.c: At top level:
/home/harry/m5602-ov9650/m560x_core.c:1578: error: expected ‘)’ before ‘(’ token
/home/harry/m5602-ov9650/m560x_core.c:1579: warning: ‘struct class_device’ declared inside parameter list
/home/harry/m5602-ov9650/m560x_core.c: In function ‘show_decoding_errors’:
/home/harry/m5602-ov9650/m560x_core.c:1579: warning: initialization from incompatible pointer type
/home/harry/m5602-ov9650/m560x_core.c: At top level:
/home/harry/m5602-ov9650/m560x_core.c:1579: error: expected ‘)’ before ‘(’ token
/home/harry/m5602-ov9650/m560x_core.c: In function ‘m560x_create_sysfs_files’:
/home/harry/m5602-ov9650/m560x_core.c:1583: error: implicit declaration of function ‘video_device_create_file’
/home/harry/m5602-ov9650/m560x_core.c:1583: error: ‘class_device_attr_model’ undeclared (first use in this function)
/home/harry/m5602-ov9650/m560x_core.c:1583: error: (Each undeclared identifier is reported only once
/home/harry/m5602-ov9650/m560x_core.c:1583: error: for each function it appears in.)
/home/harry/m5602-ov9650/m560x_core.c:1584: error: ‘class_device_attr_in_use’ undeclared (first use in this function)
/home/harry/m5602-ov9650/m560x_core.c:1585: error: ‘class_device_attr_streaming’ undeclared (first use in this function)
/home/harry/m5602-ov9650/m560x_core.c:1586: error: ‘class_device_attr_palette’ undeclared (first use in this function)
/home/harry/m5602-ov9650/m560x_core.c:1587: error: ‘class_device_attr_frames_total’ undeclared (first use in this function)
/home/harry/m5602-ov9650/m560x_core.c:1588: error: ‘class_device_attr_frames_read’ undeclared (first use in this function)
/home/harry/m5602-ov9650/m560x_core.c:1589: error: ‘class_device_attr_packets_dropped’ undeclared (first use in this function)
/home/harry/m5602-ov9650/m560x_core.c:1590: error: ‘class_device_attr_decoding_errors’ undeclared (first use in this function)
/home/harry/m5602-ov9650/m560x_core.c: In function ‘m560x_remove_sysfs_files’:
/home/harry/m5602-ov9650/m560x_core.c:1595: error: implicit declaration of function ‘video_device_remove_file’
/home/harry/m5602-ov9650/m560x_core.c:1595: error: ‘class_device_attr_model’ undeclared (first use in this function)
/home/harry/m5602-ov9650/m560x_core.c:1596: error: ‘class_device_attr_in_use’ undeclared (first use in this function)
/home/harry/m5602-ov9650/m560x_core.c:1597: error: ‘class_device_attr_streaming’ undeclared (first use in this function)
/home/harry/m5602-ov9650/m560x_core.c:1598: error: ‘class_device_attr_palette’ undeclared (first use in this function)
/home/harry/m5602-ov9650/m560x_core.c:1599: error: ‘class_device_attr_frames_total’ undeclared (first use in this function)
/home/harry/m5602-ov9650/m560x_core.c:1600: error: ‘class_device_attr_frames_read’ undeclared (first use in this function)
/home/harry/m5602-ov9650/m560x_core.c:1601: error: ‘class_device_attr_packets_dropped’ undeclared (first use in this function)
/home/harry/m5602-ov9650/m560x_core.c:1602: error: ‘class_device_attr_decoding_errors’ undeclared (first use in this function)
/home/harry/m5602-ov9650/m560x_core.c: At top level:
/home/harry/m5602-ov9650/m560x_core.c:1624: error: variable ‘m560x_vm_ops’ has initializer but incomplete type
/home/harry/m5602-ov9650/m560x_core.c:1625: error: unknown field ‘open’ specified in initializer
/home/harry/m5602-ov9650/m560x_core.c:1625: warning: excess elements in struct initializer
/home/harry/m5602-ov9650/m560x_core.c:1625: warning: (near initialization for ‘m560x_vm_ops’)
/home/harry/m5602-ov9650/m560x_core.c:1626: error: unknown field ‘close’ specified in initializer
/home/harry/m5602-ov9650/m560x_core.c:1626: warning: excess elements in struct initializer
/home/harry/m5602-ov9650/m560x_core.c:1626: warning: (near initialization for ‘m560x_vm_ops’)
/home/harry/m5602-ov9650/m560x_core.c: In function ‘v4l_m560x_mmap’:
/home/harry/m5602-ov9650/m560x_core.c:1935: error: ‘VM_WRITE’ undeclared (first use in this function)
/home/harry/m5602-ov9650/m560x_core.c:1951: error: ‘VM_IO’ undeclared (first use in this function)
/home/harry/m5602-ov9650/m560x_core.c:1952: error: ‘VM_RESERVED’ undeclared (first use in this function)
/home/harry/m5602-ov9650/m560x_core.c:1956: error: implicit declaration of function ‘vmalloc_to_pfn’
/home/harry/m5602-ov9650/m560x_core.c:1957: error: implicit declaration of function ‘remap_pfn_range’
/home/harry/m5602-ov9650/m560x_core.c: In function ‘usb_m560x_probe’:
/home/harry/m5602-ov9650/m560x_core.c:2791: error: ‘struct video_device’ has no member named ‘owner’
/home/harry/m5602-ov9650/m560x_core.c:2792: error: ‘struct video_device’ has no member named ‘type’
make[2]: *** [/home/harry/m5602-ov9650/m560x_core.o] Error 1
make[1]: *** [_module_/home/harry/m5602-ov9650] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [all] Error 2
harry@neo:~/m5602-ov9650$ 

```

please help, I want to get this working, so that I can say that every single piece of hardware in my laptop works with ubuntu.

---

### Post by okubax on 2009-01-31
I finally got my webcam to work on Acer Aspire 3680 by following this guide:

[http://m560x-driver.wiki.sourceforge.net/testing_m5602]("http://m560x-driver.wiki.sourceforge.net/testing_m5602")

1. Ensure you have mercurial (hg) source control installed.
2. Clone the gspca-m5602 tree by navigating to a suitable directory on your harddrive and type

hg clone [http://linuxtv.org/hg/~eandren/gspca-m5602/](http://linuxtv.org/hg/~eandren/gspca-m5602/)

3. Enter the directory

cd gspca-m5602

4. Type

make

to build the repository. If this fails, please ensure you have the source headers for your current linux version installed.

5. Unload all relevant modules by typing

make unload

you need to be a superuser to perform this

6. Load all relevant modules by typing

make load

you need to be a superuser to perform this.

7. If all works ok and you want to keep using this code type

make install

you need to be a superuser to perform a driver install.

You now have the latest code ready to be tested.
Please ensure that you have a current install of libv4l for optimum performance

---

### Post by whirl on 2009-05-05
Thanks alot for this thread everyone! I installed xubuntu 9.04 on my girlfriends old Acer Travelmate 2441WXMi and with the help of this thread got this orbicam working.. Atleast in ekiga anyways.

What about skype? All I get is this green screen whenever I try to use video so what about rest of you guys?

this doesnt really bother me cause I use only ekiga but my girlfriend likes to call her friends abroad so it would be kinda cool to get it working.

Cheers o/

---

### Post by dendirk on 2009-10-25
Hi guys,

Im picking up this thread again, i was searching for some time now to get the webcam working.

Today i found this forum :) and i thought yes THIS IS IT but nah its not working.

Im a noobie in Ubuntu so i was wondering if ANYONE could pls pick up this thread again and help me out.

At the moment im on 9.10 karmic , is there anyone that give me some feedback how to get this cam working in 9.10?


THANKS  greetz from Belgium

---

### Post by utilitytrack on 2010-10-28
All people who have troubles with ALi Corp. 5602 webcam (PCI vendor/device code is 0402:5602)! 

Here is new ticket on Kernel Bugzilla that describes the problem. Please share your own comments, experiences, logs and patches: **"ALi Corp. 5602 (m5602) webcam not working on (some?) newest kernels (2.6.31, 2.6.32, 2.6.35)"**
[https://bugzilla.kernel.org/show_bug.cgi?id=16575]("https://bugzilla.kernel.org/show_bug.cgi?id=16575")

---

