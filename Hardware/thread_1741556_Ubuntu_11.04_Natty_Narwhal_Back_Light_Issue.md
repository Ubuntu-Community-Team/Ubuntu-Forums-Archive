---
title: "Ubuntu 11.04 Natty Narwhal Back Light Issue"
date: 2011-04-28
forum: Hardware
---

### Post by Kalanac on 2011-04-28
Hello, I've been thrashing about the internet looking for a solution to this problem but haven't encountered very many places that even agree on what the problem is.

Firstly I'll state the problem as clearly as I can:

When booting into Ubuntu 11.04 Natty Narwhal there is no back light to the laptop display.  An image is produced and you can just make out the desktop and some of the brighter windows but there is no light behind the image to make it more visible.

This is NOT the contrast/brightness issue/bug and has nothing to do with the brightness settings or adjusting using the laptops function keys.

OK that's the problem, here's my setup:

I'm on an Acer Aspire 5736Z laptop.  It uses an Intel GMA 4500M integrated GPU.  I am booting from a liveUSB installation of Natty from todays (28th April) release i386-desktop image.  I previously installed the beta2 version to disk (I had formatted the HDD at the time an figured I'd give it a spin) and the same issue occured so I'm relatively sure it doesn't matter that I'm booting from USB.

Here's what I've tried:

There's not a great deal I can do once Natty has started to boot because it's too dark to see very much.  I have tried going to the ctrl-alt-f1 f2 f3 etc. consoles but they are also very dark.  I am able to get an image with the nosetmode boot option but this isn't a perfect fix.  The desktop defaults to gnome2 rather than unity and the resolution seems low and stretched (it's a wide screen laptop).  Going to the System> Preferences> Monitors tool doesn't allow any changes to the resolution or refresh rate (which for some reason claims to be 0).

I have checked the Additional Driver installer and it doesn't find any additional drivers.  My display works fine under 10.10 out of the box (perhaps a little bad for 3D but then it is Intel so that's expected).

If folks need more details I'm happy to get them if you tell me exactly what it is you're looking for.  Bear in mind I'll either need to use nomodeset or sit in a dark cupboard.

---

### Post by jsebean on 2011-04-28
I too am having this same issue. I had it with the beta release with 11.04 but i expected it would be fixed by final release. Well, it's not fixed :mad: I have an Emachine e725. I am booting from a burned ISO. I also had Intel graphics

---

### Post by Lennyuk on 2011-04-28
I too am having this exact same issue and was expecting it to be fixed in today's final release...but I guess not.

I was told that it was working in kernels up to and including 2.6.36 but since .38 it has not been working.

I really hope this gets sorted soon as 10.10 works perfectly and 11.04 does so long as I plug in a secondary display, but I want to be able to use 11.04 just on my laptop not having to have it plugged into a second display.

---

### Post by Kalanac on 2011-04-28
It would seem perhaps this is the issue:

[http://us.generation-nt.com/answer/2-6-38-rc2-acpi-backlight-control-missing-help-201853772.html](http://us.generation-nt.com/answer/2-6-38-rc2-acpi-backlight-control-missing-help-201853772.html)

---

### Post by Lennyuk on 2011-04-28
> **Kalanac said:**
> It would seem perhaps this is the issue:

[http://us.generation-nt.com/answer/2-6-38-rc2-acpi-backlight-control-missing-help-201853772.html](http://us.generation-nt.com/answer/2-6-38-rc2-acpi-backlight-control-missing-help-201853772.html)

maybe, there is a patch linked in the comments, maybe you could try (I am at work so can't)

---

### Post by saggitheman on 2011-04-28
having same problem to. but how do i get to fix this when i can't see anything at all? :O and i didn't understand what to do

---

### Post by mudfly9 on 2011-04-28
I'm having exactly the same problem on my Acer 5732Z.

It's staggering to think that, technically speaking, I'd be better off with Windows ME. Ouch!

---

### Post by docmark777 on 2011-04-28
I am a neophyte and will need really good instructions to do this, but I just plugged my acer aspire 5732z into my digital projector and it showed on that screen fine. 
You all probably knew this, but I assume any external monitor would work as well. 

So, if any of you find a fix, we can at least find a way to see the program well enough to implement the fix. 

I will wait for you programers to tell us what to do. 

thanks,

---

### Post by gingivere0 on 2011-04-28
I have this exact same issue on an emachines. I had it during beta and expected the issue to be resolved today but it wasn't. Right now I'm using a script that I found somewhere on the net. You just have to log in, open a terminal (Ctrl+alt+t), and execute the script or type the command. You need root permissions.
```
sudo setpci -s 00:02.0 F4.B=0
```
I don't know why it works, just that it works. Maybe someone that is better with coding can decipher and find a permanent solution. Good Luck!

---

### Post by akash87 on 2011-04-29
What do you do when that command doesnt work either?

---

### Post by akash87 on 2011-04-29
> **gingivere0 said:**
> I have this exact same issue on an emachines. I had it during beta and expected the issue to be resolved today but it wasn't. Right now I'm using a script that I found somewhere on the net. You just have to log in, open a terminal (Ctrl+alt+t), and execute the script or type the command. You need root permissions.
```
sudo setpci -s 00:02.0 F4.B=0
```
I don't know why it works, just that it works. Maybe someone that is better with coding can decipher and find a permanent solution. Good Luck!

I tried that! as well as sudo setpci -s 00:03.0 F4.B=00
Neither work

---

### Post by derrickhensley on 2011-04-29
I really wish this problem would get fixed soon. I updated this the week before my finals and I need my laptop. Has anyone found a more permanentway? that first code worked for me, but eventually it will get really tedious

Thanks

---

### Post by Tempest42 on 2011-04-29
> **derrickhensley said:**
> I really wish this problem would get fixed soon. I updated this the week before my finals and I need my laptop. Has anyone found a more permanentway? that first code worked for me, but eventually it will get really tedious

Thanks

If you add...```
setpci -s 00:02.0 F4.B=0
```...to /etc/rc.local, it will run  at startup, which has fixed this problem for me.  Massive thanks to gingivere0 for finding this solution.

---

### Post by derrickhensley on 2011-04-29
> **Tempest42 said:**
> If you add...```
setpci -s 00:02.0 F4.B=0
```...to /etc/rc.local, it will run  at startup, which has fixed this problem for me.  Massive thanks to gingivere0 for finding this solution.

I am a pretty New user could you walk me through how to do that or something

---

### Post by Tempest42 on 2011-04-29
> **derrickhensley said:**
> I am a pretty New user could you walk me through how to do that or something

Sure. First, just type the following into a terminal window:
```
gksudo gedit /etc/rc.local
```If you've just installed Ubuntu, this file will probably only have some comments at the top (each line starting with a #), and "exit 0" at the bottom.  All you need to do is add the following *before *the "exit 0" line.

```
setpci -s 00:02.0 F4.B=0
```

The rc.local script will execute when Ubuntu starts up, and will ensure that the backlight is on when you reach the login screen.  Note that you *don't* need to put "sudo" in this file, as it is run as the root user anyway.

---

### Post by saggitheman on 2011-04-29
> **Tempest42 said:**
> Sure. First, just type the following into a terminal window:
```
gksudo gedit /etc/rc.local
```If you've just installed Ubuntu, this file will probably only have some comments at the top (each line starting with a #), and "exit 0" at the bottom.  All you need to do is add the following *before *the "exit 0" line.

```
setpci -s 00:02.0 F4.B=0
```

The rc.local script will execute when Ubuntu starts up, and will ensure that the backlight is on when you reach the login screen.  Note that you *don't* need to put "sudo" in this file, as it is run as the root user anyway.

this only workes for startup... not hibernate or suspend

---

### Post by catastrophreak on 2011-04-29
EDIT: The setpci command I used below apparently worked exactly once. When I powered off and restarted later got blank screen. Tried both B=0 and B=FF without success. I did manage to get the backlight on now by adding nomodeset to boot line, but have limited resolution (1280x800 is max allowed when native I have 1920x1080).


Thank you for all those with suggestions in this thread... it got me on the right track. The following worked for me (instead of B=0).

```
setpci -s 00:02.0 F4.B=FF
```

A note that was previously not mentioned for those confused with how to get to this on a laptop... You can boot to a live 10.04 or 10.10 CD and mount your internal drive by clicking on it in "Places". The tweak to the previously mention line then used open rc.local for editing would be:

```
gksudo gedit /media/abc123/etc/rc.local
```

where 'abc123' will be different and is the mount point of your drive. Use tab when typing in terminal after media directory to auto-complete your mount point.

---

### Post by derrickhensley on 2011-04-30
I am still having issues. It is not a permanent fix, has anyone reported this bug to the coders. Because I am getting tired of having to do the code each time I want to use my laptop. I can't afford to have a crippled computer when my finals are coming up

---

### Post by Chris2243 on 2011-04-30
This worked for me on an Acer laptop, it's not perfect but ok for now.

[http://ubuntuforums.org/showthread.php?t=1742352]("http://ubuntuforums.org/showthread.php?t=1742352")

When you get to the log in screen (which you can't see), press the function button and increase brightness button to get light.
Works ok after suspend and hibernate as well.

---

### Post by Secrest on 2011-04-30
When grub comes up you can choose previous versions and choose a kernel other than the newest and the back light will work.  The newest kernel is the problem.  Once you get in go to synaptic package manager and you can just remove the newest kernel and you can get in like normal without having to chose the previous versions in grub yourself.  Let me know how it works.

---

### Post by searchfgold6789 on 2011-04-30
+1
Try booting into an earlier kernel, or install an earlier kernel from the internet. The version is 2.6.36 and you can select the correct kernel at boot.

+1
I would definitely like to go into a dark cupboard and use a laptop with a very dim display.

---

### Post by jsebean on 2011-04-30
So then should this be reported to the coders, and how?

---

### Post by Kalanac on 2011-04-30
Adding 

setpci -s 00:02.0 F4.B=0

to the rc.local file has worked for me (total hat doffage and much kudos to the guys who suggested it).  See my first post for a run down of my computer setup (Acer Aspire 5736Z).

Here's a quick run down about what I've learned of the error:

- The nomodeset kernel parameter brings the back light on but at the cost of much of the graphics.  The resolution is distorted (I have a widescreen laptop) and cannot be changed in the monitor preferences.  This also prevents Ubuntu from logging into a Unity session and forces a drop back into the Ubuntu "Classic" Gnome2 session.

- Changing the graphics driver made no difference (tried vesa and the xorg-edgers driver)

- Passing the acpi_backlight=vendor (also tried legacy instead of vendor) and acpi_osi=Linux parameters to the kernel via GRUB (individually, separately and in different orders) made no difference for me though I've read of other people it's worked for. 

- The error is present in other distros (at the very least it's in Arch Linux which I tried out) and manifests in the same manner. Again I used nomodeset which worked (didn't know of the above fix at the time so I don't know if it will work under Arch Linux but I assume it will)

- The error is present in both installed and Live environments though the minimum and alternative installers seem to run fine for the install but still result in a duffed back light.

- From what I can gather it is the 2.6.38 kernel that is responsible due to a change in the code which handles graphics.  Bug logs (such as the one I linked earlier) seem to imply the Kernel developers are aware of the issue but I think I read that the issue is closed having been resolved so the issue may get fixed in future updates, if not it may be worth telling them.  Regressing to the 2.6.32 Arch Linux LTS kernel worked fine without any other changes.

EDIT:

A further observation:  The work around fails to apply when the computer enters standby and is woken again.  Any ideas on how to get it to call the setpci when it wakes?

---

### Post by glococo on 2011-05-02
Hi,

The best workaround was:

Autorun "setpci -s 00:02.0 F4.B=00" each boot.

Steps:
1) edit rc.local

```
gksudo gedit /etc/rc.local
```

2) Add the command before EXIT 0

```
setpci -s 00:02.0 F4.B-0
```

3) Restart.


You should now be able to boot in UNITY.
(ps: nomodeset is not a good solution)

---

### Post by sheelasamana on 2011-05-02
Acer Aspire 5732Z 4GB RAM upgrade - Ubuntu Karmic Koala Desktop

---

### Post by natedogg23 on 2011-05-02
anyone having problems with the display as well? im stuck in 4:3 and theres no more 16:9 widescreen option

---

### Post by kridybel on 2011-05-04
Having the same problem with an acer 7715z. How can one see what he's doing using a liveCD?

A permanent fix would be greatly appreciated. As well as a fix for the nvidia-96 driver for my old pc that is eager for 11.04 xubuntu.

---

### Post by m3mny on 2011-05-04
That little bit of code worked for me, I too am on Acer Aspire 5732z.

Will I have to find and use this script each time I start up?

---

### Post by Kalanac on 2011-05-08
Yes and seemingly every time the display sleeps or changes resolution.  You can add the rc.local to run the code each time you boot.  I've also created a shell script in my home directory that I can run blind to restore the back light if it goes off during a res change or standby.

Hopefully future kernel releases will render this fix unneeded but for now at least we can see :)

---

### Post by Kalanac on 2011-05-12
A few further observations:

Going into a 3D program (egoboo), turns off the back light again and it doesn't seem that the fix can be used to bring the light back on :(

I've tried calling it from the tty terminal when the screen was off, but it didn't bring the light back :(  I think perhaps the 3D application keeps unsetting it again or something, or perhaps the fix can't be applied while a 3D application is running.

---

### Post by foresthill on 2011-05-12
I have been battling this backlight problem for about a week on my Gateway NV7802 notebook.

Graphics are Mobile Intel GMA 4500MHD. Screen resolution is 1600 x 900 widescreen.

I discovered, like others, that an external monitor is a partial workaround, but this sort of defeats the whole concept of using a notebook. It has allowed me to download updates though (none of which have fixed the problem) and enter desperate and unsuccessful terminal commands to try to fix the problem. 

The silver lining is that all this has brought me back to the forums. Once my wireless modem problems were sorted out by the devs a year or so ago, I have been happy as a clam with 10.04 and 10.10. 

I guess about all we can do at this point is hope for a fix in the next kernel release, since it does not appear to be a driver-related problem, or anything we can fix by entering a couple clever terminal commands.

Not caring much for Unity, there's really little reason for me to upgrade anyway, but I will keep a hopeful eye on the forums and this thread, as well as download any updates that are released. I predict this bug will be sorted out in the coming days, so I salute the devs in advance for all their hard work in finding whatever solution is eventually discovered.  :guitar:

---

### Post by foresthill on 2011-05-14
There is a new kernel in pre-release, which I installed to see if it would fix my back light problems. No dice, my screen is still blank.

However, if I plug in an external monitor, I can get a very dim display on my notebook, which is just BARELY bright enough to see what I'm doing. 

This has got to be the most bizarre and serious Linux bug I have ever encountered. :( With previous display problems in other distros, you could at least use a generic driver to see the desktop, but not with this one.

HELP!!!

---

### Post by davidvs86 on 2011-05-19
> **Kalanac said:**
> I've also created a shell script in my home directory that I can run blind to restore the back light if it goes off during a res change or standby.

Could you post your script ?

---

### Post by foresthill on 2011-05-26
OK, I have found a rather obvious solution to my backlight problems I have been experiencing with my laptop (Gateway NV7802 notebook.Graphics are Mobile Intel GMA 4500MHD. Screen resolution is 1600 x 900 widescreen.).

I had looked previously for a brightness function key on the laptop's keyboard, and was expecting it to be at the top of the keyboard somewhere, but didn't see anything. But for my model, the arrow-up, arrow-down keys, when pressed along with the "Fn" key near the bottom of the keyboard are the screen brightness adjustment.

I don't know why I didn't notice them earlier, maybe because I've never needed to mess with them. 

So anyway, using these keys, allows me to turn up my brightness to where it needs to be. Now why the default setting is so unbelievably dim, and why it goes back to the dim setting every time I reboot, I don't know.

So if anyone knows how to change the default brightness setting, please let me know. Thanks in advance.

---

### Post by MarcG on 2011-07-01
I've got an eMachines e725 with this problem. But the screen brightness controls don't work for me. I'm just running the live CD, though. I don't think I'd install until there's a real fix for this.

---

### Post by foresthill on 2011-07-06
Sir, you are a very wise man. I wish I had your patience.

I have been installing the updates for 11.04 as they become available. Amazingly, none of them have fixed the problem yet. One would think a fix for this would be a very high priority, but evidently not.

I honestly think that the option to "Upgrade" 10.10 in the Update Manager applet should be grayed out until there is a fix for this. I would be incredibly angry if I upgraded a working 10.10 installation and got nothing but a blank screen when I was finished. And I see posts every day from distressed people running into this exact problem.

---

### Post by Kalanac on 2011-07-13
This issue is still present in the recent kernel update (2.6.38-10)

---

### Post by Xarjion on 2011-07-14
Hey everybody I'm running into this same problem trying to load Backtrack (ubuntu based), and ran across this.  I know some of you have mentioned this method, but this is an easy step by step for some of the less experienced people.  I did not write, just reposting.

[http://linux-on-acer-aspire-5732z.blogspot.com/2011/06/backlight-workaround-for-linux-mint-11.html](http://linux-on-acer-aspire-5732z.blogspot.com/2011/06/backlight-workaround-for-linux-mint-11.html)

I will update when/if it works out.

---

### Post by foresthill on 2011-07-16
IT WORKED!!!!!    :guitar::guitar::guitar:

Unbelievable. I have been fighting this problem since last April. Now I can finally start using the installation of 11.04 I installed way back then.

Thanks Xarjion!

I guess you can update now. Notice I didn't say "upgrade". I would not recommend that to my worst enemy. 

Somebody mark this thread solved.

---

### Post by PCLinuxGuy on 2011-08-10
I am still looking forward to see a real fix for this with the next kernel update  (2.6.39-x or 2.6.40?)  I mean tossing in support for generic graphics wouldn't have hurt them with the .38 update to the kernel.  I'm going to retry the live usb of 11.04 and try the function key with brightness contols to see if i get any luck.  If it weren't for this issue I would've updated to 11.04 on my laptop by now, as I like keeping up with the latest stuff (not bleeding edge ish though).  I just find lack of the generic graphic support for this kind of chipset to be disappointing for linux as a whole.

---

### Post by foresthill on 2011-08-12
Has anyone who is experiencing this backlight problem in 11.04 tried the 11.10 beta / daily build? 

I'm very curious to see if the problem is being addressed or solved there, but my internet connection is too slow to download beta versions. Or actually I can download it, but would rather not because I'm on a capped wireless broadband connection that would take me about 9 hours to download.

Thanks in advance. 

FWIW, Linux Mint 11 has this exact same backlight problem, because it's based upon 11.04. I discovered this fact the hard way.

---

### Post by vidwarren on 2011-08-25
I tried:

```
sudo setpci -s 00:02.0 F4.B=0
```

in Terminal and my screen went black; I had to shut the power off manually.

I **really** don't want to add this to anything that's going to run every time I boot unless I'm sure that it's not going to do the same thing. Does anybody have any ideas why it might have done this?

If it helps, I'm running Ubuntu 11.04 on a Samsung NC10 plus netbook.

I had the same problem on 10.04 but found a solution through these forums, can't remember what that was now but it was a similar 'find a file that runs on start-up and add/modify a line of code' solution.

It's not the end of the world if I can't find a solution but it would be nice, especially as I do a lot of long distance commuting and it would suck to have to restart and then be stuck with a dim display until I can find power.

Thanks in advance.

---

### Post by foresthill on 2011-08-25
Not sure if it matters, but I see you used "0" instead of "00". Did you try "90" or "99" or something similar?

All I can say is that I carefully followed the instructions in this link and they worked:

[http://linux-on-acer-aspire-5732z.blogspot.com/2011/06/backlight-workaround-for-linux-mint-11.html](http://linux-on-acer-aspire-5732z.blogspot.com/2011/06/backlight-workaround-for-linux-mint-11.html)

None of the other solutions posted for this problem ever did. FWIW, I'm running Intel 4500 MHD graphics in my Gateway notebook.

---

### Post by Dipper on 2011-09-02
None of that is going to do any good if you can't see the screen to make those changes.  Numerous bug reports have been filed regarding this issue.  They have been given "low" priority.  Apparently, the kernel developers think that using a flashlight to see your screen is just a minor inconvenience.

---

### Post by foresthill on 2011-09-02
If you plug in an external monitor, you can see the screen and enter commands. But yeah, I agree, this seems like a quite serious bug and needs to be addressed ASAP.

---

### Post by sanreader on 2011-09-08
I had the same issue with my ACER ASPIRE 5732Z laptop when I upgraded to Natty Narwhal. After trawling through the forums, here's the solution which worked for me:

The solution:
1. Open Ubuntu with an earlier kernel (e.g. 2.6.35-28) that does not have the backlight problem.

2. Open the terminal and type:
sudo gedit /etc/default/grub
(you need to enter your admin password) then the gedit window opens.

3. Edit the line (to add acpi_osi = linux) so that it reads:
GRUB_CMDLINE_LINUX_DEFAULT = "quiet splash acpi_osi = linux"
then save the file.

4. Close the gedit window to get back to the terminal and update grub with the command:
sudo update-grub2

5. Next in terminal, type:
sudo gedit /etc/rc.local
and add before the statement exit 0: the line:
setpci -s 00:02.0 F4.B=00
and save the file.

6. Close all windows and reboot selecting the natty narwhal kernel (e.g. 2.6.38-8) and the backlight should work OK.

Note: I have been using this for a few months now and have found that if I allow the laptop to go into sleep mode then the backlight problem returns. (I have the reboot the laptop to get in again).

---

### Post by foresthill on 2011-09-11
"Open Ubuntu with an earlier kernel . . ."???

You lost me from the first sentence.

---

### Post by jibon_24 on 2011-09-12
You can use  cron job this will run the script for every 1 second. You can follow this:

1. Go to home folder & create a script at any name. For example : "display"
&& write this code:
[PHP]
 #!/bin/bash
 while [ true ]; do
 sleep 1
 sudo setpci -s 00:02.0 F4.B=0
 done
 [/PHP]2. Go to terminal & write:

[HTML] sudo crontab -e[/HTML]& select 2 if you first time.

3. Now write this line at the end :

[HTML]
*/1 * * * *  sudo sh /home/YOUR NAME/display
[/HTML]4. Now ctrl+O && then ctrl+x

Enjoy :popcorn:

---

### Post by FSoares on 2011-09-29
Hi all, first off, I'd would like to thank everybody on here, always helpful, posting solutions for the problems you've found.

I've been using Linux on/off for 3 years now, but I can't upgrade to 11.04 due to this backlight problem. I've tried the still beta 11.10, but the problem remains, which tells me nobody cares about it, though it must affect thousands of users. I've this problem on an Acer emachines e525 and on a Samsung N145plus. I wanted to try the solutions psoted above but I really can't see anything. Even if I put a light directed to the screen I cannot figure where the mouse is, nothing!!

So, is there anyone kind enough to tell me how can I get light enough to try a possible solution? How can I boot from an old kernel? Summing up, what can I do in order to avoid formatting 2 computers and install windows?

---

### Post by FSoares on 2011-09-29
> **Dipper said:**
> None of that is going to do any good if you can't see the screen to make those changes.  Numerous bug reports have been filed regarding this issue.  They have been given "low" priority.  Apparently, the kernel developers think that using a flashlight to see your screen is just a minor inconvenience.

Unfortunatelly it seems you're right. What's the point of developing an OS if you can't see anything on the screen? :(

---

### Post by brucekev on 2011-09-29
I've got a Gateway NV79 and have the same problem with 11.04. I was hoping to upgrade, but I'm not willing to have to fight to keep my screen light. I can boot fine off the LiveCD, I just have to use a flashlight to see anything on the screen! I hope they fix this soon!

---

### Post by foresthill on 2011-09-29
> **FSoares said:**
> Unfortunatelly it seems you're right. What's the point of developing an OS if you can't see anything on the screen? :(

You can plug in an external monitor and use that. Or run an HDMI cable to your TV and use that (assuming your laptop has an HDMI output).

I linked to this thread on the 10.10 beta thread and got ZERO response. 

[http://ubuntuforums.org/showthread.php?p=11289794#post11289794](http://ubuntuforums.org/showthread.php?p=11289794#post11289794)

It's very sad that nobody cares one stinking bit about this bug, they seem more interested in shaving a half second off their boot up time. :(

Devs? Anyone?

---

### Post by FSoares on 2011-09-30
> **foresthill said:**
> You can plug in an external monitor and use that. Or run an HDMI cable to your TV and use that (assuming your laptop has an HDMI output).

I linked to this thread on the 10.10 beta thread and got ZERO response. 

[http://ubuntuforums.org/showthread.php?p=11289794#post11289794](http://ubuntuforums.org/showthread.php?p=11289794#post11289794)

It's very sad that nobody cares one stinking bit about this bug, they seem more interested in shaving a half second off their boot up time. :(

Devs? Anyone?

Thank you so much! Didn't remember about a HDMI cable and  try it on TV.

As for the rest, if they're more interested about shaving a half second off in boot time, then something is wrong in the state of Denmark, as the saying goes! There's a very serious bug to sort, the new Ubuntu 11.10 keeps the same bug and nobody seems interested to sort this very serious problem affecting lots and lots of users. What's wrong?

---

### Post by FSoares on 2011-09-30
> **brucekev said:**
> I've got a Gateway NV79 and have the same problem with 11.04. I was hoping to upgrade, but I'm not willing to have to fight to keep my screen light. I can boot fine off the LiveCD, I just have to use a flashlight to see anything on the screen! I hope they fix this soon!

As I posted above I have that problem on two different computers: one is an Acer emachines e525 (a laptop) and the other is a netbook Samsung N145Plus. Ubuntu 10.10 boots fine and there's no problem of backlight. Upgrading to 11.04 is suicide because there's no light on the screen and we can't see literally anything, even using a light source pointed to the screen. I also tried the still beta Ubuntu 11.10 to check if they have sorted this problem and imagine what? The bug is still there, nothing has changed! It's like having (in my case) two dead computers! It's not fair keeping this bug eternally! [-X

---

### Post by Blasphemist on 2011-09-30
For those who haven't solved a backlight issue, are you still wanting to solve it? There are solutions within this thread and many others. There are a number of issues that can cause it and therefore a number of solutions. Most involve kernel mode setting that can be tried from grub before making the solution permanent. If you want to solve the issue for your specific configuration and you are unable to find the solution already defined, I recommend that you create a thread of your own. Please specify your gpu/video card and what if anything you have tried. For research, this is a good place to start. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

People will be willing to help if you are willing.

---

### Post by FSoares on 2011-09-30
Well, I found a way to sort the problem even if it is not the best option, but it was the best that came to mind and it actually worked. 

When computer starts to boot, press SHIFT and the grub will appear on the screen. Choose starting up using an old kernel from an old version (this just works for those who have upgraded from 10.10 to 11.04) and you'll see kernel 2.6.35-30 generic. Voilà system finally starts normally!! Hooray!

Then, open terminal and install startupmanager:

sudo apt-get install startupmanager

After installation complete:

sudo startupmanager

You'll then see a program window and under "boot options" tab, you'll find "Default Operating System" dropdown. Choose your desired kernel image (those who have the old kernel from 10.10 still installed). Reboot your computer and it will bring normally Ubuntu 11.04.

I don't know if this is the best solution as basically we'll have to downgrade the kernel, but it was the only thing that really worked for me.

However, probably the best is following what was suggested on the post above mine.

---

### Post by slicer777 on 2011-10-04
First, these posts have really helped me out. I have the same problem here as everybody else for a while.

My "black" screen was gotten around by doing the nomodeset in the boot script in grub....I then changed grub so that it would save....but of course my display sucked. I am really surprised that there is not a fix. The monitor setting is "Unknown" and I have all of two or three resolution modes.

I did find a solution that works for me....I am running 11.04 on a Gateway NV79 - Intel Laptop. I have two harddrives...one is Winblows 7...and then the other is dedicated to Ubuntu.

Ok...when I boot up, I get the blank screen....unfortunately, my dim keys (FN key and down or up arrow) do nothing for me. However, by shining a flashlight on the screen....I can make out my login. My display is perfect...all of the resolution modes that I know I should have....so I rebooted....changed my grub boot line to nomodeset...and am able to log in.

I then go into power management...and change the setting from sleep to blank screen on the "When laptop lid is closed" both in ac power and battery....along with any other settings to just blank screen...and not sleep or hibernate.

Reboot....and when grub comes up...I boot normally to a dark screen...close lid once...open and screen is on....log in and all my settings are now perfect. 

Not sure if this will help anybody else....but it sure has saved my bacon...since I use it for work.

My 2 cents.

---

### Post by foresthill on 2011-10-20
Well, I installed 11.10 last night. Same backlight problem still exists. And the irritating part is, the backlight does come on, just for an instant, while shutting down. So a solution can't possibly be that difficult. 

Meanwhile I see much less serious bugs like people not being able to get their touchpads to work just the way they want getting immediately addressed while this bug, which prevents users from even installing Ubuntu, festers and continues to be ignored.

That, combined with this horrible Unity netbook interface (which is absolutely useless on a workstation) that's been forced on us, I see little reason to wait for the next version to be any better. I see the path that Ubuntu is on and I would prefer not to deal with it.

Anyone know of any suitable Linux distros that don't have this miserable backlight bug and don't force users to deal with Unity? I'm ready to make the switch.

---

### Post by brucekev on 2011-10-22
> **slicer777 said:**
> 
Reboot....and when grub comes up...I boot normally to a dark screen...close lid once...open and screen is on....log in and all my settings are now perfect. 


I like your work around! :lolflag: Good job of thinking outside the box! 

Kev

---

### Post by rband42 on 2011-12-20
I had the same issue during the installation...
Some days after the installation I accidental discovered that whenever I adjusted the back-light immediately after I switch on the laptop the backlight stays on!

This is how I have been using my laptop for about month now, I'm still looking for permanent solution.

I an using emachines e525

---

### Post by DWade on 2012-04-11
I have found on my NV7922u gateway laptop that if you plug the HDMI cable in and boot with it in and once it boots it then put the correct video sequence to to the laptop screen so you can see and install.  After install it works correctly or at least 11.10 does.

I am waiting for the full release of 12.04, to install, but the beta works the same way.  I do not think it Ubuntu it the kernel designers.  but I could be wrong!   The same problem happens with Parted magic which is a system tool boot up disk.

---

### Post by foresthill on 2012-04-12
Does suspend work OK for you? Because on my Gateway laptop, once the screen goes dark after being idle for 10-15 minutes, I can't come back out of it (screen stays dark) and I have to hold the power button down and do a hard reset. Not good for my hard drive, I would think.

I did the workarounds for getting the backlight to work during installation and normal start-up, but this problem persists for me.

---

### Post by DWade on 2012-04-12
I have a gateway NV7922U laptop 4 megs of memory intel hd Graphics, with an I5 processor. running 11.10  till the full release of 12.04 comes out.

My black screen has only been at installation with Live CD.  Using an HDMI cable to and LCD tv at boot up it will then go to the purple screen on the TV with dots flashing and the then find the correct driver and reset the screen for the Laptop and continue to choose installation of Live CD.

But... before I discovered this I would start boot up and continuiouly press F4 to get it to come to a boot menu.  Then I would use option F6 other options and change to noapic command boot up to try Ubuntu and was able to get screen and bootup to install.

Doing that function may have inabled the proper graphics driver sequence on my laptop to function properly.

Because I left about a 45 minutes ago to walk the dog, came back to blank screen moved mouse and it came back on, then fixed breakfast and again moved mouse to get screen and now logged on a typing this.

screen set at 1600 X 900
power setting  battery.......no battery
...........10 min suspend....don't suspend
close lid Hibernate..........Hibernate

---

### Post by foresthill on 2012-06-01
Problem is still not fixed in 12.04. Can't install, screen goes black 30 seconds after I begin the installation, and never comes back on.

I am totally speechless. ](*,)

---

### Post by DWade on 2012-06-01
Problem is in the intel graphics, and the kernel.

If you have and HD tv and a HDMI cable plug it into your laptop and boot up with the cd.

The kernel trys to boot to the HDMI output instead of the LCD output.

Or as it goes from boot screen press F4 until the language screen come up.

Press enter on Language and then with the menu options press F6 and choose NOAPCI and then ESC and then F1 and boot should keep the screen going to boot live CD.  but,...

You can only boot into 12.04 or 11.10 with the Grub 2 it makes, else you will have a blank screen although I have found the following fix as long as the install is with autologon.

after hard drive lite quites press power button, pause then press it again, press the right arrow then press enter and the system will go to logon and set the video to the right monitor and you can logon..

---

### Post by DWade on 2012-06-01
If you'd like the whole installation procedure and problems I have had, send me a private email and I will write it up in Libre Office and send it to you.

How I installed it and how many different problems I had and how I lost my window 7 virtual hard drive in 12.04 as well.

---

### Post by foresthill on 2012-06-01
After weeks of fighting I've gotten 11.04 and 11.10 to install using an external VGA monitor (or maybe it was with HDMI). Then I applied a bunch of the fixes listed in this thread, but gave up when I could not get the laptop backlight to come back on after the screen would suspend, forcing a hard reset.

I had hoped that some tiny amount of progress would have been made with this problem after an entire year of people complaining about it, but it looks as though the devs have either completely ignored it, or been unable to integrate any of the various workarounds that users have painstakingly discovered into some sort of small patch.

One would think that Intel laptop users not being able to see their screens at all, might be considered a "somewhat critical" bug, but I'm really frustrated that nothing at all has been done.

---

### Post by DWade on 2012-06-02
That's because it somewhat our own faults.  I had forgotten about launchpad which is where you report bugs and problems, not here.

This is where we help each other in problems that are fixable, where we found work arounds or things we've forgotten, which others remember, or to help the new users (Newbies). If it's a major problem we are to report it.  

That error on 12.04 keep asking me to report it, so I did. and submitted with the report and errors 12.04 listed.

The reason for the error reporting is I shut the laptop off several times enough to create a problem report. I was trying to find how to log off not shut down. 

So 11.04 has the problem too.  Do you know if 10.10 does?
Also try the following and see if they will boot.  the ultimate bood cd, parted magic, latest release of gparted, and the latest release of clonezilla.

For me blank screen on UBCD, Parted Magic, GParted.  Clonezilla I haven't tried outside of virtual machine.  This is why I have been stating it's a kernel problem and not a software problem. Those are all using the new kernels too.  

Or-- could it be the new version of Grub, Grub2?

---

### Post by foresthill on 2012-06-02
10.10 installs and works GREAT on the machine, that's what's so frustrating. I would run 10.10 forever on this machine and be thrilled with it, but it seems to be nearing the end of its support cycle, since I have not had any updates for it in several weeks. 

I'm not really a software guy, so I won't speculate too much on what the problem might be. Grub 2 works fine as far as I can tell, it's just that for some reason, the Intel 4500 MHD graphics chip is not being detected during installation, and also during boot up. There there is also the inability to come out suspend, which might be an entirely different problem, I'm not sure.

Fortunately, I have a backup laptop I can use, but it sure would be nice to run the latest version of Ubuntu on this machine. It's a Gateway, and not that old, I bought it 2010, so there must millions more out there running this exact same graphics chip. So why is it only us two who are complaining about it, I wonder?

---

### Post by DWade on 2012-06-22
Try 10.04 one step back from 10.10 and it's LTS like 12.04, it works great and has a year left. And my google desk top gadgets work in it too.

Oh and by the way, when it goes into suspend, try using CTR+ALT+DEL it supposed to bring up the Log out window and press the enter key after pressing CTR+ALT+DEL.

My latest reload does not work pushing the power button and right arrow key and enter, it shuts down.

I guess my long trial of load and fixes need to be re-written.

---

### Post by foresthill on 2012-06-24
What I ended up doing is, I used an external monitor to install 12.04, then I applied the backlight fixes described ealier in this thread. 

And to prevent the problem of the system being unable to come out of suspend, I went to the power settings and adjusted them so the screen never turns off, I lock the screen manually when I'm going to be away.

Kind of an ususual amount of tweaking required before I can use the OS compared to earlier versions, but whatever.

And I'm not terribly thrilled with the overall dumbing down of the OS in these later versions. And ironically 11.04, 11.10 and 12.04 all require far more tweaking on my part, just to get an over-simplified OS that was evidently designed for children, to work. 

But I'm trying my best to get used to it. And I feel it's still miles ahead of what Windows has to offer.

---

### Post by christopher035 on 2012-08-17
I'm having the same issue with my eMachines E725 (Acer made). 
Is there a real fix for this?

"When booting into Ubuntu 11.04(or 12.04) Natty Narwhal there is no back light to the laptop display. An image is produced and you can just make out the desktop and some of the brighter windows but there is no light behind the image to make it more visible.

This is NOT the contrast/brightness issue/bug and has nothing to do with the brightness settings or adjusting using the laptops function keys."

---

### Post by foresthill on 2012-10-14
The best fix I know of is to download and install 10.04 LTS. You can do the workaround, but suspend and hibernate are still completely messed up, and you'll have to deal with that every 10 minutes the machine is idle when the screen goes black and then won't come back on.

---

