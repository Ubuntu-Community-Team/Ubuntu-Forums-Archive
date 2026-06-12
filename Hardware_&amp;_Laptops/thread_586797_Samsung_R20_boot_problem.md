---
title: "Samsung R20 boot problem"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by zoomcookie on 2007-10-22
Hi Everyone,

With the release of 7.10 I decided to give Ubuntu another try.  I ran Ubuntu on my old Toshiba laptop but since 'upgrading' to this Samsung R20, Linux has become a complete headache. I think most of my problems stem from the terrible ATI chipset.

Anyway, I installed OK  from the alternate CD in text mode. When booting it gets as far as:

running local boot scripts (/etc/rc.local)            OK

Then just stops and goes no further. I should add that every distro I have tried on this laptop seems to take forever to do anything. I got SuSE to work but the boot process seemed to keep stopping requiring me to tap random keys or trackpad to get the process going again.

On this craptop Ubuntu is my last attempt at Linux. It has just proved too much of a headache. Even if I get past this problem I know I still have to get the graphics working. Sorry to sound so negative. I like Linux but my patience is wearing thin.

Please help!

Thanks

---

### Post by serial_strat on 2007-10-24
Well, I'm having exactly the same problem. After some trials I feel the problem is related to X Server not starting. However for now I have no solution...:confused:

---

### Post by Nikos.Alexandris on 2007-10-25
This should work... : [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

But you need of course to boot somehow first (if you do a fresh install). You should try to install with the alternate CD. There is an older post which describes the steps (but for edgy!) [http://ubuntuforums.org/showthread.php?t=396751&highlight=samsung+r20](http://ubuntuforums.org/showthread.php?t=396751&highlight=samsung+r20)

and another more recent (I really don't know if somebody provided till now a clearly step-by-step method to install through the alternate gutsy CD... but maybe somebody will) [http://ubuntuforums.org/showthread.php?t=582908&highlight=samsung+r20](http://ubuntuforums.org/showthread.php?t=582908&highlight=samsung+r20)

and

[http://ubuntuforums.org/showthread.php?t=591050&highlight=ati+1250](http://ubuntuforums.org/showthread.php?t=591050&highlight=ati+1250)

Once you got your system to boot (without starting X) then you should be able to follow the unofficial ATI wiki guide.

---

### Post by viterico on 2007-11-07
I have the same problem and the solution is not in these links. This is the solution for fix the ati problem (start x system) The problem is the stoppings that makes the laptop with gutsy and NOT WITH FEISTY... WHY¿? Maybe a problem in the new kernel, maybe other daemon? I read that a guy make a downgrade with the kernel to put the kernel of feisty and everything was ok with this.... I don't know... any solution for us?

Thanks in advance!..

Sorry for my english... :-X

---

### Post by mwk on 2007-11-07
I've got an R20, which is now running GG fairly well, but still has similar problems.

I had to install from the alternate CD, which worked eventually, but with some interesting "quirks".

I don't remember my exact steps, sorry, but I do know that it required me to press the space-bar every few seconds for it to continue installing. Nothing ASKED me to press the space-bar, nothing told me that I would need to press the space-bar after every line or two of installation output, but unless I did, it would just sit there doing nothing. Well, apart from the times that the space-bar did nothing, and I had to press return or backspace instead. Again, no idea why I had to, but it made it work.

Now I just have the irritant of having to do similar every time I boot up or shut down. Unless I hit one of those three keys (and it has to be the right one, not just one chosen at random), everything stops. When the right key is hit, the hard-drive suddenly springs to life and everything carries on loading as normal until it decides to stop again.

Personally, I'm pretty sure it's a hardware issue. When I was installing I had a lot of trouble convincing a lot of things that the HDD even existed. Various Live CDs that I was using to try and format the machine insisted that there was no HDD installed, and the Ubuntu live CD just failed to start altogether. I assume it's to do with the ATI components, as nothing I bring up seems to even know what most of them are.

---

Oh, and as an aside, if anyone's interested, Samsung believe that the Windows OEM EULA doesn't apply to them, so getting a windows refund would probably require some sort of legal action.

---

### Post by Schnitzelpudding on 2007-11-11
Same problem here - boot process/hardware detection hangs at various points until I start pressing keys or use the touchpad. This didn't happen with 7.04...

---

### Post by viterico on 2007-12-18
I have resolved this problem putting the feisty repos en sources.list. After the apt-get update you can go to synaptic and put the old kernel 2.6.20 and non free modules and headers if you want...etc...
You can boot in grub from this kernel or directly delete the most modern kernel 2.6.22 when all is ok.
If you have the ati drivers instaled remember that you must to reinstall because this is a diferent kernel. You can have X but not acceleration until you make this again.
After this, remember put the old source.list for gutsy.
I did this and all is ok... It's a problem of acpi in the new kernel with our bios (r20 samsung).
Kind regards, (sorry for my english)

---

