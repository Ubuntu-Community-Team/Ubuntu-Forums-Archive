---
title: "Issue when booting?"
date: 2011-07-01
forum: Hardware
---

### Post by Whispered_Goodbye on 2011-07-01
I'm completely new to Ubuntu - have never even seen it in action before. I installed the wubi version last night but cannot seem to get it to work (I have it installed alongside Windows 7).  

When I choose to boot Ubuntu instead of Windows, it acts like it wants to load but then another screen pops up.  At the top it says GNU GRUB version 1.99~rc1-13ubuntu3, then 3 selectable options of "Ubuntu, Linux 2.6.38-8-generic" or "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" or "Windows 7 (Loader) (on / dev/sda2)".

I have tried selecting all options to get Ubuntu to load - the 1st two options bring up the BIOS? maybe command line...(no I really don't know what I am talking about here ..)

I can get further when I'm in recovery mode, to where it is asking me to login, but then I am stuck when it says:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

username@ubuntu:~$





If this information helps, I am running a brand new (so nothing is really on it) laptop.
Its a Dell Inspiron 15R, Model N5110
Intel Core i5-2410M CPU @ 2.30 GHz
6GB RAM
500GB Harddrive

Can you guys please help me get this running correctly when I can begin figuring out what I am doing? Thank you!

---

### Post by bcbc on 2011-07-01
That's sort of funny (not) since this computer is apparently "certified for ubuntu". [http://www.ubuntu.com/certification/hardware/201012-6932:201101-7008](http://www.ubuntu.com/certification/hardware/201012-6932:201101-7008)

It does say certified with version 10.10 (not 11.04 which you have) so that might be an idea. But it probably has something to do with the graphics. If you have the ability to specify that it should use onboard only (intel) you should do that.

(So don't install graphics drivers for the separate GPU if you have it).
Also if you find the brightness controls don't work once you get it sorted out, check this ppa: [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)

---

### Post by Whispered_Goodbye on 2011-07-01
Thank you for the reply! Though I am unsure how to specify to use onboard only graphics...

---

### Post by bcbc on 2011-07-02
I don't know much about the graphics. Maybe you can check the BIOS settings to see if you can set it to intel only. But I would assume that this should work normally (as the default) - unless you installed a custom graphics driver (but it doesn't sound like this).

So I don't know how much help I can be. You might want to try the 10.10 version and see if you get a better result. Or search for other users that have this model and might be able to help. e.g. perhaps post on this [thread]("http://ubuntuforums.org/showthread.php?t=1706762") (refer to post #21).

---

### Post by Whispered_Goodbye on 2011-07-03
Thank you so much for trying to help :) 

Is there any way to download the wubi version of the 10.10 version? Otherwise..how do I get it to run alongside with Windows?

---

### Post by bcbc on 2011-07-03
You can get the wubi.exe and/or the desktop CD images from [http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)

You might want to burn a CD (or create a bootable USB) - so you can figure out if everything is working before installing. The instructions to do this are found here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) (see Step 2, select CD or USB, and click on SHOW ME HOW)

Note: you can only download 11.04 or 10.04 from that last link, but the instructions to create the CD and USB are the same as for 10.10.

---

### Post by Whispered_Goodbye on 2011-07-03
Alright, I will try that the next time I go to the library :) (limited bandwidth from home desktop & no internet access from laptop...grrr)

I just was trying to mess with it a minute ago and noticed a very quick screen that flashed some text before giving me the options of safe mode ubuntu or not.  I ended up taking a picture of it to figure out what it says. This is the text..

Try (hd0,0): FAT16: No WUBILDR
Try (hd0,1): MTFS5: No wubildr
Try (hd0,2): NTFS5: error: "prefix" is not set.


Does this help anything?

---

### Post by bcbc on 2011-07-03
No. Those are 'normal' wubi messages. Well the Try (hdx,y): is normal grub4dos and the 'error prefix not set' is something that was introduced with grub changes in 11.04 wubi - but it is shown for everyone and not associated with any problems.

Your problems have nothing to do with wubi. It's something that's resulting in booting you to a command prompt.
You could try logging on and then running:
```
sudo service gdm restart
```
See what messages that gives you.

---

### Post by Whispered_Goodbye on 2011-07-04
Hmmmmm....so I restarted my computer to type in the above stuff, but this time I wasn't booted to the command promt. It logged in no problem (for the 1st time) without me changing anything.  

However, now I'm getting a new problem -_-
Now, it seems like there's some graphical/display issues.  I can get into programs and windows no problem, but the windows (not the whole screen) and the mouse pointer all flash to white then back very quickly. Its also making my mouse very laggy when its doing this. 

Would it just be best to reinstall or install a previous version of ubuntu?

---

### Post by bcbc on 2011-07-04
I don't think reinstalling is likely to fix this. Installing a different release is more likely to result in a change. But first, try running all updates: hit Windows key, enter "update-manager".

See if that changes anything.

Try the screen brightness functions keys. Make sure they are working. 

Then if things still look bad, I'd recommend burning a 10.10 CD and running it in 'live CD' mode (hit F12 when the BIOS splash shows, and select to boot from CD/DVD; then select "Try it" without installing). Do this *before* uninstalling 11.04 to save yourself some effort.

PS.. you could also check in BIOS settings F2 and see if you can set the graphics to onboard only.

---

### Post by Whispered_Goodbye on 2011-07-05
I don't have immediate internet access on the laptop so is there any other way I can get those updates?

The brightness keys are functioning perfectly right now.

I found a link in another thread that showed how to create a USB and run it live - I've tried that with 11.04 and still am facing the same graphical issue.  The menu/taskbar and the desktop background are not affected by the problem, only open windows and the mouse.  Strange..I will be making a 10.10 USB or CD tomorrow to see if that works any better..

I don't know where I would find the option to set my graphics to onboard only. When I get into the BIOS settings, I do not see any options to change that?

If this helps with anything, the video cards on the laptop according to the terminal on ubuntu are:
Intel Corporation 2nd Generation Core Process or Family Integrated Graphics Controller (rev 09)

and

ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M]

---

### Post by bcbc on 2011-07-06
You can create package download scripts using Synaptic, but I guess you need to access the repos to know what to download. Maybe you'll just have to wait until you can get online.

There might not be a bios option to set the graphics - it was worth checking.

Again I have to say - I don't know to much about graphics issues. I was hoping someone else was going to jump in on this :p

I hope you have better luck with 10.10.

---

