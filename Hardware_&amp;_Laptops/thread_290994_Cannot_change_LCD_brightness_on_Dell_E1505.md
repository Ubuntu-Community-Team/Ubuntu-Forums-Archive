---
title: "Cannot change LCD brightness on Dell E1505"
date: 2006-11-01
forum: Hardware &amp; Laptops
---

### Post by pvegdahl on 2006-11-01
I just got a new Dell E1505 laptop, and have installed Edgy Eft in parallel with WinXP.

What I cannot figure out, is how to modify the brightness of the LCD. When plugged in, it is set to maximum brightness, and on battery it sets to something lower than what I would usually prefer. In Windows, Fn+Up/Down changes the brightness, however this does not work in Ubuntu. All of the other Fn+<key> combinations (at least those that I've tested) worked without any setup. To make matters worse, I cannot find any way at all to change the brightness.

Looking for information both in these forums, and online, it appears that this is currently a difficult undertaking with Dell laptops. Is there anyone out there that has had any luck?

I would be happy for any information on how to change the brightness, even if it requires a terminal and sudo.

Relevant configuration information:
2 Ghz Core 2 Duo
1 GB Memory
ATI X1400 Graphics Card
1680x1050 Display

---

### Post by dbott67 on 2006-11-01
I've got a similar laptop (Dell Inspiron 6400 w/ ATI Radeon x1400, 2 GB RAM, 1.83 Core Duo) and it works properly in XP & Dapper 6.06.

FN + up arrow / increase brightness
FN + down arrow / decrease brightness

I have read that some Edgy users are having problems with the numlocks button not working.  Might be related... (I'll take a look).

-Dave

---

### Post by pvegdahl on 2006-11-02
Thanks.

I'm wondering if there is a config file somewhere that I just need to modify. I would be quite surprised if a newer version of Ubuntu would make it impossible to get the brightness settings changed.

I'll search around for some info on the numlock stuff and see if that gives me any insights.

---

### Post by volton on 2006-11-07
I'm running Edgy Eft on a Inspiron 640m and the brightness controls are not working for me as well. The strange thing is that they worked fine in Dapper. :-k 
Any help would be very much appreciated:D

---

### Post by pvegdahl on 2006-11-07
Thanks for letting me know that. I was actually wondering about this particular issue. It sounds like there may be something about Edgy Eft that broke this compatibility, or at least prevents it from being automatically configured correctly. I haven't found a good way to fix this yet, but am hoping a solution will turn up. My current solution is that I've set unplugged screen brightness to max in the bios. This hurts my battery life, but I'd prefer that to sometimes not being able to see the screen.

When you upgraded from Dapper to Edgy, did you do a clean install, or an in place upgrade? If you did a clean install, I'm wondering if an in place upgrade would somehow maintain the necessary configurations for the screen brightness keys.

---

### Post by dbott67 on 2006-11-07
I've been doing a little reading about this.  This seems to be an issue with IBM Thinkpads also (possibly a 'hal' bug):
[https://launchpad.net/distros/ubuntu/+source/hal/+bug/61184](https://launchpad.net/distros/ubuntu/+source/hal/+bug/61184)

One suggestion is to type the following in the terminal:
```
gnome-power-manager
```

---

### Post by pvegdahl on 2006-11-07
I'm running the power-manager, but there aren't any options in it for adjusting the screen brightness. Is this different from the version in Dapper?

---

### Post by dbott67 on 2006-11-07
The link that I posted above seems to suggest that it has a 'slider' of some sort.
> 
Re: Screen brightness buttons don't work properly on Thinkpad T60 from stbaker at 2006-10-05 14:20:16 UTC

I've also noticed that in the latest Edgy (beta release, plus updates), the brightness slider in gnome-power-manager doesn't work properly. You have to slide it back and forth a few times before it will allow you step between the different brightness settings.


I don't think Dapper does (I can confirm when I get home).

Another suggestion that I came across mentioned that the brightness can be adjusted during boot (before XWindows starts), but once X starts, the brightness cannot be adjusted.

Can you confirm?

-Dave

---

### Post by neutrino82 on 2006-11-15
I've a new 640m / e14005 and I installed Edgy. I guess i'm experiencing the same problem. Any ideas on how to solve?

---

### Post by pvegdahl on 2006-11-15
I haven't solved this yet, but I discovered something new. You can adjust the brightness of the display up until the Ubuntu login screen. Also, the brightness keys reportedly worked in previous versions of Ubuntu. That leads me to hypothesize that there is a problem where Edgy hijacks those keys away from their default functionality. Perhaps it has to do with hot key configuration. If I figure out anything more, I will certainly post it here.

---

### Post by shoronpo on 2006-11-16
Not certain this is going to be of any help, but...
What BIOS version are your laptops running on ?
In my case, Fn+Up/Down was working perfectly well when I was on BIOS A08 ; it is only yesterday, when I upgraded to A09 (on an Inspiron 6400/E1505) that it started not working anymore.
So maybe there is an incompatibility between Gnome and that specific BIOS ?

---

### Post by pvegdahl on 2006-11-16
Thanks for the insight!

I am running A09, so it could be that. I suppose I could downgrade and see if that works, although I am hesitant to go to an older BIOS that may have other unknown bugs in it (The devil you know versus the devil you don't sort of thing.). Maybe I'll do a little research to find out what I will supposedly lose by dropping down a BIOS version.

Also, are you running Edgy? I've gotten the impression that the keys generally work in Dapper, but not in Edgy. I have not tried this myself as there are features new to Edgy that I am not eager to give up. Maybe I'm just stubborn, but I probably wouldn't use Linux if I wasn't at least a bit stubborn.

---

### Post by wiggum26 on 2006-11-18
Me too.

I'm running a Dell Inspiron 6400 with Edgy.
I did a clean install.
I can confirm that the fn-up fn-down brightness buttons work fine until the login window comes up, but not after.
All the other fn button combinations I've tested work ok.

---

### Post by neutrino82 on 2006-11-18
Running Edgy on 640m with fresh install. i confirm brightness keys works till login screen. I have BIOS A05 .

---

### Post by lucads on 2006-11-20
Same problem here, i'm with inspiron 6400 and the issue started when i upgraded the bios from A06 to A09.

Is there a way to check if is gnome or xorg blacklisting this keystroke sequence, in order to check deeply where is the bug located?

---

### Post by Orion2000za on 2006-11-22
> **neutrino82 said:**
> Running Edgy on 640m with fresh install. i confirm brightness keys works till login screen. I have BIOS A05 .

Edgy seems to be the pain, I have same problem. And others. Am seriously considering going the painful path of reinstalling Dapper though it means I will lose days of productivity. 

Also, when you press these keys up to X login and you are not on quiet you see it reacts by saying something about keypress. It hangs my boot though so don't want to mess with it

Sinclair :evil:

---

### Post by patrickfromspain on 2006-11-22
If you open gconf-editor, under apps -> gnome-power-manager, there you should have: AC_brightness, and battery_brightness. Change the values and it should be fine

---

### Post by lucads on 2006-11-23
> If you open gconf-editor, under apps -> gnome-power-manager, there you should have: AC_brightness, and battery_brightness. Change the values and it should be fine

This method does not affect current session, but only when you unplug+replug the AC cable.

---

### Post by lucads on 2006-12-05
according to : [https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/74284](https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/74284)

A temporary workaround for the issue (until a proper debug on acpi module will be performed) is to edit the file /etc/modprobe.d/blacklist inserting "blacklist video" at the end of the file.

This workaround works properly on my inspiron 6400/E1505 with ubuntu 6.10 & bios revision A09

---

### Post by pvegdahl on 2006-12-05
> **lucads said:**
> A temporary workaround for the issue (until a proper debug on acpi module will be performed) is to edit the file /etc/modprobe.d/blacklist inserting "blacklist video" at the end of the file.


Thanks, that seems to work for me too. I haven't noticed anything else that it breaks... yet. Does anyone know what the video module does? Obviously it is not required by the x server.

For the record, video related things I have tested and that still work:
X-server
3D acceleration
ATI graphics card clock and voltage throttling.

If I find anything that this seems to break, I'll let you know.

Thanks again for the fix. This was one of the biggest things I was still unable to get working on my laptop!

---

### Post by meethead on 2006-12-06
Try setting the brightness (using your fn keys) on the Grub screen prompt; or any screen before the login shows up.

I had the same problem (Dell 9200); this (the brightness quickset), for whatever strange reason, appears to work BEFORE the OS has booted.

Go figure ;)

Cheers,
Warren

---

### Post by MarkRobert on 2006-12-17
Damn. Went from A08 to A11. Bye bye brightness controls.

---

### Post by MarkRobert on 2007-01-10
Same on A12

---

### Post by lilmienboy on 2007-01-10
well the blacklist work on my laptop but im not sure what bios i have

---

### Post by Dygear on 2007-01-11
Seems to be a hal bug.

```
$ lshal|grep smbios.system
  smbios.system.uuid = 'E2E40880-47E1-11CB-8D09-DA52A91E8010'  (string)
  smbios.system.serial = 'L3AT721'  (string)
  smbios.system.version = 'ThinkPad Z61m'  (string)
  smbios.system.product = '945035U'  (string)
  smbios.system.manufacturer = 'LENOVO'  (string)
```

I can go down brightness on this, I just can't go up with out it throwing a fit. By fit, I mean, I have to press the Fn + Home key three times to get my screen back from blank.

I'm going to try the blacklist thing, I'll be right back ...

... WORKS ...

It only patches the issue tho, not fixing it. The gnome power manager has little to no clue what's going on with the screen brightness (while it still comes up when changing brightness it only displays the bar at max). I also have not checked for performances side effects, but there should be none.

---

### Post by Vladimir_BG on 2007-01-23
I too can cofirm that bug. I am running Edgy on Inspiron 6400.

Also, I think it's a kernel related issue cause I was running Fedora Core 5 and brightness controls worked, after updating only the kernel those controls stoped working. I have also filed that bug at redhat's bugzilla. I see that launchpad already has the bug filed so I wont spam.

Will try that blacklist trick and get back to you on that one.

---

### Post by The_night on 2007-01-26
[http://www.ttuttle.net/blog/computers/software/dell-inspiron-e1405-bios-a05-linux-brightness-hotkey-fix.html]("http://www.ttuttle.net/blog/computers/software/dell-inspiron-e1405-bios-a05-linux-brightness-hotkey-fix.html")

I am assuming that this is a problem with all dell computers.  It is related to a bios change.  I have the same problem and I dont understand it.  Please help!

---

### Post by sgardne on 2007-01-31
I just wanted to chime in and say that the blacklist hack worked for me as well. Inspiron 6400, A12 BIOS, on Eft. Thanks for the hack.

--s

> **lucads said:**
> according to : [https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/74284](https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/74284)

A temporary workaround for the issue (until a proper debug on acpi module will be performed) is to edit the file /etc/modprobe.d/blacklist inserting "blacklist video" at the end of the file.

This workaround works properly on my inspiron 6400/E1505 with ubuntu 6.10 & bios revision A09

---

### Post by nachotronics on 2007-02-06
I am about to try the blacklist workaround on my Inspiron 6400 / ATI x1400, my bios version is A09, and the brightness control worked just fine one day ago, on Edgy, but i've been trying to fix many things so i don't know when i lost it  :P

>> Anyone knows what the video module is (specifically) for?

---

### Post by mrmailer on 2007-02-15
drat, i am on fc6 and i am having this problem.  I don't full brightness on no battery, just the ability to control brightness.

---

### Post by mrmailer on 2007-02-17
doesn't the blacklist mean you can't control brightness at all, it just stays brighter?

---

### Post by nachotronics on 2007-02-18
> **mrmailer said:**
> doesn't the blacklist mean you can't control brightness at all, it just stays brighter?

No, blacklisting that module you get the full working brightness control back, you can adjust the 7 levels of brightness using Fn + Up/Down

(At least thats what I got)

---

### Post by f3ua on 2007-02-19
I can confirm that the blacklist workaround works on my new dell xps m1210 with intel video card. Also beryl and all other programs installed still work.

Perhaps changing the topic title may be useful because i've searched hard to find this.

Bye!

---

### Post by rahulthewall3000 on 2007-02-27
Hello! 

The blacklist fix worked on my Dell Latitude D520 with an Intel 945GM chipset as well, with no problem whatsoever!

Cheers
Rahul Jain

---

### Post by tschneiter on 2007-02-27
Just chiming in...
The blacklist hack works on a dell 640m, i945gm video, A09 bios as well. Thanks for the tip!

(now, can you make my sleep function work?;-))


EDIT -
This is quite a fix, because sleep is now working perfectly (as opposed to not at all before).... On the other hand, my screen will no longer turn back on after being shut...

---

### Post by mrmailer on 2007-03-01
I am hoping now that I am going to blacklist video that suspend2ram still will work.

---

### Post by ishmeetahuja on 2007-03-01
just to add in..


"blacklist" hack works pretty well on my Dell 6400 too.

Nice hack !!!!

---

### Post by Robrecht on 2007-03-02
Hello,

The intention of this post was to summarize the topic and to try and give some explanation what is wrong, so if you already solved it thanks to the other posts you can skip this one. If you only read this one, credit goes out to other posters here :).

I am in fact a Gentoo Linux user but I did find some useful help here for the issue we are all talking about.
The other place where this post is based on can be found at [the genoo wiki]("http://gentoo-wiki.com/HARDWARE_Dell_Inspiron_E1405").

The first problem I had was that the brightness keys themselves were not working, so i had to use "setkeycode" to assign keycodes to them. This seems not to be the case in Ubuntu, or at least I did not understand that from the posts in this topic :).

Second problem was the same as everybody else here had. I couldn't change brightness after kernel booted. As mentioned earlier in this topic, the problem resides within the acpi video module in the kernel. There seems to be some sort of bug in it, that was not present in older versions, as I read that changing brightness did work in previous versions of Ubuntu (and thus in previous versions of the Linux/Ubuntu kernel).

The solution suggested here disables loading of that kernel module, and therefor the bug wont be there:

> **lucads said:**
> according to : [https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/74284](https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/74284)

A temporary workaround for the issue (until a proper debug on acpi module will be performed) is to edit the file /etc/modprobe.d/blacklist inserting "blacklist video" at the end of the file.

This workaround works properly on my inspiron 6400/E1505 with ubuntu 6.10 & bios revision A09


Here is another solution that basically does the same thing, but in another way. Beware that I am no Ubuntu user so this might not be the best way to do it on your favorite Linux distribution.
I recompiled my kernel without the acpi/video module, so its simply not there, so it won't be loaded, it won't even be attempted :).

I expect that this issue will be resolved in future kernel releases, as I saw this issue has already been reported, so if and when its fixed, don't forget to undo your changes if you used the blacklist method. If you used the other way I described, you probably know some basics about configuring and compiling a kernel (that sounds a lot harder than it actually is, really). The problem is that Ubuntu ships kernels as binaries, so if you update the kernel and the problem is not resolved yet (withing that acpi/video module) then you will have the same problem adjusting brightness again and do this all over.

So maybe after all it's better to use the blacklist method anyway :)

You might wonder what the module actually is made for, well its an acpi module so that means it provides power saving features and the like. Nothing you need to worry about too much, unless you think battery life is as important as your own ;).

PS: Sorry for not providing a lot of references, but I really can remember all the places google referred me to :)

---

### Post by dom on 2007-03-04
Blacklisting the video module works well on my inspiron 9400, bios A06 (12/18/2006).

I did notice before adding video to the blacklist that the brightness keys would work after a hibernated session was restored !

---

