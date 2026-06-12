---
title: "Initramfs + Ubuntu 8.04 booting"
date: 2008-08-13
forum: General Help
---

### Post by prabath_fun on 2008-08-13
Hi,
I am facing some problem with my desktop + Ubuntu + Busybox + initramfs. It shows as

"BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Build-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)"

after orange colour bar. No  further action can be done.

Few details:
Ubuntu 8.04 in wubi.
Motherboard: D102GGC2.

It was working fine for more than 2 months. I got this problem after power shutdown problem. 
  I have searched in forum, But, got such a problem faced with Live CD threads only.
Please help me.

---

### Post by Orlsend on 2008-08-14
Is this done with Windows or the LiveCD?

---

### Post by prabath_fun on 2008-08-14
Done with Windows Vista and Live CD. 
That is, wubi8.04.exe was triggered under Vista and on rebooting the system as wubi prompted, Ubuntu 8.04 was installed with Ubuntu 8.04 Live CD instead of downloding .ISO from web (Because of, non-availability of high speed net connection).

With Thanks,

---

### Post by spike.robinson on 2008-08-14
This "power shutdown problem", did it crash your PC? You might need to check your filesystems. 

The first time you installed Wubi, 2 months ago, was that the same version? Did it install "out of the box" or did you need to tweak anything?

After the power shutdown problem, did you re-install Wubi? Did you un-install Wubi before re-installing it? 

In summary: check your disks, uninstall Wubi, re-install Wubi.

---

### Post by Orlsend on 2008-08-16
Is prov a incorrect shut down, load windows and whne you get to the login screen just click "turn off" when its finished turn your PC on and then Choose Ubuntu

---

### Post by prabath_fun on 2008-08-18
**HI spike.robinson,**
 Thanks. Crashed means? I believe so, based on the appearance of Busybox.
   Before 2 months, I installed Ubuntu with Wubi from D:\ in Vista. It formed an Ubuntu folder in same drive. Are you meaning this is "out of box"? Or it was installed without any problem? (i.e., No driver problem)
   Before and after powerproblem (Improper shutdown), I have not installed or reinstalled wubi. Just as it is there. I am trying to solve it.
  Uninstall and install Wubi means, fresh installation of Ubuntu with Wubi?

**Hi Orlsend,**
   You solution was useful, Only, when there was improper shutdown of windows. During that time, I had seen message asking to restart the Ubuntu after proper shutdown of windows. But, This time I am seeing message that 
"Enter 'help' for a list of built-in commands."
So, Proper shutdown of windows and Ubuntu are not helping.

---

### Post by jmszr on 2008-08-19
Prabath_fun,

  This is from the Wubi Wiki-lots of good information there:

The Ubuntu splash screen loads for awhile then exits to a BusyBox/(initramfs) prompt.

Try The Following Solutions : 1) Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in.Click Properties.
Select the "Tools" tab and click "check now" under error checking( On Vista, You might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After The checking is done, restart the pc by using the start menu(Do not hard reboot) and try using ubuntu now.

2) Reboot and hit Esc when prompted to enter the boot menu. Hit 'e' to edit the first line. Next select the second line and hit 'e' again. Input 'irqpoll' towards the end of the bootline. Then hit 'enter' and then 'b' to boot.

Hope this works for you.

---

### Post by Orlsend on 2008-08-19
> **jmszr said:**
> Prabath_fun,

  This is from the Wubi Wiki-lots of good information there:

The Ubuntu splash screen loads for awhile then exits to a BusyBox/(initramfs) prompt.

Try The Following Solutions : 1) Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in.Click Properties.
Select the "Tools" tab and click "check now" under error checking( On Vista, You might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After The checking is done, restart the pc by using the start menu(Do not hard reboot) and try using ubuntu now.

2) Reboot and hit Esc when prompted to enter the boot menu. Hit 'e' to edit the first line. Next select the second line and hit 'e' again. Input 'irqpoll' towards the end of the bootline. Then hit 'enter' and then 'b' to boot.

Hope this works for you.
Also if that does not work maybe run defrag on where Ubuntu is installed.

---

### Post by prabath_fun on 2008-08-28
Hi Thanks for all your post. After my last post, I have reinstalled my ubuntu with wubi. I will try the solution provided by next time. So, I am leaving this thread open without closing it. 
  Since, Power shutdown problem is common in my area, I believe that, I will get this problem again very soon. I will update the thread that time.

---

### Post by rlanham on 2008-08-29
> **jmszr said:**
> 

The Ubuntu splash screen loads for awhile then exits to a BusyBox/(initramfs) prompt.

Try The Following Solutions : 1) Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in.Click Properties.
Select the "Tools" tab and click "check now" under error checking( On Vista, You might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After The checking is done, restart the pc by using the start menu(Do not hard reboot) and try using ubuntu now.

2) Reboot and hit Esc when prompted to enter the boot menu. Hit 'e' to edit the first line. Next select the second line and hit 'e' again. Input 'irqpoll' towards the end of the bootline. Then hit 'enter' and then 'b' to boot.


I've had this come up a few times and I tied it back to an improper shutdown of windows. The above may help, however; I would boot into windows and do a complete shutdown then startup before trying the above.

---

