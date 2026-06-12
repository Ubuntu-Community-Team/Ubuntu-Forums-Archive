---
title: "Display driver problem after trying to root 14.04"
date: 2014-11-21
forum: Hardware
---

### Post by dkc.com on 2014-11-21
Hi friends,

I have recently installed ubuntu 14.04 on my Dell inspiron 1520. Also installed kubuntu desktop. Everything was working fine until I tried to root. I used the following method: [http://www.fogproject.org/wiki/index.php/Ubuntu_14.04]("http://www.fogproject.org/wiki/index.php/Ubuntu_14.04"). When I entered the last command ```
shutdown -r now
```. It restarted and stuck on the screen where it's only showing 'kubuntu' blinking. It says something is wrong with my display drivers. System is hung there and not going even to login screen.

What should I do?

Thanks in advance.

---

### Post by houstonbofh on 2014-11-21
Looking at the page the first thing that jumps out at me is > **DO NOT USE THIS VERSION OF LINUX, IT IS TOO NEW AND THERE ARE ISSUES WITH TFTP UPSTART AGAIN, WHEN TIME ALLOWS AND MAJOR ISSUES WITH FOG HAVE BEEN RESOLVED, WE WILL TACKLE FIXES FOR THE UBUNTU 14.04 OPERATING SYSTEM!**

That said, the next thing is why are you enabling root?  And then setting up the greeter to allow root login?  I have been admining Linux and Unix for many years, and have never found a case where sudo was not usable...

But to answer the question, it is probably the line > echo "greeter-show-manual-login=true" >> /etc/lightdm/lightdm.conf which assumes a Unity or Gnome login, and may be different for KDE.

---

