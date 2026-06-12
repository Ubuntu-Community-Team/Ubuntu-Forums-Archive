---
title: "Installed video card, wrecked x-windows"
date: 2012-06-20
forum: Hardware
---

### Post by aceprry on 2012-06-20
After installing a video card to replace the on-board graphics, then replacing the drivers, my desktop doesn't function anymore.  The mouse pointer will move around, but I can't click on anything.  The launcher doesn't move up and down for the mouse, and the "top bar" (I forgot the name at this moment), doesn't have any info or titles (time, power button, volume, etc).  I can switch vt into a console and use the system that way, but the x-windows system is hosed.

The original on-board graphics chip (GeForce 6150) was replaced with a Radeon HD 4350 chipset card (pci).  I went through the process of installing the proprietary ATI drivers, using the downloaded binary from AMD, added required software to compile the drivers.  I ripped out the nvidia drivers, reinstalled many times, including trying the open source Radeon driver, the Ubuntu repository's proprietary drivers, etc.  Lots of different things.  The system only boots up into a frozen x-windows desktop (Unity) with a moving mouse pointer, no matter what I've tried.  I've toyed with the idea of reinstalling Ubuntu, but didn't think I should have to do that.

Any ideas or help would be greatly appreciated.

Thanks

---

### Post by QIII on 2012-06-20
There is no need to go through the painful and often fatal process of installing from the ATI binaries.  The 12.4 driver is in the repos.  

Did you first uninstall the NVIDIA driver?  If not, you need to uninstall the other driver before you install the new in the future.  You also need to be sure you set your BIOS to use the dedicated card.

Try uninstalling per ATI's instructions and installing via Additional Drivers.  If that doesn't work, see the link in my signature.

---

### Post by aceprry on 2012-06-20
I didn't uninstall the nvidia drivers at first, but unintalled them later.  The main problem now is that there is no access to the x-windows desktop, so graphical applications are not usable.

If you know what needs to be done through the command line, then I can try it.  Right now, I've got the open-source drivers installed but I still have a locked up desktop.

What I probably need is the set of packages to reinstall that will bring up the desktop in working order.  If anyone has that, I'd be grateful.

Thanks.

---

### Post by typhoon_tip on 2012-06-21
Try to run:
```
unity --reset
```

Ignore all the errors that might appear on the terminal. Do not close the terminal after is done, just logout or reboot.

---

### Post by aceprry on 2012-06-21
I finally got it running, after reinstalling all of unity and compiz. [http://ubuntuforums.org/showpost.php?p=11319420&postcount=4](http://ubuntuforums.org/showpost.php?p=11319420&postcount=4)

BTW, "unity --reset" would hang the computer, so that wasn't going anywhere.

Everything seems to work now, although much slower than when I was using the on-board graphics chip.  Hopefully I can tune it to work faster.

Thanks for everyone's suggestions.

---

### Post by typhoon_tip on 2012-06-21
> **aceprry said:**
> Hopefully I can tune it to work faster.

Thanks for everyone's suggestions.

From an old post of mine:

Try this simple fix, worked for me (I have the compiz idle effect too, but it's not related to the choppy I think... at least not that much !).

- Install fglrx driver (stock driver is choppy...)
- Open AMD Catalyst (after reboot !)
- Enable "tear free" desktop option
- Open compiz config
- OpenGL plugin, untick Sync to VBlank, Texture = BEST, Lighting effect ON
- Composite plugin, Detect refresh rate unticked, set the refresh rate at double your video frequency (in my case 60 Hz, I set it to 120)
- Close compiz
- Log off
- Log in again, it should be now smooth as silk and tear free

Please give me a feedback on this procedure, as it worked for me since 10.04 till 12.04, seems quite consolidated.

Be careful not to touch anything else in those OpenGL and Composite plugins !

---

### Post by aceprry on 2012-06-22
Well, ok... maybe this shouldn't be marked as solved.  :)

Thanks for the tips typhoon.  Unfortunately, I reinstalled ubuntu before I saw your message.  And boy was that quicker than wrangling with the driver.

After the reinstallation, without any drivers, the desktop was pretty responsive.  When I installed the ATI drivers from the ubuntu repo, everything started lagging immediately.  Actually, the desktop wouldn't even start without logging on with the 2D desktop, the 3d desktop doesn't even load fully, and locks up, except for the cursor.  This is what I experienced and didn't realize was happening when I started this thread.

As for typhoon's recommendations, the "tear free" option removed most of the lag from the mouse pointer.  Everything else was still slow.  Before applying all of the other tips, I had to first install the compiz software, which didn't get installed with a clean install.  The result was that everything was much better and smoother, not as good as when I first booted up without any special drivers though.  The ATI driver seems to act as a video decelerator, doesn't really allow booting into the 3d desktop, and doesn't add any video acceleration as promised by the driver.

Essentially, this card is a complete waste of time and money.  I wanted to free up some memory from the onboard graphics chip, add 3d and video acceleration to my older hardware but found out that this ATI/AMD card is really worthless.  The onboard GeForce chipset performs MUCH better and very smoothly.  I'm glad I paid less than $15 for the ATI card though.

---

### Post by typhoon_tip on 2012-06-22
The "SYNC TO VBLANK" of compiz heavily interferes with the one in ATI driver, and must be disabled. Moreover, make sure that you have a configured xorg.conf file in /etc/X11/

The radeon open source driver works fine in 12.04, but the temperature of the GPU is always sky-high.

Do the steps above, and if you cannot find xorg.conf file, type:
```
sudo amdconfig --initial -f
```

Or..
```
sudo aticonfig --initial -f
```

And the file will be created, then reboot. It will be as smooth as silk.

---

### Post by aceprry on 2012-06-25
Just to be completely clear, I followed all of the steps suggested:

<quote>
- Install fglrx driver (stock driver is choppy...)
- Open AMD Catalyst (after reboot !)
- Enable "tear free" desktop option
- Open compiz config
- OpenGL plugin, untick Sync to VBlank, Texture = BEST, Lighting effect ON
- Composite plugin, Detect refresh rate unticked, set the refresh rate at double your video frequency (in my case 60 Hz, I set it to 120)
- Close compiz
- Log off
- Log in again, it should be now smooth as silk and tear free
</quote>

So everything that I wrote in post #7 is the end result.  No need to go through all of that again because I've taken out the card and started using the onboard graphics chip again.  Which works so much better than the ATI video graphics card.

---

### Post by typhoon_tip on 2012-06-25
> **aceprry said:**
> No need to go through all of that again because I've taken out the card and started using the onboard graphics chip again.  Which works so much better than the ATI video graphics card.

Point of view, since is a quite established and well known procedure for ATI around all the Ubuntu community. Enjoy your Ubuntu anyway ! ;)

---

### Post by kaldor on 2012-06-25
This might not be the best advice, but is it possible you could just use the open source driver in this situation? It'll be slower than using Fglrx, but the 4000 series ATI cards have overall great support for the default driver. 

It should also allow you to do basic 3d gaming as well; with a low end ATI/AMD card, I'm assuming gaming wasn't your goal anyway. There are some PPAs that keep your graphics in sync with upstream, too.

---

### Post by aceprry on 2012-06-27
> **kaldor said:**
> This might not be the best advice, but is it possible you could just use the open source driver in this situation? It'll be slower than using Fglrx, but the 4000 series ATI cards have overall great support for the default driver. 

It should also allow you to do basic 3d gaming as well; with a low end ATI/AMD card, I'm assuming gaming wasn't your goal anyway. There are some PPAs that keep your graphics in sync with upstream, too.

In the original post, I stated that I used the open source driver.  None of the ATI drivers that I tried worked well.  They all cause lagginess, prevented video files from displaying, and overall poor performance.

---

