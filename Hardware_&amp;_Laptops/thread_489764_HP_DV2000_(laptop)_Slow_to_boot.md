---
title: "HP DV2000 (laptop) Slow to boot"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by jstur8jv on 2007-07-01
The boot time is extremely long on my new-ish laptop with fast hardware, lotsa ram, etc.  Bootchart output is located at:

[http://blog.sonandfoe.com/wp-content/uploads/2007/07/feisty-20070701-1.png](http://blog.sonandfoe.com/wp-content/uploads/2007/07/feisty-20070701-1.png)

I tried commenting out my wireless card in the etc/network/interfaces file, which did significantly speed up the boot times, but that wasn't/isn't a good fix, as I need my wireless card.

Any ideas?

---

### Post by EXCiD3 on 2007-07-02
I have tweaked my feisty settings and still have a long boot time. Probably near your time. However my shutdown time is ridiciulously short. I dont know what would help.

---

### Post by syko21 on 2007-07-02
Follow these instructions and see if boot time gets any better.
[http://ubuntuforums.org/showpost.php?p=2419738&postcount=16](http://ubuntuforums.org/showpost.php?p=2419738&postcount=16)

---

### Post by EXCiD3 on 2007-07-02
> **syko21 said:**
> Follow these instructions and see if boot time gets any better.
[http://ubuntuforums.org/showpost.php?p=2419738&postcount=16](http://ubuntuforums.org/showpost.php?p=2419738&postcount=16)

Thanks for that link. I just tried it and it seemed to speed up boot time quite a bit. Thanks! :D

---

### Post by bsawler on 2007-07-03
Hey, 

Thanks.  It really sped up the boot of my dv2000. 

Now if I can only get my sound to work on my dv2000.  You anyone has some insight I would greatly appreciate it.  I have a tread here regarding the sound.

[http://ubuntuforums.org/showthread.php?p=2953497#post2953497](http://ubuntuforums.org/showthread.php?p=2953497#post2953497)

Cheers,
Bradley

---

### Post by jstur8jv on 2007-07-03
Commenting out those lines on my laptop fixes the boot time problem, but it also turns off the wireless (or rather, it makes it so the wireless fails to load).

At the moment, I have decided to use the "fix" and have created a launcher that I can click on to start the wireless once logged into Ubuntu  --  it runs "sudo ifup -a" and a few seconds later, voila!

How come this takes ten-fifteen seconds in ubuntu to pull off, but when booting up, it takes over a minute?

And is there any way to tell the computer to run sudo ifup -a during the boot process so I don't have to click on the launcher I created?

---

### Post by sargentdean on 2007-07-03
> **jstur8jv said:**
> Commenting out those lines on my laptop fixes the boot time problem, but it also turns off the wireless (or rather, it makes it so the wireless fails to load).

At the moment, I have decided to use the "fix" and have created a launcher that I can click on to start the wireless once logged into Ubuntu  --  it runs "sudo ifup -a" and a few seconds later, voila!

How come this takes ten-fifteen seconds in ubuntu to pull off, but when booting up, it takes over a minute?

And is there any way to tell the computer to run sudo ifup -a during the boot process so I don't have to click on the launcher I created?

Go to System-Preferences-Sessions and add new. Give it a name like Wifi laucher and put sudo ifup -a in the command line. If you do this you won't need the laucher you greated.

I tried this and it speeded up my startup considerably but even though network  shows wireless I am unable to use it because it doesn't show up in Network Manager. There is nothing showing to enable wireless and no wirless connections.

How are you accessing your wireless?

Earl

Update:

I undid all those ## in S40networking and rebooted my computer, but I still have no wireless even using sudo ifup -a. I really need my wireless back any help is greatly appreciated.

TIA

Earl

---

### Post by jstur8jv on 2007-07-04
> I undid all those ## in S40networking and rebooted my computer, but I still have no wireless even using sudo ifup -a. I really need my wireless back any help is greatly appreciated.


I'm not doing anything too special.  I don't remember the specific commands, but an abstract of what I did to get wireless working is

1. blacklist the drivers that came with Feisty
2. compile the latest ndiswrapper
3. download compatible windows driver for the wireless, and
4. put 2 and 3 together

>  I tried this and it speeded up my startup considerably but even though network shows wireless I am unable to use it because it doesn't show up in Network Manager. There is nothing showing to enable wireless and no wirless connections.

How are you accessing your wireless?

I'm just using the network manager applet, with my wireless card set on roaming mode.  Once ndiswrapper is loading the proper driver, it's a snap and all automatic.  (Getting there is a PITA, though.  There should be an automated process that takes care of it, I think, like there is with the binary video card drivers.)

Also, in case anyone else stops by and has the same problem, I forgot to mention that the specific command entered into the launcher to run 'sudo ifup -a' is:

```
xterm -e 'sudo ifup -a'
```

---

### Post by SendDerek on 2007-07-04
This is an interesting thread to me, so I'm going to subscribe.

I have the same problem.  After commenting out the quiet boot options, I was able to see that the progress bar stops on networking for a while and then continues again.  It would be great to know why this happens!

My laptop:
Sony Vaio VGN-FE550G with Intel 3945 wireless card.

---

### Post by sargentdean on 2007-07-04
jstur8jv,

I did some more searching on the forum and found out that if you add ndiswrapper into /etc/module that you don't need your fix. I did this and my boot time is a lot faster and I didn't need to run your launcher.

Hope this helps.

Earl ;)

---

### Post by CrankyFilipino on 2007-07-04
> **sargentdean said:**
> Go to System-Preferences-Sessions and add new. Give it a name like Wifi laucher and put sudo ifup -a in the command line. If you do this you won't need the laucher you greated.

I tried this and it speeded up my startup considerably but even though network  shows wireless I am unable to use it because it doesn't show up in Network Manager. There is nothing showing to enable wireless and no wirless connections.

How are you accessing your wireless?

Earl

Update:

I undid all those ## in S40networking and rebooted my computer, but I still have no wireless even using sudo ifup -a. I really need my wireless back any help is greatly appreciated.

TIA

Earl

I hope you guys can figure out your problems. I commented out those lines just like that link suggested and I got an extremely faster boot up time now and I didn't get any problems with my wireless connection at all. I have no clue why, I'm just happy about it.

---

