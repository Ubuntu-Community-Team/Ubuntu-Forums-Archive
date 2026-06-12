---
title: "Problems installing Ubuntu on laptop"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by Agent.Logic_ on 2009-04-02
Hi,

I installed Ubuntu on my desktop PC a few months ago and completely fell in love with it. So much so that I wanted to install it completely on my laptop. However, I couldn't get the LiveCD working properly. I tried the noapic, acpi=off, nolapic options, and different combinations of those, but regardless of that, I would see the default Ubuntu LiveCD wallpaper, and the installation window starting, and right there it would hang. Same deal with Xubuntu.

Here is a screenshot of my system specs:
[[IMG]http://img3.imageshack.us/img3/118/sysinfo.th.png[/IMG]](http://img3.imageshack.us/my.php?image=sysinfo.png)

After getting impatient, I downloaded the alternate CD and tried installing from that. Look at how my laptop displays the menu:
[[IMG]http://img3.imageshack.us/img3/5900/image068r.th.jpg[/IMG]](http://img3.imageshack.us/my.php?image=image068r.jpg)

[[IMG]http://img6.imageshack.us/img6/8276/image000bfr.th.jpg[/IMG]](http://img6.imageshack.us/my.php?image=image000bfr.jpg)

My PC monitor displays the same thing when I connect that to the laptop. I'm guessing this is a motherboard/chipset incompatibility issue? I'm dreading at the thought that my laptop is made only to support M$. :(

---

### Post by b@sh_n3rd on 2009-04-02
Hi, The pics look as if it's a video issue. Ubuntu doesn't seem to detect your video card's resolution in text-mode. I have an older system which hangs when i boot with the livecd though i don't get any distorted screens. It just stalls at boot when loading X in the livecd session with a blank screen. I was able to get around it by hitting F4 from the boot menu of the livecd and selecting, "safe mode graphics" from the pop-up menu that appears. After that i selected the first command to boot into the livecd session. This worked fine without any problems thereafter.  But in my case, the system didn't boot at all and i was using Ubuntu, not Xubuntu. If you were able to boot and use it before, then it possibly couldn't be video.

---

### Post by tlois on 2009-04-02
Is it possible that you are using rewritable cds?  I spent days trying to install 8.10 on my older thinkpad, only to discover that for whatever reason, when I used 8.10 I had made on a regular cd, it worked.  I tested out the theory with some other Linux os's I had made on the rewritable cds (and another type-48x I think)- same thing- hung on splash screen.

Anyway.  Good luck.  You'll get it working.

---

### Post by Agent.Logic_ on 2009-04-02
Hi b@sh_n3rd and tlois,

Thanks for your replies! I think I used the "safe graphics" mode on the LiveCD, which is the only reason I could have it boot upto the default wallpaper and the semi-transparent installation menu. After that, it hung up on me. But for the heck of it, I'll try the safe graphics mode and post updates.

@tlois: I think you might be correct! I am indeed using rewritable CD's, both for ubuntu Live/alternate CD's and for Xubuntu! But ubuntu installed without coughing up a single error on my desktop, I was using the same rewritable CD. Does this apply only to laptops then? I'll try and find a regular CD and check back here.

Cheers mates! :D Thanks again for your replies!

---

### Post by b@sh_n3rd on 2009-04-02
Hey, does that mean I can't use re-writables for linux installations? coz I was thinking of buying one so that I could save some money for each time I update my Ubuntu CD's. And I tend to use it for troubleshooting purposes. Furthermore, I read somewhere that when burning distro images to disk it's best to write at a higher quality rate which helps prevent various problems, including installation, on the livecd. Could this overcome the CD-RW problem, if any, or will I have to record on normal CD-R's?

---

### Post by Agent.Logic_ on 2009-04-02
Update 1:

Well, I tried the safe graphics mode again, along with acpi=off and noapic, and it only coughed up one error: BIOS bug #81 found. Definitely an improvement, or so I thought... after all that, I saw it render a glitchy "Windows is shutting down" message that is shown when you log out of Windoze. Where did that come from??? Then it rendered the glitchy startup message I get from my laptop vendor. Then the blank screen. So I guess I'm down to trying out installing from a regular CD. I'm wrting it as I type this. Will get back with the results.

Cheers.

---

### Post by xaos on 2009-04-02
just my 2 cents:

I run into trouble recently as well installing ubuntu on a laptop, after some googling I found out that sometimes laptops and specially the CD drives can get very hot resulting in read errors. I don't know if it applies for you as well, but you might trying to shut down your computer and let it cool and then install from a cold boot. Also, my guess is the rewritable CDs are more error prone, I always burn linux distro CDs at the lowest possible writing speed to minimize possibility of errors.

Hope it works for you!

---

### Post by b@sh_n3rd on 2009-04-02
Hey Agent.Logic_ when u say "glitchy", what exactly does it look like? like lines on the screen or something?

---

### Post by Agent.Logic_ on 2009-04-02
Thanks for your reply xaos! Of the many tries installing Ubuntu on my laptop, a good number of them were on cold boot. But I had burnt the rewritable CD's on maximum speed, maybe that was it. I burnt the CD-R at half speed, and with safe graphics mode, it finally works. But there is the proverbial catch that comes along when you finally figure out a way to make something work! On step 4 of the installation where you prepare the partitions, none show up. It's empty! What is up with that?

---

### Post by Agent.Logic_ on 2009-04-02
> **b@sh_n3rd said:**
> Hey Agent.Logic_ when u say "glitchy", what exactly does it look like? like lines on the screen or something?
Hmmm, how do I put it... something like a 4-bit bitmap version of said screens, you could say. I also saw the ubuntu load screen, with the meter in the halfway mark. It disappeared quickly, so I couldn't take a picture. There were 8 tiles (4 columns x 2 rows) of the ubuntu load screens on top, the intel startup logo below it, then the Microsoft shutdown screen below that one. Must be a display adapter issue, I guess. It only lasts a moment.

---

### Post by b@sh_n3rd on 2009-04-02
what i really don't like about laptops is the cost and heating...then again i can't customize it myself..where i live a laptop is quite expensive..
anyways, when it get's hot, the video adapter might tend to draw some crappy images...it happened to me on a desktop comp...

---

### Post by Agent.Logic_ on 2009-04-02
Same here mate. Laptops are just too f***in' costly, and coming from a tropical country, heating is inevitable! I managed to get a quick shot of the 4-bit/8-bit screen, I'm putting it here just for the heck of it, in case anyone has this problem in the future.

[[IMG]http://img4.imageshack.us/img4/9764/image070a.th.jpg[/IMG]](http://img4.imageshack.us/my.php?image=image070a.jpg)

I finally managed to install Ubuntu successfully on my laptop using a LiveCD. I still wonder why CD-RW LiveCD works on my desktop but not on my laptop.

And now, I'm stuck with Ubuntu booting to a blank screen. Just wondering what the grub commands are for safe graphics boot, so that I might be able to configure the xserver/xorg configuration files or whatever. Any pointers?

**EDIT**: It seems that Ubuntu locks up after the blank screen, because I can't get it to go to the command line interface by pressing ctrl+alt+f#. How can I make it boot in safe graphics mode?

---

### Post by b@sh_n3rd on 2009-04-03
Then it could be a driver issue since it freezes with a blanks screen. Thats exactly what happened to my system. How old is your laptop btw? To boot in safe mode graphics I think u need to load those drivers at boot. For that, u will have to edit whatever file via the LiveCD, which would be easiest. I'll check up on that for you. And, previously, I was never able to find what kind of video card you have.

---

### Post by b@sh_n3rd on 2009-04-03
Hey, you can boot into recovery mode in your ubuntu installation by hitting ESC just before GRUB loads, and selecting "Recovery Mode" from the menu. Then, once you boot into recovery mode you can reconfigure your X Server. You can check the second post on the following thread for more info. [http://ubuntuforums.org/showthread.php?t=67884811](http://ubuntuforums.org/showthread.php?t=67884811)

---

### Post by Agent.Logic_ on 2009-04-03
Thanks for the heads up, b@sh_n3rd! My laptop is fairly new, about a year old. It's a 1.46GHz pentium dual core with 1GB RAM. But for some reason, the manufacturer opted for VIA display adapter rather than some fairly decent one. I have never even heard of VIA before. Anyway, I'm due for a new laptop, talked my bro into a favour lol, 'cause I'm fed up with the heat it generates and the touchpad buttons slowly becoming non-functional.

Yeah, I read a few threads on X Server configuration. Nothing too simple though, all of them were full of 1337 speak, sigh. The link you posted isn't working, it gives me a "No Thread specified. If you followed a valid link, please notify the administrator" message. What's up with that? Also, when I do a **dpkg-reconfigure xserver-xorg** which is supposed to bring up the settings for the video adapter, I only get a screen for keyboard settings. After I'm done with the keyboard settings (I just set everything to default), the configuration ends, with no display configuration coming up at all.

After hours of playing around with a CD-RW LiveCD, only to find out it is best to use a CD-R, then writing the LiveCD image to a CD-R, installing Ubuntu only to get the blank screen at boot, then downloading Xubuntu to see if I have better luck and only to find out at 35% installation progress that there has been a write error so it aborts, so installing Ubuntu again and are still stuck with the blank screen with no decent google hits on the issue, I guess it's safe to say that I'm *somewhat* exhausted. :P

---

### Post by Agent.Logic_ on 2009-04-03
OK, after a bit of googling, I did a **nano /etc/X11/xorg.conf**, and the contents of the config file are as follows:

```
Section "Device"
<tab> Identifier <tab> "Configured Video Device"
<tab> Driver <tab> "vesa"
EndSection

Section "Monitor"
<tab> Identifier <tab> "Configured Monitor"
EndSection

Section "Screen"
<tab> Identifier <tab> "Default Screen"
<tab> Monitor <tab> "Configured Monitor"
<tab> Device <tab> "Configured Video Device"
EndSection
```

As far as I can see, it should work because Vesa worked fine when I used the LiveCD (safe graphics) to install Ubuntu...

---

### Post by b@sh_n3rd on 2009-04-03
woops, srry about that...I usually check my URL's. It seems to have two extra digits at the end. "11". If your machine is about a year old it oughta be some bugs with the drivers or something to do with your laptop. To tell you the truth I haven't had many problems on any of my Ubuntu systems so I'm quite inexperienced with that xorg command and "Recovery Mode".

PS: If you're gonna get a new laptop, why not get a dell? it IS expensive but awfully reliable. This desktop im using is a dell and it's 11yrs old this month. I never have any probs with it. Anyways, good luck. (I really dislike laptops cuz the one "we" had got destroyed for an expired batt. which leaked all over the mainboard. Lost about SLR.34,000 on that, but portability is a quality one wouldn't easily forget.)

---

### Post by Agent.Logic_ on 2009-04-03
Ah yes, the link works now. I tried reconfiguring the X Server, but like I said in a previous post, the reconfiguration ends with just a few questions about the keyboard layout. :( Turns out that **dpkg-reconfigure xserver-xorg** only works for Fiesty and below, as posted [here](http://ubuntuforums.org/showthread.php?t=690760). Later versions auto-configure themselves, apparently. I think I have hit a dead end for the moment. Gotta work on my uni assignments before getting back to breaking my head over this little problem!

Regarding Dell, you read my mind mate! I'm indeed looking for an "affordable" Dell machine. :D Woah, a 11 year old desktop :O. Never heard of anyone using a PC that long! Ah, battery leaks are a menace. I'm lucky to even have my laptop battery maintaining it's capacity over the last one year. But I'm beginning to get disgusted with it. Anything that is specifically made to run Windows and refuses to run linux deserves to be thrown out the window!

Cheers mate.

---

### Post by Agent.Logic_ on 2009-04-03
Well, I've made *some* progress since breaking my head over college assignments. I read about the OpenChrome driver which was apparently specifically made for VIA chipsets. Installed it from the shell prompt @ recovery mode, and now instead of the black screen, I get a white screen. :D I guess I have to play around with the OpenChrome settings until the laptop is happy. :(

---

### Post by b@sh_n3rd on 2009-04-03
Hey, it seems that your installation IS suffering from a video driver issue (or defect :D). It's automatically installed on Hardy but not on Intrepid. (you may have heard of this.) I found this link at [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) that explains how to install the driver and shows a few bugs in it. Just check it out. It mentions freezing after loading GDM (somewhere near the end of the article) which sounds exactly like your problem. Just give it a shot and let me know how it goes. You could also check, [http://www.openchrome.org](http://www.openchrome.org) which is the official site just in case u run into other probs. Good hunting! :D

---

### Post by Agent.Logic_ on 2009-04-04
No, I hadn't heard of that! Thanks for pointing that out! :D I had the vesa driver replaced by OpenChrome yesterday from the recovery mode, and yes, it indeed freezes when GDM starts up. Now instead of the black screen, its the brown screen lol. Thanks for the links man! It seems to be down at the moment (the first one), I'll check it out when the site is back online and let you know how it goes. Keeping my fingers crossed! :D Cheers, and thanks again mate!

---

### Post by b@sh_n3rd on 2009-04-04
You're welcome. I know how frustrating when something doesn't work right. Especially something like Ubuntu ;). There IS a fix for when it freezes. You've gotta edit the xorg.conf file if i remember correctly. It is indeed closed for maintenance, just our luck. Well, try again later and hope it works for u this time. :D

---

### Post by Agent.Logic_ on 2009-04-04
Guess what? It finally works!!! As Borat would say, "great success!" All I had to do was to add the **XaaNoImageWriteRect** option and specify my laptop's resolution to the xorg.conf, like it was mentioned in the openchrome community link you had posted. :D Now it works like a charm! Thank you dude, I really appreciate the time you took to help me out! :D :popcorn:

---

### Post by b@sh_n3rd on 2009-04-04
Cool!, you're welcome. Have fun playin with Ubuntu! :D

---

### Post by tlois on 2009-04-04
Glad you got it working after a couple of glitches!  People on these boards are so helpful.

That re-writable cd thing is strange- they worked for installing on my emachine and my stepdaughter's new dell inspiron, but not on my thinkpad.  I thought the cd rom was going out on this machine, but was puzzled by the fact that it could read a rewritable cd when it was booted up in 8.04, which was on the system.

Have fun setting up your new laptop.

---

### Post by Agent.Logic_ on 2009-04-04
Yep, so helpful and so much more knowledgeable than any "tech support" you get from Windoze or any other commercial undertaking! Yeah, still have quite a way to go before I can say that I'm done with the customisations and other settings and software installations! I still haven't gotten around to enabling 3D to run without glitches, but atleast I got things running finally from all of your help and support! Cheers man.

---

