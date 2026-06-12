---
title: "Update broke about everything!!!!!!!!!!!"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by barbolanero on 2009-03-02
Today (2 March 2009) I saw that there were some updates and therefore, updated. There were some kernel updates. To my surprise, after resetting, I found that:

-first, it says there's some kind of conflict with tomboy applet
-If I press the shutdown button or menu entry just quits the panels but hangs in there, I can still see and use any aplication, and even worst, it doesn't give me the shutting down options!
-Firefox and Tomboy just doesn't work.

I'm really desperate since I'm a teacher and most of my files are there. What can I do to avoid a fresh install (out of the question due to time reasons)?. 

This happen on my desktop computer using hardy.

---

### Post by James_mtl on 2009-03-02
You are at least more lucky them me ! 

My Lenovo T61 running Ibex does not even boot now that I updated to new kernel !  It actually look like it's booting but screen is black so I cannot tell !!  I booted with the old kernel for now !

---

### Post by jerrrys on 2009-03-02
[http://ubuntuforums.org/showthread.php?t=812394](http://ubuntuforums.org/showthread.php?t=812394)
[https://help.ubuntu.com/community/Kernel/Upgrade](https://help.ubuntu.com/community/Kernel/Upgrade)

---

### Post by gard76 on 2009-03-02
I have a T61 also, and I experience the same problem after upgrading the kernel form version kernel 2.6.27-12-generic to kernel 2.6.27-13-generic. The laptop boots more or less, but the upgrade of the kernel blacks the screen instead of showing the gdm login. I havent been able to find anything else in the logs than this error in /var/log/messages:

Mar  2 19:41:44 gard-laptop syslogd 1.5.0#2ubuntu6: restart.
Mar  2 19:45:22 gard-laptop kernel: [159158.870766] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input14
Mar  2 19:52:54 gard-laptop kernel: [159610.583905] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Mar  2 19:52:59 gard-laptop bonobo-activation-server (gard-16353): could not associate with desktop session: Failed to connect to socket /tmp/dbus-Q7fPybfzW6: Connection refused
Mar  2 19:53:05 gard-laptop exiting on signal 15
Mar  2 19:54:05 gard-laptop syslogd 1.5.0#2ubuntu6: restart.

Anybody know which log file is best to use for troubleshooting the problem described?

---

### Post by barbolanero on 2009-03-02
> **jerrrys said:**
> [http://ubuntuforums.org/showthread.php?t=812394](http://ubuntuforums.org/showthread.php?t=812394)
[https://help.ubuntu.com/community/Kernel/Upgrade](https://help.ubuntu.com/community/Kernel/Upgrade)

I don't think that will help, since I've already tried older grub entries and all do the same now. Can't really understand why. Any more ideas, please!!!!!!!!!!!!:(:confused:

Also, the minute the desktop appears this warning comes up:

[QUOTE= The panel encountered a problem while loading "OAFIID:TomboyApplet"
Do you want to delete the applet from your configuration?[/QUOTE]

And it doesn't matter if I delete it or not, it just keeps appearing.

---

### Post by Mark Phelps on 2009-03-02
You didn't say anything about selecting older kernel versions, so I'm guessing that you aren't seeing the GRUB menu.

Next time you boot, press the Esc key until you see the GRUB menu, and select a recovery mode or an older kernel.   

GRUB only adds new kernel versions to an existing menu, it doesn't replace them.  The older versions are left there for specifically this kind of situation.

---

### Post by barbolanero on 2009-03-02
> **Mark Phelps said:**
> You didn't say anything about selecting older kernel versions, so I'm guessing that you aren't seeing the GRUB menu.

Next time you boot, press the Esc key until you see the GRUB menu, and select a recovery mode or an older kernel.   

GRUB only adds new kernel versions to an existing menu, it doesn't replace them.  The older versions are left there for specifically this kind of situation.

That's not what I said. I said that I've already tried booting from older entries, and they all do the same thing!!!! And everything was working just fine! It just seems to have broken about everything. Am I the only one with this trouble?

---

### Post by e_hervet on 2009-03-03
Hi all,

It's pretty frustrating when a kernel upgrade breaks everything :-(((
I have the same problem as the first person in this thread, I have a black
screen at the end of boot. I can log on my computer from another with
ssh, then I see that usual processes and modules are here ...
so it seems boot ended correctly but I can just not log on the computer itself since screen is black.
Hope a new upgrade will fix it soon ... I still love Ubuntu, but as a 
computer scientist it's hard to tell non computer scientists people
to use it when things like that happen ...

Eric

---

### Post by civillian on 2009-03-03
> I have a black
screen at the end of boot.
I have had a similar problem, although it tells me that it cannot load the nvidia modules, and that my monitor is detected but not configured...
For the moment I'm still just using my older kernel version. I'm considering downgrading to 8.04 for stabilities sale :S (or, heaven forbid; debian)

---

### Post by elvisd on 2009-03-03
See [http://ubuntuforums.org/showthread.php?t=1084959](http://ubuntuforums.org/showthread.php?t=1084959)

---

### Post by WatchingThePain on 2009-03-03
The same happened to me on Fedora 10 so now I use Ubuntu.
It's freakin dumb.
Why can this happen?.
It's like a serious flaw in the update system mechanism.
There must be a way to prevent this.
If you install a new kernel update it's like saying 'Yes, experiment on my pc even if it breaks it'.
I'm gonna check if there's a way to backup your kernel. I think the old one stays there and you can select it.
My problem was a bit different because the old kernel wouldn't boot and the new one did but there was a dependency problem with the graphics driver for it.

---

### Post by e_hervet on 2009-03-03
Hi,
I confirm that when I connect to my computer from another one with ssh,
everything seems fine, even nvidia module is loaded, so no x-server
problem, all my processes are here, gdm, ftpd, sshd, webmin, mysqld, etc.
So weird to have this black screen!
Of course for now I boot with previous kernel: 2.6.27-12-server.

I have to say too that yesterday I updated 4 computers with kernel
2.6.27-13-server (another one with Ati Radeon Mobility X600,
another one with Nvidia GeForce 7600GS, and another one with
Nvidia Quadro NV44) and only my laptop has the problem: it's a Dell
precision M4300 with video car Nvidia Quadro FX 360M and 4Gb RAM.
One difference with the other computers is that I had to install
OSS (Open Sound) on my laptop a few weeks ago due to lack of sound
with Alsa. But OSS modules are loaded as well so I don't think
that's the source of the problem.

Hope to see a fix soon.

Eric

---

### Post by perks.williams on 2009-03-04
Same here with Dell Latitude D630

-A William

---

### Post by barbolanero on 2009-03-04
I don't mean to be rude, but no has helped me yet. And please, read properly. I say this because a lot of people are saying "that's the same problem as me" and then just explain a completely different problem!

Things are like this:

I updated (there were some kernel ups within), then when I tried to boot from latest kernel everything was fine, but when the desktop appeared it gave me this message:

>  The panel encountered a problem while loading "OAFIID:TomboyApplet"
Do you want to delete the applet from your configuration?
 
It really doesn't matter if I select to delete it or not, because it will ask em everytime I log in. Now, obviously my Tomboy Notes applet has gone lost, and I can't remove it mannually.

Also, firefox doesn't run. Same thing for Opera.
Finally, if I press the turn off button the panels dissapear but everything else (desktop, open apps, etc) stays there ready to be used; and the "shutting down options" never appear, therefore I can't switch the computer off. All of these happens with the newest kernel, so I tried to boot from older kernels... and they all do the same!!!!. So I can't just boot another kernel, since the same problems will occur.

To sum up:

-an applet conflict
-web browser conflicts
-shutting down severe conflicts
-from every single kernel that I can boot
I'm not genius in this, not even close, but I think that maybe it has something to do with the pannels since most mistakes focus there. 

I hope that someone can help me. Please help me!!!!!!!:(:(:(

---

### Post by dugh on 2009-03-04
Same here dude.  I have proposed-updates enabled.

I updated today and now my computer won't boot.
Completely black screen.  Dell Latitude D820.

Could use some help with how I can go about tracking down the problem.  Using Windows right now, I'll try booting to an older kernel.

---

### Post by barbolanero on 2009-03-04
> **dugh said:**
> Same here dude.  I have proposed-updates enabled.

I updated today and now my computer won't boot.
Completely black screen.  Dell Latitude D820.

Could use some help with how I can go about tracking down the problem.  Using Windows right now, I'll try booting to an older kernel.

But that's not my problem at all!!!!! I can boot, read carefully please, otherwise you might confuse those trying to help me.

---

### Post by barbolanero on 2009-03-05
Can anyone help me?!!!! Please!!!! What can I do? I'm risking losing some sensitive information and having to do a clean install. To make matters worst, my computer can't run Intrepid, so I'm afraid that when I install hardy this will happen again. Please help me!!!

---

### Post by usawrestler_9 on 2009-03-05
well im sort of having the same problem except no matter what kernel i start in unless its in recovery mode all the kernels make a "black screen" so im not sure what to blame or what to do.
help!

---

### Post by barbolanero on 2009-03-10
Well, for me it all ended in doing a clean install. I wouldn't know what to say to you, but maybe you could do a x-server fix from recovery mode.

---

### Post by bubwitmaingay on 2009-03-10
Same here folks. My Firefox seems to hide every button after an update. I can't refresh, can't go back or forward, it doesn't remember anything and worst of all it lost the home page of ubuntu. What is this all about? Can they fix this up for us?

What I did is to remove firefox completely for now and use epiphany for the moment until somebody fixes this up.:(

---

### Post by amadeus266 on 2009-03-10
I would suggest that you back up everything you can and reinstall an LTS version (Hardy). If you insist on using the latest releases you will always risk having some problems. IMHO 6 months is not enough time to kill every bug in a system before release no matter how many people you have working on it. My laptop is being used in a production network and therefor I only use LTS releases to avoid the most dangerous bugs and problems. My desktop at home is not a production system and so there is no information on it that I can't afford to lose. I don't mind trying out the latest releases on it.

---

### Post by barbolanero on 2009-03-13
My orginal problem was on Hardy, the LTS, on my desktop. On my laptop I use Intrepid and it works just fine. I guess it's only luck.

---

