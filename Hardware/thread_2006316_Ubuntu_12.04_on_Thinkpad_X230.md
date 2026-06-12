---
title: "Ubuntu 12.04 on Thinkpad X230"
date: 2012-06-19
forum: Hardware
---

### Post by beudycool on 2012-06-19
Hi,

I get random freezes with Ubuntu 12.04 on a new Thinkpad X230 Ivy Bridge. 

No response form mouse/keyboard and power button shutdown/restart needed in that case. Frequency : about once a day. 

CPU i5-3210M
RAM 4GB
SSD intel 330 

Since it freezes, no crash report is being sent. I don't how can I help to fix this.

---

### Post by graxspoo on 2012-06-19
I'm having a similar lock-up on my Thinkpad T60. It's probably the same bug, so let me know if you figure something out, and I'll do the same.

---

### Post by typhoon_tip on 2012-06-19
When in that status, pressing CTRL+ALT+F1 brings up a terminal window or not ?

---

### Post by beudycool on 2012-06-19
> **typhoon_tip said:**
> When in that status, pressing CTRL+ALT+F1 brings up a terminal window or not ?

No effect.

---

### Post by typhoon_tip on 2012-06-20
> **beudycool said:**
> No effect.

After hard reboot, check the XORG log, you may find something useful there. I think is X related, happens very seldom also to me, seems related to Touchpad in my case.

---

### Post by graxspoo on 2012-06-20
> **typhoon_tip said:**
> After hard reboot, check the XORG log, you may find something useful there. I think is X related, happens very seldom also to me, seems related to Touchpad in my case.

Sorry for the newbie questions, where is the XORG log? When you say "X" do you mean "X Windows?" One time I got this freeze was after I ran Gimp, so that seems possible.

---

### Post by beudycool on 2012-06-20
I did not see any clue in the Xorg.log (/var/log) 
My touchpad is disabled (BIOS)

---

### Post by typhoon_tip on 2012-06-20
Was it a fresh install or an upgrade from previous versions ? I suggest you to try out the LiveCD for your Ubuntu, and see if it blocks even like that or not.

---

### Post by beudycool on 2012-06-20
> **typhoon_tip said:**
> Was it a fresh install or an upgrade from previous versions ? I suggest you to try out the LiveCD for your Ubuntu, and see if it blocks even like that or not.

Fresh install, bought the X230 on the release day this month.
I suppose it's too new hardware

---

### Post by pdietzsch on 2012-06-22
Same here (x230-i7/ivy).

Might be related to the HD4000 graphics.

Try to use kernel 3.4 (which seems to work for me) as described here:
[http://ubuntuforums.org/showpost.php?p=12035647&postcount=16](http://ubuntuforums.org/showpost.php?p=12035647&postcount=16)

---

### Post by JanneM on 2012-06-23
Same thing for me. Lenovo T430, fresh install of 12.04. About once a day or so, nothing in the logs and doesn't seem connected to anything I do.

---

### Post by beudycool on 2012-06-25
> **pdietzsch said:**
> Same here (x230-i7/ivy).

Might be related to the HD4000 graphics.

Try to use kernel 3.4 (which seems to work for me) as described here:
[http://ubuntuforums.org/showpost.php?p=12035647&postcount=16](http://ubuntuforums.org/showpost.php?p=12035647&postcount=16)

Thanks. I'll update the kernel at the next freeze.
No freeze for a full day of work yesterday though

---

### Post by beudycool on 2012-06-25
Updated.

3.4.0-030400-generic #201205210521 SMP Mon May 21 09:22:02 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by beudycool on 2012-06-29
No freeze for since the kernel update.
SOLVED. thanks !

---

### Post by jpds on 2012-06-29
Potentially related bug report: [https://bugs.launchpad.net/bugs/999910](https://bugs.launchpad.net/bugs/999910) .

---

### Post by jpds on 2012-06-29
> **jpds said:**
> Potentially related bug report: [https://bugs.launchpad.net/bugs/999910](https://bugs.launchpad.net/bugs/999910) .

Please test the test kernel by installing it with:

```
$ sudo add-apt-repository ppa:kernel-ppa/pre-proposed
$ sudo apt-get update
$ sudo apt-get dist-upgrade
```

And report if the freezes no longer occur on the bug report linked above.

---

### Post by phaed on 2012-06-29
Had the same problem.

---

### Post by phaed on 2012-06-30
Finally fixed.

---

### Post by beudycool on 2012-07-02
What's the downside of using 3.4 vs 3.2 kernel ?
My instinct would say use the newest, if that's working of course

---

### Post by phiamo on 2012-07-08
I have the same issue on T430s with I7.
I will try the kernel update and report, thnaks a lot.

---

### Post by phiamo on 2012-07-10
Ok uptime now 1 day 13 hours ... seems to work,
only have some probs with pulseaudio, need to do a pulseaudio -k here and then

---

### Post by anmar on 2012-07-27
I boght an Ivy Bridge MB and noticed the same lockups when using 3.2 kernel (default in Ubuntu 12.04). If you switch to anything beyond 3.4-rc3, then you are fine. I am running 3.5 kernel and it works like a charm.

Just download all 4 packages (for i386 or AMD86) and dokg -i * .

You can get them from the Canonical Kernel Team PPA here: 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")

---

### Post by phaed on 2012-07-29
I think it is fixed.

---

### Post by beudycool on 2012-08-27
After an Ubuntu update last week, 3.4 kernel boot failed.
Reverting to 3.2.0-29 workaround the boot crash but I am now back to the initial issue, ie: ramdom freeze.

Linux X230 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Ulrik Nyman on 2012-08-28
I have the same problem with occasional lockups also running 3.2.0-29.

A fresh install of 12.04 on a new ThinkPad X230.
i7, Samsung 256GB SSD 

Linux ulrik-think 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by beudycool on 2012-08-28
Trying pre-proposed 3.2.0-31 right now:

Linux X230 3.2.0-31-generic #48~pre201208250400-Ubuntu SMP Sun Aug 26 04:33:20 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by beudycool on 2012-08-28
3.2.0-31 freezes as well.

Tried 3.5.3 (for quantal) but my external display isn't detected.

Linux fabrice-X230 3.5.3-030503-generic #201208252335 SMP Sun Aug 26 03:35:56 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by nmaster on 2012-09-24
any updates? i'm interested in getting an x230 but i'd like to know if everything works auto-magically first.

---

### Post by Ulrik Nyman on 2012-09-25
I am current running the 3.2.0-31-generic.

I do not have problems with the machine hanging after suspend.

I experience two other problems occasionally: 

About once a week: A complete halt of the machine with no response at all.

Several times a week: Suddenly Compiz fails: This only resluts in the the screen going completely white for a few seconds followed by all my windows being on the same vritual desktop and ubuntu reporting that Compiz had an internal error.



Linux ulrik-think 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:16:45 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by bikko on 2013-04-18
I'm running 12.04 on an X230 as well. I've had a COMPLETE system freezes -- no mouse movement possible, no kernel message (I ran netconsole, even, to check). I've had spontaneous hard resets.

I updated the BIOS (or should I say the EFI?), and that seemed to helped stop the spontaneous hard resets, but I was still getting a lot of total-freezes.

I put in the RAM from my MacBook Pro, and the freezes are 95% gone.

This seems silly but I think that Lenovo is shipping PC3-12800 RAM in this machine and it's supposed to be running PC3-10600 RAM... that's the main difference between the factory RAM and the MBP RAM I have in there now -- the MBP RAM is 10600.

WTF?

Any other updates from anybody?

I also can't hibernate (hibernate option is grayed out in gnome power manager), but I think it's because I have no special partition...(?)

---

### Post by Ulrik Nyman on 2013-04-19
Hi.

I still get an occasional freeze. I do not have hibernate as an option even in the system menu in the upper right hand corner. But I can hibernate from a terminal by writing "sudo pm-hibernate".

A question: Can I check the type of my ram with a command or do I have to open the machine?

---

