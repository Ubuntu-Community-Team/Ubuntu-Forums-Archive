---
title: "Suspend2?"
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by madchicken on 2005-07-19
Hi...is there anyone using Suspend2 to hibernate the laptop? I would like to know if it works well under ubuntu, because I still can't hibernate my Vaio.

Thanks

--Pierpaolo

---

### Post by adwait on 2005-07-19
Never used this......but there's an option to hibernate the computer under the log out menu.

---

### Post by madchicken on 2005-07-19
I know it, but it doesn't work for me (my laptop shutdown but freeze when it tries to boot up again).

bye

--Pierpaolo

---

### Post by Laurent Cazalet on 2005-07-20
Yes, I patched a vanilla kernel 2.6.10 with Software Suspend 2.1.7 and it works great, and it so much faster than the software suspend included in the kernel.

The only (minor) inconvenience; you cannot use the "Hibernate" option provided in ubuntu anymore, but instead run the hibernate script that you should install from the swsusp2 site.
HTH

---

### Post by mlord on 2005-07-21
[QUOTE=Laurent Cazalet]
The only (minor) inconvenience; you cannot use the "Hibernate" option provided in ubuntu anymore, but instead run the hibernate script that you should install from the swsusp2 site.
HTH[/QUOTE]

I haven't bothered with swsusp2 yet (because suspend-to-RAM is so much nicer), but you should be able to integrate their script into the Ubuntu Hibernate stuff by replacing things in /etc/acpi/hibernate.sh

Cheers

---

### Post by madchicken on 2005-07-26
Thank you guys for your help.
Now I'm trying to recompile kernel 2.6.12.3 with suspend2 support.
In the howto I found this:

> Using an initrd with Software Suspend 2 is possible. To use this, you MUST edit your linuxrc (or init) script to contain the line

    echo > /proc/software_suspend/do_resume 

BEFORE the script mounts your filesystem. If the line is missing, your system will not resume. If the line comes after mounting file systems, you will most likely suffer from filesystem corruption. You have been warned. 

Is there anyone that can explain me what does it means?

thank you very much.

--Pierpaolo

---

### Post by netsyd on 2005-07-27
It means ... don't use initrd because its going to be a pain in the you know what. You can build a 2.6.x kernel that doesn't require the use of initrd although everyone seems to say otherwise. 

I'm not using initrd running 2.6.12.3 running swsusp2 just fine.

---

### Post by madchicken on 2005-07-27
Thank you very much netsyd.
I tryed to compile my kernel without the initrd, but I got a kernel panic.
I'll try again...only a curiosity: is the /usr/share/initrd-tools/init  the right script to put the line referred by the howTo?

Another question: now when I start the pc with the new kernel I get an error saying that my suspend2 is not properly configured and the current image file is invalid, and ask me to continue with risk of damaging my filesystem or to reboot (so I choosed to reboot with an older kernel to avoid fs problems).
Why is this thing happening? It's the first time I boot with suspend2, I don't have any image file on my hd. I get the same error with the noresume2 parameter, too.

Thank you

--Pierpaolo

---

### Post by netsyd on 2005-07-27
[QUOTE=madchicken]Thank you very much netsyd.
I tryed to compile my kernel without the initrd, but I got a kernel panic.
I'll try again...only a curiosity: is the /usr/share/initrd-tools/init  the right script to put the line referred by the howTo?[/QUOTE]
I'm not quite sure how to answer this... I don't recall doing anything with this directory. Recall that I didn't have an initrd for my kernel. Mine works however magically without one despite the kernel panic issue that many people seem to get without one. 

> 
Another question: now when I start the pc with the new kernel I get an error saying that my suspend2 is not properly configured and the current image file is invalid, and ask me to continue with risk of damaging my filesystem or to reboot (so I choosed to reboot with an older kernel to avoid fs problems).
Why is this thing happening? It's the first time I boot with suspend2, I don't have any image file on my hd. I get the same error with the noresume2 parameter, too.


I am going to go out on a limb here and say this has something to do with the leftovers of a prior failed hibernate (leftover from the default used by Ubuntu which failed when you tried it?)

I ran into some issues with using the hibernate functions built in to Ubuntu that ultimately corrupted the file system... hence me moving to suspend2. I did all of this from a clean install and I purposefully avoided using hibernate until I had swsusp2 installed.

I do know that if you were to try to do boot from this image you would have the drive report file system corruption and it would automagically run fsck during boot. 
Ultimately fsck will fail and you'll be stuck giving it a root password and running fsck manually, which really wasn't all that hard, and then once its done it "SHOULD" boot up just fine. It yelled at me for running it on a mounted drive/partition but it worked. I figured if it was already broken, I couldn't really break it anymore since it wasn't letting me boot anyway.

With all of that said, I'm not quite sure how you should proceed. I would venture to guess you could boot to a "recovery" mode and then format/erase (fdisk maybe?) the swap partition which should in turn destroy this "invalid" image. But again this is Linux so theory sort of runs rampant for me... Hopefully someone will hop on here and give you a little better guidance that understands this kernel/file system junk a bit more than I do. [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

---

### Post by art on 2005-07-28
Well I am also trying to get suspend2 working, and I was getting the same big fat warning, and as their website suggests you need the IDE compiled in the kernel,  or have initrd load them before resume2 kicks in. So just run make xconfig again and change IDE from module to compiled into kernel. That way I now am able to get in the newly compiled kernel, although still can hibernate. This way you also don't need initrd.img file.
Please post if you get somewhere, maybe we can get this hibernate working...

---

### Post by madchicken on 2005-07-28
[QUOTE=art]Well I am also trying to get suspend2 working, and I was getting the same big fat warning, and as their website suggests you need the IDE compiled in the kernel,  or have initrd load them before resume2 kicks in. So just run make xconfig again and change IDE from module to compiled into kernel. That way I now am able to get in the newly compiled kernel, although still can hibernate. This way you also don't need initrd.img file.
Please post if you get somewhere, maybe we can get this hibernate working...[/QUOTE]
 Thanks, I'll give it a try.
If I can get out of this mess, I'll write an howto about suspend2 on ubuntu...
My problem is that I don't have a "test machine" on which try: I'm doing all this stuff on my work laptop...I really can't risk to loose my file system now, it would be a big shock for me :)

---

### Post by netsyd on 2005-07-28
[QUOTE=madchicken]Thanks, I'll give it a try.
If I can get out of this mess, I'll write an howto about suspend2 on ubuntu...
My problem is that I don't have a "test machine" on which try: I'm doing all this stuff on my work laptop...I really can't risk to loose my file system now, it would be a big shock for me :)[/QUOTE]


I know what you mean, but either way once you finally get it working you'll be glad you put the effort into it!!! Although, this is one of the few things that I love about Windows... suspend and hibernate are a no brainer and take no effort at all.  :-#

---

### Post by madchicken on 2005-07-28
[QUOTE=netsyd]I know what you mean, but either way once you finally get it working you'll be glad you put the effort into it!!! Although, this is one of the few things that I love about Windows... suspend and hibernate are a no brainer and take no effort at all.  :-#[/QUOTE]

Eheh...You're right man. ACPI support in Windows is still better...but I'm a patient guy  :wink: 

P.S.- Looking around to solve this problem I found a post in a group saying:
> "If you are in a hole, stop digging."

Is this a sign?  :shock: 

bye

---

### Post by netsyd on 2005-07-28
> "If you are in a hole, stop digging."  

I only worry about digging a hole so deep that I end up on some dammed playground in China. Because I don't know how to ask where the bathroom is in Chinese. 

I say backup your data to CD and march on soldier!   [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

*Unless IT is threatening you. At which point I say knock it off and go back to your cube!!!*

---

### Post by art on 2005-07-28
I don't know, man... This is too hard. I even tried to compile exacly the same kernel with the same settings (except for the /dev/hda5 obvioulsy) as you have, just to see if it works,  no go... The thing is, I see HDD activity when I type hibernate in the console, and then it all stops and hangs there forever. This seems to be too hard for me, I am on the edge of giving up (but not there yet:))

---

### Post by netsyd on 2005-07-28
[QUOTE=art]I don't know, man... This is too hard. I even tried to compile exacly the same kernel with the same settings (except for the /dev/hda5 obvioulsy) as you have, just to see if it works,  no go... The thing is, I see HDD activity when I type hibernate in the console, and then it all stops and hangs there forever. This seems to be too hard for me, I am on the edge of giving up (but not there yet:))[/QUOTE]


Ok, so.... you have a working 2.6.12.3 kernel based off of my config (wow... if you do)?

You told it (during make menuconfig) to have it suspend to **your** swap partition? 

Define forever (how long roughly are you waiting)?

I guess the only other real questions are... are you running the correct hibernate script? 

```
sudo /usr/local/sbin/hibernate
``` The thing here is it takes mine about 30 (I never really timed it) seconds or more to hibernate, and the screen is blank the whole time. I know they have some other piece that gives you a progress bar... but I never put it on. 

Also, have you checked you log files?

Boy... I got questions coming out of everywhere!

---

### Post by art on 2005-07-28
yeah, as I said the only difference i put was swap partition. And I forgot to mention , CPU type too, mine is Celeron. But these are irrelevant. 
I defined the resume2 as my swap partition. Here comes a question. Did you make anothere swap partition to hibernate to, or you are using the swap you had?
Forever in my definition is more than 3 minutes, since in the same time I can just shut it down, and boot up again, so it doesn't make sense to have it hibernate. But in relaity I have waited for around 10 minutes or more, which obviuosly means it is not working.
The kern.log has 


Software Suspend Core.
Software Suspend Compression Driver loading.
Software Suspend Encryption Driver loading.
Software Suspend Swap Writer loading.
Swapwriter: Signature found.
Software Suspend 2.1.9.9: Suspending enabled.


These are boot time messages and the messages after hibernate script has run are

Resume block device is dffff880.
Software Suspend 2.1.9.9: Swapwriter: Signature found.
Software Suspend 2.1.9.9: Suspending enabled.
Software Suspend 2.1.9.9: Initiating a software suspend cycle.
suspend_userui: userui_program not configured. suspend_userui disabled.
Resume block device is dffff880.
Software Suspend 2.1.9.9: Swapwriter: Signature found.
Software Suspend 2.1.9.9: Suspending enabled.
Freezing processes

and that's it. The next message is already next boot ](*,)

So it seems to be starting but never finishing. 
Can you post the relevant parts of your kern.log
Thanks a lot

---

### Post by netsyd on 2005-07-28
After a straight reboot..... 


```
Jul 28 21:29:33 localhost kernel: Software Suspend Core.
Jul 28 21:29:33 localhost kernel: Software Suspend Compression Driver loading.
Jul 28 21:29:33 localhost kernel: Software Suspend Encryption Driver loading.
Jul 28 21:29:33 localhost kernel: Software Suspend Swap Writer loading.
Jul 28 21:29:33 localhost kernel: ACPI wakeup devices: 
Jul 28 21:29:33 localhost kernel: C044 C0B9 C183 C188 C189 
Jul 28 21:29:33 localhost kernel: ACPI: (supports S0 S3 S4 S4bios S5)
Jul 28 21:29:33 localhost kernel: Resume block device is ddfc0ac0.
Jul 28 21:29:33 localhost kernel: Software Suspend 2.1.9.9: Swapwriter: Signature found.
Jul 28 21:29:33 localhost kernel: Software Suspend 2.1.9.9: Suspending enabled.
```

Be right back ..... gonna make lappy take a nap....  [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]


Nothing more to report after multiple hibernates. I get no log messages at all. (kern.log or syslog)

---

### Post by art on 2005-07-29
Thanks man!
So as far as I can see the only difference you have is that you don't get this

Software Suspend 2.1.9.9: Initiating a software suspend cycle.
Freezing processes

messages? 
Other than that it's all the same... 
Why is my stupid laptop not working :mad: I even installed the hibernate script from repos, not working either...

So what about the swap, did you create another one, or it is the one you had before?
Also how big is it?

---

### Post by netsyd on 2005-07-29
I didn't create a second swap... I used the original one I defined during installation. 

And If I recall correctly it was roughly about 1.1GB ... I wasn't sure how much space it would really need for hibernate so I over did it a bit (512MB ram). I'm on a 60GB drive - 30 Windows, 5GB fat32 transfer and the rest for Linux, so I wasn't to worried about space.

---

