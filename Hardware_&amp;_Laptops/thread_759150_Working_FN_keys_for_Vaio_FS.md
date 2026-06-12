---
title: "Working FN keys for Vaio FS*"
date: 2008-04-18
forum: Hardware &amp; Laptops
---

### Post by Toufik on 2008-04-18
[COLOR="Red"][size=+2]This is intended for the VAIO VGN-_FS_... only[/size] (i.e. not FE nor C nor N, etc !)[/COLOR]

[COLOR="Red"]Tested with Hardy but should also work with Gusty[/COLOR]
[COLOR="Red"]No idea for Feisty and older: try at your own risk!! (it shouldn't harm but...)[/COLOR]


If you have a Vaio FS* you'll probably discover that none of the FN keys are working out of the box. This is a bug in the sony-laptop driver [Bug #29987]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/29987") and [Bug #119672]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119672"). It seems that the FS series is handled in a different way than the other series (N, FE,...)

Historically, the driver was called sony_acpi. The driver has then evolved to sonypi and now to sony-laptop. Each version being better, except for the FS :(

Long time ago, someone wrote a little daemon to tweak sony_acpi in order to get the fnkey working. This daemon is called fsfn. But now sony_acpi is deprecated so you have to install it over the brand new sony-laptop. This was a quite annoying operation that has to be done after each kernel update...

So, I modify fsfn to work with sony-laptop instead of sony_acpi in order to avoid this annoying procedure of installation. So, basically, all you have to do now is to download this package:

**Download:**
[http://www.fyma.ucl.ac.be/files/fsfn_2.1-1_i386.deb](http://www.fyma.ucl.ac.be/files/fsfn_2.1-1_i386.deb)

Open it via firefox or nautilus with gdebi, or for the terminal fan, type:
$ sudo dpkg -i fsfn_2.1-1_i386.deb

It will install the daemon and the man page and write an init script to launch it at each boot-up. And... it should work immediately: try FN-F5 for instance

If you want an OSD for each FN keys:
Go to the Ubuntu Menu > System > Preferences > Sessions > Startup Programs
Click "Add"
Name --> Fsfn OSD
Command --> fsfn -o
Comment --> Sooo Nice!

Then logout and login again


Note: if you want to parametrise the deamon, there is a configuration file:  /etc/fsfn.conf
$ gksudo gedit  /etc/fsfn.conf

The syntax is explained here:
$ man 5 fsfn

Please report working and non working laptop and Ubuntu version!

Toufik

NB:
* Tested with Vaio VGN-FS 315B and hardy beta
* As this is the first version, please report any problem
* Dependencies may not be completed so tell me if it is the case

**Removing**
If you want to remove this daemon:
```
$ sudo apt-get remove --purge fsfn
```

**Sources are here**:
[http://www.fyma.ucl.ac.be/files/fsfn-2.0-1.tar.gz](http://www.fyma.ucl.ac.be/files/fsfn-2.0-1.tar.gz)
configuration and init.d files are to be found in the debian directory.

**What if it doesn't work...**
Please report the following informations:
* ```
$ uname -r
```
* ```
$ lshal | grep system.hardware
```
* ```
$lsmod | grep sony
```
you should get ```
sony_laptop
```
* ```
$ ls /sys/class/backlight/sony
```
you should get (at least):
```
brightness  actual_brightness
```
* ```
$ ls /sys/devices/platform/sony-laptop/
```
you should get (at least):
```
brightness_default  fnkey
```
* If you have all of this, and it still doesn't work prepare this command in a terminal but don't press enter yet!
```
$ cat /sys/devices/platform/sony-laptop/fnkey
```
Now press a fn key and just after press enter! You should get a number. The number should be different for each fn key

---

### Post by Tripmonkey_uk on 2008-04-18
Cheers Toufik, nearly 4.30 in the morn here, so I'm off to sleep and I'll give a full test tom.
p.s this post was jst to draw some attention to the thread and to subscribe to the replies ;)

---

### Post by Tripmonkey_uk on 2008-04-19
Tested on VGN-FS215E and the latest Beta version of Hardy Heron.

Package installs fine,
Volume keys work,
Brightness keys work,
Mute key works.

On screen display seems a little funky and shows 2 bars instead of just one for some reason?

[IMG]http://ubuntufs.files.wordpress.com/2008/04/osd_error.png[/IMG]

Not tested the screen change key yet,
Sleep key doesn't work (should be easy to set up),
Magnifier key doesn't work, mapped to anything yet?
Neither of the S keys are mapped to anything yet either I don't think?

I'm going to have a mess about with the config file now and see if we can make use of all the keys, plus find out which is the best sound server to set it up for.

Thanks again Toufik :D

---

### Post by Toufik on 2008-04-19
The double bar OSD is because you have twice "fsfn -o" in the your "Startup Programs" (Go to the Ubuntu Menu > System > Preferences > Sessions > Startup Programs). I know because I had the same issue :)

The conf file is quite basic. We can surely make something better. Default behaviour
* FN-F2, F3, F4 are Mute, Vol Down and Vol up of the "Front Volume" of the HDA intel card (have a look in Alsa Mixer)
* FN-F5 and F6 are Brightness Down and Up.
* FN-F7 is not assigned (Switch Display). You can assign i810rotate (from the i810switch package). That should work but I'd like to test it before shipping it :)
* FN-F10 is not assigned (Zoom). I don't know which kind of program could be assigned here...
* FN-F12 is not assigned (Hibernate or Suspend). We should try /etc/acpi/sleepbtn.sh or /etc/acpi/hibernatebtn.sh
* S1 and S2 are not assigned but you can easily do it in the conf file

Remember that fsfn is a temporary and dirty fix :)

---

### Post by Tripmonkey_uk on 2008-04-19
Good call on the double startup Toufik. God knows how I ended up with two in there?

**/etc/acpi/sleepbtn.sh** works fine for FN+F12 too. I take it only shell scripts can be executed from the configuration file?

I was just reading up on the i810switch package a couple of days ago. I think someone got it working with that before, but I can't remember who it was :confused:

As we don't know when a native version will be included in Ubuntu, I think it could be a good idea to treat this as a decent fix and put a little more work into it Toufik. It certainly won't do any harm :)

---

### Post by geetarista on 2008-04-19
Thank you so much for this!  I've just gone without the FN keys for quite some time now since they stopped working.

Now everything works perfectly!  Sysinfo:

Sony Vaio VGN-FS980
Ubuntu Hardy Heron RC

Thanks again!!

---

### Post by Tripmonkey_uk on 2008-04-20
> **Toufik said:**
> 
* FN-F10 is not assigned (Zoom). I don't know which kind of program could be assigned here...


I was thinking about using that to toggle the desktop effects on and off. This would help save power when running on battery. Either that or using it for the Compiz zoom shortcut when desktop effects are already on. It kinda makes sense with the picture on the key (adding visual enhancements) :)

I tried setting the F10 key like this..
> F10_CMD=/usr/local/bin/compiz-switch
..after installing [Compiz Switch]("http://forlong.blogage.de/article/pages/Compiz-Switch") of course, but it doesn't seem to work :(

Any ideas?

---

### Post by Amorget on 2008-04-21
Any chance this will work on the AR series laptop?

---

### Post by traxtar3 on 2008-04-21
I would like to try this on a VGN-NR*** laptop but i am running 64-bit version of Gusty. Any chance you have a 64bit version of the deb built up?

Thanks in advance

---

### Post by Tripmonkey_uk on 2008-04-21
> **Amorget said:**
> Any chance this will work on the AR series laptop?

> **traxtar3 said:**
> I would like to try this on a VGN-NR*** laptop but i am running 64-bit version of Gusty. Any chance you have a 64bit version of the deb built up?

Thanks in advance

I'm not too sure if either of them models handle the FN keys the same as the FS series do. You guys ever try using [this]("http://ubuntufs.wordpress.com/2007/03/06/special-keys-tutorial-part-1/") tutorial before? I can't make any promises but it might work, or it could at least give you a better understanding of the problem.

I'd try the .deb file first though as that is easier to remove if it doesn't work :)

---

### Post by Amorget on 2008-04-21
Thanks, I'll give it a shot :)

I tried the tutorial, but as I remember I didn't fix anything.

---

### Post by Toufik on 2008-04-22
I don't have another model than the FS so I cant test but I would say it should work with any almost Vaio model. Requirements:
* kernel >= 2.6.22 (sony-laptop present)
* ```
$ ls /sys/class/backlight/sony
```
should say (at least):
```
brightness  actual_brightness
```
* ```
$ ls /sys/devices/platform/sony-laptop/
```
should say (at least):
```
brightness_default  fnkey
```

If you have all of this, it should work (at least partially)!

For the next version, there will be a 64bit package. You can still dowload and compile the sources (follow the instrucions in README and INSTALL).

Some news:
* when assigning a script to S1 and S2, the program is executed as root. I've got a dirty fix for this in the next release
* Ideally, the conf should be different for each user and should not be in /etc/ I'll see if I can do that without to much rewriting.
* I'd like to add some code to get a graphical way to assign the shortcuts. But I've never wrote any graphical interface :) So be patient or... help me :D

---

### Post by Tripmonkey_uk on 2008-04-22
Any idea why some scripts and programs aren't executed from the config file Toufik (not just for the S keys) ?

I had a look through the code last night to see if it was anything obvious, but I'm not a programmer and drew a complete blank. This is something that I've always wondered about though :confused:

EDIT: I did notice that the keys that seem hard to map, are the same ones that don't have any default programs associated with them in the source code. Anything to do with that?

---

### Post by Toufik on 2008-04-22
At fisrt sight, I would say the problem is because any program executed by FSFN is executed as root (but I've not tested). This can be easily fixed if there is only one user but this is more complex with more users as there is only one config file and because the daemon is run as root, I don't know how it could know which user actually pressed the keys! I've looked in btnx, which is a daemon which map all the buttons of your mouse. Their solution is to add a field containing the uid of the user for each program to execute. I've almost done it for fsfn, wait for the next release.

---

### Post by Amorget on 2008-04-22
* ```
$ ls /sys/devices/platform/sony-laptop/
```
Gave me:
```
brightness_default  bus  driver  modalias  power  subsystem  uevent
```

No fnkey.  However, this is before I've attempted an install of your stuff... should I be checking this after the install?

---

### Post by Toufik on 2008-04-22
No, if it isn't before, it won't be there after. This is created by the sony-laptop driver not by fsfn. Fsfn only reads this file. But you can still look for a "fnkey" file somewhere within /sys/. If you find one, tell me and I'll do something for you.

---

### Post by Tripmonkey_uk on 2008-04-22
Amorget, is your system information detected correctly if you enter the following in a terminal?..

> lshal | grep system.hardware

It might not give you the FN stuff unless your laptops completely detected as being a Sony one?? 

Mine gives me..

>  system.hardware.primary_video.product = 9618  (0x2592)  (int)
 system.hardware.primary_video.vendor = 32902  (0x8086)  (int)
 system.hardware.product = '**VGN-FS215E**'  (string)
 system.hardware.serial = '28195260-5601958'  (string)
 system.hardware.uuid = '**BE12D580-DF2D-11D4-83C6-00014A5F0457**'  (string)
 system.hardware.vendor = '**Sony Corporation**'  (string)
 system.hardware.version = 'C300C2EH'  (string)

With yours being a different model, maybe nobody's contributed a [**dsdt**]("http://ubuntufs.wordpress.com/2007/06/09/attention-all-vaio-owners/") file yet to help it get recognized?

Just a thought :)

---

### Post by rishiamrit on 2008-04-22
Is there a source code of FSFN ver 2 available ?. I got a 64 bit system installed so I cannot install the deb. I tried forcing it but then it say some library missing:

fsfn: error while loading shared libraries: libxosd.so.2: cannot open shared object file: No such file or directory

Bump !

---

### Post by Amorget on 2008-04-22
When I run:

> lshal | grep system.hardware

I get

>  system.hardware.product = 'VGN-AR670E'  (string)
  system.hardware.serial = '9633904-3000001'  (string)
  system.hardware.uuid = 'A4323940-7BA6-11DC-814F-001A801E548C'  (string)
  system.hardware.vendor = 'Sony Corporation'  (string)
  system.hardware.version = 'A2229ZUL'  (string)


So that means (I think) it is being recognized as a Sony laptop.

It may very well be nobody has submitted one... I didn't think I was so special that I would be the first, but I'll check that thread and if nobody has, I will.

---

### Post by Toufik on 2008-04-23
> **rishiamrit said:**
> Is there a source code of FSFN ver 2 available ?. I got a 64 bit system installed so I cannot install the deb. I tried forcing it but then it say some library missing:

fsfn: error while loading shared libraries: libxosd.so.2: cannot open shared object file: No such file or directory

Bump !

Yes, they are on the last line of the first post :) [http://www.fyma.ucl.ac.be/files/fsfn-2.0-1.tar.gz]("http://www.fyma.ucl.ac.be/files/fsfn-2.0-1.tar.gz")

If you install by and, look at the README and at the INSTALL files. You need to install some stuff:
```
$ sudo apt-get install libxosd-dev libxosd2
```


For the next release (fixing S1, S2 and others), I've made some modifications: it works but not after a boot :( I have to start fsfn by hand after login into X... Still investigating

---

### Post by Tripmonkey_uk on 2008-04-23
I have a spare hard drive if you need a Beta tester Toufik.
Thanks for still working on it by the way :)

@Amorget - Even if someone has already submitted the same model laptop, it could be that they are using a different bios which can alter the way that the laptop handles power etc.. Best for them to get as many as they can I think :)

---

### Post by Amorget on 2008-04-23
> **Tripmonkey_uk said:**
> 

@Amorget - Even if someone has already submitted the same model laptop, it could be that they are using a different bios which can alter the way that the laptop handles power etc.. Best for them to get as many as they can I think :)

I submitted mine as it doesn't seem there are too many AR owners out there (I can understand why... their design is HORRIBLE).  Figured the more the merrier, like you said :)

---

### Post by rishiamrit on 2008-04-24
> **Toufik said:**
> Yes, they are on the last line of the first post :) [http://www.fyma.ucl.ac.be/files/fsfn-2.0-1.tar.gz]("http://www.fyma.ucl.ac.be/files/fsfn-2.0-1.tar.gz")

If you install by and, look at the README and at the INSTALL files. You need to install some stuff:
```
$ sudo apt-get install libxosd-dev libxosd2
```


Thanks. In the readme file it says:
If your kernel is older, you may try FSFN but check ** before ** that these files are present:

ls /sys/class/backlight/sony

You should see (at least)

        brightness  actual_brightness

ls /sys/devices/platform/sony-laptop/

You should see (at least)

        brightness_default  fnkey

I do not have a sony folder in the backligh folder.
Also, I do have the second folder, but does not contain files with names "brightness_default" and "fnkey"

Any ideas what to do ?

Rishi

---

### Post by Toufik on 2008-04-24
What is the answer of ?
```
$ lsmod | grep sony
```
You should get "sony_laptop"

---

### Post by benhur99ph on 2008-04-25
Uh... I installed the .deb package but it didn't work. 
For now I adjust the brightness and volume by using the panel applets.

How do you get the monitor switch function to work. I somethimes need to connect my laptop to a projector for presentations. 

I use a Sony Vaio FS940 laptop. 
Does anyone here use the same model? If you do and have made the Fn keys work, please pm me. I've had problems with my Fn keys ever since Feisty. That's what keeping me from removing my windows partition.

Thanks!

---

### Post by Toufik on 2008-04-25
I've updated the first post, could you post all the debugging informations mentioned there.
Thanks

---

### Post by rishiamrit on 2008-04-25
> **Toufik said:**
> What is the answer of ?
```
$ lsmod | grep sony
```
You should get "sony_laptop"

I do have that

sony_laptop            40624  0 

But FSFN still doesnt turn my FN keys on. Here r the contents of my /sys/devices/platform/sony-laptop/

driver  modalias  power  subsystem  uevent

See, there is no brightness :(

---

### Post by rmnboss on 2008-04-26
your tool works partially on a "sony vaio vgn fs-315m", except for the s-buttons and the hibernate-button (fn+f12) and only after adding "fsfn -o" manually to the sessions manager (i don't know if that should be like this or not).

---

### Post by hsiehinator on 2008-04-26
Hey...the fn keys still not workin for me, heres all the info u requested


$ lshal | grep system.hardware
  system.hardware.primary_video.product = 359  (0x167)  (int)
  system.hardware.primary_video.vendor = 4318  (0x10de)  (int)
  system.hardware.product = 'VGN-FS675P_H'  (string)
  system.hardware.serial = '28198236-3499999'  (string)
  system.hardware.uuid = 'C10DC600-DF2D-11D4-83D6-00014A5D7054'  (string)
  system.hardware.vendor = 'Sony Corporation'  (string)
  system.hardware.version = '01'  (string)
$ 
$ lsmod |grep sony
sonypi                 22408  0 
sony_laptop            34512  0 
$ 
$ ls /sys/class/backlight/sony
actual_brightness  brightness      power      uevent
bl_power           max_brightness  subsystem
$ 
$ ls /sys/devices/platform/sony-laptop/
brightness_default  driver  fnkey  modalias  power  subsystem  uevent
$ 
$ cat /sys/devices/platform/sony-laptop/fnkey
0
$ cat /sys/devices/platform/sony-laptop/fnkey
0
$ cat /sys/devices/platform/sony-laptop/fnkey
0


What i see doesn't match up is the output of lsmod|grep sony... but i dont know how to fix that.  Also the last fn key tests are w/ fn+f2,f3,f4 respectively, so that doesn't work as well.  Thanks for all the help

---

### Post by Toufik on 2008-04-27
@rishiamrit : could you please post the debugging informations as explained in the first post

@rmnboss : this is completely normal :) fn12 and S1-2 will be functionnal in the next release which is currently being tested. fsfn -o is a matter of choice  so if you want it you have to put add it manually.

@hsiehinator: strange... it should work... what is your kernel? ($ uname -a)

---

### Post by Tripmonkey_uk on 2008-04-27
Just to let people know..

If you plan on using desktop effects, the on screen display won't work with Compiz so you don't need to bother adding fsfn -o to your startup :)

@Toufik - Got a clean install on the spare HD. Tested that version, but got the same results.

---

### Post by Veio on 2008-04-28
Any idea how to do it for CR computers?

Here is the info you asked:


$ uname -r
2.6.24-16-generic

$ lshal | grep system.hardware
  system.hardware.primary_video.product = 10754  (0x2a02)  (int)
  system.hardware.primary_video.vendor = 32902  (0x8086)  (int)
  system.hardware.product = 'VGN-CR160A'  (string)
  system.hardware.serial = '28205449-3000071'  (string)
  system.hardware.uuid = '72418B40-A184-11DB-8BB5-0013A9F0ED64'  (string)
  system.hardware.vendor = 'Sony Corporation'  (string)
  system.hardware.version = 'C1018Y44'  (string)

$lsmod | grep sony
sonypi                 23192  0 
sony_laptop            35292  0 

$ ls /sys/class/backlight/sony
actual_brightness  brightness      power      uevent
bl_power           max_brightness  subsystem

$ ls /sys/devices/platform/sony-laptop/
driver  modalias  power  subsystem  uevent


Thanks,

         Veio

---

### Post by happysubby on 2008-04-28
thank you. it worked for me

Sony FS640/W
Ubuntu 8.04 Hardy Heron..

---

### Post by Toufik on 2008-04-28
@Veio: Sorry, this is a "patch" for the sony-laptop driver designed for the FS serie. It won't work for other model.

@Tripmonkey_uk: weird, weird, weird...

---

### Post by hsiehinator on 2008-04-28
Sorry... but i was being kinda stupid.... the sound fn keys work, it just changes "front" not master so i didnt see it change with no OSD as well.  However the brightness does not work, even with the brightness applet... non fn key problem? any suggestions to have the osd working w/ compiz? thanks for all the help and sorry for not being smarter. 

found the conf file
any reason this isnt working?
"S1_CMD=/usr/bin/firefox-3.0"

and im using
2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

---

### Post by Tripmonkey_uk on 2008-04-29
> **Toufik said:**
> @Tripmonkey_uk: weird, weird, weird...

_Maybe_ one of the other programs is interfering during boot? Have u tried changing the boot order and making sure it's one of the last things to boot up?

p.s I got them working with the command in the terminal and tried to save the session in Gnomes session manager hoping that might do it, but that had no effect either.

---

### Post by Cris(c) on 2008-04-29
Same situation as hsiehinator here. The volume fn keys work alright but the brightness don't. Here is the info of my laptop:

 system.hardware.primary_video.product = 10146  (0x27a2)  (int)
  system.hardware.primary_video.vendor = 32902  (0x8086)  (int)
  system.hardware.product = 'VGN-C240E'  (string)
  system.hardware.serial = '28249431-3003426'  (string)
  system.hardware.uuid = 'A6B0C940-95E5-11DB-81B5-0013A9A37708'  (string)
  system.hardware.vendor = 'Sony Corporation'  (string)
  system.hardware.version = 'C3LN8HFU'  (string)

I am using Heron (kernel 2.6.24-16 though I've experienced some other problems with this kernel...2.6.24-14 works better but keys don't work with this kernel either). Any suggestion/hint in how to proceed?

---

### Post by Mr_B on 2008-04-29
Thanks for the info. However, it did not work on my VAIO VGN-C140G. How can I uninstall the [http://www.fyma.ucl.ac.be/files/fsfn_2.0-1_i386.deb](http://www.fyma.ucl.ac.be/files/fsfn_2.0-1_i386.deb) package since it did not work? I apologize if this is a trivial question, but I just dropped Vista for Hardy yesterday :-)

Thanks

---

### Post by l2oi3 on 2008-04-29
Vaio VGN-FS8900 Here, worked beautifully. Getting the other fn keys to do something sounds sweet.

Two quick questions for you other vaio users; what video driver are you using to get compiz to work? Have any of you managed to get suspend and hibernate working?

---

### Post by Tripmonkey_uk on 2008-04-29
> **Mr_B said:**
> Thanks for the info. However, it did not work on my VAIO VGN-C140G. How can I uninstall the [http://www.fyma.ucl.ac.be/files/fsfn_2.0-1_i386.deb](http://www.fyma.ucl.ac.be/files/fsfn_2.0-1_i386.deb) package since it did not work? I apologize if this is a trivial question, but I just dropped Vista for Hardy yesterday :-)

Thanks

Easy, just go into the **System** menu, then into the **Administration** sub-menu and choose **Synaptic Package Manager**.
Enter your password and search for **fsfn** in the Synaptic program.
**Right click** the little green box next to the fsfn program from the results and choose **Mark for complete removal**.
Click on the **Apply** button and it will do all the hard work for you :D

We all had to start somewhere, hope u enjoy it :)

> **l2oi3 said:**
> Vaio VGN-FS8900 Here, worked beautifully. Getting the other fn keys to do something sounds sweet.

Two quick questions for you other vaio users; what video driver are you using to get compiz to work? Have any of you managed to get suspend and hibernate working?

Suspend and Hibernate both work on my VGN-FS215E laptop perfectly and Compiz is working with my Intel graphics.

Compiz won't work with the open Nvidia driver I'm afraid, try the closed source one. ATI? couldn't tell you sorry.

Take a look at the tutorials on [Forlong's Blog]("http://forlong.blogage.de/") if your having trouble. The sites pretty much dedicated to getting Compiz working.

Good luck all :)

---

### Post by Toufik on 2008-04-30
I've released a new deb (fsfn V2.1). The main difference is the ability to choose the user id before launching a program. For instance, if you want S2 to launch firefox, add this in /etc/fsfn.conf (this is already there by default):
S2_CMD=/usr/bin/firefox

In the previous version, firefox was launched as root user. That might be dangerous! Now you have a new parameter:
S2_CMD_UID=1000

The number you write (1000 here) is the user ID: 0 for root, 1000 for the default first user in Ubuntu (probably yours). To know your ID: ```
$ echo $UID
```

**known bug**
* brightness and volume worked great
* other fn keys doesn't work after a fresh boot. You need to start the deamon again before it work :(
Restarting the daemon:
```
$ sudo /etc/init.d/fsfn restart
```
* if someone knows why and/or a way to solve this, let me know...


About hibernation and suspend: it worked better with gutsy than with hardy :( (but it works)

Compiz is great with i810 integrated

---

### Post by Toufik on 2008-04-30
> **Tripmonkey_uk said:**
> _Maybe_ one of the other programs is interfering during boot? Have u tried changing the boot order and making sure it's one of the last things to boot up?

Yes, I changed the order, fsfn is the last thing to load. I've got the feeling that the problem is because when it loads, there is still no X and therefore fsfn was initialized with an empty $DISPLAY variable. I'll try to look deeper in that direction... (adding a display "by hand")

---

### Post by dontcopymusic on 2008-04-30
Thanks, my FN keys work great!

But I was wondering, is there a way to replace the osd that comes with fsfn, with the volume/brightness osd used in gnome/compiz (I'm not sure)?
Is there a way to link the gnome osd for volume/brightness to the fn keys?

---

### Post by Tripmonkey_uk on 2008-05-01
> **dontcopymusic said:**
> Thanks, my FN keys work great!

But I was wondering, is there a way to replace the osd that comes with fsfn, with the volume/brightness osd used in gnome/compiz (I'm not sure)?
Is there a way to link the gnome osd for volume/brightness to the fn keys?

I'm looking into this too, but I haven't managed to find anything yet. I'll let you know if I do :)

---

### Post by DJSmidge on 2008-05-03
Thanks for this, my brightness settings now work perfectly. The audio settings don't matter as my sound card has died.

My laptop is the VGN-FS215B

---

### Post by smel on 2008-05-06
thx very much
it works graet on my sony vaio vgn -fs 415 s

e.s

---

### Post by hihihi on 2008-05-07
hello,
i am an unlucky FZ guy. (fz 31 m / ubuntu hardy 64)
nothing seems to work regardin fn keys.
i tried all.including your fsfn 2.1., cause i am running 64bit, so the deb wont install.
but nothing at all happened...
i also tried installing sony_acpi, but than the three files under /proc/bla/bla wont appear...
i want to cry...
snif
snif
(tears)
is there a secret link to a cia site with a solution, or sony.corp. super secret linklinklink?
no?
yes?
perhaps?
antway, thaks for your community-help,
i appreciate it...

---

### Post by dontcopymusic on 2008-05-07
> **hihihi said:**
> (...)
i also tried installing sony_acpi, but than the three files under /proc/bla/bla wont appear...
(...)

Before these appear it is necessary to reboot your machine. Hope it helps!

---

### Post by hihihi on 2008-05-11
> **dontcopymusic said:**
> Before these appear it is necessary to reboot your machine. Hope it helps!

noo, unfortunately not, after reboot no files...
i guess this FZ-problem goes deeper, must be a mix of new kernel,
new priorety-hardware, and some other for me abstract stuff...

---

### Post by tidalwav1 on 2008-05-17
Finally, working FN keys for my FS690P.

I'm running Ubuntu Hardy, and everything works great. The OSD even displays properly with Compiz enabled.

Thanks so much!

EDIT: This thread should really be taken out of the 'archive' section of these forums.

---

### Post by pihhan on 2008-05-27
Would you reveal please what instructions have you used to get OSD display with brightness? I have working pretty much on my vaio, but i dont see any support of gnome for my display backlight support, yet it is X extension and gnome should be able to see what brightness i have or change it like xbacklight utility can. I can see popup for volume up and down, but not for brightness. Can you tell me what program is used for OSD? I can hack it myself if i know that at least.

---

### Post by dontcopymusic on 2008-05-27
@pihhan: How did you get the gnome OSD for your volume to work? I'm sure many would like to know :)

Another question:
My mini-jack socket has broken, so I had to buy an external usb sound card. Everything works fine, but how do I get the FN-keys working with my usb sound card? I managed to get the gnome-volume-applet working with it by selecting *Playback: ALSA PCM on front:0 (USB Audio) - Master* in the preferences menu. Anyone got an idea how to link the FN-keys to this?
By the way, my onboard sound card is blacklisted so it would not interfere with the usb one.

Thanks!

---

### Post by Channon on 2008-05-28
The file worked for Hardy on a VGN-FS810/W for the mute, volume, and brightness controls.

I'm also interested in finding a way to tie the fn controls to the Compize OSD instead of fsfn OSD

THANKS!

---

### Post by pihhan on 2008-05-28
In my Vaio FZ210 multimedia keys are connected directly to keyboard and they does generate keypresses with right multimedia symbols itself. Nothing was needed for that, it worked out of box in gutsy and does work in hardy also. If i run xev command, i get XF86Play and such keys when pressed multimedia keys. Ubuntu has these keys predefined and it did show volume OSD on vol + key itself. Nothing needed on my side. Interesting is mute (fn+f2) only worked from FN keys when sony-laptop havent worked for FZ yet. If you see some events in xev, you should be able to map it in shortcuts menu. If you do not, you cannot map it easily. You can map it to acpi scripts, but then you propably wont have any OSD, as ACPI does not have access to X screen. For me, xev does not report any other key but FN+F2.

---

### Post by Toufik on 2008-05-28
Wow, so many questions :)

@pihhan: 
* my OSD worked correctly after following instructions on the first post
* the library used for OSD is libxosd2 (libxosd-dev for the sources)
* the sony-laptop driver for FS series is buggy. A keypress is detected and written to a file but it fails to be forwarded to the X and the ACPI. Therefore xev shows nothing! And you cannot map anything :( That's the reason of being of this daemon: do the job of the acpi by reading the file with the keypress code.

@dontcopymusic:
* have a look at this file: /etc/fsfn.conf
```
gksudo gedit /etc/fsfn.conf
```
You should see :
```
ALSA_NAME=Front
#ALSA_NAME=Master
#ALSA_NAME=PCM
```
the # start a commented line. So what you have to do for your problem is:
```
#ALSA_NAME=Front
ALSA_NAME=Master
#ALSA_NAME=PCM
```

@Channon
* Do you know which library is used in compiz OSD? I can have a look...

---

### Post by Channon on 2008-05-28
> @Channon
* Do you know which library is used in compiz OSD? I can have a look...

I'm not sure - some quick googling suggests that its a gnome thing, not a compiz thing.  Before the fn key fix, I had just assigned volume control to a hotkey combination (something like Shift+F3). It worked OK, and gave the nice rounded-corner OSD showing a little speaker and the volume slider.

So right now, I can get both flavors of OSD: the fn key version (FN+F3, etc) and the gnome/compiz(?) version (Shift+F3).  I should note that, in Hardy, the FN key approach seems to be much more effective than the hotkey approach (I couldn't get much sound out of the laptop speakers before the fn fix).

I'll try to fiddle with it tonight and see if I can locate whatever library it's tapping...

Thanks-

---

### Post by elfuegodiego on 2008-05-28
Hi,

Just tested on a vgn fs315e running hardy and everything works including the osd.

Thanks for writing this!

---

### Post by Oztafan on 2008-06-01
Hi Toufik

Excellent!!! Your FSFN script (fsfn_2.1-1_i386.deb) works out-of-the-box on my old Sony Vaio VGN-FS195VP (a swiss model bought about three years ago) together with Hardy Heron. Nice on-screen display for volume and brightness, too. I sincerely hope that it will continue to work even after the next major Hardy updates. 

Keep up the good work! André Barmasse

---

### Post by pihhan on 2008-06-18
Hello, 

i made some guide to get FN keys and other stuff working on recent Sony Vaio laptops. I would be grateful and check it. If you find any hard to understand or even advices that are not true, please let me know. If you find grammar mistakes and such, you might also write me. 

So, guide is at [http://www.pihhan.info/sony/sony-hotkeys.html](http://www.pihhan.info/sony/sony-hotkeys.html)

Edit: ok, sorry i made a mistake. This guide will work for most vaios but FS series needs different aproach. This wont work for polling only hotkeys.

---

### Post by Toufik on 2008-06-19
I tried that a few month ago, it fails because FS* series do not report acpi event... (bug in sony-laptop). But I'll have a look following your guide. But pleeeeaaaase do NOT use .png format for picture!! And pleeeaaaase, resize them to something acceptable! It takes ages to load...

A quick way to do it: imagemagick
```
sudo apt-get install imagemagick
```
and then to convert xxx.png to yyy.jpg (or whatever extension you want: .bmp, .eps, .pdf,...) and resize to 400 pixel horizontally (vertically: keep aspect ratio)
```
convert -resize 400 xxx.png yyy.jpg
```

---

### Post by trelirodia on 2008-06-24
Hi, 

This is such a great fix! Everything works great on my laptop (running Hardy on VGN-FS195XP). Thanks a million.

Have you made any progress in making the F7 key work to switch between displays? 

Much obliged :-)
M

---

### Post by pihhan on 2008-06-24
geez, thank you. I haven't realized how big they are, i have that server on fast local network and i haven't looked on its size.

I looked at the fsfn daemon and i see there one problem. Does it not report really any event on keypress of hotkey? It might be alway the same event, code to get scancode is known. Have you tried loading sony-laptop with debug=1 option, and checking if on keypress it complains about uknown event or something in kernel log? It is strange if it needed polling on laptop, where you want save power.

---

