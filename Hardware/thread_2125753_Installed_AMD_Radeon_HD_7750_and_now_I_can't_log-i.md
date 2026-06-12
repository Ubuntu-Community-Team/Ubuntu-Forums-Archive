---
title: "Installed AMD Radeon HD 7750 and now I can't log-in"
date: 2013-03-14
forum: Hardware
---

### Post by penn919 on 2013-03-14
Hi,

I recently upgraded my GPU from a Radeon HD 6670 to a Radeon HD 7750 and now my log-in screen stays frozen when I try to boot into Ubuntu 12.04. I guess I should've remembered to remove the previous AMD proprietary driver before I upgraded, but I forgot. 

Here are a couple things I've tried so far (which were suggestions I read from searching these forums):

1. Re-configuring my xorg file via ```
sudo dpkg-reconfigure xserver-xorg
```

2. Removing xorg.conf via ```
sudo rm /etc/X11/xorg.conf
``` and then rebooting.

I should also note that the graphic failsafex mode doesn't work, so I had to drop to root shell prompt in recovery mode to use the commands.

Any help would be appreciated.

Thanks

---

### Post by QIII on 2013-03-15
12.04.2?

---

### Post by penn919 on 2013-03-15
> **QIII said:**
> 12.04.2?

I think it was just 12.04, but it's entirely possible I have 12.04.2....I guess. idk

---

### Post by QIII on 2013-03-15
OK.  

Did you install the driver originally from the repo (using the terminal or the additional drivers GUI) or from the ATI website?

---

### Post by penn919 on 2013-03-15
> **QIII said:**
> OK.  

Did you install the driver originally from the repo (using the terminal or the additional drivers GUI) or from the ATI website?

I used the additional drivers GUI, so it's from the repo.

---

### Post by QIII on 2013-03-15
Watch this space.  On cellphone on train on way to work.  Will try to get back to this in the next few hours and edit this post.

---

### Post by penn919 on 2013-03-15
Sure. I'll keep checking back throughout the day.

---

### Post by penn919 on 2013-03-15
Bump

---

### Post by QIII on 2013-03-16
Sorry it took so long to get to this.

Let's start from the top and make sure we cover all the bases.

Uninstall whatever may be there now:
```
sudo apt-get purge fglrx fglrx-amdcccle
```

Reboot.  This should get you back to the open source Radeon driver, which is installed by default.

Then install generic linux headers (this my not be necessary or they may already be there, but do it anyway):
```
sudo apt-get install linux-headers-generic
```

You shouldn't need to, but reboot here, too.

Then install the driver:
```
sudo apt-get install fglrx fglrx-amdcccle
```
```
sudo amdconfig --initial
```

Reboot.

You should be running the ATI driver, but you will probably have to make adjustments through the Catalyst Control Center.  For some reason this often fails to launch from the icon, so just go back to the terminal:
```
gksudo amdcccle
```

IMPORTANT NOTE:  Notice the "gksudo".  Graphical applications should always be started using gksudo rather than sudo.  Using sudo to start graphical apps can cause no end of permissions issues later.

---

### Post by penn919 on 2013-03-16
> **QIII said:**
> Sorry it took so long to get to this.

Let's start from the top and make sure we cover all the bases....



I followed all the steps above; however the only difference now is that when I reach the log-in screen there's a watermark in the lower right-hand corner of the screen that has AMD's logo and "Testing use only" written below it.

The log-in screen is still frozen.

---

### Post by onilink422 on 2013-03-16
I myself am having issues with this driver, if you were able to log in before, you can restore this by doing

```
sudo apt-get remove --purge fglrx
```
however, you will still not have graphics acceleration.

Also, downgrading your xserver may help due to a discontinuation of support.

```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```
```
sudo dpkg-reconfigure xserver-xorg
```

then reboot, if you are having trouble rebooting try
```
sudo reboot
```

---

### Post by penn919 on 2013-03-16
> **onilink422 said:**
> I myself am having issues with this driver, if you were able to log in before, you can restore this by doing

```
sudo apt-get remove --purge fglrx
```
however, you will still not have graphics acceleration.

Yep. I was able to log-in, but it would really be nice If I could get acceleration back :(

---

### Post by onilink422 on 2013-03-16
I am pretty sure that these drivers are now legacy, so we probably will not see support for them anytime soon, we will have to rely on open source alternatives provided. Someone may have a different approach though, that would be nice.

---

### Post by QIII on 2013-03-16
[This]("http://askubuntu.com/questions/25519/how-to-remove-amd-unsupported-hardware-without-reinstalling-the-driver") should help you get rid of the watermark.

And section 4 in [this]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") should help you get the little bit of acceleration that the fglrx driver supports.

---

### Post by penn919 on 2013-03-16
> **QIII said:**
> [This]("http://askubuntu.com/questions/25519/how-to-remove-amd-unsupported-hardware-without-reinstalling-the-driver") should help you get rid of the watermark.

And section 4 in [this]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") should help you get the little bit of acceleration that the fglrx driver supports.

The watermark was removed after I purged fglrx; however, the freeze problem has returned again.

I left the computer for a while and when I returned the screen lock was frozen so I had to reboot. Unfortunately, when the log-in screen appeared it was frozen yet again. I did a few more reboots and I got the same results.

Any other suggestions?

---

### Post by QIII on 2013-03-16
So currently you do not have the fglrx driver installed?

---

### Post by penn919 on 2013-03-16
Correct. I tried the commands you posted, but my log-in screen was still frozen so I couldn't log-in to finish the final steps. I then tried onilink422's suggestions which entailed purging fglrx and reinstalling libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core. It allowed me to finally log-in, but it froze again.

While I was logged-in I checked additional drivers and confirmed that Fglrx was indeed uninstalled.

---

### Post by kmsalex on 2013-03-30
Experiencing same issues as you. Ubuntu 12.04.2.

If you install either the 12.8 Catalyst from the AMD site or the "Post release" update from the additional drivers menu you can have a working desktop.... but not a working loin.
From all the hours of research I've done the ultimate problem seams actually to the fact that the driver breaks sound.  Remember that little drum beat sound as the log in screen (lightdm) lunches? well there's a bug in it that causes it to freeze if the sound is disabled. 

Now the HD 7750 comes with an HDMI port that can output sound, the driver is broken so that it doesn't allow sound to be passed like it should. I have on board audio, that wasn't working. So disabled on board audio in the bios and tried throwing in a old SB0200 that didn't work. After trying multiple solutions to get sound working (see this post for a few ideas [http://askubuntu.com/questions/223549/no-sound-after-video-card-replaced-amd-radeon-hd-7770](http://askubuntu.com/questions/223549/no-sound-after-video-card-replaced-amd-radeon-hd-7770) ) I still have nothing. Clicking on the sound icon gives me a little (--) and trying to lunch the sound menu in system settings causes the settings to hang. Also tired a slew of sound management programs from the software center.

Now someone said there was a fix for the the bug in lightdm in the "postrelease" updates, so I enabled them and pulled down all the updates and no improvement. Though as you can tell I can login, do a ctrl+alt+f1, log in and do

```
ctrl+alt+f1

sudo service lightdm restart
```

With that hopefully you can get into a desktop with fully functional acceleration at least (amusing you've installed the "post-release" driver or catalyst 12.8 from the website)

The workaround for me at the moment is to enable auto log in, but this ins't my main computer its for the family so more then one person has to log in on a day to day basis so this is by no means a permanit solution.

Can other confirm that they have no sound/enabling auto log in work for them?
Hope I've been of some help since there seams to be so much truble with this card.

---

### Post by kmsalex on 2013-03-31
I've found that installing 13.04 and using Catalyst 13.3 beta 3 has nearly everything working perfect.

[http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-3LINBetaDriver.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-3LINBetaDriver.aspx)

Though my problem is that it seams to break something with opencl. My personal problem being that bitminter doesn't detect and opencl GPU's under Catalyst 13.X....
But it does seam that the problem has been the driver and that AMD has been working on fixing the problem.

I'd recomand giving 13.04 and 13.3 beta 3 a spin.

---

### Post by Kai_F._Lahmann on 2013-10-15
I got it! The problem is *not* the graphics part, it's the audio part! Even worse, it even blocks from switching to the onboard Audio or another card. And so I wondered, if I can disable the (broken) HDMI-Audio on the 7750 card. And bingo: **Just add 'blacklist snd-hda-codec-hdmi' to /etc/modprobe.d/blacklist.conf and the Audio device is disabled.** I won't be surprised, if with this short fix you can even use the old fglrx 12.4 (despite getting the 'unsupported' warning).

---

### Post by heir4c on 2013-10-15
Edit: I missed some part of the tread I see. I have to quickly responded to a post and don't see the other pages. Therefore my answer is a little bit late and I think no more relevant.  sorry.


to inform you:
[http://askubuntu.com/questions/206558/how-to-remove-the-amd-testing-use-only-watermark](http://askubuntu.com/questions/206558/how-to-remove-the-amd-testing-use-only-watermark)
[http://support.amd.com/en-us/download](http://support.amd.com/en-us/download)
First try to remove the fglrx driver and to boot up Ubuntu with the open source driver. If that works than you can go to Software&Updates and there you can go to the last Tab. See what drivers there be recommended.
Try this and if no luck, than download the driver from the AMD website and install it. (Search for your care)
But if its work on the OpenSource driver, keep these to run Ubuntu. Here it works fine for me. (APU E-350 with  HD 6310 but works also with my Sapphire HD 7750 and 7770. Not only the OpenSource but even the fglrx).

---

