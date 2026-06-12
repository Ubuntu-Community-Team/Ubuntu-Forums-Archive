---
title: "Mouse pointer lags while laptop charging"
date: 2012-02-23
forum: Hardware
---

### Post by ncjones on 2012-02-23
When my laptop is charging (the power cable is connected and the battery is below 100%) the computer is reduced in responsiveness. The reduced responsiveness is especially noticeable with the mouse pointer (using both track pad and external wireless/USB mouse) which becomes so laggy as to render it unusable.

These symptoms are not present when using Windows 7 on the same hardware with the same battery/charging state.

While the laptop is charging I also notice a couple of the "kworker" processes shoot up to around 20% CPU usage each and a third at around 4%. No other processes appear to be using any CPU.

I found other reports of issues with laggy mouse pointers and rogue kworker processes but none that linked this to the battery charging state.

The workaround for this is simple - always have the power connected so the battery is always at 100% - but it would be nice to know if there is a proper fix.

Laptop model: Dell Latitude E5420
Linux kernel: 3.0.0-15-generic (64 bit)

---

### Post by elyawm on 2012-03-09
I have the same laptop (DELL Latitude E5420 i5-2520M) and the same problem. When charging, only using Ubuntu 11.10 (32-bit) (the problem is not present using Windows 7 Pro 64-bit), the mouse pointer is too slow (when using the touchpad or my microsoft mouse (wireless mobile mouse 6000)). The problem is not present if the battery is not charging.

(I'm always updating Ubuntu to the latest version and the problem still exist if charging)

---

### Post by LadyBlub on 2012-03-15
I am having the same problem and it is really annoying.

I have also a Windows 7 installation were there is no problem with the mouse, but I encountered another problem while charging. When I watch TV with a DVB-T stick the video signal starts lagging while charging. Audio is fine. When I stop charging the video runs normal again. 

Any suggestions would be great!

---

### Post by chicken159 on 2012-03-17
I have a new dual-boot E5420 and it has the same issue - anyone find any solutions?

---

### Post by chicken159 on 2012-03-17
Having googled and seasrched the forums...here is the solution:

Adding the following line in /etc/modprobe.d/local.conf

options drm_kms_helper poll=N     

Then restart. If you wnat to check it works first...just do this:

echo N> /sys/module/drm_kms_helper/parameters/poll

---

### Post by mnemonical on 2012-03-17
> **chicken159 said:**
> Having googled and seasrched the forums...here is the solution:

Adding the following line in /etc/modprobe.d/local.conf

options drm_kms_helper poll=N     adding the following line in /etc/modprobe.d/local.conf:

options drm_kms_helper poll=N 

Then restart. If you wnat to check it works first...just do this:

echo N> /sys/module/drm_kms_helper/parameters/poll

Worked for me, except I didn't have local.conf on my system. I edited alsa-base.conf to include the line above, and it worked fine. the file is in a read only, so to avoid all the fun permissions, you can use 

gksudo gedit /etc/modprobe.d/alsa-base.conf

to edit it.  Just copy and paste to terminal.

---

### Post by chicken159 on 2012-03-19
Yeah - I didn't have that file either, but creating it with that line in it did the trick ;)

---

### Post by LadyBlub on 2012-03-19
Thanks chicken159! Worked for me too.

---

### Post by alibanna on 2012-09-05
> **chicken159 said:**
> Having googled and seasrched the forums...here is the solution:

Adding the following line in /etc/modprobe.d/local.conf

options drm_kms_helper poll=N     

Then restart. If you wnat to check it works first...just do this:

echo N> /sys/module/drm_kms_helper/parameters/poll

I'm sorry but I'm not a very bright computer guy but I've had this problem for a while so here's my question ---> What do add and where do I add it? An explanation would be very helpful. 

Thank you

---

### Post by bongbong on 2012-09-06
Hi,

I am using Ubuntu 12.04 in a  Desktop PC. In my mouse, the right click and scroll button not working. 

Please help.

---

### Post by asohal on 2013-02-05
Same here. I have the same exact model of laptop, it is a Dell Latitude, E5420. Every time I plug in my Laptop Charger, the mouse and display lags. I know there was a solution mentioned above, asking to add a specific file on the local.conf. I dont see that file/directory when I do ls under /etc/modprobe.d

Do I have to create this file? If I do need to create it, i get into a little problem. I go vi /etc/modprobe.d/local.conf. This warns me that this is a new file. But when I paste the line: options drm_kms_helper poll=N, it wouldn't take the whole line, am I missing something? 

Any other solutions?

---

### Post by bruceherrera on 2013-02-14
> **chicken159 said:**
> Having googled and seasrched the forums...here is the solution:

Adding the following line in /etc/modprobe.d/local.conf

options drm_kms_helper poll=N     

Then restart. If you wnat to check it works first...just do this:

echo N> /sys/module/drm_kms_helper/parameters/poll

> **mnemonical said:**
> Worked for me, except I didn't have local.conf on my system. I edited alsa-base.conf to include the line above, and it worked fine. the file is in a read only, so to avoid all the fun permissions, you can use 

gksudo gedit /etc/modprobe.d/alsa-base.conf

to edit it.  Just copy and paste to terminal.




Thanks a lot!!!

I've been dealing with this mouse lag in my laptop for some months. I was starting to believe that my PC wasn't working well.-

Cheers. I'll be using it for another years to come :)

---

