---
title: "Hibernation Problem"
date: 2015-04-16
forum: Hardware
---

### Post by putz182 on 2015-04-16
First topic means I'm desperate.

I tried Mint forum as well, but until now, no answer.

I use Linux as server since 2004, and only nowadays I was able to accept as first OS for my notebook and struggle against all commercial engineering softwares.
So far so good, but my laptop was stolen and I bought an Asus S46CB.

:shock:

This is my last try, otherwise I will have to live with Win8 :oops:

The computer has hybrid everything.
Hybrid graphic card and hybrid HDD.

Installed Bumblebee and works good. Suspend is fine but it does not hibernate.

I have a laptop that does not hibernate! Please, help me...

I went through all of the topics and bugs but none of them solved my problem.
It stores the image, and resume (100% loaded), but right after the image is loaded it freeze.

I tried uwsusb and I got a successfully message but freeze again (I have waited many kernel updates, but the same).

I have this bug, but the workaround does not work.
[https://bugs.launchpad.net/ubuntu/+source/hibernate/+bug/1159205](https://bugs.launchpad.net/ubuntu/+source/hibernate/+bug/1159205)

> 
    /dev/sda1: LABEL="SYSTEM" UUID="B8C2-587E" TYPE="vfat"
    /dev/sda2: LABEL="Recovery" UUID="7EAE88C7AE887983" TYPE="ntfs"
    /dev/sda4: LABEL="OS" UUID="3C7E8C7D7E8C31A6" TYPE="ntfs"
    /dev/sda5: UUID="B68877E38877A093" TYPE="ntfs"
    /dev/sda6: LABEL="Data" UUID="C0B08DC4B08DC200" TYPE="ntfs"
    /dev/sda7: LABEL="Restore" UUID="4E189011188FF66D" TYPE="ntfs"
    /dev/sda9: UUID="d90343a7-d078-48ae-a947-e3f4a7b72bf9" TYPE="ext4"
    /dev/sda10: UUID="eefa9b77-578c-428f-b968-f727ea329c3e" TYPE="ext4"
    /dev/sda11: UUID="fde9a2c9-2a29-4337-9e00-54b1823a6beb" TYPE="swap"



I can try again any suggestion...

---

### Post by ajgreeny on 2015-04-16
You do not actually tell us what you have tried in order to get hibernation working so let's start a #1
[LIST=1]
[*]Do you have at least as much swap as you have ram? Without that hibernation will always fail.
[*]Have you made the required edits to the system file as shown below at #3?
[*]# save as **/etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla**
[/LIST]
[INDENT][Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate
ResultActive=yes
[/INDENT]

---

### Post by putz182 on 2015-04-16
Ok

> Do you have at least as much swap as you have ram? Without that hibernation will always fail.

I tested format, relabel, resize and I believe the swap partition is working so far.

```

$ free -mh

             total       usado      livre    compart.  buffers     em cache
Mem:          7,7G       1,1G       6,5G        90M        67M       615M
-/+ buffers/cache:       483M       7,2G
Swap:          12G         0B        12G



```

> Have you made the required edits to the system file as shown below at #3?

I went a bit further.

```
sudo pm-hibernate
```

or 

```
sudo hibernate
```

Both work, but the problem happens right after the image is resumed. It says, successfully loaded and freeze. 
The log also show successfully hibernation message.

---

### Post by weatherman2 on 2015-04-16
There's a good reason that hibernation was removed from the power menus by default a few releases ago: it's difficult to make hibernation work reliably in Linux across a variety of hardware.

I've spent hours in the past trying to get hibernation to work on various laptops.  I have often been successful - but in the end, I have mostly stopped using it.  It's not worth the hassle.

Suspend/resume does work reliably for me on my various laptops and I use it all the time.  There's no reason to use hibernation anyway unless you are going to not use the laptop for a good while, say a day or more.  Suspend should not use very much battery power.

---

### Post by putz182 on 2015-04-16
This is something that I lived with for 3 months, but the truth is that can not accept it anymore.

I lecture and from a place to another I suspend it. The problem is that my battery runs out and in the end I don't have more power for my classes. 

Indeed I lost many hours trying to figure it, tried many solutions and my last hope is to post here.
 
I thank you for share your experience, but I still wanna try a bit more with some help.
I believe to be Nvidia problem. 

Does anyone know any bumblebee incompatibility?

---

### Post by weatherman2 on 2015-04-16
I don't really understand the problem you mention with suspend, unless some devices are not really sleeping when the laptop is supposedly suspended.  Then it could be draining the battery much faster than it should.  Otherwise, on a typical laptop, your battery should last at least a day if not longer when suspended.  If your laptop is running on AC power when you give a lecture, then you suspend, then you give another lecture say four hours later...your battery drain from being suspended should be almost negligible.  I leave my laptop suspended for four hours or more routinely and the battery is generally still fairly full when I resume.

Presumably this is a newer laptop as well, with a strong battery?  An old laptop might have a weak battery that only holds a small charge, so then suspend might drain the battery pretty quickly.

---

### Post by putz182 on 2015-04-20
This is almost an offtopic, but let me explain better.

There are many peculiarities for me as user that I can't describe the need.

For example, I do agree with you that my battery last long enough, but it happens that sometimes I'm in the middle of something important with many tab of my browser opened, many pdfs and text editor, also some math programs running, and I realize that I forgot my charger in the school, like yesterday.

Can you feel the trouble, every time that I have to close each of the applications, memorize the files locations to re-open after, and stop any of my calc scripts?
Maybe it is a bad habit, but sometimes I ran programs on windows and If I have to leave, or the battery ran out, I just hibernate with the program running (programs that last hours to find results). This is a needed and resourceful tool, I can't ignore it. 

Maybe just want to return my activities two days after and suspend will not help much.

---

### Post by tcll5850 on 2015-04-20
I absolutely love hibernate, and was honestly rather appalled and almost disgusted the option wasn't available...
I downrate linux because of it.
(just because Windows is a completely different OS, that's no excuse for linux to not be able to do what windows can do AND THEN SOME)

mine would do the same thing, after loading, it froze, this was fixed by uninstalling uswsusp
```
sudo apt-get remove hibernate uswsusp
```
[http://chriseiffel.com/everything-linux/step-by-step-how-to-get-hibernate-working-for-linux-ubuntu-11-04-mint-11/#resume-fail](http://chriseiffel.com/everything-linux/step-by-step-how-to-get-hibernate-working-for-linux-ubuntu-11-04-mint-11/#resume-fail)

---

### Post by dankegel on 2015-04-21
I need hibernate to work because I use a Thinkserver TS140 as a desktop, and it doesn't support suspend at all.
With Ubuntu 14.04.1, pm-hibernate worked fine the one time I tried it.  (Ubuntu 15.04beta2 not so much, see [https://bugs.launchpad.net/bugs/1443762](https://bugs.launchpad.net/bugs/1443762) )

---

### Post by putz182 on 2015-04-21
> **tcll5850 said:**
> 
mine would do the same thing, after loading, it froze, this was fixed by uninstalling uswsusp


Tried again but still nothing!

---

### Post by putz182 on 2015-04-25
Please, any help!

---

### Post by tcll5850 on 2015-04-25
> **putz182 said:**
> Please, any help!

patience my man ;)
trust me, I can't use my mic and line-in at the same time.
and I've been waiting a while for a responce from about 5 or 6 sources including 2 on AskUbuntu.

I'm afraid I don't know anything about your issue, but if I could take a guess, try uninstalling hibernate and see if `$ sudo pm hibernate` actually does anything.
(it did for my brother's crappy non-standard rig)
play around with it ;)
that's how I got mine working. :P

my brother's however, may as well wait an hour for it to store 700MB and boot it as well...
(it works though, it's just unnaturally slow for some reason)

my brother's stuck with an older kernel because his audio doesn't work on anything newer.
(still waiting for a responce from 3 sources on this)

---

### Post by Bucky Ball on 2015-04-25
@ OP: Are you using Mint?

---

### Post by putz182 on 2015-04-25
> **Bucky Ball said:**
> @ OP: Are you using Mint?

Yes and no. 

I usually work with 2 desktops and 1 notebook.
Both desktops I have linux mint installed, however for the notebook, I still trying to fix the hiberbation problem, so I'm formatting one in a while.
Tried to use opensuse as well, but had lot of boot problem and ubuntu distro like was the only one that got really close to perfection.

But still, no hibernation fix.

---

### Post by putz182 on 2015-04-29
The kernel update fixed the problem.

---

### Post by Bucky Ball on 2015-04-29
Excellent. Please mark the thread as solved to help future travelers (see second link in my signature). Thanks and good luck. ;)

---

