---
title: "dell inspiron 6000 total freeze (reboot)"
date: 2005-06-10
forum: Hardware &amp; Laptops
---

### Post by jeroevi on 2005-06-10
hi,

I started out a month ago by installing suse 9.2. It worked more or less ok unless that some of the software was outdated and i sometimes had a freeze of my screen which required me to reboot.

Since I had only hear good things about ubuntu and saw it as number one on distrowatch I decided to give it a go. So I installed the 5.0.4 without any issues.
Congrats for the makers!!

I have however on two accasions had a complete freeze of my laptop. Once when the openGL screensaver thematrix was running and another time for no apparant reason.

I have a intel centrino 2.13Ghz, 1024 RAM, XWGA 1920x1200

Does anyone know why these freezes are occuring?

thanks,
Jeroen

---

### Post by banditti on 2005-06-10
If it is the machine locking, but the mouse still moves try adding the following to /etc/X11/xorg.conf, under the device section.

"backingstore" "true"

If that doesn't work, remove it and try:

"RenderAccel" "true"

You take a performance hit if you go straight to renderaccel, so try it last.

---

### Post by Matt05 on 2005-06-10
I have a Dell Latitude D610.  Installing 5.04 worked also out of the box, but the system ran _very_ unstable.  As a test case I wrote a script that copied files in the background while a video was running at the same time.  About 1 complete freeze every 2h or so.

After days of trial and error I settled for the linux-image-2.6.12-1-686 kernel from breezy (manually downloaded from the ubuntu packages site and installed with dpkg).  Then I added the kernel parameters "idle=halt pci=bios" in /boot/grub/menu.lst and switched the BIOS starting routine from "fast" to "thorough" (to make sure devices are initialized properly).

This improved things a lot: The system now runs much more stable (with normal use about 1 freeze in a week) and is usable for the first time.

It's a bit a pity though that I still have to boot Windows when I need a 100% reliable system (for presentations, etc).

---

### Post by jeroevi on 2005-06-11
Thanks for your replies,

The mouse also freezes, so the first solution will not work for me.

[QUOTE=Matt05] As a test case I wrote a script that copied files in the background while a video was running at the same time.  About 1 complete freeze every 2h or so.[/QUOTE]
I will try this test as well to see what happens. My last freeze however happened for no apparant reason. There was no load on the machine at all.

If I work normally on the machine (couple firefox screens, eclipse, nautilus, some terminals, mysql and some small stuff) it works quite well.

Another freeze I had the last day was while I was surfing and firefox switched to a new page. i have the impression something is wrong with the screen driver. Could it be that the driver causes the crash? I'm using the ATI driver for my graphics card (ATI Technologies, Inc. Radeon Mobility M300 (M22)).
Does anyone have bad experiences with this?

greetz,
Jeroen

---

### Post by jeroevi on 2005-06-20
[QUOTE=jeroevi]Thanks for your replies,

The mouse also freezes, so the first solution will not work for me.


I will try this test as well to see what happens. My last freeze however happened for no apparant reason. There was no load on the machine at all.

If I work normally on the machine (couple firefox screens, eclipse, nautilus, some terminals, mysql and some small stuff) it works quite well.

Another freeze I had the last day was while I was surfing and firefox switched to a new page. i have the impression something is wrong with the screen driver. Could it be that the driver causes the crash? I'm using the ATI driver for my graphics card (ATI Technologies, Inc. Radeon Mobility M300 (M22)).
Does anyone have bad experiences with this?

greetz,
Jeroen[/QUOTE]
 I have looked in all the log files under /var/log and I cannot find anything that could explain the freezes I'm having. I there any other way to monitor the system for system failures??

Please help me this is becoming a pain!!

---

### Post by pifgold on 2005-06-21
Hello,

I installed ubuntu Hoary 5.04 too on my new Dell Inspiron 6000. Installation OK, no pb ! But I've got some stranges freezes on about 2h regularly (sometimes 1minute or 20 are sufficient to freeze the laptop.. :(

Help needed... No log. Looks like an hardware problem... ? Somebody found a solution... ?

Thanks,

Fred.

---

### Post by jeroevi on 2005-06-30
Another day, another freeze on my laptop...
Yesterday I have developed on my pc during the complete day, using tomcat and eclipse. I had no problems. Today my machine was booted, but not yet used, and it froze for no reason. What can this be? acpi? apm? kernel?
If anyone has a suggestion please let me know.

regards,
jeroen

---

### Post by ewinslow on 2005-06-30
[QUOTE=jeroevi]froze for no reason. What can this be? acpi? apm? kernel?
If anyone has a suggestion please let me know.
[/QUOTE]
I wonder if this can be related to bad RAM? Can you swap out RAM to test that? My Inspiron 6000 has no freezes whatsoever. I'm running the 2.6.10-5-386 kernel.

---

### Post by XDevHald on 2005-06-30
**jeroevi - **Have you tried re-installing the OS?

---

### Post by jc3835 on 2005-07-01
[QUOTE=BB]**jeroevi - **Have you tried re-installing the OS?[/QUOTE]
 Looks like I'll have to keep an eye on this thread... No like issues with my Inspiron 6000 yet, but then again I can't even get wireless working!

---

### Post by Houman on 2005-07-02
Hi there;
I also have a Dell Inspiron 6000 runing ubuntu hoary, for me everything was perfect until i decided to enable 3D acceleration, after this my computer kept freezing and i couldnt find anything out of the ordinary with th elog files until one day i stumbled upon a forum entry talking about mysterious X related crashes due to some ATI cards.  Anyways got rid of 3D accel  :?  :mad:  and now everything is working

Houman

---

### Post by mlord on 2005-07-02
>Does anyone know why these freezes are occuring?

If your newer machine is using libata for the hard disk and optical drives ("ata_piix" module), then the lockups may be due to a serious bug in libata.

Try leaving a disc in the optical drive, and see if the freezes go away.  If so, then that's the bug.  I am using a libata_error_handling.patch applied to my kernel to fix this.  You can find it on my site (with other libata fixes for stock kernels on my i9300) at [http://rtr.ca/dell_i9300/](http://rtr.ca/dell_i9300/).

---

### Post by jeroevi on 2005-07-04
[QUOTE=ewinslow]I wonder if this can be related to bad RAM? Can you swap out RAM to test that? My Inspiron 6000 has no freezes whatsoever. I'm running the 2.6.10-5-386 kernel.[/QUOTE]

How do I swap out RAM?

---

### Post by jeroevi on 2005-07-04
[QUOTE=BB]**jeroevi - **Have you tried re-installing the OS?[/QUOTE]

I did not reinstall the OS. However I had the same problem under SuSE 9.2. So it must be related to some component installed under both distro's.

---

### Post by jeroevi on 2005-07-04
[QUOTE=Houman]Hi there;
I also have a Dell Inspiron 6000 runing ubuntu hoary, for me everything was perfect until i decided to enable 3D acceleration, after this my computer kept freezing and i couldnt find anything out of the ordinary with th elog files until one day i stumbled upon a forum entry talking about mysterious X related crashes due to some ATI cards.  Anyways got rid of 3D accel  :?  :mad:  and now everything is working

Houman[/QUOTE]

3D is not yet installed on my machine, so can't be that:

[I]jeroen@wxp-verelje:~$ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect[/I]

Thanks,
jeroen

---

### Post by jeroevi on 2005-07-04
[QUOTE=mlord]
If your newer machine is using libata for the hard disk and optical drives ("ata_piix" module), then the lockups may be due to a serious bug in libata.

Try leaving a disc in the optical drive, and see if the freezes go away.  If so, then that's the bug.  I am using a libata_error_handling.patch applied to my kernel to fix this.  You can find it on my site (with other libata fixes for stock kernels on my i9300) at [http://rtr.ca/dell_i9300/](http://rtr.ca/dell_i9300/).[/QUOTE]

I am indeed using the ata_piix module. I will leave a CD in the bay to see if I have no more freezes. The anoying thing is that I can not really test this.

mlord, do you know how to trigger a freeze with this specific bug?

thanks,
jeroen

---

### Post by dr06anju on 2005-07-04
Hello,

Sorry, don't have the answer, but :

1) my dell 6000 (ati x300) works perfectly (no freeze since 3 months) on ubuntu 5.04 (kernel 386, ati drivers from ubuntu repository, ata_piix module)

2) I had this issue with my previous machine, due to nvidia drivers & xorg (there are some threads on that on ubuntu or gentoo forums). The machine seemed to  be freezed but it was "only" X server that take 100% of the cpu load.
To figure out if your pb is due to X server, you could monitor your cpu with a background script and check after a freeze if Xserver was overloaded.
(Or you could try to connect to your laptop with another machine, if you have one)

Anyway, your pb "is" due to some software configuration because I don't have the pb with the same hardware.

ciao,
david

---

### Post by mlord on 2005-07-04
[QUOTE=jeroevi]I am indeed using the ata_piix module. I will leave a CD in the bay to see if I have no more freezes. The anoying thing is that I can not really test this.

mlord, do you know how to trigger a freeze with this specific bug?
[/QUOTE]

The bug is a race-condition in the libata device error handling code.  Hard drives rarely have errors, so in this case it is the ATAPI (cd/dvd) device that causes them.

The Kubuntu desktop likes to automatically create and display icons for inserted discs.  To do this, it must constantly poll for an inserted disc.  These polls fail with a device error when no disc is inserted, thus triggering the buggy error handling in libata.

But since the bug is a "race condition", it does not always cause a system lockup.  Just once in a rare while..  For me, that was about once every couple of hours until I figured out what was going on.

If a non-blank disc is left in the drive, then the polling always succeeds with no error, and therefore no lockups.

There is a kernel patch on my site to fix the problem (not my patch, but it works).

I don't know if the Gnome desktop behaves the same way as Kubuntu (KDE) in this regard.

Cheers

---

### Post by jeroevi on 2005-07-05
[QUOTE=mlord]I don't know if the Gnome desktop behaves the same way as Kubuntu (KDE) in this regard.[/QUOTE]

I does, an icon is displayed as long as a CD is inserted.
No freeze yesterday (I kept a CD in all day)
Today I will work without the CD inserted. And strange but true, I am hoping that my machine will freeze ...

thanks for your help
Jeroen

---

### Post by moment on 2005-07-06
Try this.  Open the xorg.conf file and comment out the line which says
```
Option     "DPMS"
```
in the Monitor section.

---

### Post by vasdee on 2005-07-11
i had similar problems with Mandrake 10 a while back and now with Hoary. I don't know if my problem stems from me using a Dell Laptop or not, but basically my freezing problem occurs randomly after i make the switch from AC to battery power and vice versa.

I dug up the old mandrake solution and tried it with hoary and so far so good.
It just requires appending a few boot params to grub. (/boot/grub/menu.lst)

```

title Ubuntu, kernel 2.6.10-5-386 
root (hd0,4) 
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro quiet splash pci=bios idle=halt noapm nolapic noapic 
initrd /boot/initrd.img-2.6.10-5-386 
savedefault 
boot

```

The fix lies with the "noapm nolapic noapic" args. Its been a couple days of switching between battery / AC power and i haven't had any freeze ups.

---

### Post by jeroevi on 2005-07-12
[QUOTE=mlord]>
If your newer machine is using libata for the hard disk and optical drives ("ata_piix" module), then the lockups may be due to a serious bug in libata.

Try leaving a disc in the optical drive, and see if the freezes go away.  If so, then that's the bug.  I am using a libata_error_handling.patch applied to my kernel to fix this.  You can find it on my site (with other libata fixes for stock kernels on my i9300) at [http://rtr.ca/dell_i9300/](http://rtr.ca/dell_i9300/).[/QUOTE]

After a week with a CD in the tray and without freezes I have decided to upgrade my system with the patch of mlord. I now have a 2.6.12.2 kernel with patches. I all goes well I will have no need to post anything further in this thread.

Thanks mlord. :razz:

---

### Post by supanova on 2005-08-02
This is freaky

I thought that all my problems were with the i810 driver and after following all manner of suggestions on ubuntuforums, linuxquestions and fedoraforums I thought I was going mad changing xorg.conf and kernel parameters

I just popped in a CD hoping that this could be the case and Xorg dropped instantly from about 9% utilisation to 0.3% utilisation at most.

Are all the problems with freezes that people are pointing us to be X not maybe just a wild goose chase?..... Does anyone have any more insight on this?

I'm going to monitor......

Thanks

---

### Post by nocloud on 2005-08-08
i am also getting these freezes, i am going to try the cd thing and see what happens.  i will post back in a few days with the results

---

### Post by nocloud on 2005-08-08
i am also getting these freezes, i am going to try the cd thing and see what happens.  i will post back in a few days with the results

---

### Post by mlord on 2005-08-10
[QUOTE=jeroevi]After a week with a CD in the tray and without freezes I have decided to upgrade my system with the patch of mlord. I now have a 2.6.12.2 kernel with patches. I all goes well I will have no need to post anything further in this thread.

Thanks mlord. :razz:[/QUOTE]
 I have now updated my kernel and patches for my dell i9300 (and most similar Centrino notebooks) at [http://rtr.ca/dell_i9300/kernel/](http://rtr.ca/dell_i9300/kernel/)

The libata total-system-lockup bugfix patch has now shrunk to a single line, and seems to still work for me after a couple of days.  If somebody else here (jeroevi?) could try this instead of the earlier bulky patch, then that would be useful.

Anyway, my site has the 2.6.12.4 kernel + bugfixes, including a prebuilt tree and some rudimentary install instructions in the updated README file.

Cheers

---

### Post by Pogo on 2005-08-11
[QUOTE=mlord]I have now updated my kernel and patches for my dell i9300 (and most similar Centrino notebooks) at [http://rtr.ca/dell_i9300/kernel/](http://rtr.ca/dell_i9300/kernel/)

The libata total-system-lockup bugfix patch has now shrunk to a single line, and seems to still work for me after a couple of days.  If somebody else here (jeroevi?) could try this instead of the earlier bulky patch, then that would be useful.

Anyway, my site has the 2.6.12.4 kernel + bugfixes, including a prebuilt tree and some rudimentary install instructions in the updated README file.

Cheers[/QUOTE]

I've added a bug to bugzilla.ubuntu.com for this. See

[http://bugzilla.ubuntu.com/show_bug.cgi?id=13370](http://bugzilla.ubuntu.com/show_bug.cgi?id=13370)

Regards

---

### Post by bubblegum on 2005-08-12
[QUOTE=Pogo]I've added a bug to bugzilla.ubuntu.com for this. See

[http://bugzilla.ubuntu.com/show_bug.cgi?id=13370](http://bugzilla.ubuntu.com/show_bug.cgi?id=13370)

Regards[/QUOTE]


Interesting I have these random crashes after a few hours on a recent sony VAIO laptop using ata_piix. Except it's running the PCLinuxOS distro running KDE 3.4.2, kernel 2.6.12.3. I never had a crash using Hoary which uses gnome and an older kernel. (btw PCLOS 9.1 is much more faster than Hoary this is shocking!)

I'll try with a CD left in the drive and see how it goes. This problem has driven me nuts for some time, I hope it is it!

---

### Post by jeroevi on 2005-08-30
[QUOTE=mlord]I have now updated my kernel and patches for my dell i9300 (and most similar Centrino notebooks) at [http://rtr.ca/dell_i9300/kernel/](http://rtr.ca/dell_i9300/kernel/)

The libata total-system-lockup bugfix patch has now shrunk to a single line, and seems to still work for me after a couple of days.  If somebody else here (jeroevi?) could try this instead of the earlier bulky patch, then that would be useful.
[/QUOTE]

Have installed a 2.6.12.4 kernel with the latest patch from mlord. If any troubles I will post them here.

---

### Post by gravestone on 2005-08-31
I have a Dell 6000 as well, and am experiencing random total lock ups. Mouse does not even move. Ctrl-Alt-Del or Ctrl-Alt-Backspace both fail, but on reboot the file system is clean.

I tried ubuntu, and now run kubuntu, and still experience the problem. I noticed it occurs when playing MP3s. Either with the Juk (worse) or XMMS. Went a couple of days with no music, and no lock ups.

Still testing my theory.

---

### Post by Titan3025 on 2005-09-01
guys.. are u running a vanillla kernel with mlords patches to fix this problem? do all the nice ubuntu things like automount, hotplug etc. work with vanilla kernels? I thought the ubuntu team did some heavy patching for all this to work.

if u all are having a special 2.6.12.x kernel plz point me to the download location.

Thanks,
Titan3025

---

### Post by Pogo on 2005-09-02
[QUOTE=Titan3025]guys.. are u running a vanillla kernel with mlords patches to fix this problem? do all the nice ubuntu things like automount, hotplug etc. work with vanilla kernels? I thought the ubuntu team did some heavy patching for all this to work.

if u all are having a special 2.6.12.x kernel plz point me to the download location.
[/QUOTE]

If you problem is with SATA and optical drive that is addressed in this bug:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=13370](http://bugzilla.ubuntu.com/show_bug.cgi?id=13370)

then it has been fixed and next kernel by ubuntu will have the patch.

Pogo

---

### Post by Titan3025 on 2005-09-02
wow.. nice.. lets hope this patch finds its way to the hoary 2.6.10 kernel soon.

---

### Post by jeroevi on 2005-09-06
[QUOTE=jeroevi]Have installed a 2.6.12.4 kernel with the latest patch from mlord. If any troubles I will post them here.[/QUOTE]

The patch of mlord is still working perfectly. However since I am now using kernel 2.6.12.4 I am unable to compile the ATI driver kernel module. It simply does not compile on a 2.6.12 kernel.

My question to everybody and mlord in specific: can the patch be redone on the 2.6.10 kernel of hoary?

greetz

---

### Post by mlord on 2005-09-06
[QUOTE=jeroevi]
My question to everybody and mlord in specific: can the patch be redone on the 2.6.10 kernel of hoary?
[/QUOTE]

Question for ATI:  Why not release the source code for your video drivers so that you don't have this support nightmare in the future?????

---

### Post by mlord on 2005-09-06
[QUOTE=jeroevi]
My question to everybody and mlord in specific: can the patch be redone on the 2.6.10 kernel of hoary?[/QUOTE]

You should be able to patch the standard Hoary kernels with the 2.6.13 version of the patch:  a one-liner now:
```
--- linux-2.6.12/drivers/scsi/libata-scsi.c     2005-08-15 18:24:13.000000000 -0400
+++ linux/drivers/scsi/libata-scsi.c    2005-08-15 18:22:54.000000000 -0400
@@ -667,6 +667,7 @@
         * appropriate place
         */
        host->host_failed--;
+       INIT_LIST_HEAD(&host->eh_cmd_q);

        DPRINTK("EXIT\n");
        return 0;


```

---

### Post by spooky-mac on 2005-11-02
My new Smartbook lappy shows the same symptoms. Complete freezes at unregular intervals. Sometimes one freeze in a week, sometimes two a day. It is interesting however that the system writes to the harddisk irregulary for extented periods of time and sometimes, it freezes while doing it. No matter if I hear music, use Openoffice, browse the net or do nothing. Very disgusting.:???:

---

### Post by olov on 2005-11-19
I have the same problem with my Inspiron 6000.
Random lockups, mouse and everything. Cold boot only option.

BUT, it only happens when I'm connected with wlan and not when using a cable.
It also happens more frequently when on Wlan + transfering alot of data and possibly moving the mouse at the same time. (Not sure about the mouse, but it seems to happen more often when I'm actually using the computer while downloading).

If you have the same problem, do you use a wireless connection? Try to switch to cable to see what happens.

Regards.

---

