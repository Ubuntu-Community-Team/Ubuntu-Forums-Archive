---
title: "Toshiba Portege R835 locking up"
date: 2011-05-17
forum: Hardware
---

### Post by e_racer on 2011-05-17
[LEFT]Just bought a Toshiba Portege R835 that I want to run linux on. Problem is Ubuntu 64/32 and opensuse 64 lock up, followed by the cpu fan spinning out of control.  Like the look and feel of Ubuntu over opensuse, any ideas on why the lockups on the Toshiba R835?
[/LEFT]

---

### Post by e_racer on 2011-05-18
Fedora is working flawlessly, hum.
[B]
[/B]

---

### Post by svast on 2011-05-21
I do not have issue running Ubuntu 11.04 x64 on my Toshiba Satellite R830 (yeah, not branded as a 'Portege', but they do look the same), for the moment...

---

### Post by AciiiD on 2011-05-23
I do have the issue with the Toshiba Portégé R830, with the stock 2.6.38-8 natty kernel : freeze and then the fan is going mad.
Note: alt + ctrl + sys + R/E/I/S/U/B doesn't work when this happen !?

I'd try with the 2.6.39 one, but btrfs keeps kernel panicing my computer...but that's for another thread.

---

### Post by e_racer on 2011-05-24
I was starting to think it was a kernel issue as the same lockup then crazy fan spin now happens with Fedora and Debian also. I will try the 2.6.39, thanks.

---

### Post by e_racer on 2011-05-27
Updated the kernel and no lock-ups for three days and counting.

---

### Post by siar09 on 2011-06-01
Hi everyone! I updated my toshiba portege r830 to the 2.6.39 kernel, and the problem don't dissapear... Ubuntu run more faster, but suddenly happen the freeze and the fan goes crazy... please any have any idea to solve this?? I don't wanna use Windows....

Best regards.

---

### Post by svast on 2011-06-03
I am wondering: is this a kernel, or X issue?

I don't know what log file show the faulty component, but I know that X is not using the accurate driver: i915, instead of HD3000 or whatsoever...
If X is freezing (meaning lock up of display and input), it looks the same as kernel panic!

my 2 cents,
Stephane

---

### Post by e_racer on 2011-06-05
To clarify, I am running kernel 2.6.39 rc4 with natty and still have no lockup issues at all. Of course I have lost the ability to run Toshset.

---

### Post by svast on 2011-06-08
@e_racer : thank you very much for this feedback. It leads to several questions:

1°) how do you use toshset utility, what is it useful for?

2°) I also run Natty, and for now already faced the lockup issue a couple of times. So I would like to test that kernel as well: do you have a magic recipe, or tutorial? How do you install that (ppa, direct compiling from the source)?
Any detailed process (or URL) will be much apreciated :-)

Best regards

---

### Post by MyCarsDead on 2011-06-14
I have been experiencing this exact issue with my toshiba R835-P50, this appears to be a reoccurring problem with the model. I hope someone can find a good fix for this, but I thought I'd mention this is seeming rather consistent.

---

### Post by e_racer on 2011-06-16
> **svast said:**
> @e_racer : thank you very much for this feedback. It leads to several questions:

1°) how do you use toshset utility, what is it useful for?

2°) I also run Natty, and for now already faced the lockup issue a couple of times. So I would like to test that kernel as well: do you have a magic recipe, or tutorial? How do you install that (ppa, direct compiling from the source)?
Any detailed process (or URL) will be much apreciated :-)

Best regards


1. toshset:  [http://www.schwieters.org/toshset/](http://www.schwieters.org/toshset/)

2, .deb file: [http://ubuntuguide.net/how-to-install-linux-kernel-2-6-39-rc4-in-ubuntu-11-04-natty](http://ubuntuguide.net/how-to-install-linux-kernel-2-6-39-rc4-in-ubuntu-11-04-natty)

---

### Post by svast on 2011-06-17
@e_racer: thank you, did not know this site. How about the stable kernel more recently released, did you test it?
 
[http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0](http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0)

---

### Post by e_racer on 2011-06-18
Never tested it, went straight to the rc4. Running kernel 3.0 now and don't see any improvement nor issues.

---

### Post by joshcrack on 2011-06-23
Hey I just wanted to say that I have the same problem on my toshiba r835-p50. Is this fixed with the new kernel or no?

---

### Post by e_racer on 2011-06-24
The kernel 2.6.39 rc4 solved the lockup issue for me on natty, now running kernel 3.0.

---

### Post by Retor on 2011-06-24
I'm on a Toshiba R830, and tried to do the kernel upgrade. (It's now 2.6.39-0 generic). 

I just had another freeze and then the fan went nuts, so for me this still isn't solved. (Also see [this thread]("http://ubuntuforums.org/showthread.php?p=10947395")).

I was only running the Chrome browser when it froze.

---

### Post by Retor on 2011-07-05
Still not solved for me. Others?

---

### Post by theMayor on 2011-07-09
I'm having the same issue. I have a Toshiba r835-p50x. I thought it was just me bug glad(well ... not really) that others are having the same problem. It happens what appears to be randomly. 

If anybody has any fixes, It'd be appreciated.
Thanks!
:popcorn:

---

### Post by Retor on 2011-07-09
Are you also using the 2.6.39 kernel? This seems to have fixed it for many. Not me, though. Guess I'm special. :(

---

### Post by e_racer on 2011-07-12
> **Retor said:**
> Are you also using the 2.6.39 kernel? This seems to have fixed it for many. Not me, though. Guess I'm special. :(

What specific 2.6.39 kernel are you running?

---

### Post by Retor on 2011-07-13
I tried 2.6.39-0-generic first, but still had issues. So I thought it might be since I had 4 GB memory. Therefor I upgraded to PAE, so now I have: 2.6.39-0-generic-pae  - gave me more memory, but still freezes randomly with fan escalating to max. 

More on my efforts here: [http://ubuntuforums.org/showthread.php?t=1784140](http://ubuntuforums.org/showthread.php?t=1784140)

---

### Post by hedrinbc on 2011-07-18
I'm running the 3.0 kernel on 11.04 (Natty) and haven't had a lockup in quite a while, possibly since the upgrade... don't remember specifically. Locked up a ton on stock 11.04 and less but still occasionally on Fedora 15. Will keep you updated. 11.10 will ship with the 3.0 kernel by the way.

---

### Post by BlueCanary9999 on 2011-07-19
Is this a huge problem for R835 owners?  I was considering buying one....

---

### Post by e_racer on 2011-07-19
You need kernel 2.6.39 rc4 or newer, just go install 3.0.


> **Retor said:**
> I tried 2.6.39-0-generic first, but still had issues. So I thought it might be since I had 4 GB memory. Therefor I upgraded to PAE, so now I have: 2.6.39-0-generic-pae  - gave me more memory, but still freezes randomly with fan escalating to max. 

More on my efforts here: [http://ubuntuforums.org/showthread.php?t=1784140](http://ubuntuforums.org/showthread.php?t=1784140)

---

### Post by e_racer on 2011-07-19
> **BlueCanary9999 said:**
> Is this a huge problem for R835 owners?  I was considering buying one....

Not sure but the kernel update is an easy fix.

---

### Post by fenix_1 on 2011-07-22
I have a portege R835-p56x running Ubuntu 11.04 64 4gb ram kernel 2.6.38.10
same problem: freeze and fan going to max speed but only when running on battery.
seems to be solved after installing kernel 2.6.39-020639-generic from this page: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39-oneiric/")
(i folow a link given by e_racer)
thank you all who help on this! much appreciated

---

### Post by BlueCanary9999 on 2011-07-22
I know this isn't the topic, but are there other hardware or driver issues?  Or does everything work once you install that kernel?

---

### Post by enthusaroo on 2011-08-12
I just bought a Toshiba Portégé R835-P56X. I want to install Ubuntu.. I haven't used Linux in years.. but I'm totally sick and tired of Windows.

I tested the latest release of Ubuntu on a "live disk". I was also having the issue of it freezing. So does the RC kernal solve these freezing issues. Are there any other issues specific to the Portege R835? Thanks!

Also will this kernal issue with the Toshiba Portégé R835-P56X be a problem with future releases of Ubuntu? Or after I install the kernal update will it be fixed indefinitely?

---

### Post by BlueCanary9999 on 2011-08-15
> **enthusaroo said:**
> I just bought a Toshiba Portégé R835-P56X. I want to install Ubuntu.. I haven't used Linux in years.. but I'm totally sick and tired of Windows.

I tested the latest release of Ubuntu on a "live disk". I was also having the issue of it freezing. So does the RC kernal solve these freezing issues. Are there any other issues specific to the Portege R835? Thanks!

Also will this kernal issue with the Toshiba Portégé R835-P56X be a problem with future releases of Ubuntu? Or after I install the kernal update will it be fixed indefinitely?

Well I decided to bite the bullet and get this laptop.  Within a few hours I got this locking-up, fan-goes-crazy problem, so I immediately installed that kernel.  Two days later, it happened again.  So I dunno if this is a permanent fix.  Maybe that was just an anomaly?  I haven't noticed any other major problems.

[EDIT]
It just happened again, actually.  These crashes have been happening with 2.6.39. I'll install 3.0.1 and see how that goes.

---

### Post by trowerm on 2011-08-15
I haven't had any issues since updating to 3.0rc7.

---

### Post by Wize Adz on 2011-08-20
The lockups on Ubuntu Natty amd_64 appear to have stopped for me when I updated to the 2.6.39-02063904-generic.

A couple of funny things:
1. I had to use the oneric version of the 2.6.39 kernel, not the natty version.  The lockups continued with the Natty version.
2. When I tried the 3.0.0 and 3.0.3 versions of the kernel, sudo stopped working.  I didn't investigate deeply, just downgraded.

This is slightly offtopic, but has anyone else had issues with adjusting the screen brightness on this laptop after sleep/resume?  I've found that I can adjust the screen brightness using the Fn keys and the GUI tools before the first sleep, but not afterward.

---

### Post by ppsw on 2011-09-26
I also had this problem on my R835, running 11.04.

I recently installed 3.1 kernel from Oneiric, and it seems to be running quite stably (fingers crossed).

These are the files I installed:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-rc2-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-rc2-oneiric/)
linux-headers-3.1.0-0301rc2_3.1.0-0301rc2.201108150905_all.deb
linux-headers-3.1.0-0301rc2-generic_3.1.0-0301rc2.201108150905_amd64.deb
linux-image-3.1.0-0301rc2-generic_3.1.0-0301rc2.201108150905_amd64.deb

As a side plus, cpu frequency scaling using "ondemand" governor is doing its job properly, whereas before it was stuck on 800 MHz. 

Who knows, perhaps they are related.

Although 3.1 supposedly uses more power:
[http://www.phoronix.com/scan.php?page=article&item=linux_31_power_regress&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_31_power_regress&num=1)

---

### Post by clkndk on 2012-02-13
Perhaps my reply to this older post is interesting (still no solution though):
[http://ubuntuforums.org/showthread.php?p=11685212#post11685212](http://ubuntuforums.org/showthread.php?p=11685212#post11685212)

---

