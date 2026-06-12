---
title: "Problems + USB Mouse freeze prob"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by yes9111 on 2007-07-11
HI..
I installed Ubuntu (feisty / 7.04)  just today (Go me >.<)
and my mouse started freezing usually 2 minutes to 5 minutes after turning on.

Had to press TAB like mad when this happened to click on links -_-;;
Is there any fix for this problem?
If you need some files posted, just tell me =(  
And, I'm dualbooting on this computer with Windows XP and the mouse works fine on XP.

My two, less important questions are -
for feisty, is there a way to increase your screen resolution to anything larger than 800X600?  I have a 19 inch computer so everything looks really big -_-
And the Numpad doesn't seem to work (whether numlock is on or not) ..
Any solutions there?

THANKS

P>S> 
I have a Dell computer dimension E521.
and am using the black ball mouse that came with it...

P.S.2 
I tried adding the "noqpic irqpoll" at the end of the kernel line at the GRUB menu but it didn't solve it.

BUMP HELP PLEASE

---

### Post by yes9111 on 2007-07-12
Bump 

Anyone plz help?

---

### Post by Riyonuk on 2007-09-29
I'm having the same problems buddy, have you fixed it yet?

---

### Post by leffler on 2007-10-01
I've got the same computer, same problems.  No luck yet on the mouse-freeze.  it's pretty much a show-stopper until I can find a fix.  Anyone else have success?

I've tried adding noacpi to the boot options in the grub setup menu, without luck.  I also saw a suggestion for acpi=force irqpoll, but I'm not sure I applied it correctly.  Will try it again later.

Screen resolution is easy if you've got  Nvidia graphics : Use Automatix (will need to install) to grab and install the Nvidia drivers.  Then reboot ... you should get a Nvidia option under  Applications|System.

Use this to reset to your fav resolution.  Note : you need to both Apply the new settings and save the xorg.conf file to somewhere besides /etc/X11/xorg.conf.  Then copy it to /etc/x11 

sudo cp /etc/x11/xorg.conf /etc/x11/xorg.conf.backup
sudo cp /home/you/xorg.conf /etc/x11/xorg.conf

Restore the backup if this causes video grief.

---

### Post by Riyonuk on 2007-10-01
Well for me, the bluetooth usb needs to be re-inserted for me to even get past the login screen. I cant wait to this fixes, so I can actually enjoy Ubuntu >.>

---

### Post by leffler on 2007-10-01
OK, I think I have some success with the acpi=force irqpoll  setting.  To make the change, edit your  /boot/grub/menu.lst :

sudo gedit /boot/grub/menu.lst

The line that begins 

#kopt=root       is where I put the option:  My line is :

# kopt=root=UUID=79bba47e-9b46-4c33-90ff-f3a0c48b6ff7 acpi=force irqpoll ro

I assume the UUID  is different for each install.  Then save the modified menu.lst, and run :

sudo update-grub

Then reboot.

My mouse (Logitech trackball USB) has worked OK since making the change.  I'm pretty new at this .. I've played a little with a couple of distros from time to time, but it's been a while.   I got the the bug to give it another shot.  Hopefully the major hurdles have been surmounted.

---

### Post by leffler on 2007-10-04
Still no joy ... The force irqpoll setting let the mouse go a few more minutes before freezing, but it's still a problem.  I just found this link ... 

[http://swik.net/Linux/YALB/Dell+E521,+Linux,+Freezing+USB+Mouse+Problem+Resolved/uo3x](http://swik.net/Linux/YALB/Dell+E521,+Linux,+Freezing+USB+Mouse+Problem+Resolved/uo3x)

It says to update the BIOS  (The problem is pretty common, across multiple Linux distros).  Will try it when I get time.

---

### Post by sunilattri on 2007-10-04
I have also the same problem, will read the link you suggested. Thanks

---

