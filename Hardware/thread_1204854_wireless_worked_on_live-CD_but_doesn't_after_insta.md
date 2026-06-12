---
title: "wireless worked on live-CD but doesn't after install"
date: 2009-07-05
forum: Hardware
---

### Post by Kolkat on 2009-07-05
Hello everyone!
I have been using Windows my entire life but recently read a review about how excellent and problemfree Ubuntu is, so I thought I'd give it a try. I am using Toshiba Satellite M100, so I installed a 32-bit version of Ubuntu. It booted fine from the live-DVD, found my sound, and with a little help, the wireless card. So, I decided to install it. That's when the problems started. 
First, after partitioning my HDD for about an hour and a half, Ubuntu gave me an error message and said that partitioning could not be completed. I tried the whole thing one more time - the same story. 
After browsing Ubuntu help forums (thank's God I went for the dual boot!) I learned that I can use wubi. Now, Ubuntu was formatting the swap file for many hours (seriously), so I left it overnight. When I finally booted the system in the morning, and tried to install the wireless card (which worked just fine from the live-DVD), it sas that "wireless windows drivers cannot be installed on this computer (i386)". 
Why is that? It did work less than 24 hours ago! 
Anyway, I would be thankful for any help. 
I have to admit that at this point I am fairly frustrated with Ubuntu and with all the hassle it has been giving me (I literally killed the entire Saturday and Sunday morning trying to install it) I start to like Windows much more. :-(

---

### Post by Kolkat on 2009-07-05
Well, the wireless magically started to work after a reboot, although Ubuntu froze during the bootup on the message "activating swap file swap" and then it froze completely when I tried to restart the computer through Ubuntu, so I had to manually disconnect the power. 
I don't want to upset everyone here, but with this many errors and problems, I don't see the point in switching to Linux if Windows is working. 
My Ubuntu has been successfully uninstalled now and the only thing I am not happy about is the time that I envested in trying it out. I could have done something useful instead.
I hope everyone's experience is different than mine.
Good luck, everyone!

---

### Post by ivanvajar on 2009-07-05
Stop blaming everybody else. First of all, did you defragment your drives before installing Ubuntu? NTFS is famous for it's fragmentation.
2) you installed Ubuntu with wubi and by doing that made situation more difficult. Linux is not Windows. Two days ago I installed Ubuntu on HP laptop and WiFi works under Ubuntu and DOES NOT WORK under Win. We are here by our free will, not by duty.

---

### Post by Kolkat on 2009-07-05
> **ivanvajar said:**
> Stop blaming everybody else. First of all, did you defragment your drives before installing Ubuntu? NTFS is famous for it's fragmentation.
2) you installed Ubuntu with wubi and by doing that made situation more difficult. Linux is not Windows. Two days ago I installed Ubuntu on HP laptop and WiFi works under Ubuntu and DOES NOT WORK under Win. We are here by our free will, not by duty.
 
Well, I didn't make up all the problems I had just to badmount Ubuntu.
To answer your question: yes, I did defrag the drives.
 
By the way, it takes at most several hours to install Win XP, Office, drivers, codecs etc. For Ubuntu just the installation took 3 hours plus another 3-4 hours for 'preparing the swap file'. AND then it froze during bootup AND started complaining about installing the wireless (which worked when I booted up from the DVD). 
 
It's just that considering the amount of problems and error messages I got from Ubuntu during my short encounter with it, I don't see how Linux is supposed to be better than Windows. That's all.

---

### Post by Naruth on 2009-08-28
Sorry to hear that your Ubuntu experience was so unsatisfying.  I can understand how making the switch from Windows to Linux can be frustrating; a fact that many Linux users forget (unless they're just so skilled as to never had problems).  I hope you give Ubuntu another shot; it's the best for starting out.

Linux has a steep learning curve.  Once you get the hang of it, reinstalling Ubuntu takes a lot less time, around 20 min. for me.  Of course, it depends on your hardware.  On the other hand, people who complain about Windows make no sense to me either.  I haven't had a virus or crash in over a year and I have no anti-virus software.  Not to mention, I'm not exactly anti-piracy ; )  I'll shut up now.

BTW, had the same problem.  Tried installing source, using NDISwrapper, edited confs.  Just reinstalled and now it seems to work.

---

