---
title: "AMD 7690m gpu and Ubuntu 12.04"
date: 2012-06-01
forum: Hardware
---

### Post by rolltide101x on 2012-06-01
Installing the drivers via the repository does not work after the reboot it sends me to Unity 2D and will not load "regular" Unity period until I unload the driver. I attempted to load the CCC drivers manually I successfully installed CCC but the gpu is not working. Does anyone have any suggestions? Thanks for your time!

---

### Post by rolltide101x on 2012-06-01
anyone?

---

### Post by rolltide101x on 2012-06-02
No one has a suggestion?

---

### Post by Redblade20XX on 2012-06-02
What do you mean the gpu isn't working?
Take a look here : [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

-Red

---

### Post by rolltide101x on 2012-06-02
If I install the drivers supplied by "Additional Drivers" Ubuntu will boot into Ubuntu 2D and will not boot into Ubuntu 3D until I uninstall the driver supplied. If I uninstall the driver Unity 3D begins to work again.

I have googled the issue with no luck and wanted someone more experienced than me to help me.

---

### Post by mastablasta on 2012-06-03
try installing them manually and don't forget to initialise them after install.

---

### Post by QIII on 2012-06-03
See the link in my signature.

For some people the "additional drivers" method does not work well.

---

### Post by rolltide101x on 2012-06-03
I did this listed here
[http://ubuntuforums.org/showthread.php?t=1982640](http://ubuntuforums.org/showthread.php?t=1982640)

and I get this for the command

[B]sudo vainfo

libva: VA-API version 0.32.0[/B] [B]
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/i386-linux-gnu/dri/i965_drv_video.so
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
clate@ubuntu:~$ [/B]

CCC appears to be working correctly though. I checked if my gpu was mentioned under "Details" but it isnt listed

---

### Post by rolltide101x on 2012-06-03
CCC sees my gpu as a 7670m not a 7690m any help? Is that even an issue?

---

### Post by rolltide101x on 2012-06-05
Any more help?

---

### Post by QIII on 2012-06-05
The acceleration is probably a simple matter.

Let's look at your GPU first.

Do 

```
aticonfig --od-getclocks
```

and post the results.  This will tell us the engine clock speed.  The 7690M runs at 900MHz, the 7670M at 800MHz.

(I don't remember off hand if you need to use sudo for that.)

---

### Post by rolltide101x on 2012-06-05
Thank you for your help and giving me a start
[B]


clate@ubuntu:~$ aticonfig --od-getclocks

Default Adapter - AMD Radeon HD 7670M
                            Core (MHz)    Memory (MHz)
           Current Clocks :    100           150
             Current Peak :    725           900
  Configurable Peak Range : [400-725]     [900-900]
                 GPU load :    22%
clate@ubuntu:~$ [/B]

My laptop

[http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/catalog.workflow:category.details?current-catalog-id=12F0696583E04D86B9B79B0FEC01C087&current-category-id=7794F9514CE80460C7C2782FB02A5EB6&action=init](http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/catalog.workflow:category.details?current-catalog-id=12F0696583E04D86B9B79B0FEC01C087&current-category-id=7794F9514CE80460C7C2782FB02A5EB6&action=init)


its the $1,079.00 one

---

### Post by QIII on 2012-06-05
Looks like name/model misidentification only, since the engine clock is correctly detected ad 725 and memory as 900MHz per spec.  (I had that bass-backwards in my previous post.)

---

### Post by rolltide101x on 2012-06-05
Should it be working properly now even with the errors mentioned prior? 

[B]sudo vainfo

libva: VA-API version 0.32.0[/B] [B]
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/i386-linux-gnu/dri/i965_drv_video.so
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
clate@ubuntu:~$ 


[/B]I have not managed to get anything but C&C Tiberium Sun working under wine yet and it will work fine with the integrated graphics my PC has. If you think the primary gpu is working correctly now I can start trying to get Oblivion to work to properly test it[B].
[/B]

---

### Post by QIII on 2012-06-05
Try un-installing the four acceleration packages (sudo apt-get remove -- purge ...) and reinstalling.  If that doesn't work, we may have to manufacture a symlink for the .so

---

### Post by rolltide101x on 2012-06-05
I have done it 3 times already (on fresh installs) but I will give it one more shot.

---

### Post by QIII on 2012-06-05
OK.  If it doesn't work, we'll walk through making a symlink.

---

### Post by rolltide101x on 2012-06-05
Still not working. What do I need to do?

---

### Post by rolltide101x on 2012-06-06
Thanks for your help so far!

---

### Post by rolltide101x on 2012-06-06
I still need help with the symlink. Thanks

---

### Post by ysNoi on 2012-06-07
Hi rolltide101x...

You may want to try the link below...

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

HTH...

---

### Post by rolltide101x on 2012-06-07
> **ysNoi said:**
> Hi rolltide101x...

You may want to try the link below...

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

HTH...


Thanks but I had tried that before I posted this.

---

### Post by ysNoi on 2012-06-07
I have also AMD 7450M but I haven't yet tried.

I am waiting for other member to answer my question on lspci  | grep VGA test...

I wonder why it appears that my card is HD 6400M instead of HD 7450M.

On hardware compatibility list, it also appears that our cards are not yet supported (please correct me if I'm wrong)

[http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)

---

### Post by QIII on 2012-06-07
@rolltide:

The symlink isn't something I want to talk through off the top of my head from memory and I haven't been near my notes fore a couple of days.  I'll try to get back to you tonight.

I roll back through my posts periodically when someone hasn't gotten a problem resolved, so I know you are still waiting on this.

---

### Post by rolltide101x on 2012-06-07
> **QIII said:**
> @rolltide:

The symlink isn't something I want to talk through off the top of my head from memory and I haven't been near my notes fore a couple of days.  I'll try to get back to you tonight.

I roll back through my posts periodically when someone hasn't gotten a problem resolved, so I know you are still waiting on this.


Thanks, it is no rush I just thought you forgot about me lol

---

### Post by QIII on 2012-06-07
A symlink itself is trivial to construct.  I need to look at my notes to find out where the target file should be located.  It's not where vainfo expects it right now.

---

### Post by QIII on 2012-06-08
OK.  I'm back.

Reviewing your post about the error you are getting with regard to acceleration:

Does your machine have switchable hybrid graphics?  That is, do you have both an ATI GPU and an Intel GPU?

---

### Post by rolltide101x on 2012-06-09
Yes, the Intel graphics appears to work fine

---

### Post by QIII on 2012-06-09
I realized you had hybrid graphics when I saw the i965 .so file when I reviewed the thread.

Are you able to switch back and forth between the two cards, the Intel and the ATI?

---

### Post by rolltide101x on 2012-06-09
On Windows yes, I am not sure how on Linux. I assumed the AMD gpu was not working yet because of the errors so I have not really tried to switch

---

### Post by QIII on 2012-06-09
Please check [this](http://ubuntuforums.org/showthread.php?t=1930450) out and see if you can get the switching to work.

---

### Post by rolltide101x on 2012-06-09
When I try that[B]

clate@ubuntu:~$ sudo aticonfig --initial -f
[sudo] password for clate: 
aticonfig: No supported adapters detected
clate@ubuntu:~$ sudo aticonfig --px-dgpu
aticonfig: No supported adapters detected
clate@ubuntu:~$ 
[/B]
Should I run this command?

**sudo apt-get install xvba-va-driver libva-glx1 libva-egl1  vainfo**

They are uninstalled right now.  They were installed earlier though

---

### Post by QIII on 2012-06-09
No, don't work on the acceleration because it won't work without the ATI driver working.  The instructions are specifically for the ATI driver.

Did you leave a post in that thread?

---

### Post by rolltide101x on 2012-06-09
No, I guess I should?

---

