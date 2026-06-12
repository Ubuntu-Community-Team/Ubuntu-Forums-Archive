---
title: "fujitsu tablet stylus does not work"
date: 2009-11-30
forum: Hardware
---

### Post by aussiedwarf on 2009-11-30
Hi, I recently installed 9.10 on my fujitsu t4010 tablet. All seemed to work well. I got pen and rotation working. After changing he xorg.conf the eraser and right click operated correctly. Now, for some reason right click and eraser on the stylus does not work. I thought this could be because I used compiz (even though I am pretty sure I had right click working) so I tried without. No success. I tried installing 9.10 again on another partition but same problem but taking it slow to see if it worked. No right click. That install also happens to come up with a crash report.

I still have 8.10 and windows which work fine. I tried 9.04 when it came out but it had rotation problems.

I have included xorg.conf and xinput. xsetwacom list produces nothing.

Can anyone give me a hand?

Thanks in advance, aussiedwarf

---

### Post by Favux on 2009-12-01
Hi aussiedwarf,

Your situation is a little strange because it looks like the 10-linuxwacom.fdi is grabbing your tablet and the xorg.conf isn't doing anything.  This is surprising, but may be due to Karmic.

According to xinput the .fdi/HAL is calling your devices:

stylus = "PnP Device (FUJ02e5)"

eraser = "PnP Device (FUJ02e5) eraser"

There's a couple ways to handle it but easiest would be to get a .fdi that parses the HAL names into linuxwacom names like stylus and eraser.  That should let you use wacomcpl and get your eraser and stylus button back.

I have a couple experimental .fdi's for serial tablets.  You'd want to return the xorg.conf back to pristine default (comment out the Wacom stuff or whatever).  See the serial tablet pc .fdi attached to the bottom of this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Or you could do me a favor and try the [new generic .fdi]("http://ubuntuforums.org/showpost.php?p=8367378&postcount=579") which I'm hoping will work for everyone.

Notice it's now 10-linuxwacom.fdi in Karmic rather than 10-wacom.fdi like in Jaunty.  Same location though so:
```
sudo cp /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi /home/yourusername/Desktop/10-linuxwacom.bak
```
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi
```

---

### Post by aussiedwarf on 2009-12-03
Well, I replaced the old fdi with the test3.5 fdi and removed the xorg.conf. It didnt work after the first reboot but after the second the pointer worked. xsetwacom list showed
```

stylus stylus
eraser eraser

```

I did not have right click though. I then thought I might as well try test1 fdi. I put that in and after a couple of reboots I found that I had the same problem, no right click. xsetwacom list showed
```

eraser eraser

```

This looked to be a step backward so I went back to test3.5 fdi. This time it took many reboots and the pointer did not work at all. Going to test1 fdi has the same effect. Basically, either fdi will sometime give me no stylus at all. Other times I seem to get only the eraser. Its seems random. xsetwacom is as it was above when the eraser works. I have included my xinput list below when the eraser works.

Did I do something wrong? What can I do?

[edit]
right, using test1 fdi i just got the stylus. xinput is listing it as "PnP Device (FUJ02e5)"	id=2 while the eraser is still "eraser"	id=3	[XExtensionKeyboard]
[/edit]

[edit 2]
ok, looking back when I had stylus and eraser, I could have changed the settings to get right click working. Oh well
[/edit 2]

---

### Post by aussiedwarf on 2009-12-11
Well, its been a while. Sometimes I get stylus,sometimes I don't. At one stage everything worked correctly but it all seems to be fairly random. So the quewstion is, what can I do to try and tell why all of the wacom stuff is not loading correctly or being detected when this computer restarts. Are there logs I can look up to see what is happening?

---

### Post by Favux on 2009-12-11
Hi aussiedwarf,

A couple of new things.  One guy could get his working by restarting X.  We noticed in his Xorg.0.log that when things worked (after restarting X) there was no mention of plug and play like there was on a reboot.  So maybe something is squirrelly with plug and play with serial devices.

Another user said compiling and installing linuxwacom 0.8.4-4 and using new-generic rc1 (basically the same as test3.5) worked for him.  I don't know if he tested it as long as you did 0.8.4-1.

So Xorg.0.log and messages in /var/log/.  And rc1 and a debug version are at the same place as test3.5.  The debug version would show you the lines to add to the serial section to increase the information in the  logs.  Holler if you need help.

---

