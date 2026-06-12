---
title: "Lubuntu 16.04 and the i915 Driver"
date: 2016-04-22
forum: Hardware
---

### Post by roler2 on 2016-04-22
If any of the Forum Members can verify whether or not Lubuntu 16.04 will work with the i915 Driver I would really appreciate the feedback. The Beta releases did not. Actually I think it is the updated Kernel that is the issue.

Go ahead and blast me for having a really old Computer (Dell). It still works great. Never had a problem with it. Lots of the Dell P4's came with the pre-packaged i915 or a variant thereof. Lubuntu 14.04 works great, but only for another year. I have tried the LXLE OS and did not like it at all.

So If the i915 isn't going to work with 16.04 and/or the updated Kernel hasn't been fixed to accommodate the i915, then I give up with Linux.  

Thank you for your assistance.

---

### Post by Bucky Ball on 2016-04-22
*Thread moved to **Hardware**.*

---

### Post by Yellow Pasque on 2016-04-22
What exactly happens when you try to boot/install from a 16.04 LiveCD/USB?

---

### Post by roler2 on 2016-04-25
[COLOR=#000000]Hello-I posted the answer in two other threads applicable to the i915. Also, I tried both DVD and USB. Same results. Frustrating. If you are able to share any fixes or even a way to check to see if it is a Kernel issue (which I am fairly sure it is), I would very much appreciate your feedback. Thank you![/COLOR]

---

### Post by Yellow Pasque on 2016-04-25
> **roler2 said:**
> [COLOR=#000000]Hello-I posted the answer in two other threads applicable to the i915.[/COLOR]

Links?

---

### Post by roler2 on 2016-04-26
[http://ubuntuforums.org/showthread.php?t=2321452](http://ubuntuforums.org/showthread.php?t=2321452)

[http://ubuntuforums.org/showthread.php?t=2321772](http://ubuntuforums.org/showthread.php?t=2321772)

---

### Post by tos3 on 2016-04-26
> **roler2 said:**
> If any of the Forum Members can verify whether or not Lubuntu 16.04 will work with the i915 Driver I would really appreciate the feedback. The Beta releases did not. Actually I think it is the updated Kernel that is the issue.

Go ahead and blast me for having a really old Computer (Dell). It still works great. Never had a problem with it. Lots of the Dell P4's came with the pre-packaged i915 or a variant thereof. Lubuntu 14.04 works great, but only for another year. I have tried the LXLE OS and did not like it at all.

So If the i915 isn't going to work with 16.04 and/or the updated Kernel hasn't been fixed to accommodate the i915, then I give up with Linux.  

Thank you for your assistance.

Hello,

I have exactly the same problem with an old IBM PC ThinkCentre and an i945 graphic controller. Previously, I used Lubuntu 14.04 without problem.
So I tried a live usb of Ubuntu and it works. This issue seems to happen only with Lubuntu. Then I don't understand why because, for me, Ubuntu and Lubuntu use the same Kernel.
I tried also the nomodeset option and I can start up Lubuntu in live but with a low screen resolution. So it's not a good solution, I prefer to continue to use the KMS.

Someone can confirm that it's a Lubuntu's issue only? What is the plan to fix this ? Is it taken into account by the Lubuntu team?

Thanks in advance for your comments.

---

### Post by roler2 on 2016-04-26
The issue appears to be centered more with Lubuntu than with other Distros, such as Xubuntu. I might try a download of Xubuntu and attempt a Live Mode to see if that works. Unfortunately I don't have the hardware or the RAM to run Xubuntu on a regular basis. Yet according to the BayTrail article, the issue does appear to be affiliated with other Distros, not just Lubuntu. 

Oh apparently it is not totally the Distro itself, it is the updated Kernel incompatability with the i915 Driver. With Lubuntu, it might even be LXDE related, given that there are reports Xubuntu hasn't had the issue on a regular basis.

---

### Post by tos3 on 2016-04-27
> **roler2 said:**
> The issue appears to be centered more with Lubuntu than with other Distros, such as Xubuntu.

I tried also Xubuntu and there is no problem to boot with the same computer than with Lubuntu. The issue seems to be focused on Lubuntu. 

Ubuntu, Xubuntu and Lubuntu share the same kernel ?

---

### Post by roler2 on 2016-04-27
I believe they do share the same Kernel. Does your Computer have the i915 Driver? Mine is the P4 Dell Dimension 2400 with the i915 built-in. Would there a way to install the LXDE Desktop and uninstall the XFCE? I don't have the ability to run XFCE effectively.

---

### Post by tos3 on 2016-04-27
Yes my computer uses the i915 driver. It starts up until the display of the choice window between "Try without installing" and "Install". When I choose Try, I have a black screen with a blinking cursor in the top left corner and that's all.

---

### Post by tos3 on 2016-04-27
I found a way to install Lubuntu 16.04 with Intel graphic controller !!

Actually, the driver xserver-xorg-video-intel is not installed by Lubuntu. Source = [https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1575460](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1575460)

So, we can run the installation normally after a boot from LiveCD/USB. After the first reboot, we have a black screen. At this time, open a terminal (Ctrl+Alt+F1) and run sudo apt-get install xserver-xorg-video-intel.
After that, reboot and now it's ok. The system boots normally.

---

### Post by roler2 on 2016-04-27
@tos3-I will try your suggestion! Thank you! The last time I tried Ctrl+Alt+F1 I got a reboot so I will try and open a terminal. I might try and go into Recovery Mode and attempt to install via the Command Line in Recovery if Ctrl+Alt+F1 doesn't work.

---

### Post by roler2 on 2016-04-28
@tos3-Good job! I would recommend that you post your solution in a separate thread. However, the Font Rendering is horrific, especially with LXDE and the Start Menu. I am attempting to utilize Infinality, however I am not sure how to tweak it. I am able to utilize the Ubuntu Style, yet I am not able to implement any other style. Is there any way to make the Start Menu Fonts crisp and clear and somewhat bold like they were in 14.04?

Also I might attempt to install upstart-sysv and remove systemd-sysv. I do not know if that will help but it might.

I was able to install the Driver via Recovery Mode. Ctrl+Alt+F1 kept giving me a reboot rather than a Terminal. I also had to cold reboot in order to initialize the Driver. You are correct, the Intel Driver does not install automatically.

Thank you again for your fix!

---

### Post by Yellow Pasque on 2016-04-28
Can you give a /var/log/Xorg.0.log so we can see where you are at?

---

### Post by roler2 on 2016-04-28
I am not sure how to access the log. Can you please give the instructions?

Also upstart does not work with Lubuntu 16.04. Not in any way, shape or form. I tried every fix, every tweak, everything.

Further, there are continual issues with updating, scanning for updates and some minor Desktop freezes. Infinality helped a little bit with Font Rendering. Yet the Font clarity and sharpness within 14.04 is above and beyond 16.04 by miles and miles.

Lubuntu should just stick with a Kernel that works well with Lubuntu, such as the 3.13 Series.

---

### Post by Yellow Pasque on 2016-04-29
> **roler2 said:**
> I am not sure how to access the log. Can you please give the instructions?

Just open it up in a text editor and copy/paste. Use [ code ][ /code ] tags (no spaces in between brackets) as it's a lot of text. I don't know what text editor Lubuntu uses (maybe leafpad?).
```
leafpad /var/log/Xorg.0.log
```

---

