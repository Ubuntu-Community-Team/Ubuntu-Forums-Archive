---
title: "Ubuntu wont install"
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by jamesgl on 2007-07-17
I downloaded the 7.04 desktop iso, made the cd.

The cd checks out (using the check cd option)

booted from the cd.
and get the following error message:

Loading hardware drivers:
firmware helper 6909  main: error loading `lib/firmware/bcm43xx_microcode5.fw for device '/class/firmware/0000:03:00.0 with driver ' (unknown)'
[ 137.639942] bcm43xx: Error microcode "bcm43xx_microcode5.fw" not available or load failed

same error for:
firmware_helper 6963
and 

firmware_helper 6969
then continues loading with :

Loading kernel modiules   ok
loading manual drivers      ok
checking file systems       ok
mounting local file systems ok
activating swap file swap   ok
configuring network interfaces ok

and it LOCKS UP AND STOPS!!
(repeated numerous times)


Any help would be appreciated.

email addy [email]jamesgl@pobox.com[/email]

Cmp is pavilion laptop, (dc9074cl)
 2 GB of memory, amd 64 turion processor, 
and using the 64 bit version of Umbutu.

thanks in advance!!

Jamesgl

---

### Post by cosborn72 on 2007-07-17
It would seem like Ubuntu is having a problem with your wireless card.  I've never heard of a card preventing Ubuntu from installing, though....

Is the wireless card removable?  You could try install without it and see if that is the problem.

---

### Post by jamesgl on 2007-07-17
after the wireless, the word okay appears.  It's after that, the things lockout.  I don't know if that means that the wireless card installed okay, and if something else is wrong.

I don't have a way to disable the wireless card as it is built into the laptop.  But thank you very much for taking the time to reply.

Jim

---

### Post by 0and1 on 2007-07-20
Exactly same thing here. Laptop is a HP pavillion dv6305 US and there is a Broadcom wireless card in it. I am wondering why its stopping the install. Any help?

---

### Post by hessiess on 2007-07-20
booting puppy linux on this comp dus prittymutch the same as what you describe ubuntu dooing

---

### Post by 0and1 on 2007-07-20
Any solutions? Wireless card not being recognized by the OS is one thing. But the wireless card preventing installation is very bad.  Has a bug been filed yet?

---

### Post by valingnor on 2007-07-20
I have a Compaq V6120US laptop and was getting the same error you were.  I even tried switching to the 32-bit version of Ubuntu....still a no-go.  I actually found a solution through trial and error, and reading the help during the install screen.

If you hit F6 on the initial screen, it will bring up a command line.  Hit ESC once that is up.  It should ask whether or not you wish to go to a text-based installer.  Hit OK.  Once there you should see....

boot:  

If you do, type the following (without quotes) "live noapic nolapic" one space after that.  It should look like.....


boot: live noapic nolapic


It worked perfectly for me.  I can't remember what it does, but I found it in the F6 section of Help (F1).

---

### Post by kcramakrishna on 2007-08-03
noapic is necessary for AMD chipset comps. You will need to put it in the boot parameters during normal boot up after installation too. 'live' is not necessary.

---

### Post by merlinus on 2007-08-03
I believe you can add noapic to the end of the kernel line in /boot/grub/menu.lst so as not to have to enter it manually every time on startup.

-merlin

---

### Post by twistadias on 2007-08-05
thanks for the   noapic   thing. i have the same wireless card and my laptop wouldnt boot up. all is fine now. onlyif i could get the wireless drivers to worrk.

---

