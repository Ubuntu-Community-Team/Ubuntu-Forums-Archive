---
title: "HDAPS on Thinkpad"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by holihue on 2007-05-20
I have Thinkpad R60.

How do I use hdaps?

I only get this:

$hdaps-gl
open: No such file or directory

---

### Post by Kobalt on 2007-05-20
Do you want to enable hdaps ? If so, just run ```
sudo modprobe hdaps
```

---

### Post by holihue on 2007-05-20
I got:
FATAL: Error inserting hdaps (/lib/modules/2.6.20-15-generic/kernel/drivers/hwmon/hdaps.ko): No such device

---

### Post by holihue on 2007-05-20
IBM Active protection system worked in Windows.

---

### Post by Kobalt on 2007-05-21
You may need to install hdaps-utils first ```
sudo apt-get install hdaps-utils
```

---

### Post by holihue on 2007-05-21
I have hdaps-utils.

I'm trying to compile tp_smapi.

do I need to do that?

---

### Post by Kobalt on 2007-05-21
Which kernel are you using ? There was a bug for hdaps loading in kernel 2.6.20-14-generic but it is solved in 2.6.20-15. You can know what kernel you use with the command line ```
uname -r
```

---

### Post by holihue on 2007-05-21
I use 2.6.20-15-generic.

---

### Post by Kobalt on 2007-05-21
I've found [this]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_on_a_ThinkPad_T43") on Google, maybe a good help but activating the hdaps seems heavy, you'll need to recompile your kernel apparently...

---

### Post by holihue on 2007-05-21
The compiling worked without any errors, but:

$ mesg | grep hdaps
$

And:

$ hdapsd -d sda -s 15
open(protect_file): Permission denied

So I ran:

sudo hdapsd -d sda -s 15
open(/sys/devices/platform/hdaps/position): No such file or directory

Do you know what the problem is?

---

### Post by airbornespent on 2007-08-10
Issue the following commands ```
sudo -s
echo 1 > /sys/block/sda/queue/protect
``` while copying files or with the gnome-hdaps-applet running. See if the applet turns from play to pause or if the files stop copying and your HDD light turns off if you re-enter the command over and over (arrow-up, return, arrow-up, return...) If it works then your kernel is patched and everything is working, just not hdapsd...

I followed [these]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_on_a_ThinkPad_T43#Disk_Protection") instructions at the thinkwiki site and found everything works fine except the hdapsd[aemon].

EDIT: I got the hdapsd working! There is a note on the thinkwiki page I linked to above that mentions using gcc-3.4 to compile hdapsd, I ignored it at first but then I checked synaptic. You must install gcc-3.4 then when compiling hdapsd use:```
gcc-3.4 -o hdapsd hdapsd-*.c
sudo cp hdapsd /usr/local/sbin/
```

At this point you can run the command "hdapsd" to see the options, ex. "hdapsd -d sda -s 15" 

Now I simply need to figure out where is te best place to start the daemon on startup. rc.local is one place, but I'd personally like it to start ASAP after boot, which means as close to when the tp_smapi modules are loaded as possible.

---

### Post by holihue on 2007-08-13
Thanks 
I will try

---

### Post by sumek on 2007-11-05
Will all problems related to the running Linux on your Thinkpad you should try 
[http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)

---

### Post by holihue on 2007-11-15
I used the guide to install tp_smapi on [http://www.thinkwiki.org/wiki/Tp_smapi.]("http://www.thinkwiki.org/wiki/Tp_smapi")
It worked.:)

And the hdaps-gl is working.:)

But it is inverted.

What's wrong?

---

### Post by Rubadubdub on 2007-11-16
Hi all, 

I just bought a T61 and I am trying to get the hdapsd to work.

I have managed to install tp_smapi and hdaps-gl is working but hdapsd -d sda -s 15 gives me this message:
open(protect_file): no such file or directory

What am I doing wrong?

---

### Post by Rubadubdub on 2007-11-16
Hi all, 

I just bought a T61 and I am trying to get the hdapsd to work.

I have managed to install tp_smapi and hdaps-gl is working but hdapsd -d sda -s 15 gives me this message:
open(protect_file): no such file or directory

What am I doing wrong?

---

### Post by holihue on 2007-11-19
I had a kind of the same error...

You can try [this.]("http://www.thinkwiki.org/wiki/Tp_smapi#Installation_on_Ubuntu.2FDebian")


It worked for me.

---

### Post by nemik on 2007-12-26
after last kernel update, HDAPS with tp_smapi, even the new 0.33 version, it is not working anymore.

does anyone have a fix?

---

### Post by pardasaniman on 2007-12-29
Hi, I've been struggling with this for an embarassingly long time!

A recap, and summary of what I understand is going on on my T61.

1st.  Ubuntu does not have the patch for "disk protection" which exports a sys interface necessary for the whole schabang to work for any thinkpad.  check out [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_Thinkpad_T60#Building_a_custom_kernel](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_Thinkpad_T60#Building_a_custom_kernel) is a step by step guide with a link to a special patch, just skip the part relevant to the ATi graphics part and you should be good.[/i]

2nd.  The current HDAPS module included in ubuntu doesn't have my laptop on the whitelist.  I decided to ignore it and try for the more superior option of using tp smapi.

3rd.  OK, so tp_smapi builds according to [http://www.thinkwiki.org/wiki/Tp_smapi#Installation_on_Ubuntu.2FDebian](http://www.thinkwiki.org/wiki/Tp_smapi#Installation_on_Ubuntu.2FDebian) , but, hdaps-gl or pivot still doesn't work.  dmesg says that hdaps_check_ec returns an error. No Good!
So, since I had the source anyway, I just commented out a bunch of lines in there to get it to load!
Success!  It loads! And hdaps-gl works.

4th.  I found hdapsd still not working because of (1).  


5th. Long story short, this is the biggest mess I've ever got into in linux.  Hopefully I can get something working.

---

### Post by bomanizer on 2008-01-26
> **nemik said:**
> after last kernel update, HDAPS with tp_smapi, even the new 0.33 version, it is not working anymore.

does anyone have a fix?

I'd like to know too, see attached log from tp_smapi make.

---

### Post by bomanizer on 2008-01-26
OMG I got it!

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_Thinkpad_T60#Active_Protection_System_.28Reduced_Power_Version.29](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_Thinkpad_T60#Active_Protection_System_.28Reduced_Power_Version.29)

Just note, that in step "And install tp-smapi-modules:" type (autocomplete) the name of the package that you just downloaded. This Thinkwiki-manual has a typo, methinks.

now to make those adjustments to prolong my battery's life....

---

### Post by bomanizer on 2008-01-27
> **bomanizer said:**
> OMG I got it!

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_Thinkpad_T60#Active_Protection_System_.28Reduced_Power_Version.29](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_Thinkpad_T60#Active_Protection_System_.28Reduced_Power_Version.29)

Just note, that in step "And install tp-smapi-modules:" type (autocomplete) the name of the package that you just downloaded. This Thinkwiki-manual has a typo, methinks.

now to make those adjustments to prolong my battery's life....

This was early celebration, but I was on the right track.. :)

I think this is Gutsy/Thinkpad R50 spesific, but anyways, this needs a custom kernel with the patch attached here below. After that, I reinstalled tp_smapi and hdaps as instruced in the link on my previous post. Please note, that at least on my system the keyboard froze when booting with the custom kernel. I had to reinstall the tp_smapi & hdaps packages running in failsafe mode. I think there was some conflicting suff. The patch addresses the issue described in this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/139881](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/139881)

Please note, that I'm no expert on this, just a lucky tinkerer ;)

---

### Post by holihue on 2008-02-04
I get the hdaps-gl working in Gutsy, after installing the last version  of tp_smapi from source.

But the values are inverted, so the 3d thinkpad in hdaps-gl is rotating to left when I rotate my thinkpad to right.

Also when I play Neverball, I have to rotate my Thinkpad in the opposite direction.


When I try hdapsd, I get "open(protect_file): no such file or directory" as Rubadubdub got, and that is because I haven't compiled the kernel with the hdaps module that support APS daemon.

But my only problem is that the values I get is inverted.


EDIT:
the inverted problem is fixed, I ran:
```
sudo su
echo options hdaps invert=1 >> /etc/modprobe.d/options
```

and restarted, and now it works.:):):)


I won't mark this thread as solved since I see it is many who have problems here...

---

### Post by pflanzenmoerder on 2008-02-13
The above exception comes from the missing
/sys/block/sda/queue/protect
Does anybody have the slightest idea why that doesn't exist???
I mean, I got everything to work, I can use that opengl tool to see my t61 tilt and everything seems to be installed correctly.
I read every frickin forumpost, newsgroup message and howto I could find but I can't find a solution.

---

### Post by pflanzenmoerder on 2008-02-13
I found something.
Apparently the tp_smapi (and also the one shipped with the regular kernel) need a protect patch:
[http://article.gmane.org/gmane.linux.drivers.hdaps.devel/1162]("http://article.gmane.org/gmane.linux.drivers.hdaps.devel/1162")
Can anybody confirm that (got tp_smapi running right no, don't know if it is included)

---

### Post by Rubadubdub on 2008-02-14
Hi,

Well, I got hdaps-gl working (again) with the new tp_smapi-0.36
So I see how I move my T1 laptop but when I try to run  hdapsd -d sda -s 15 I get the following error:

WARNING: Cannot open hdaps position input file /dev/input/hdaps/accelerometer-event (Permission denied). You may be using an incompatible version of the hdaps module, or missing the required udev rule. Falling back to reading the position from sysfs (uses more power). Use '-y' to silence this warning.
open(protect_file): No such file or directory

If I use sudo  hdapsd -d sda -s 15 i just get:

open(protect_file): No such file or directory

I followed these HowTo's:
[http://www.thinkwiki.org/wiki/How_to_protect_the_harddisk_through_APS]("http://www.thinkwiki.org/wiki/How_to_protect_the_harddisk_through_APS")
and
[http://article.gmane.org/gmane.linux.drivers.hdaps.devel/1040]("http://article.gmane.org/gmane.linux.drivers.hdaps.devel/1040")

And as I said, hdaps-gl works just fine.

What am I missing, doining wrong? Help is appreciated!

Thanks in advance from a hdaps newby

---

### Post by pflanzenmoerder on 2008-02-18
That's what I said in my last post.
The module itself doesn't have support for actually turning off the harddisk.
You can monitor it for tilting but that's it.
The patch is still not available so right now you can watch your harddisk tilt to death but you cannot save it ;)

---

### Post by Rubadubdub on 2008-02-18
Check!

I'll keep looking in on this thread when it is possible to park the hard disk.

Thanks for the info

---

### Post by cantormath on 2008-02-25
After reading launchpad, it sounds like everyone with a T61p is ###T out of luck until hardy.  Its sounds like they are not planing to fix this issue for gutsy........Which is kinda lame.
Unless you maintain your own kernel, you should just hold off I guess.

---

### Post by EarloftheWest on 2008-04-25
Rubadubdub,

I'm at the same point as you.

I recompiled with tp_smapi and that seems to be working fine. 

If I did that, do I still have to do the kernel patch as described here:
[http://www.thinkwiki.org/wiki/HDAPS#Kernel_patch](http://www.thinkwiki.org/wiki/HDAPS#Kernel_patch)

Success is close. I can almost taste it.

---

### Post by holihue on 2008-04-26
I think you have to patch the kernel if you want hard drive protection, maybe it is fixed in Hardy, I haven't tested it yet.

---

### Post by curley_sue on 2008-05-05
I don't really know what I am doing but I have found a patch (protect) for kernel 2.6.24 at:
[http://www.thinkwiki.org/wiki/HDAPS#Kernel_patch](http://www.thinkwiki.org/wiki/HDAPS#Kernel_patch)

where you could also find loads of warnings regarding its instability and a suggested fix.

I am trying it now - if I don't come back it probably means my laptop blew up...

---

### Post by Whiffle on 2008-05-05
I ran that patch for a bit under 2.6.24, it locked up my laptop a couple of times.  I have it again under 2.6.25 and it appears to be working fine.

The patches for hdaps are done by one guy as far as i can tell, and he does a good job but they're still not quite there yet.

---

### Post by curley_sue on 2008-05-05
have you tried the suggested fix? ( [http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2008-February/042226.html](http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2008-February/042226.html) )

how do you install the 2.6.25 kernel - is it in the repos or have you compiled it yourself?

---

### Post by Whiffle on 2008-05-05
> **curley_sue said:**
> have you tried the suggested fix? ( [http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2008-February/042226.html](http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2008-February/042226.html) )

how do you install the 2.6.25 kernel - is it in the repos or have you compiled it yourself?

That fix was released after I tried it, and then stopped using it, so no I havn't used it.

I'm actually on Arch Linux, and there is a package in the Arch User Repository that is 2.6.25 thinkpad-specific and included the hdaps patches.  That is what I'm using.

---

### Post by pfoff on 2008-05-31
Same on Hardy. T61p and installed everything.
Added KERNEL=="event[0-9]*", ATTRS{phys}=="hdaps/input1", ATTRS{modalias}=="input:b0019v1014p5054e4801-*", SYMLINK+="input/hdaps/accelerometer-event"
to udev.rules
and 
options libata protect_method=1
to modprobe.d
Still no success...
Will have a look, if it works with the kernelpatch from 
[http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2008-February/042226.html](http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2008-February/042226.html) and the other patched mentioned there.
I dont know why, but that patch seems not to be contained.

---

