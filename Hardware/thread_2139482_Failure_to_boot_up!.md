---
title: "Failure to boot up!"
date: 2013-04-27
forum: Hardware
---

### Post by bobbytheman on 2013-04-27
Hi guys I'm new here,
Anyway I have a problem. I had Ubuntu 12.10 running pretty efficiently for a while. I usually remove the crapware like the amazon stuff. However like 4 months ago after the update to a new kernel the system wasn't booting. It would hang on the ubuntu loading screen. I tried cleaning packages and restarting it in fail-safe graphics. This didn't help, but it got worse. After bios it would just go black. I decided to reinstall the whole thing. I tried to load up the ubuntu dvd and the disc hangs when it loads the ubuntu screen. I tried making three news discs all to no avail. I tried reseting bios. The dvd reader is fine. I don't really know what's wrong.

---

### Post by bobbytheman on 2013-04-27
If it helps I have a old hp workstation with a asus radeon 6570, a core 2 duo, and 2 gigs of ram. The hard drive is a old hitachi deskstar.

---

### Post by ppjdee on 2013-04-27
Your computer is not booting at all?
If you have multiple sticks of RAM I would pull one out or swap them and check if it will boot after that.
Sorry I dont fully understand your post, my brain stops working at midnight and its 1am here lol.

You could also try pressing and holding down shift when you reboot to access the grup, and then choose advanced something and boot from a previous kernel.

---

### Post by bobbytheman on 2013-04-27
Sorry my computer boots but after bios it goes blank.

---

### Post by tycoon35 on 2013-04-27
I am really new and not so familiar with Ubuntu either. But if my recent experience is considered, I think your GPU is failing! Try to remove it and restart to check if it is ok. I had a similar problem few days back on a windows machine(planning to get new Graphics Card soon).

---

### Post by ahallubuntu on 2013-04-27
~

---

### Post by bobbytheman on 2013-04-27
> **tycoon35 said:**
> I am really new and not so familiar with Ubuntu either. But if my recent experience is considered, I think your GPU is failing! Try to remove it and restart to check if it is ok. I had a similar problem few days back on a windows machine(planning to get new Graphics Card soon).

If my gpu was failing it wouldn't show anything? right?

---

### Post by bobbytheman on 2013-04-27
> **ahallubuntu said:**
> There's a reason the Hitachi Deskstar earned the nickname "Deathstar."

Check the hard drive's S.M.A.R.T. health.  If you can boot your live CD or live USB, boot it now and start a live session.  Install GSmartControl in the live session, then start it up and check the Attributes tab.  Are any Attributes highlighted in red or pink?  If so, what are they?

You an also get the Linux distro called Parted Magic and do the same thing.  GSmartControl is already installed on it - they call it "Disk Health."

I can't boot any dvd. When it gets to the ubuntu screen with the dots it just freezes.

---

### Post by bobbytheman on 2013-04-27
So no one know what's wrong?

---

### Post by ahallubuntu on 2013-04-27
~

---

### Post by bobbytheman on 2013-04-27
> **ahallubuntu said:**
> What do you mean by "Ubuntu Screen?"  Do you mean the beginning part of booting the DVD?  As soon as you see that, hit the Esc key and see if you can get a boot menu.  One of the choices in the menu is Memtest.  Try running it.  If you get errors, then one or more(?) of your RAM sticks may be bad.

If there are no Memtest errors but you still can't boot the live CD/live USB, try unplugging the hard drive and see if you can boot again.  If you are then able to boot the disc without a hard drive, maybe the hard drive has completely failed.  Sometimes a completely failed hard drive will cause a system to hang when trying to boot.

I get to here: [http://www.linoob.com/wp-content/uploads/2011/04/Ubuntu-Bootscreen.png](http://www.linoob.com/wp-content/uploads/2011/04/Ubuntu-Bootscreen.png)
I don't think the hard drive has failed. It was working and then boom after a reboot it fails?

---

### Post by ahallubuntu on 2013-04-27
By that time shown in your picture, you can't choose a boot menu.   You need to hit the Esc key earlier, as soon as you see this screen (or one very similar - I think this is 12.04):

[http://2.bp.blogspot.com/-Fjw6yl1x3Zc/TVUlk_57J_I/AAAAAAAAAEg/cljA9QoAW7o/s1600/boot.png](http://2.bp.blogspot.com/-Fjw6yl1x3Zc/TVUlk_57J_I/AAAAAAAAAEg/cljA9QoAW7o/s1600/boot.png)

Once you hit the Esc key (hit it a few times) you should get a menu.  Run Memtest from the menu.

If you never see that screen - are you sure that isn't your hard drive booting instead of the disc?

---

### Post by bobbytheman on 2013-04-27
> **ahallubuntu said:**
> By that time shown in your picture, you can't choose a boot menu.   You need to hit the Esc key earlier, as soon as you see this screen (or one very similar - I think this is 12.04):

[http://2.bp.blogspot.com/-Fjw6yl1x3Zc/TVUlk_57J_I/AAAAAAAAAEg/cljA9QoAW7o/s1600/boot.png](http://2.bp.blogspot.com/-Fjw6yl1x3Zc/TVUlk_57J_I/AAAAAAAAAEg/cljA9QoAW7o/s1600/boot.png)

Once you hit the Esc key (hit it a few times) you should get a menu.  Run Memtest from the menu.

If you never see that screen - are you sure that isn't your hard drive booting instead of the disc?

If I boot from my hard drive, after bios it goes blank. I used to get to the Ubuntu boot screen but now it just goes blank.

---

### Post by ahallubuntu on 2013-04-27
OK, you need to boot from the original CD/DVD or live USB you used to install - not from the hard drive.  If you can do that, you can test the RAM and the hard drive.

Do still have an Ubuntu DVD or live USB to boot from?  Do you know how to boot from it instead of from the hard drive?

Yes, I know your hard drive worked until this problem.  Hard drives can fail suddenly.  Don't make any assumptions - test the drive anyway.

---

### Post by bobbytheman on 2013-04-27
ok thanks I will test the hard drive. When i boot up from the disc I hit esc a couple times. Then I go to mem test. Alright thanks I am going to try it and get back to you on that.

---

