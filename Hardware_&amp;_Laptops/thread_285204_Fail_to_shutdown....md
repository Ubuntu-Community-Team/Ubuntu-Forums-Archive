---
title: "Fail to shutdown..."
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by Elrohir on 2006-10-26
this bug keeps me going like this -> ](*,)

I have a Toshiba Satellite A105 where I first installed Breezy, which had no trouble on shutdown, it in fact shut down...
But when I upgraded to Dapper, Ubuntu didn't shut down the laptop... I went for a clean install, same problem...

Here's my fdisk output:
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        2802     1534207+   5  Extended
/dev/sda3            2803        4714    15358140   83  Linux
/dev/sda4            4715       14593    79353067+  83  Linux
/dev/sda5            2612        2802     1534176   82  Linux swap / Solaris

```

having /home on a different partition from root ( / ) may cause this problem? oris it because the dual-boot (which I seriously doubt)? or is it some bug with the shutting down process?

---

### Post by Shay Stephens on 2006-10-26
My computer doesn't shut down either.  I have heard a few others experiencing the same thing.  So I think it is a bug with some setups.

---

### Post by Elrohir on 2006-10-27
any developer that can help these simple mortals to fix this?

---

### Post by andygodwin on 2006-10-28
I'm having this problem as well - the laptop simply doesn't power off at the end of the shutdown process. It also doesn't reboot, suspend or anything like that (I have to manually cycle the power to reboot).

It looks like an ACPI bug, but I'm nowhere near clever enough to figure out where it is...

Oddly enough, it worked once (and worked all the time in Dapper). Strange...

---

### Post by Elrohir on 2006-10-30
the only bug I have is in Shut Down, it hibernates just perfect, reboots without a problem...

---

### Post by andygodwin on 2006-10-31
Lucky for you... perhaps we have a slightly different problem then.

Actually, this post is to bump it up so it gets noticed, but it needs some content :)

---

### Post by Elrohir on 2006-11-09
*bump*

lol... just kidding...

seriously, has anyone managed to have a successful shut down on a Toshiba Satellite A105?

---

### Post by doobit on 2006-11-09
Edit your grub menu:
```
 sudo nano /boot/grub/menu.lst
```
add this to the end of the boot command line: acpi=force
then ctrl-x to save it and enter to write it.
reboot.

---

### Post by Shay Stephens on 2006-11-09
> **doobit said:**
> Edit your grub menu:
```
 sudo nano /boot/grub/menu.lst
```
add this to the end of the boot command line: acpi=force
then ctrl-x to save it and enter to write it.
reboot.

Thank you so much!  That worked for me!!!

This is where I added the command (in red):

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet  splash [COLOR="Red"]acpi=force[/COLOR]
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

---

### Post by Shay Stephens on 2006-11-09
nothing to read here...move along ;-)

---

### Post by freshofftheufo on 2006-11-11
Another thread describing the same problem suggests a different solution.

[http://www.ubuntuforums.org/showthread.php?t=290713](http://www.ubuntuforums.org/showthread.php?t=290713)

I, of course, have the same problem as everyone else, and I have no idea why there's two different solutions. I'm going to try the one on this thread first and see if anything bad happens.

---

### Post by Elrohir on 2006-11-13
I'll go for the ACPI instruction... more portable than editing the /etc/modules file...

---

### Post by Chonnawonga on 2006-11-17
Beautiful! Now it's running my power settings correctly, too. Thank you!

---

### Post by viking777 on 2006-11-28
I have tried all the 'solutions' given here and have also tried 9 different distros on my laptop (ubuntu 6.06,ubuntu 6.1,suse 10.0, suse 10.1, mepis, mandriva, fedora core 6,slackware 11 and xandros 3.0.2), not one of them can shut it down properly.](*,) ](*,) (although windows can:confused: )

Now I know nothing, but surely this is a kernel bug not a ubuntu one??

---

### Post by Elrohir on 2006-12-08
same here... tried modifying /etc/modules, adding acpi=force and nothing... any other ideas???

kernel bug? hmm... on next format I'll use personalized kernel...

---

### Post by Kross on 2006-12-08
> **Elrohir said:**
> same here... tried modifying /etc/modules, adding acpi=force and nothing... any other ideas???

kernel bug? hmm... on next format I'll use personalized kernel...


I have already posted this...

I am glad the ACPI add work for you..another thing is you can try to downgrade the kernel..

her is more InFO
Try This=
 [http://ubuntuforums.org/tags/index.p...er-hang-ezfix/](http://ubuntuforums.org/tags/index.p...er-hang-ezfix/)
 
 Maybe this can help.
 Let Me Know..
 
 <=Kross=>

---

### Post by Elrohir on 2006-12-10
> **Kross said:**
> I am glad the ACPI add work for you..
no, it didn't... could you please fix the link? thanks...

---

### Post by uBo on 2006-12-14
I have a A105-S2716

i will try the acpi=force

but could someone explain what it means. what else will it change? is there any risk of braking other things?
thanks!

---

### Post by xmastree on 2006-12-16
Hmm, mine stopped working... Then I remembered.
 There was a new kernel update, which I installed so my grub menu was re-written *without* acpi=force...  :oops:

---

### Post by uBo on 2006-12-17
"acpi=force" does not work on my Toshiba A105-S2716 system :(

---

### Post by uBo on 2006-12-19
The Toshiba people can try this, it worked for me as a test:

1. kill the "mixer_applet2" (sound) through the System Monitor or anything like that, that could be using the sound module that us unloaded in the next step: 

2. unload the snd-hda-intel kernel module:

```
sudo rmmod snd-hda-intel
```

3. Just shut down the computer through the normal procedure.


It worked. It seems that this sound module is the problem. 

The question is how do I integrate this steps into my automatic shutdown routine? The sound icon on the GNOME panel was removed too.

Any help is apreciated.

---

