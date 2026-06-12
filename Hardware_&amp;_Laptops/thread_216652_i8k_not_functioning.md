---
title: "i8k not functioning"
date: 2006-07-15
forum: Hardware &amp; Laptops
---

### Post by Tweek84 on 2006-07-15
I've got a dell inspiron 1000 and have been trying to install i8kutils so I can control the fan. (the fan hardly runs, and never goes to high speed anymore. used to under xp)

I have the i8k module running but when I use any of the i8k utilities it comes back with invalid data.

This is the output i get from i8kctl
[quote]root@lappy2200:~# i8kctl
1.0 (null) 5JB2251 -1 -1 -1 -1 -1 -1 -1
[quote]

i8kctl fan simply returns -1 -1 and I am unable to change any of the values.

Now from what I understand i8k should work w/ this laptop. I know it's been considered compatible with the inspiron 1100 which is basically the same thing as the 1000 with a few changed components.

Now all i've done is installed the packages for i8k from the repos and no other configuration. I couldn't find any other documentatino for i8k.

What have I missed?

---

### Post by gesho on 2006-07-31
do you have /proc/i8k
process?
 
if not, have you loaded kernel module 
insmod i8k.ko

it should be in /lib/modules/2.6.15-26-686/kernel/drivers/char

---

### Post by alvenegas on 2006-08-02
Good, but how do i configure the kernel so i don't have to do 
insmod i8k.ko everytime?

Alberto

---

### Post by 5-HT on 2006-08-02
> **alvenegas said:**
> Good, but how do i configure the kernel so i don't have to do 
insmod i8k.ko everytime?

Alberto

Append the module's name to /etc/modules.

---

### Post by jethomp3 on 2006-10-10
I have an inspiron 4000 and have the exact same problem described above.  I already have an i8k in proc and I have i8k.ko in my kernel.

when I insmod i8k.ko I get:
insmod: error inserting 'i8k.ko': -1 File exists

Help?!?

when I i8kctl I get the following:
jt@jt-laptop:~$ i8kctl
1.0 (null) 6BGFG01 -1 -1 -1 -1 -1 0 0

when I i8kctl fan 2 2 I get:
jt@jt-laptop:~$ i8kctl fan 2 2
-1 -1

---

### Post by David Corrales on 2006-10-10
You have to use the -force flag to load it.

---

### Post by jethomp3 on 2006-10-10
So is the following correct?

insmod i8k.ko -force

Also, despite the fact that the i8kfans displays "-1 -1", my fans are not spinning.  Is it possible that my fan is dead?  why would they display "-1 -1" if they are truly not spinning?

btw, thanks for the quick reply, after working on this for two hours in frustration, it's nice to know there is a simple answer, even if I don't know how to do it yet.

JT

---

### Post by jethomp3 on 2006-10-10
Oh, btw I already did the following "sudo modprobe i8k force=1" per another forum.  It seems modprobe and insmod are similar, so it should have accomplished the same thing.  Yet I still get the output I posted before.

---

### Post by David Corrales on 2006-10-12
Hmm maybe your hardware is incompatible :(?

---

### Post by jethomp3 on 2006-10-12
That's what I was afraid of.

Is there any way to download drivers for this sort of thing from Ubuntu?

It appears my temp sensor is working and I get a temp readout, however, I don't get fan operation.  Does this mean my fun with Ubuntu is over and I'm gonna have to go to windows again?:-k 

I really hate this, because aside from the fan issue, Ubuntu ran much smoother on my machine.  Ubuntu shuts off because it overheats, windows shuts off because it wants to.](*,) 

Please help me keep Ubuntu, I just got all my multimedia, printers, and wireless working.  Tell me it's not for naught.

JT

---

### Post by David Corrales on 2006-10-13
Are you running Dapper or Edgy? Maybe upgrading to Edgy will sort out some bugs?

---

### Post by jethomp3 on 2006-10-13
Good thought, did it, but no such luck.

Oh well.  If anyone has any other ideas they would be greatly appreciated.

Thanks

---

### Post by jethomp3 on 2006-12-11
Found my problem.  A VERY OLD dell BIOS.  Updated bios, now I'm up and running with Ubuntu 6.10 and i8kctl is working beautifully.

JT

---

### Post by David Corrales on 2006-12-11
Grats :)!

---

