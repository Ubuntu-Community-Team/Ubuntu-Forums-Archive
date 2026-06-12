---
title: "Trust DS3400 wireless keyboard doesn't work"
date: 2011-04-17
forum: Hardware
---

### Post by Mortesins93 on 2011-04-17
Hello,
so I have a laptop with a Trust wireless keyboard and mouse and it works fine on Xubuntu 9.10 (kernel 2.6.31-14), but I wanted to change so I tried Ubuntu 10.10 (i don't remember the kernel but it should be: 2.6.35) on my laptop hoping it would be great. I installed it without problems expect for the fact that I had a pretty hard time writing in my info because the cursor on the blank space where I had to write my name, the name of the computer, etc. kept on blinking without letting me write. Even after I rebooted, I still got this problem that when I try typing something the cursor just blinks faster and I can't type anything. So I tried Linux Mint 9 xfce (kernel: 2.6.32-21) and the keyboard worked fine. Then I tried Puppy Linux 5.11, Puppy Linux 5.25 (kernel: 2.6.33.2) and it worked fine. Then I tried OpenSUSE 11.4 (i don't remember the kernel but it should be: 2.6.37) and it didn't work. I tried Linux Mint 10 GNOME and it didn't work (i don't remember the kernel but it should be: 2.6.35). Could this be a kernel issue? If so what should I do? If not what should I do? Every distro I tried I saw the following modules loaded : hid,usbhid,hid_sunplus, and I know these are what make my keyboard work, but they were always loaded even when I had the problem. Why do the same modules work differently? Could this not be a module issue?
I hope you can help me because it's getting pretty annoying.
Thanks in advance.

---

### Post by Mortesins93 on 2011-05-01
Obviously it doesn't work on ubuntu 11.04. WHY?!?!?!?!?

---

### Post by Mortesins93 on 2011-05-01
**[SIZE=3]Trying  out Xubuntu 11.04 and my Trust DS3400D wireless  keyboard works. Only on Xubuntu 9.10 and 11.04 it  works, why is that?[/SIZE]**

---

### Post by Mortesins93 on 2011-05-01
[SIZE=2]Trying  out Xubuntu 11.04 and my Trust DS3400D wireless  keyboard works. Only on Xubuntu 9.10 and 11.04 it  works, why is that?[/SIZE]

---

### Post by Mortesins93 on 2011-05-13
So I was playing around with Xubuntu trying to replace thunar with nautilus and I found out that when I replaced the file in /usr/bin xfdesktop with nautilus so that nautilus would run instead of xfdesktop
>  				 				**Re: Replace Thunar with Nautilus** 			
 			 			 		   		 		i didn't think it would be that easy. i do have a plan b, but it may screw you later if those programs get up dated, just letting you know.
 so plan b, would be to replace xfdesktop with a link to nautilus.

in a terminal:

[B]sudo mv /usr/bin/xfdesktop /usr/bin/xfdesktop-off
sudo ln -s /usr/bin/nautilus /usr/bin/xfdesktop[/B]

that's it, just remove your startup stuff, logout and back in and hopefully it will be using nautilus.

[http://ubuntuforums.org/showthread.php?t=1167149](http://ubuntuforums.org/showthread.php?t=1167149)
When I did this the keyboard stopped working.

---

