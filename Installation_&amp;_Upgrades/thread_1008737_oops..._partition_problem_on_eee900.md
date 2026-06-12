---
title: "oops... partition problem on eee900"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by bernardo06 on 2008-12-11
so i installed ubuntu on my eeepc and i forgot to format the 16gb partition so now i have ubuntu on the 4gb partition and stuff left over from xandros on the 16gb. so the 16gb partition doesn't show up right and i cant add music, videos etc amarok etc. it shows the 16gb drive as password protected and i know the password but every time i want to acces the drive i have to put it in, very annoying. so what should i do?

---

### Post by mdebusk on 2008-12-12
> **bernardo06 said:**
> so i installed ubuntu on my eeepc and i forgot to format the 16gb partition

What's preventing you from formatting it now?

---

### Post by bernardo06 on 2008-12-12
no external cd drive handy

---

### Post by Ifaistos on 2008-12-12
Another solution would be to create a bootable USB stick with Ubuntu.  It is in System > Administration > Create a USB startup disk.

So all you have to have is a 1GB or more USB stick and boot your eeePC from your USB stick, and you will get the option to reinstall everything from the very beginning ;-)

---

### Post by mdebusk on 2008-12-12
> **bernardo06 said:**
> no external cd drive handy

I may be misunderstanding the issue. I'm under the impression that the disk with which you're having problems is NOT the one to which you installed Ubuntu.

If this is the case, there should be no problem with unmounting it and formatting it. If not, the bootable USB flash drive is your answer. (It's how I put Ubuntu on my EeePC.)

---

### Post by bernardo06 on 2008-12-14
i used gpart and formatted it. now it shows up as a usb drive with nothing known about it in properties and it wont let me mount it.

***edit

now its asking for a password again. i cant make any new folders or anyhting in it. 

it says that is a usb drive also

it also said something about not being able to do something with it because it is an internal drive.


im confused.

---

### Post by mdebusk on 2008-12-15
> **bernardo06 said:**
> i used gpart and formatted it. now it shows up as a usb drive with nothing known about it in properties and it wont let me mount it.

Cool. It's clean now. What, exactly, did you do in your attempt to mount it? And what do you mean by "shows up"?

> now its asking for a password again. i cant make any new folders or anyhting in it.

Root probably owns it. You have to use "sudo".

> it says that is a usb drive also

It might be.

> it also said something about not being able to do something with it because it is an internal drive.

We'll need better error messages than that. :)

> im confused.

You're learning. Confusion is good.

---

