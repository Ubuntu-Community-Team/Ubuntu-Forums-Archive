---
title: "fglrx causes irregular reboot/shutdown function in kubuntu feisty"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by inportb on 2007-04-24
I've a Toshiba Satellite L25-S119 laptop with Kubuntu Feisty installed. I had Edgy on the same machine before and did not have this problem. When I replaced the oss ati driver with the proprietary fglrx (the version that is available precompiled), my computer refused to reboot and shutdown -- I end up having to hold down the power button. Now, I've read other posts like this, but in this case, the computer does not just sit there idly. The harddrive appears to be on, the fan appears to be on, and so on.

Usually, the screen displays the Kubuntu logo with a progress bar going in reverse. What happens is that when the bar is empty, the computer switches into textmode with no text and the blinking cursor at the top-left corner. Then it switches back into graphics mode with the Kubuntu logo and empty progress bar. Then it switches back into textmode. And so on... ... ... until I force it off.

The problem persists until I go back to ati. This only happens when I do the procedure using the GUI. If I type **sudo shutdown now** or **sudo shutdown now -r**, it works, but, as expected, there are problems with things not exiting properly.

Does anyone have any tips for me? Now I know all the hardcore Ubuntu users will tell me to stop using fglrx because it's not opensource, but I would prefer to keep using it and fix the problem, if that's possible =D

Thanks!


FIXED:
> My solution --

1. open **/etc/X11/xorg.conf** and add to *Section "Device"*:
	Option "UseInternalAGPGART" "no"

2. open **/etc/kde3/kdm/kdmrc** and uncomment/add this line:
	TerminateServer=true

If you're using Gnome, you might want to instead do

2. open **/etc/X11/gdm/gdm.conf** and uncomment/add this line:
	AlwaysRestartServer=true

This forces the system to restart the X server completely instead of just resetting it.

---

### Post by sudo_nym on 2007-04-24
> **inportb said:**
> [...]

Does anyone have any tips for me? Now I know all the hardcore Ubuntu users will tell me to stop using fglrx because it's not opensource, but I would prefer to keep using it and fix the problem, if that's possible =D

Thanks!

No, I won't tell you that.  Maybe I'm just not hardcore enough.  ;-)

But I wil say that if fglrx is giving you trouble, why not switch to OSS and see how it works out?  Or, if you can find or still have an older version of fglrx, why not try that?  I just noticed in [another post]("http://ubuntuforums.org/showthread.php?t=420423") that someone's having similar problems right after `upgrading' their ATI driver [in quotes, because how can you call it an upgrade when the new version's more hassle than the old?].

By the way, just so you know I'm suggesting this for practical, rather than idealogical reasons; I use Opera because it's smaller, and generally less of a resource-hog than Firefox [sorry, but 30 megabytes of web browser is *Too_Many_Megabytes*].  Seems to fit my limited disk space, CPU and RAM a little better.  Not something I'm especially proud of though, and I will use Lynx or Dillo whenever possible [eg, if a site doesn't absolutely *require* JavaScript to be usable].  Some other closed-source stuff too, but that's the first thing that comes to mind because I'm using it right now.


Good luck,

Patrick.

---

### Post by inportb on 2007-04-24
Thanks for your advice. I think I should be able to get my hands on an older version from ATI, and compile it for the current kernel.

I'm also thinking about switching video drivers just before bringing the system down. Is there a script that is executed when one actuates the shutdown/reboot graphical button? I tried to **rmmod fglrx**, but could not do so because fglrx was still in use (X was still up). I notice that X gets killed, but some graphical process is started right after that displays the progress screen, presumably using the selected graphics driver. Is it practically feasible to insert a sequence in-between that swaps fglrx for ati?

This person also seemed to have some issue with fglrx (on Dapper), but mentioned switching drivers, which is where I got my idea from. [https://answers.launchpad.net/ubuntu/+source/firefox/+question/2326](https://answers.launchpad.net/ubuntu/+source/firefox/+question/2326)

Thanks so much for responding to my post.

---

### Post by inportb on 2007-04-24
If it makes a difference to note this... hibernate (suspend to disk) works. standby (suspend to ram) leaves laptop in a non-resumable-dead-screen state, but that's an issue for another thread. the idea is that the computer shuts down properly by itself when hibernating.

---

### Post by stearic on 2007-04-25
I've noticed this myself. Same problem. I also had the problem of the screen going black when i logged out. I switched back to the OSS ati driver and everything seems to be fine. I think i'm just going to stick with this tell something is figured out about this.

---

### Post by inportb on 2007-04-26
There seems to be others with similar problems, but with older versions of the OS...
[http://www.linuxquestions.org/questions/showthread.php?p=2724803](http://www.linuxquestions.org/questions/showthread.php?p=2724803)

I tried compiling the latest fglrx into a kernel module... same problem. I haven't tried disabling DRI yet, but I have a feeling that it's going to allow proper shutdown/reboot... which is totally pointless and defeats the purpose of using fglrx in the first place.

---

### Post by sudo_nym on 2007-04-28
> **inportb said:**
> Thanks for your advice. I think I should be able to get my hands on an older version from ATI, and compile it for the current kernel.

I'm also thinking about switching video drivers just before bringing the system down. Is there a script that is executed when one actuates the shutdown/reboot graphical button? I tried to **rmmod fglrx**, but could not do so because fglrx was still in use (X was still up). I notice that X gets killed, but some graphical process is started right after that displays the progress screen, presumably using the selected graphics driver. Is it practically feasible to insert a sequence in-between that swaps fglrx for ati?

That would be usplash [the thing that shows a progress-bar and logo, during boot-up and shut-down].  I've dropped the `quiet splash' part from my */boot/grub/menu.lst* because it's not very informative, so I can't say much about that [1].  Must be quite primitive though, since it loads before the kernel.  Probably has nothing to do with the video driver, but if not, how does it draw that logo on the screen?  Damned if I know.

For the reasons you mention, it's probably not a good idea, and maybe not even possible to swap video drivers while X is running.  But maybe right after Xorg shuts down...  Sorry, I don't know how to do this.

Just one question; am I wrong, or do the basic video drivers work with these fancy monitors?  My understanding was that they work, but you don't get any hardware accelleration features.  So basically, what you get is a very expensive video setup that works, but only works as well as some cheap, generic blinken-box from Radio Shack [not that there's anything wrong with Radio Shack].


[LIST=1][*]Yes, I see reams of text spewing across the screen at boot-up.  Usually goes by too fast to read, but sometimes I catch stuff like a USB driver not loading, or loading at the wrong time or something.[/LIST]

> This person also seemed to have some issue with fglrx (on Dapper), but mentioned switching drivers, which is where I got my idea from. [https://answers.launchpad.net/ubuntu/+source/firefox/+question/2326](https://answers.launchpad.net/ubuntu/+source/firefox/+question/2326)

Thanks so much for responding to my post.

Can't say I've been much help though.  I honestly don't know what I'm talking about, just asking questions, and learning from you.  :-)  I do hope some of those questions send you off to look up the right answers, though.

By the way, have you kept track of that other thread I'd linked to?  Umm, this one;
[http://ubuntuforums.org/showthread.php?t=420423](http://ubuntuforums.org/showthread.php?t=420423)
KmooreUSN's made a lot of progress since his/her original post, so you might want to have another look over there.  Might help.



Still wishing you luck,

Patrick.

---

### Post by sudo_nym on 2007-04-28
> **inportb said:**
> There seems to be others with similar problems, but with older versions of the OS...
[http://www.linuxquestions.org/questions/showthread.php?p=2724803](http://www.linuxquestions.org/questions/showthread.php?p=2724803)

I tried compiling the latest fglrx into a kernel module... same problem. I haven't tried disabling DRI yet, but I have a feeling that it's going to allow proper shutdown/reboot... which is totally pointless and defeats the purpose of using fglrx in the first place.

Maybe the relevant thing here is that you're not logging out?  When you drop the machine into sleep or hibernation, your X sessions doesn't end, it's just kind of put on hold.



Patrick.

---

### Post by inportb on 2007-04-28
Yes, I think you're right. I don't think it logs out when I issue the halt command. I actually came here to post exactly the same thoughts.

I've tried KmooreUSN's solution. I've reinstalled the OS twice, thinking that I might have to install the driver from scratch. I'm going to disable usplash and see if I get any informative messages. Thanks for your suggestions!

---

### Post by sudo_nym on 2007-04-29
> **inportb said:**
> Yes, I think you're right. I don't think it logs out when I issue the halt command. I actually came here to post exactly the same thoughts.

I've tried KmooreUSN's solution. I've reinstalled the OS twice, thinking that I might have to install the driver from scratch. I'm going to disable usplash and see if I get any informative messages. Thanks for your suggestions!

With apologies, I've just found that typing *dmesg* at the terminal will give you the same information -- and more importantly, give you plenty of time to read it.  Yes I'm a n00b.  It's also updated regularly while the system's up and runing; handy, because you can do things like insert a PCMCIA card, USB stick or whatever, then check the last few lines from dmesg to see if it was recognized properly, and if not, why not.

But I still kind of prefer booting without the `quiet splash' options.  Doesn't really make it load any faster, but it sure *looks* faster that way.  ;-)

I'd also replied to the wrong post, there.  Meant to quote your note on hibernation / sleep, but you probably knew that.

Sorry I can't tell you much else right now -- well, nothing useful anyway -- but maybe dmesg can.  Hope it helps.



Cheers,

Patrick.

---

### Post by inportb on 2007-05-01
Thanks so much for your help anyway =D  I'm going to just type 'halt' for now until i could find a nice way around it.

---

### Post by inportb on 2007-05-03
Wow. I am excited, to say the least. Why? Because I have finally fixed the hang-on-logout-shutdown-reboot bug!!!

My solution --

1. open **/etc/X11/xorg.conf** and add to *Section "Device"*:
	Option "UseInternalAGPGART" "no"

2. open **/etc/kde3/kdm/kdmrc** and uncomment/add this line:
	TerminateServer=true

If you're using Gnome, you might want to instead do

2. open **/etc/X11/gdm/gdm.conf** and uncomment/add this line:
	AlwaysRestartServer=true

This forces the system to restart the X server completely instead of just resetting it.
Thanks for all the help!!

---

### Post by sudo_nym on 2007-05-04
> **inportb said:**
> Wow. I am excited, to say the least. Why? Because I have finally fixed the hang-on-logout-shutdown-reboot bug!!!

My solution --

1. open **/etc/X11/xorg.conf** and add to *Section "Device"*:
	Option "UseInternalAGPGART" "no"

2. open **/etc/kde3/kdm/kdmrc** and uncomment/add this line:
	TerminateServer=true

If you're using Gnome, you might want to instead do

2. open **/etc/X11/gdm/gdm.conf** and uncomment/add this line:
	AlwaysRestartServer=true

This forces the system to restart the X server completely instead of just resetting it.
*Very* cool.  :-)

So the reset instead of restart left some [but not all] components running, and that's what was screwing up fglrx?  Glad you figured it out, anyway.

I wondered where the conf-file would be for Xubuntu, but it seems to use /etc/X11/gdm/gdm.conf as well.  [Makes sense, because it does utilize some, if not the full set of GNOME libs.]
> Thanks for all the help!!
Umm, what I do?



Cheers,

Patrick.

---

### Post by inportb on 2007-05-05
What did you do? You showed me that I wasn't going insane and that this problem is not unique to my setup lol. Having this inconvenience out of the way, I proceeded to install XGL+Beryl, which, I must say, is very impressive, and just a bit buggy. Anyway, I hope this helps other ppl with ATI X200M and fglrx.

---

### Post by wieman01 on 2007-07-26
Great stuff! Fixed my problem too. Kubuntu Feisty Fawn. Now I can happily shut down the PC via GUI.

---

### Post by checho4 on 2007-09-12
I just installed the fglrx drivers yesterday and am quite happy that I can now play my OpenGL games!  I too have this shutdown problem and hope that this fix can work for me.

However, I have a question:  in the kdmrc file, what does "uncomment/add" mean?  Do I just add "TerminateServer=True" to the bottom of the file?

Any help is greatly appreciated!

---

### Post by inportb on 2007-11-10
Sorry, if you're still looking for an answer... yes, add it to the bottom. If that line already exists and the value is false or something, you can also just make it true.

---

### Post by TMcKSmith on 2008-03-27
> **inportb said:**
> Wow. I am excited, to say the least. Why? Because I have finally fixed the hang-on-logout-shutdown-reboot bug!!!

My solution --

1. open **/etc/X11/xorg.conf** and add to *Section "Device"*:
	Option "UseInternalAGPGART" "no"

2. open **/etc/kde3/kdm/kdmrc** and uncomment/add this line:
	TerminateServer=true

If you're using Gnome, you might want to instead do

2. open **/etc/X11/gdm/gdm.conf** and uncomment/add this line:
	AlwaysRestartServer=true

This forces the system to restart the X server completely instead of just resetting it.
Thanks for all the help!!

This fix worked perfectly on Kubuntu Gutsy Gibbon!  Thanks so much.  Such a relief to finally solve this after a few days of frustration.

---

