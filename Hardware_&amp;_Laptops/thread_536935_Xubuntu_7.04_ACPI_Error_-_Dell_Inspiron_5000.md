---
title: "Xubuntu 7.04 ACPI Error - Dell Inspiron 5000"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by Amadeo on 2007-08-28
Hello,

I am wanting to install Xubuntu on this old laptop.  It is a Dell Inspiron 5000 which has a P3 500MHz processor and 512MB RAM.  On the initial Xubuntu LiveCD boot, I see an error spam of something like:

ACPI: [package] has zero elements (debD6cc0)

It shows that line numerous times, but with different numbers at the end.  They seem to change each boot.  That may be off a bit, because I couldn't read it fast enough and am not sure where to find a log of the error.

If anyone can help me resolve this so ACPI will work properly, please let me know!

Thanks!

---

### Post by Amadeo on 2007-08-28
Anyone? 

The OS installs fine, but I don't think ACPI is working because I hardly have any battery life at all.

---

### Post by Amadeo on 2007-09-15
Still unresolved,

Have also tried 7.10 and get the same errors.  Should I just go back to Microsoft?

---

### Post by 0darn on 2007-09-16
hi Amadeo , there is a boot'cheatcode' you can try for the current boot : noacpi

- On boot when grub loads ,use  'ESC' , then you should come to a 'hidden' boot-menu ..
 ( default on top , highest kernel version ... )
 Use 'e' to edit choosen boot-line , behind text '/boot/vmlinuz..... ro quiet splash nodma' 
 insert 'a space' and 'noacpi' , then 'Enter', then 'b' ( for booting that edited line )

Any success/difference in acpi errors?

If yes , you need to edit the grubs menu.lst , instead of above - ev boot .

More : 
Linux usually uses '/etc/rc0.d - rc6.d' , to start different runlevels ( rc5 = xwindow ) modules/services ( Acpi is 1 )...
In those folders there's listed things ( ie links to real files ) that should start in choosen runlevel ( defined in '/etc/inittab' ) - but Ubuntu Feisty converted to boot with new boot/daemon 'Upstart' , that uses folder/settings in '/etc/event.d' ....
and here im lost - just trying to understand upstart :)

But when booted into xubuntu xfce , you can turn on/off some of those services here : 
 Applications - System - Services

G.luck / 0darn

Edit : if you want Acpi to work - have you checked the Bios-setting that powersaving is enabled ?

---

### Post by Amadeo on 2007-09-18
Thank you for the reply, 0darn.

I haven't had a chance to try the steps you've listed yet, but I will note that I do need ACPI to work since this is a laptop.  I worry about it overheating.  In fact, I had a different distribution of Linux on it and noticed that the laptop fan wasn't coming on.  I had stepped away from it for a little bit and came back with the laptop overheating on me and wasn't sure if it would work again.

This is really the main issue I've been having with Linux in general on this laptop right now.  I can't seem to get ACPI to work right and along with that, the laptop fan doesn't like to run in Linux.  I'm not sure if the two are tied together or not.

---

### Post by 0darn on 2007-09-18
hi again Amadeo ,

 i found following on osdir.com:
> > .....Dell Inspiron 5000 is really an APM BIOS machine with some early
 > development ACPI interface support. It used to suspend perfectly with 2.4 kernels and apmd.
 > With 2.6 kernel which I am using now only acpi module can be inserted.
 > Please find out exact release where APM stopped working, locate change that made it stop
 > working......

Sadly more sites pointing like this to dell 5000 + kernel-issue , and it looks fancontrol/acpi/kernel issue...

Then i saw this "..standalone, no special kernel module is required.." ( read Acpi ) for dell laptops :

diefer.de/i8kfan/index.html  , ( even here the win-version is bad for 5000 , linux at end points to.. )
dellfand.dinglisch.net , ( wich work on kernel 2.6 -> , but maybe not on all models :/ , and needs doing "make" on target machine .... 

- well not much hope, but Good luck :(
/ 0darn

---

### Post by Amadeo on 2007-09-18
Thank you again for your help, 0darn.

I'm not very advanced at using Linux, and I think this is starting to go over my head.  I'll try to read into this i8kfan more and see what I can do with it.

Edit:  I just checked out the i8kfan website and it says the Inspiron 5000 is incompatible.  I guess the only OS that will run this laptop is Windows.  That's something I wouldn't have expected of Linux.  Perhaps there is another option...

---

### Post by Michael451 on 2007-11-18
> Perhaps there is another option...

Yes, you could try doing as Odarn suggested with the noacpi.  Or just add "acpi=off" to your boot kernel line in grub or lilo.  I have not used Ubuntu on my machine (a 5000e P3), but this did do the trick for me running Arch Linux.  I think because both acpi and apm are built into the kernel, but acpi just doesn't work well.  I was then able to suspend (or standby) by pressing Fn+Esc.  This also worked for me running Gentoo on same machine with only apm support in kernel and without the "acpi=off" in my boot file.  You say you need acpi, but it seems you just want to be able to suspend your computer.  And with this machine apm works better in my experience.

---

### Post by TygerTung on 2008-03-06
I am also having an acpi issue, whatever acpi is!

When I boot it up it tells me the acpi package thing has no elements, it appears to have no effect to the running of the laptop, is this a big issue?

---

