---
title: "vid issues after update"
date: 2010-02-17
forum: Hardware
---

### Post by papahonk on 2010-02-17
i normally dont use my netbook much at home, acer Aspire One 751h with the polsbo sp? chip. but i let it upload the update  and it asked to restart i i justturned it off and went to class when i turned it on i got this 

(EE) PSB(0): the stolenBase is:0x7f800000:
(EE) PSB(0): screnindex is: 0;fbPhys is :0x7f800000; fbsizeis:0x007bf000
(EE) PSB(0): first SDVO output reported failure to sync or input isnot trainded!!!
(EE) [drm] drmOpen failed.
(EE) PSB(0): [dri] DRIScreenlnit failed. Disabling DRI.
(EE) [drm] Could not uninstall irq handler.
(EE) PSB(0): This driver currently needs DRM to operate.


 does anyone know of a way to fix this? im running now in low res   but i want it back to normal. 

will i have to go and reresearch how to work around that dang polsbo vid chip agian and start over or can i uninstall all the updates? 

thanks for any help

---

### Post by papahonk on 2010-02-17
when starting  computer  it gives you the option to review Start up errors and this is what i got

Fatal server error:
Server is already active for display 0
        If this is no longer running, remove /tmp/.XO-lock and start agian


Please consult the The X.Org Foundation support 
         at [http://wiki.x.org](http://wiki.x.org)
for help

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: bad file descriptor
ddxSigGiveUp: Closing log

review xfile log

---

### Post by papahonk on 2010-02-18
ok following the site

[http://wiki.x.org/wiki/FAQErrorMessages#Ikeepgettingthemessage.3A.22Serverisalreadyactivefordisplay0.22](http://wiki.x.org/wiki/FAQErrorMessages#Ikeepgettingthemessage.3A.22Serverisalreadyactivefordisplay0.22)


and i get this so i have one running but it wont let me add another  like it says to 

mike@mike-laptop:~$ ps aux | grep `cat /tmp/.X0-lock`
root      1537  0.8  0.4  16700 10012 tty7     S<s+ 06:15   0:02 /usr/bin/X :0 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log
mike      1979  0.0  0.0   3044   868 pts/0    S+   06:21   0:00 grep --color=auto 1537
mike@mike-laptop:~$/

---

