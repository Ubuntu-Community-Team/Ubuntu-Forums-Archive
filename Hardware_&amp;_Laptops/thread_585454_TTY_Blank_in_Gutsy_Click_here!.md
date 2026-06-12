---
title: "TTY Blank in Gutsy? Click here!"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by El Chupacabras on 2007-10-21
There's a slight problem with the init scripts in Gutsy/Hardy involving its new kernel. It appears that the framebuffer has been incorporated into the kernel, instead of being added as a separate kernel module.

So what, you ask? If you press ctrl+alt+F1 through ctrl+alt+F6, you're supposed to see a terminal, much like a fullscreen version of gnome-terminal. However, (and I'm not sure how prevalent this issue is) in Gutsy/Hardy, you may see one of the following:[LIST]
[*]If your monitor REALLY old, it might fry. (you may want to press ctrl+alt+F7 or ctrl+alt+F9 before this happens)
[*]If your monitor is semi-old, it might just display nothing
[*]if your monitor is modern, you will see "Out of Range" upon it
[LIST]
[*]or a black screen with a cursor blinking
[*]... or a black screen with nothing on it.
[/LIST][/LIST]These are all caused by the same bug, which is marked CRITICAL in launchpad, so hopefully an update will fix it soon. (see it [here]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910")). 

This guide may or may not cause your resolution to go a bit wonky until you get the settings right, but it shouldn't completely break X. If you see that you get an error message, please press ok. The X server did that to me a few times, but it reverted to VESA (crappy graphics mode), and allowed me to log in once more. I can't guarantee this won't break your installation, but I don't think it should. **As a final word of warning: please don't do this if you're afraid to muck around in your system. If that's you, please wait for the Ubuntu devs to fix this.**

However, I *think* I may have found a solution whilst looking through launchpad, and mixing and matching others' methods of solving this issue.

**NOTE:** Wherever it says `$ sudo vi «text file»`, you can either type it as you see it and use vi, or if you don't know how to use it, just use `sudo gedit` (Ubuntu) or `sudo kate`(Kubuntu), instead of `sudo vi`.

There are four parts to this solution:

**STEP 1** - Edit /etc/modprobe.d/blacklist-framebuffer.

$ sudo vi /etc/modprobe.d/blacklist-framebuffer
It should look like:
```
 # Framebuffer drivers are generally buggy and poorly-supported, and cause
# suspend failures, kernel panics and general mayhem.  For this reason we
# never load them automatically.
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist cyblafb
blacklist gx1fb
blacklist hgafb
blacklist i810fb...
```Find the fb module **corresponding to your video card's driver**. You may have to experiment, but its generally straightforward. If you use a radeon driver, try radoenfb. Try vesafb first if you have another card. It's a generic video driver, and may be what you're supposed to use. Comment out the line that blacklists the module you have chosen. (This means you should add a # before the line).

**[COLOR="Red"]WARNING:[/COLOR] If you use the proprietary nvidia driver, save yourself some time and comment out *vesafb*. *nvidiafb* is the kernel module for the open-source _nv_ driver's framebuffer, with which the proprietary driver is not compatible.** Maybe it should be called nvfb to be more consistent?

You may or may not have to comment out vga16fb. If you try with vesafb and it still fails, try again with your card's specific fb module, and if it's still failing, add vga16fb as well. Be warned though- vga16 might make windows in compiz appear white after you use a tty.

**STEP 2** - Edit /etc/initramfs-tools/modules
$ sudo vi /etc/initramfs-tools/modules
It shoud look like:
```
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod

``` Add the following after the last line.
```
fbcon
vesafb
```Again, vesafb is what *I* used. Remember the driver you uncommented for step 1? Use that one. Also, if you un-blacklisted vga16fb above, type it in right after vesafb. It probably isn't necessary though (At least, it wasn't for me...)

**STEP 3** - Update the init scripts. This step is fortunately, simple.
$ sudo update-initramfs -u -k all

**STEP 4**- Edit /etc/grub/menu.lst
by now you should know: 
$ sudo vi /etc/grub/menu.lst

Scroll down until it says: ## ## END DEFAULT OPTIONS ##
go to the first line that starts with Kernel,
```
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=763f09b5-cf76-42a1-8dd2-123a2739b3ab ro quiet splash
```and select a resolution from below:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=47213&stc=1&d=1193009037[/IMG]
(Image Coutesy of [Zenwalk Wiki]("http://wiki.zenwalk.org/index.php?title=Index:FAQ#Documentation"))

Remember the **decimal** value for it, (the one that has no 0x at the start) and change the line that says kernel to something like:
```
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=763f09b5-cf76-42a1-8dd2-123a2739b3ab ro quiet splash vga=###
``` (Replace the ### with the aforementioned number)

The vga=XXX parameter allows you to select the resolution at which you will see your tty. Apparently the default setting may be too low for some monitors. 

**Conclusion**-
I have an Nvidia GeForce 7600 GS, and this worked for me, after a bit of testing. I can now use TTY 1-6. I'm not sure if there are any negative side effects to this, but at least the terminals work again. Post your feedback below. I won't be able to get back to you until Tuesday, but if I get a chance to pop in on my free time, I'll try and answer any questions/remarks.

For simplicity's sake maybe the framebuffer should be compiled as a module in the future? :-#

---

### Post by patrickthebold on 2007-10-23
My terminals are not blank, but sort of a black and white scrambled mess.  Also mine worked fine before I installed nvidia-glx.  Do you think this is the same bug or something different.  I tried a similar solution to your post, and it did not work.  Basically I did everything except pass the vga=###  parameter.  I will try again with the parameter when I get home.

---

### Post by patrickthebold on 2007-10-24
So I followed the instructions and I my terminals are still scrambled but a different color, I did not try all of the vga codes yet, so I guess I can play with it some more.  I also didn't try vgafb.  Its kinda of annoying when there are several dozen options and a reboot is required. :(

---

### Post by Farax on 2007-11-12
Hi, i followed every step and all my terminals were still black with blinking underscore, plus my X became black + underscore.

OK, i've fixed all the changes in the files, so i'm at the starting point and i've noticed that my ctrl + alt + F1 works normally(i see the X starting procedure without any problems) but all F2-F6 are dead (black screen + underscore). Do I understand correctly that it's not a graphics bug since one of terminals is alive?

---

### Post by piccobello on 2007-11-15
Thanks a lot! I had the same problem, now I can see the ttys again!
On a thinkpad X31 I had to use radeonfb.
One thing that I still don't understand is that I don't see anything on the screen
between grub menu and x. I mean where are all the messages gone?
Is it a new "feature" of gutsy, or am I still missing something?

---

### Post by cyberslayer on 2007-11-16
I tried this method for the vesafb and radeonfb driver and although the tty's are visible now and can be used, switching to and from Xorg with ctrl-alt-F7/F1 occasionally fails and the screen goes black and the system locks up.  At this point, I cannot switch back to the tty or Xorg.  This happens with both the vesafb and radeonfb drivers (I have not tested the others).  Anyone else have this problem?

Thanks for posting this guide.

---

### Post by th3t1nm4n on 2007-11-29
I think step 4 should be:
sudo vi /boot/grub/menu.lst 
or
gksudo gedit /boot/grub/menu.lst

---

### Post by exjinn on 2007-12-13
Just wanted extend my thanks for helping me fix this issue. Works just fine with the radeonfb and vesafb!

---

### Post by amikrop on 2008-01-12
Greetings. I have a GeForce FX Go5650 and I use the nvidia-glx-new driver. I followed your guide, and my problem is solved. TTYs are OK and look nice (with the graceful framebuffer support). I chose vga=773. Thanks a lot for publishing this, it was very helpful :-)

PS: I hope the respective launchpad bug will be fixed soon.

---

### Post by H_Plow on 2008-02-03
THIS IS A DUPLICATE OF thread #105 in "ATI 8.1 Drivers -- Post Your results " (#671726), trying to post here to find a solution...

Ubuntu GUTSY AMD64 Desktop
Kernel 2.6.22-14-generic (also tried on a 2.6.20.3-custom..)

Using fglrx 8.1 here on my HD2600XT 256MB PCI-E

My situation:

- fglrx installed and working "properly" (Note: I have disabled ATIEVENTSD on startup to fix the famous "CTRL+ALT+BACKSPACE" problem);
- compiz is working "like a charm"

but..........

TTY console are unaccessible.. 

Before or after GDM LOGIN, if I try to access any TTY (CTRL+ALT+F1-F6) the screen goes black (whatever the monitor sync LED remains always ON...not blinking) and I can't neither go back to X (CTRL+ALT+F7-F9) nor switch to another console (CTRL+ALT+F1-F6)...can only hard reboot or ALT+R SIST+S+U+B to reboot.....

I've tried to:

1) unblacklist "vesafb" driver:
$ sudo gedit /etc/modprobe.d/blacklist-framebuffer (and put a # before the vesafb line..);

2) $ sudo gedit /etc/initramfs-tools/modules
and add lines "fbcon" and "vesafb" lines

3) update the init scripts:
$ sudo update-initramfs -u -k all

4) add a vga=XXX as a kernel parameter in /boo/grub/menu.lst

Results are:
- I can see usplash (but this wasn't a problem yet before...)
- I can see "text lines" (system messages) during bootup...after the usplash
- I CANNOT STILL ACCESS THOSE FU**IN TTY CONSOLES...like before!!! 

This is rather frustrating.... 
Any suggestion from the experts?
Thanks.

---

### Post by H_Plow on 2008-02-12
Find better solution to any fglrx/ATI problem !!!

SAY "BYE BYE ATI" !!!  :lolflag:

GOOD LUCK !!

---

### Post by tribble222 on 2008-02-14
Thanks a lot for the guide!

nvidia 7800GT

I upgraded from feisty to gutsy and the restricted driver wouldn't work right (max 800x600) so I used envy to install the driver.  Great, but no TTY!  Followed your guide exactly, using the vesafb and not touching vga16fb and all my tty's work again!

---

### Post by toasterboy1 on 2008-03-20
Had blank/black ttys in gutsy after installing NVIDIA driver with Envy. Thought it had something to do with running the Hardy kernel. Never had any luck with drivers from repositories. After some searching today found a post on the nvidia linux forum were someone else was having this same problem. They realized tty stopped working after driver 96.43.05. I installed that driver and restarted kdm. Viola. My ttys show up and I have all my nvidia abilites. He reported it as a bug but I have not found any fixes. Hope that helps some of you.

---

### Post by gasparov on 2008-03-21
Its not a bug of the new nvidia drivers, I have the latest drivers on gentoo and i have my tty, its just ubuntu that lately sucks big.....

---

### Post by fela on 2008-04-09
i had this problem, but instead of going thru all the steps here, all i did was delete the 'vga=xxx' parameter in my /boot/grub/menu.lst. That's right, DELETE. Now my ttys work :)

---

### Post by ax-ax on 2008-04-13
Yay
My TTYs work!

---

### Post by jimbren on 2008-04-19
Thanks!  I've been having a similar issue since doing a fresh install about a week ago.  In my case, the terminal resolution looked to be about 640x480, and the text was so large that it was taking up so much of the screen that doing even the most simple functions was out of the question.  

This resolved the problem perfectly.

---

### Post by El Chupacabras on 2008-04-30
> **Farax said:**
> Hi, i followed every step and all my terminals were still black with blinking underscore, plus my X became black + underscore.

OK, i've fixed all the changes in the files, so i'm at the starting point and i've noticed that my ctrl + alt + F1 works normally(i see the X starting procedure without any problems) but all F2-F6 are dead (black screen + underscore). Do I understand correctly that it's not a graphics bug since one of terminals is alive?
Can't say I know if it is...
Perhaps it has to do with memory, or some sort of cache...

Did you try this with and without vga16?
If that hasn't worked, try upgrading to Hardy...

EDIT: I seem to remember something like this happening to me when using Compiz + VSync after a suspend. Try this: [http://ubuntuforums.org/showthread.php?p=3918664#post3918664](http://ubuntuforums.org/showthread.php?p=3918664#post3918664)

---

### Post by El Chupacabras on 2008-04-30
Glad I could solve some of your problems. (And sorry I disappeared for about 6 months...)

> **th3t1nm4n said:**
> I think step 4 should be:
sudo vi /boot/grub/menu.lst 
or
gksudo gedit /boot/grub/menu.lst
Whoops! It's fixed now! Heheh...

> **cyberslayer said:**
> I tried this method for the vesafb and radeonfb driver and although the tty's are visible now and can be used, switching to and from Xorg with ctrl-alt-F7/F1 occasionally fails and the screen goes black and the system locks up.  At this point, I cannot switch back to the tty or Xorg.  This happens with both the vesafb and radeonfb drivers (I have not tested the others).  Anyone else have this problem?

Thanks for posting this guide.
It doesn't *sound* like a video card/driver issue, but it may still be, if for example the memory is being managed incorrectly... 

> **patrickthebold said:**
> My terminals are not blank, but sort of a black and white scrambled mess.  Also mine worked fine before I installed nvidia-glx.  Do you think this is the same bug or something different.  I tried a similar solution to your post, and it did not work.  Basically I did everything except pass the vga=###  parameter.  I will try again with the parameter when I get home.

For those of you still having issues such as scrambled terminal, I'm not sure if this guide is for you. That sounds like a different, but similar issue. It could be that they are unrelated.

This guide was meant to help those that were having the same issue, but it's not a catch-all solution, since the drivers WERE blacklisted to begin with. (Blacklisted drivers are not loaded due to bugs.) I believe that for the people for whom it worked, the drivers were blacklisted erroneously.

For those I couldn't help, I would suggest maybe upgrading to Hardy Heron. It *is* a Long-Term Support release, and therefore it should theoretically be more stable. It works for me, but I'm not sure if these changes I made in Gutsy have been carried over during the upgrade. It's still worth a try, in the least.

---

### Post by earache on 2008-05-03
> **El Chupacabras said:**
> 
For those I couldn't help, I would suggest maybe upgrading to Hardy Heron. 
I just tried the guide under Hardy and no result at all. The tty's are still blank.
EDIT: Ha, works perfectly with fglrx, though! Maan, awesomee!

---

### Post by El Chupacabras on 2008-05-03
EDIT: Glad you got it working! Yeah, you have to try all the possible modules that could be affecting it. If you have an ATI card, that would probably be fglrx, or radeonfb, depending on your card, and which driver you use.

---

### Post by El Chupacabras on 2008-05-03
> **patrickthebold said:**
> So I followed the instructions and I my terminals are still scrambled but a different color, I did not try all of the vga codes yet, so I guess I can play with it some more.  I also didn't try vgafb.  Its kinda of annoying when there are several dozen options and a reboot is required. :(
Well, yes it's annoying, but if you really need the tty's, rebooting a few times, shouldn't be too much of a sacrifice. Again, this is purely optional.

---

### Post by El Chupacabras on 2008-05-03
Try removing radeonfb from the blacklist, uncomment vesafb and vga16fb and remove them from /etc/initramfs-tools/modules. Then add radeonfb to the modules, and it should work.

---

### Post by El Chupacabras on 2008-05-03
I don't know... I'm not an ATI user. Flgrx is the open-source driver right? Then I suppose radeonfb wouldn't work. 

Have you tried without the vga line? Some of the other said that fixed it.

---

### Post by zzart on 2008-05-10
has anyone managed to find the right config for thinkpad t22 ?? 
i've alredy tried a dozen of different settings and get the blank screen everytime :( 

help!!

---

### Post by ufef on 2008-05-26
I had the same problem with Hardy/GeForceGo 6200, and installing 96.43.05 drivers (using EnvyNG) instead of later ones solves the problem.

---

