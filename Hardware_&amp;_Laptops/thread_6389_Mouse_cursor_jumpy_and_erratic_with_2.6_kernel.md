---
title: "Mouse cursor jumpy and erratic with 2.6 kernel"
date: 2004-11-28
forum: Hardware &amp; Laptops
---

### Post by blujay on 2004-11-28
I have an old Compaq Presario 1690 laptop.  It has a Synaptics touchpad.  When I use Knoppix with it, booting a 2.4 kernel, it works fine.  If I try a 2.6 kernel with Knoppix, the cursor jumps all over the place, and mouse clicks happen randomly.  The same erratic behavior occurs with SimplyMEPIS and with Ubuntu's LiveCD.  If I plug in a PS/2 mouse with a 2.6 kernel, it's erratic also.  Using a USB mouse isn't really an option, because there's only one USB port, and I need that for a memory card reader.

I've spent a lot of time looking on forums and on wikis and on Google, but I can't find a solution.  I've tried using "acpi=off" in the boot line in Ubuntu, but that doesn't help.  I read somewhere that you might need to run "modprobe psmouse" and "modprobe mousedev", but when I tried running those from a root console in Ubuntu, the modules weren't found.

I would really like to use a 2.6 kernel for the enhancements it provides.  Does anyone have any ideas for how to fix this erratic cursor problem?  Thank you in advance for any help.

---

### Post by feneks on 2004-12-20
hi blujay

I'm using synaptic touchpad too and I have got the similar problem. 

[http://ubuntuforums.org/showthread.php?t=7565](http://ubuntuforums.org/showthread.php?t=7565)

If you have got the same errors at /var/log/messages it might be because of a kernel bug. This bug exists since kernel 2.6.6 I think. Actually I don't use GNOME's battery-applet. This isn't satisfying but I don't know better.

All types of external mice should work as I read.

---

### Post by blujay on 2005-01-14
FINALLY, by upgrading to a 2.6.10 kernel (Debian 3.1 testing, used kernel-image package from unstable), it is fixed!   =D> 

If anyone else is having this problem, e-mail me and I will try to help you.

---

### Post by homer pieman on 2005-02-17
I had the same problem on a Dell CPx laptop with a PIII 650. I stopped powernowd and it wasn't jumpy any more. ACPI is still running. It's running the latest kernel, 2.6.8.1-16.11.

---

### Post by kernelsandirs on 2005-04-14
[FONT=Arial]I also found that killing the powernowd process completely fixes the issue for me too, thanks for the post, I also removed S20powernowd from /etc/rc2.d/ so when I boot it does not start again, :-)[/FONT]

I am also using a laptop with a synaptics pad and a PS/2 mouse w/wheel
I have a Dell C600.

---

### Post by UncleFoo on 2006-12-04
I have same problem but not on a laptop. I have a Dell CPX and a PS2 mouse (I have tried wheeled and non-wheeled).

I am running Dapper Drake (K)Ubuntu. How do I tell which Kernel I am using? I I upgrade to Edgy will that upgrade the Kernel?

---

### Post by UncleFoo on 2007-03-17
I bouaght a new mouse (Logitch Optical), and the problem went away.

---

### Post by Regnibb on 2008-06-14
This problem (erratic, jumpy mouse cursor) is a major problem on my HP dv4000. Whats the quickest, easiest fix.

---

