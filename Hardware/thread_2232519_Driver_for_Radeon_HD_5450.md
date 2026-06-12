---
title: "Driver for Radeon HD 5450"
date: 2014-07-02
forum: Hardware
---

### Post by rbuxton on 2014-07-02
Hey,
 Im currently running Ubuntu 12.04 LTS and as you could probably guess from the title, have a [Saphire Radeon HD 5450]("http://www.sapphiretech.com/presentation/product/product_index.aspx?pid=316&lid=1"). My problem is I do not now which video driver would be the best for this specific card. I enjoy playing games like Garry's Mod and Minecraft with my friends and getting the best performance possible is big to me.
These are my choices under the Additional Drivers tab:
[LIST]
[*]ATI/AMD proprietary FGLRX graphics driver (This one appers to only be good for ATI cards and I think that is not what I have)
[*]ATI/AMD proprietary FGLRX graphics driver (**Experimental**beta) (This one does provide support and is the one suggested by Steam, but lowers performance on about everything else other than GMod)
[*]ATI/AMD proprietary FGLRX graphics driver (Post-release updates) (Same as first, but some what more recent. Works nice with Minecraft)
[/LIST]
Also if it helps at all this is all running on a Dell Optiplex GX620.

(Oh, and I am still relatively new the forums, if you spot a error I made please notify me, I will do my best to fix it. Thanks!)

---

### Post by QIII on 2014-07-02
Hello!

You are most definitely using an ATI GPU.  Sapphire is one of many companies that use ATI GPUs -- they source their own PCBs and other components to make the slick "card" you pull out of the box.  But the engine is built by AMD/ATI.

As for which driver is best ...

If the default open source Radeon driver works well for you, you may as well use that.  It has gotten very good over the last couple of years.

If you really need the proprietary ATI driver, go with the -updates version from the repo, which is what I am using right now.  I occasionally download and install the very latest from AMD/ATI for testing purposes, then go back to the one in the repo just so I am aligned.

The following is not *supposed *to be necessary any longer, but as many as I have helped through it I still recommend doing the following in the terminal AFTER installing the driver and BEFORE rebooting:

```
sudo amdconfig --initial
```

Cheers!

---

### Post by rbuxton on 2014-07-02
Thanks for the reply!
What do you mean by the '-updates version from the repo'? Is there a driver that I am missing some where? I thought the proprietary driver was the end-all-be-all other than the default Ubuntu video driver.
Thanks again.

---

### Post by Yellow Pasque on 2014-07-02
QIII is referring to the 3rd option (post-release updates).

---

### Post by rbuxton on 2014-07-02
Thank you for the clarification! So I should install it and then run the code right after it has installed correct?

---

### Post by squakie on 2014-07-03
I would first remove flgrx:

sudo apt-get remove fglrx <press enter>

If it says not found that's ok.

Then:

sudo apt-get install fglrx-updates <press enter>


I had that same card in the last desktop I had (less than a year ago).  I had to install fglrx-updates to use the card correctly.

You can also do this through the package manager.  If synaptic package manager is not installed (it isn't by default with the "newer" Ubuntu's) install it via:

sudo apt-get install synaptic <press enter>

After that finishes, you can find synaptic in the menus - start it.  Enter fglrx in the search string.  Mark the "normal" fglrx packages for removal and mark the fgrx-updates package for install, then click apply.

Reboot when that is all done.

---

### Post by rbuxton on 2014-07-03
So, I shout deactivate the current driver, remove fglrx, then reactivate the post-release driver after a reboot?

Thanks for the patience I really appreciate all the help I'm getting.

---

### Post by Yellow Pasque on 2014-07-03
The bottom line is that the 3 options are all different releases of the same driver. Just use whichever one works best.

Steam probably recommends beta fglrx/Catalyst versions to cover owners of the latest cards.

---

### Post by rbuxton on 2014-07-03
Yeah, it is recommending the latest I believe.. I will try the uninstalling of fglrx trick and tell you how it goes.

---

### Post by squakie on 2014-07-03
That's why I said fglrx-updates.  I had the card.  It wasn't supported in fglrx worth a dang, fglrx-updates has direct support for the card.  Of course, that's just my experience.  Same card.  Also had a HD6450 and had to use the same driver.

---

### Post by rbuxton on 2014-07-03
You lost me squakie. Disable whatever proprietary driver I have on, do your fglrx trick then reboot, and then activate the best driver or do I just go with fglrx-updates package?
Thanks

---

### Post by squakie on 2014-07-04
I *think* if you just do the following the removal of fglrx and the installation of fglrx-updates will be done:

sudo apt-get install fglrx-updates

You may also want to try what QIII said -  	sudo amdconfig --initial

I haven't ever used that after installing the driver - don't know if I should have or not ;)


After that, just reboot.

Sure *hope* that works for you.

---

### Post by rbuxton on 2014-07-04
Sorry about the wait. 
I got around to doing this after a break from the endless array of screens that is my desk, and when I run the uninstall of fglrx, it wasnt found! I felt that was a clear indication but I still continued and ran the install of fglrx-updates and found that it was already installed. I ran Qlll's command, and now I've got some strange occasional lag but I figure that's either from not having turned it on for a while or the sheer size of my monitor.
Anyway, I think I got it running as well as I can. Thanks for all the help getting it here!

---

### Post by squakie on 2014-07-05
Sorry I couldn't have been of more help.  I'll keep this thread in mind in case I run across something in the future.

---

### Post by jp734 on 2014-07-05
I've been using Lubuntu 13.10 since it was released and used synaptic to install fglrx, **NOT the fglrx-updates**, and never had any problem. And I'm using two video cards hd5450, driving three monitors. Not sure what's the big difference between Lubuntu 13.10 and Ubuntu 12.04 LTS, but I thought I'd share the experience.

---

