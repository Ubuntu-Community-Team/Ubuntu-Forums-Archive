---
title: "Easy Sony Vaio Brightness Fix"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by xenoph0be on 2007-06-19
If you are having problems with the gnome-power-manager controlling the brightness on your Sony Vaio laptop with an Intel video chipset then this fix should work for you.  

This is a documented problem: [https://launchpad.net/distros/ubuntu/+source/hal/+bug/68617]("https://launchpad.net/distros/ubuntu/+source/hal/+bug/68617")

Copy/Paste the following into a terminal window.  It will require you to enter your password since the command modifies root owned files. Enter the password that you use to login to you your account.

```
sudo locate -u && for i in $(locate lcd-???-brightness); do sudo cp $i $i.bak; sudo sed -i '1 s|#!/bin/sh|#!/bin/bash|g' $i; done
```

This is confirmed working in feisty on my laptop (a VGN-FE660G) and should work in other ubuntu distros.  Hopefully this helps.  Please let me know if you try this on a different distro and whether or not it works.  Currently my FN+F5 and FN+F6 do not change my brightness.  You can also add the brightness applet to one of your Gnome panels.

There is work being done to make the function keys work on all Vaio laptops.  Currently the function keys only work on FS series laptops.  

Please read and post your DSDT to this thread to help further research and development on the Vaio features: [http://ubuntuforums.org/showthread.php?t=465491]("http://ubuntuforums.org/showthread.php?t=465491")


IntuitiveNipple informed me that this fix only works on Intel chipsets and that the following information should help on NVidia chipsets.
> **IntuitiveNipple said:**
> Some Vaio's have Nvidia video chip-sets, in which case the 'standard' brightness controls don't work (they're for the Intel video chip-sets). I wrote a [Gnome panel applet](http://ubuntuforums.org/showthread.php?t=451781) to work with smartdimmer, one of the utilities (the other being nvclock) that can adjust brightness for Nvidia chip-sets.

---

### Post by Lancellor on 2007-06-20
I had some problems with my Sony Vaio VGN-N130G controlling the brightness and i used your hack and know is working thanks ..................

---

### Post by xenoph0be on 2007-06-20
> **Lancellor said:**
> I had some problems with my Sony Vaio VGN-N130G controlling the brightness and i used your hack and know is working thanks ..................

Sweet... Glad I could be of assistance...

---

### Post by gregorygreg on 2007-06-20
how do I use this to change my brightness after I have typed the code into the console?

---

### Post by buggybug on 2007-06-20
Thanks for the code xenoph0be! Worked fine for me on my Vaio PCG-K215S :D

> **gregorygreg said:**
> how do I use this to change my brightness after I have typed the code into the console?

Go to the power manager... left klick battery shown in your system tray ;)
edit: sorry, just seen in your other post that you have a NVIDIA chipset... as indicated in the first post, this fix only works for INTEL chips... sorry

---

### Post by xenoph0be on 2007-06-20
For the Intel chip-sets after you have ran the code above in your console you can adjust the brightness 1 of 2 ways.  One way is to change it in the gnome-power-manager (the battery icon on your gnome panel).  The other way is to add the brightness applet to a gnome panel and use it.  

Right click on any empty space on any gnome panel and select 'Add to panel...'  Scroll down to 'System & Hardware' and drag and drop the 'Brightness Applet' (looks like a white sun) to any gnome panel.  Left click brightness applet and drag the slider to the desired setting.

---

### Post by Depressed Man on 2007-06-20
It works! Thanks. You just helped move my Sony Vaio laptop one step closer to using Ubuntu more then Vista. 

Now if only hibernate and suspend would work lol.

---

### Post by gregorygreg on 2007-06-20
should have read above...sorry for confusion

---

### Post by gnocci on 2007-06-23
Great!

Worked on a VGN-C140G (Intel innards)

---

### Post by benivilch on 2007-06-24
thanks. it works on my Sony Vaio VGN-FE870E with ubuntu 7.04

---

### Post by cyndessa on 2007-06-24
Thanks for the code, it worked on my Sony VGN-C290!

---

### Post by Nubbie on 2007-06-26
Thank you so much for this! all i need now is to fix suspend to RAM, as my vaio vgn240e/s' screen won't turn back on upon waking. if you know of a fix for that too, give me a shout please :) using intel drivers.

---

### Post by pVilaça on 2007-06-26
This is only for intel graphics card? I' ve Nvidia card (fe31h)

---

### Post by Depressed Man on 2007-06-27
The posted method was for Intel only. But there was a method for Nvidia given in the first post. But here's the link to it anyway..

[http://ubuntuforums.org/showthread.php?t=451781](http://ubuntuforums.org/showthread.php?t=451781)

---

### Post by belladona123 on 2007-06-28
hei!
Is there any way to have the state before executing this command

[I]sudo locate -u && for i in $(locate lcd-???-brightness); do sudo cp $i $i.bak; sudo sed -i '1 s|#!/bin/sh|#!/bin/bash|g' $i; done
[/I]

---

### Post by Belgatom on 2007-07-15
Well, I tried your fix and after a lot of rattling from the hard disk, I was ready to change the brightness with both methods that were quoted. Alas, no success . Coming from the world of MS, I decided to reboot to see if maybe this was necessary. No success with that idea. 

BUT, yes a big BUT. It does now work with F5 and F6 which is even better than I could have hoped. So you guys still have some work cut out for yourselfs but this is one greatfull Ubuntu user who ain't going back to MS on this laptop.  I think this deserves a groovy smiley to show you my appreciation. 

:guitar: You guys rock!!!

For the record: I own a Japanese  VAIO TR5 running Feisty.

---

### Post by xenoph0be on 2007-07-15
> **Belgatom said:**
> 
For the record: I own a Japanese  VAIO TR5 running Feisty.

You might keep an eye on [this thread]("http://ubuntuforums.org/showthread.php?t=465491"), and watch for then the new sony control kernel module is released...

---

### Post by cpangratzbg on 2007-07-21
Thanks for this great fix.

Works fine on my Vaio VGN-A417M !!!!

---

### Post by Anagonda on 2007-07-25
It "works" on vaio txn25n. I have only maximum britghess(and thats alot!) and then there is "under half way". With ac-power other is too bright and the other is too dark. Maybe I get used to this darker with battery...

I can move the brightness thing up and down, but brightness changes only when I but it all the way up or approx 30% down. But this is better than nothing...

---

### Post by sstucke on 2007-08-07
Great! I have a VGN-N350FE. Everything works but the FN for brightness (still work with the gnome-applet).
I wrote a howto (in spanish) to upgrade kernel to 2.6.22.9 plus powertop, plus what you indicate here.
Feel free to check it out:
[http://sebastianstucke.wordpress.com/2007/08/07/howto-ubuntu-feisty-sony-vaio-vgn-n350fe/](http://sebastianstucke.wordpress.com/2007/08/07/howto-ubuntu-feisty-sony-vaio-vgn-n350fe/)
Thanks a lot!

---

### Post by Depressed Man on 2007-08-07
For me it worked in Feisty but when I installed the Gutsy kernal (2.22.9) this no longer works (and I can't control my screen brightness).

---

### Post by sfh1975 on 2007-08-16
i was using a solution from linux mint and had to type the command, but now its much better. i dont mind adding it to panel, there are a lot many others there and make things handy.
thanks folks!

---

### Post by NeoTech on 2007-08-18
Working great on: SONY VAIO PCG-R505JE.

Thanks for the help !! 
[http://ubuntuforums.org/images/smilies/star.png](http://ubuntuforums.org/images/smilies/star.png)


> **xenoph0be said:**
> If you are having problems with the gnome-power-manager controlling the brightness on your Sony Vaio laptop with an Intel video chipset then this fix should work for you.  

This is a documented problem: [https://launchpad.net/distros/ubuntu/+source/hal/+bug/68617]("https://launchpad.net/distros/ubuntu/+source/hal/+bug/68617")

Copy/Paste the following into a terminal window.  It will require you to enter your password since the command modifies root owned files. Enter the password that you use to login to you your account.

```
sudo locate -u && for i in $(locate lcd-???-brightness); do sudo cp $i $i.bak; sudo sed -i '1 s|#!/bin/sh|#!/bin/bash|g' $i; done
```

This is confirmed working in feisty on my laptop (a VGN-FE660G) and should work in other ubuntu distros.  Hopefully this helps.  Please let me know if you try this on a different distro and whether or not it works.  Currently my FN+F5 and FN+F6 do not change my brightness.  You can also add the brightness applet to one of your Gnome panels.

There is work being done to make the function keys work on all Vaio laptops.  Currently the function keys only work on FS series laptops.  

Please read and post your DSDT to this thread to help further research and development on the Vaio features: [http://ubuntuforums.org/showthread.php?t=465491]("http://ubuntuforums.org/showthread.php?t=465491")


IntuitiveNipple informed me that this fix only works on Intel chipsets and that the following information should help on NVidia chipsets.

---

### Post by sfh1975 on 2007-08-18
every time i reboot, the brightness is set to minimum/ zero. is there any way i can set a default value at boot up?

---

### Post by frychiko on 2007-08-24
This failed to work for my Sony Vaio FE32HB/W on Ubuntu Feisty.

EDIT: worked after a reboot! excellent saves me from having to change the hal script headers from sh to bash everytime manually!

---

### Post by sstucke on 2007-08-28
Cool man, even though the FN keys do not work, it's great.
Since I want to use it with kernel 2.6.22, I wrote a howto here:
[http://en.tuxero.com/2007/08/howto-ubuntu-feisty-sony-vaio-vgn.html]("http://en.tuxero.com/2007/08/howto-ubuntu-feisty-sony-vaio-vgn.html")
Thanks!

---

### Post by xenoph0be on 2007-08-30
> **sfh1975 said:**
> every time i reboot, the brightness is set to minimum/ zero. is there any way i can set a default value at boot up?

Check the power settings for battery and mains power.  Set them to the level that you desire and it should adjust accordingly, whether on mains power or battery.

Jacob

---

### Post by choch on 2007-08-31
not working on my Sony Vaio VGN-N11S, but I have made some hacky scripts to do the same without gnome-power-manager, so it could just be that.

edit: Working after a restart :D Now i just have to remove all those other scripts i made -,-

---

### Post by rfcompte on 2007-09-22
Thanks ... Worked like a charm on my Vaio VGN-FS965F
Fn keys don't work though... I haven't tried the sonypi hack because that's supposedly fixed in gutsy, thanks to the new kernel. And I'm planning on upgrading soon

---

### Post by srirammurali on 2007-09-25
awsome. works fine on my VGN-N365E.. thanks a ton:guitar::guitar:

---

### Post by Depressed Man on 2007-09-29
Upgraded to Gutsy (well more like a delete the old partition, recreate and install since Gusty upgrade kinda shredded Feisty).

And it still doesn't work :(
Edit: After two reboots it works.. o.O

---

### Post by artr on 2007-10-12
Thank you so much!
Fix works on my Sony PCG-7V2L under Ubuntu 7.04 64bit  (Intel Core 2 Duo).  I am amazed at how well things work on day one of install.  Dual boots with Vista Home Premium, and Audacity 1.3.2 shows a dramatic speed increase vs. Vista version.  Again, my eyes really thank you.

---

### Post by farmerjack on 2007-10-15
Thanks very much!:)=D>
It works (with the brightness control button) on my PCG-K115M

---

### Post by zakeen on 2007-10-16
This worked on my Sony VGN-TZ18GN.

thanks!

---

### Post by theverde on 2007-10-20
Hi to all! My first message here...lets go on. Well, i have a Sony PCG-Z1M, with Gutsy, freshly installed yesterday. And i have some troubles with the gnome-power-manager backlight control. Even after writing this line of code (or changing by hand the /bin/sh to /bin/bash in the two hald scripts) im still not able to set the brightness from the applet. Anyway, i can set the backlight manually setting the value in /sys/class/backlight/sony, or even pressing the Fn key in combination with f5 and f6. But the thing that confuses me the most, is that if i load the Ubuntu Gutsy CD and i stay just in the live session, the brightness applet works perfectly...how this can change once the operating system is installed on the HD?...:confused: what i am missing? Maybe a matter of permissions? Thanks in advance to all, any help is appreciated!

p.s. you rock guys, keep up the good work, this community is becoming the best GNU/linux resource in the universe!

---

### Post by jhkuo on 2007-10-21
I am having identical problem with my TX3 in Gutsy. After digging around in hal scripts, I discovered that while the value in /sys/class/backlight/sony/brightness ranged from 0 to 7, the $value parameter passed into hal-system-lcd-set-brightness-linux actually ranged from 4 to 134648563. It appears to be some possible conversion issue between hal and gnome-power-manager.

As a temporary fix (for myself), I just simply added the following line in the beginning of hal-system-lcd-set-brightness-linux,

value="`expr $value / 19235509`"

Not great, but I guess it would do for now until the real fix is released.

---

### Post by theverde on 2007-10-22
> **jhkuo said:**
> I am having identical problem with my TX3 in Gutsy. After digging around in hal scripts, I discovered that while the value in /sys/class/backlight/sony/brightness ranged from 0 to 7, the $value parameter passed into hal-system-lcd-set-brightness-linux actually ranged from 4 to 134648563. It appears to be some possible conversion issue between hal and gnome-power-manager.

As a temporary fix (for myself), I just simply added the following line in the beginning of hal-system-lcd-set-brightness-linux,

value="`expr $value / 19235509`"

Not great, but I guess it would do for now until the real fix is released.

Indeed, it seems that i have almost your identical problem. I have started a new thread about this, i hope it is not a duplicate.

[http://ubuntuforums.org/showthread.php?t=585745]("http://ubuntuforums.org/showthread.php?t=585745")

EDIT:

> value="`expr $value / 19235509`"

I just did the trick....and it worked!!!!! :) Anyway, i would like to understand more about this: how did you get  19235509 as value? Can you link any resource about this? Thanks again, i have to say that this brightness bug was the only thing that didnt work on my laptop, Gutsy is an incredible great distro.

EDIT:

Oh, yeah, ok...i got it! 134648563/19235509 = 7 :)

---

### Post by jhkuo on 2007-10-22
I found the range of the $value is 4 to 134648563, so 134648563 divided by 7 is 19235509.

It looks like hal and gnome-power-manager are using different types of variable to store the brightness. 

Just note that this trick doesn't fix the problem fully, if you unplug the AC adapter, you will see the slider stops working properly. This is due to $value seems to have a different range again when AC is off.

---

### Post by theverde on 2007-10-22
Actually, it seems that this fix works properly for me. If i unplug the AC, the light dims properly to the value i have set, plugging it back the light goes up again at 100% (or whatever value i set). Also, with the unplugged AC, the gnome-brightness-applet slide changes in the range of the "unplugged AC" brightness value. To make an example, if i set "dim display brightness by" 50% in the "On battery power" tab of the gnome-power-manager prefrences, and then i unplug the AC, the light dims to 50%, and moving the slide of the gnome-brightness-applet  the backlight will change between the minimum and the 50% of the maximum. It seems the correct behaviour to me, or im missing something?

---

### Post by jhkuo on 2007-10-22
for my TX3, the sliders on battery and ac mode behave in opposite direction, For example, with ac plugged in, max brightness would be sliding to the right, whereas it would set to minimum brightness when ac is unplugged.

---

### Post by gsoundsgood on 2007-11-04
it didn't do any harm, but it didn't help either...still not working from the applet, not working from the command line..
i'm on a sony vaio vgn-nr11z

---

### Post by makrook on 2007-11-06
on a NR11S/S with gutsy didn't crash anyhing but doesn't work neither.
I still have no way at all to dim my lcd.:(
and (and this explains that), even though I have sony_acpi an sonypi installed, I don't have any /sys/class/backlight/sony.

---

### Post by Ferri on 2007-11-06
Thanks. Finally my Sony Vaio VGN-FS415B reacts as expected when I unplug the AC adapter.

---

### Post by Kissaki on 2007-12-29
My Sony VGN-315M finally responded to my flood of demands to dim the display. Thanks man, keep on rocking some finest Japanese craftmanship with Ubuntu...

---

### Post by danscali on 2008-03-23
did not work for me. I still have to use xbacklight to change brightness VGN-FZ240E

---

### Post by wieman01 on 2008-03-31
This fix worked for me as well. Although I hate do lose the FN keys... what a pity.

Sony Vaio VGN-T27GP on Gusty... Man, I wished I hadn't upgraded from Feisty.

---

### Post by lunanueva on 2008-06-13
the code didn't work for my Sony VGN-N320E.
however, adding the brightness applet to my top panel did the trick.
thanks for the idea.

---

### Post by e.alozie on 2008-07-04
I'm using a SONY VAIO NR21M series and i tried the above concept and its still not workin...i'm also using Intel Chipset

Can any one help?

---

### Post by e.alozie on 2008-07-04
i encountered an error which states invalid option --u

Still need help

---

### Post by farazhussain on 2008-07-04
> **e.alozie said:**
> i encountered an error which states invalid option --u



Exact same problem for me...

---

### Post by farazhussain on 2008-07-04
I could get the command to work by replacing locate with slocate.

But brightness still didn't work... in fact my earlier scripts aren't working any more...

---

### Post by half-bite on 2008-07-20
Hi,

Unfortunately, it didn't work for me either...have a fz 240 and nothing has worked (intel).  Tried xbacklight, this hack, etc.  Any ideas?

Thanks!

---

### Post by reder01 on 2008-07-21
Hi,

I tried the solutions described in this thread with a Sony Vaio VGN SZ-71 and nothing worked. 

I found in the the sonybrightness.sh script a comment that the ACPI setter and getter methods for the display brightness do not work recent models. But I did not find more information about this issue. Does anyone have more information about that?

Cheers,
Ray

---

