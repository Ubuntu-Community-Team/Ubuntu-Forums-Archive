---
title: "ASUS P5B dlx. motherboard in Edgy Eft?"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by datil on 2006-10-30
hi, so i've read mixed opinions and experiences regarding this motherboard and the lattest Ubuntu release.

this motherboard, asus p5b deluxe, has got the ICH8R for the SATA drives and that JMicron controller for the PATA drives.
now, i've read that in 6.06 LTS the JMicron wasn't supported but the ICH8R was supported.. and now it seems that in 6.10 Edgy Eft it's the opposite? so that ICH8R is not working?

could anybody tell me if that was just a bug when that version was released? should i get one of those 'daily' updated livecd images in case it's now fixed?

thanks.

---

### Post by antidrugue on 2006-11-09
> **datil said:**
> 
this motherboard, asus p5b deluxe, has got the ICH8R for the SATA drives and that JMicron controller for the PATA drives.


I recently bought an Asus P5B myself. At the moment I have Debian Etch installed on it, on a custom vanilla kernel 2.6.19-rc5. 

Some observations :
-Debian daily-build installer (whihc use kernel 2.6.17 at the moment) would work (at least I didn't figure it out).
-Using a modifyed Debian Sarge installer (from [http://kmuto.jp/debian/d-i/](http://kmuto.jp/debian/d-i/)) I got it working in no time.
-Reading the Linux Kernel changelogs it appears that both ICH8 and JMicron support where introduced in kernel 2.6.18 ([http://kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.18](http://kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.18))

Regarding Ubuntu, as daily-build of the installer are not being made since October 25 (*cf* [http://cdimage.ubuntu.com/daily-live/)](http://cdimage.ubuntu.com/daily-live/)), you may be out of luck.

Then again, the Ubuntu kernels are heavily patched and it is very well possible that, even if Edgy's one is based on 2.6.17, they include support for both ICH8 and JMicron.

You may want to look at this page for more info on that :
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

---

### Post by drtvasudevan on 2006-11-11
i was hoping some good soul would compile a working cdimage and upload it some where. there does not seem to be any. does any one know?
compiling with new kernels are beyond non tech folk.
:-(

---

### Post by drtvasudevan on 2006-11-12
> <<-Using a modifyed Debian Sarge installer (from [http://kmuto.jp/debian/d-i/](http://kmuto.jp/debian/d-i/)) I got it working in no time.>>

can you tell me what method you followed?
hard disc install? net install?
what happens after starting with the modified installer?
i have downloaded it.
i will need an iso of debian?
will a ubuntu iso image work?
just waiting for your comments.

---

### Post by antidrugue on 2006-11-12
I simply use that image to install a Debian Sarge system (it's a netinstall). It is exactly the same as a Debian netinstall, except mainly for the kernel.

Once you have Sarge installed, perhaps you can upgrade to Ubuntu Edgy (modifying your /etc/apt/sources.list file) or Debian Etch.

Then again, if you read this page :
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

there are some success stories using the Ubuntu Edgy installer.

---

### Post by drtvasudevan on 2006-11-12
> **antidrugue said:**
> I simply use that image to install a Debian Sarge system (it's a netinstall). It is exactly the same as a Debian netinstall, except mainly for the kernel.


ok.
just tried booting with the modified Debian Sarge installer.
first time met the cd rom not detected problem and so had to exit.
acting on the advice by mr.kmuto for such problem i booted with the option atapi=true
error no kernel found.
had to exit.
any ideas?

> 
Once you have Sarge installed, perhaps you can upgrade to Ubuntu Edgy (modifying your /etc/apt/sources.list file) or Debian Etch.


> Then again, if you read this page :
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)


that has been my home page the last month!
i have no usb one gig flash drive. mine is 256MB
no adapter avbl here or i am reluctant to spend on it.
so none of the success stories help me.

i tried a netinstall with some other image two weeks back and ended up with a base system installed in hd5 but further progress could not be made with regard to installing further applications.
there were network problems. perhaps the gigbit driver.
i still have that base installation but dont know enough how to build further on that.
:-(
btw mine is an intel DG965RY MoBo

---

### Post by antidrugue on 2006-11-12
[quote=drtvasudevan]
just tried booting with the modified Debian Sarge installer.
first time met the cd rom not detected problem and so had to exit.
acting on the advice by mr.kmuto for such problem i booted with the option atapi=true
error no kernel found.
had to exit.
any ideas?
[/quote]

Which one did you use ? The latest one built on 2.6.19-rc3 ? That one worked for me.


[quote=drtvasudevan]
i have no usb one gig flash drive. mine is 256MB
[/QUOTE]

You could try installing from a USB key using this method :
[http://ubuntuforums.org/showthread.php?p=1694569#post1694569](http://ubuntuforums.org/showthread.php?p=1694569#post1694569)

I did it with a 256mb key, but it would work even with a 64mb one.

---

### Post by drtvasudevan on 2006-11-13
> **antidrugue said:**
> Which one did you use ? The latest one built on 2.6.19-rc3 ? That one worked for me.
sarge custom 1030.  that is the latest in that site of kenshi muto


>  You could try installing from a USB key using this method :
[http://ubuntuforums.org/showthread.php?p=1694569#post1694569](http://ubuntuforums.org/showthread.php?p=1694569#post1694569)

I did it with a 256mb key, but it would work even with a 64mb one.

256  enough? i will have a look.
thanks

---

