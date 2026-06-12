---
title: "Two Grub Menus ?"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by l0stb0y760 on 2009-04-03
Ola,

the issue I have is not critical but yet quite annoying and am wondering if there is a fix for this. However this will take some explaining. So here goes..

My set up includes two hard drives, one C drive and one D drive. My Windows XP install resides on my C drive by itself. I have some previous experience with Ubuntu and recently wanted to install it again. However I didnt want to touch my C drive, I wanted it dedicated to Windows XP. So I figured ill just put it on the D drive no problem, plenty of space. As I proceeded to install Ubuntu 8.10 I noticed it had an option to ''install inside of windows''. 

Which in turn, would also give you the options to simply uninstall Ubuntu if needed there for no partitioning needed. Sounds good to me so far. So I went with the option of installing Ubuntu inside of Windows and I chose to install it on the D drive again leaving my C drive untouched. 

I rebooted and immediately got to the Grub menu and booted to Ubuntu no problem. However this grub menu looked different from the Grub menu which lists the ubuntu kernel, (generic), and memtest. The grub menu I was getting simply had Ubuntu and Windows XP listed, no problem. I figured it was this way because I had not done any partitioning, great. Anyway, I ended up deciding to simply partition my C drive an put Ubuntu on there. You still with me? Okay here's where the problem comes in. Before I actually installed Ubuntu on my C drive by partitioning I said well let me uninstall it first from the D drive. I did so rebooted and for some reason i still got the same Grub menu that said, windows xp and Ubuntu. 

I selected Ubuntu and of course it failed to boot. So basically the Grub menu was still remaining after the initial install on the D drive inwhich I ''installed ubuntu inside windows''. I wiped the D drive clean but this made no difference. I searched for any remaining ubuntu files on the C drive but found nothing and nothing in the registry as well. I cant figure out why this Grub menu with ubuntu was still remaining. So in hopes that if I partitioned my C drive and installed Ubuntu on there it would fix the Grub. This went smoothly however, now when I boot up i get the normal grub menu which lists ubuntu, generic, memtest and other operating systems lists XP which is fine. BUT now when i select XP it forwards me to that other Grub menu and I have to select windows XP again. The 2nd Grub menu should have been gone when I removed ''install ubuntu inside windows'' off the D drive. I hope this is making sense to someone. To sum it up, my C drive is partitioned with XP and Ubuntu. 

When I boot up it takes me to the standard boot menu but then when I select XP it forwards me to another boot menu from a previous installation of Ubuntu. How can i clean this up so when i hit XP it sends me straight into XP and not into a 2nd Grub menu inwhich i have to select XP again. I also believe this is slowing down my boot time because ever since all this drama occurred my boot time into xp jumped from 45 seconds to about 120 seconds :[ In conclusion, how do i get rid of this 2nd boot menu which is not needed? 

~l0stb0y760/www.youtube.com/drakeerick

---

### Post by Soundmaster on 2009-04-03
Similar issues. May need to investigate fixmbr as in fix Master Boot Record.

---

### Post by l0stb0y760 on 2009-04-03
Thanks for the reply. Yea possibly, but I already attempted to fix the MBR via Windows recovery consel but this does not eliminate the 2nd grub menu which was left over from my first install of ubuntu...weird. Although, I been playing with it a bit and have found a satisfactory solution. When I boot into the first grub menu XP is at the bottom of the list so I have to navigate to it by hitting the down arrow about three times then I hit enter. This then brings me to the 2nd Grub menu that lists Ubuntu and XP again. XP is on top so I just hit enter again and it boots me into xp. 

So what i did was edit the main boot loader menu list (1st Grub Menu) so that XP is on top instead of Ubuntu:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		6f395aef-25ce-47bb-9844-44d60e864875
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6f395aef-25ce-47bb-9844-44d60e864875 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		6f395aef-25ce-47bb-9844-44d60e864875
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6f395aef-25ce-47bb-9844-44d60e864875 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
uuid		6f395aef-25ce-47bb-9844-44d60e864875
kernel		/boot/memtest86+.bin
quiet

So now when I boot up, all I have to do is hit enter twice and bam im booting in to XP :] as opposed to hitting the down arrow 3 times then hitting enter twice to boot into xp. Not the best fix but deffinitely a satisfactory solution (in my opinion) haha. But if anyone else has any input on how to get rid of the 2nd Grub menu altogether let me know, thanks. 

~l0st

---

### Post by dandnsmith on 2009-04-03
I'm a little confused by all the words.
What I seem to see is that you have a grub menu with an option to boot XP at the start - when you take this you get a second menu with XP and Ubuntu on it.
If I followed your actions correctly, then that second menu is from the XP boot process (as a result of using wubi), and you can change it how you like.
I think, from what I have read, that you need to edit the XP boot.ini, which you can do from XP by Start|run and use msconfig - the boot.ini tab allows editing (simplest way to get XP without further action is to set the timeout to zero).

---

### Post by l0stb0y760 on 2009-04-03
Yea I think you got it. First boot menu is the standard Ubuntu one we all see when you have your hard disk partitioned with XP and Ubuntu. Looks sorta like this:

Ubuntu-generic
ubuntu-recovery mode
ubuntu-memtest
Other Operating Systems:
Windows XP

something like that..(sorry dont have a screen shot)

But from that menu Ill hit XP and it'll then take me to another boot menu that looks sorta like this:

Windows XP
Ubuntu

At this Grub, I have to hit XP again and then Ill boot into XP. However if I hit Ubuntu at this Grub screen it will fail to boot. 

Anyway, I went into MSCONFIG and clicked on the boot.ini tab but am unable to edit anything...? The 2nd GRUB is what im trying to eliminate because it pointless to get forwarded there. I should just boot into either OS from the 1st Grub menu. Get what im saying? 

In other good news, I cannot boot into ubuntu at all anymore as it errors out with ''Ubuntu is in low graphics mode''. The only change I think of that was made was when I was adjusting my system text sizes to try and fix another problem. For some reason the text at my log in screen is itty bitty, like when i type my user name and pass i can hardly see what im typing. 

Obviously that is another issue and I am currently resarching the blogs for a solution before opening up a new thread. But man, it seems my Ubuntu luck is running out :\ Im seriously about to just re-install XP and Ubuntu. There goes my friday night -sigh....

---

### Post by l0stb0y760 on 2009-04-03
Additionally,

this 2nd grub has to be residing on my C drive somewhere with Windows because I already Zerod out my D drive and the 2nd Grub menu still remained. I figured out how to edit my bootini file by navigating to C:\BOOT.INI. However I am not at home now and will try this later on and place my update here, thanks.

---

### Post by l0stb0y760 on 2009-04-03
Well that sure enough was it. I found a Ubuntu entry listed in my bootini file. I removed this entry and now I am back to one Grub YAAAY! ;] Thanks Derek! Peace..

~l0stb0y760/www.youtube.com/drakeerick

---

### Post by l0stb0y760 on 2009-04-03
O and for those of you who dont know, to edit your bootini file--->

open the run menu (go to start and click run or hit your windows key and press R)

Then type in:

sysdm.cpl

Then click the ''Advanced'' tab. Then under ''Start Up And Recovery'' click ''settings'' then click ''edit''. It will open your boot.ini file in a notepad. Also be careful with this one. Highly recommended you make a back up copy of your original boot.ini file because if you mess it up you wont be booting into windows anytime soon ;/

k bye.

~l0stb0y760

---

### Post by dandnsmith on 2009-04-04
Glad you found the alternative - I was, when I saw your earlier post, about to suggest that alternative approach, but then saw you'd got it - or rather an equivalent (as you can right-button on My Computer, if you have it, select Properties,go to the Advanced tab, and get the system settings button)

I'm not sure why you are stopped doing it via msconfig - must be protected somehow (I've never actually done it that way, always by direct editing)

---

