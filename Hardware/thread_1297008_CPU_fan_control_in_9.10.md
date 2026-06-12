---
title: "CPU fan control in 9.10?"
date: 2009-10-21
forum: Hardware
---

### Post by Anonymousable on 2009-10-21
OK, I'm trying the 9.10 beta. Ever since the upgrade, I've been having problems with the CPU overheating. I have no problems in Windows (surprisingly) and never had the problems in 9.04.

I'm using an Intel DG33TL motherboard. pwmconfig:
There are no pwm-capable sensor modules installed

I've tried to disable BIOS fan control, but there are no options for that.

Thanks in advance.

---

### Post by Anonymousable on 2009-10-22
bump
I'm throttling at the moment... Would be great if someone could help.

---

### Post by co0z on 2009-10-22
Hey,

Im also having the same problem - In fact it was one of the reasons i moved to ubuntu I found an answer to this question but im a total n00bee lol and i dont know how to execute the instructions...

If this answer works - can someone explain what to do once i open
[B][I][B][I]sudo nano /etc/default/grub
[/I][/B][/I][/B]
Heres what it said.. 

**Laptop fan runs constantly under Ubuntu 9.10 beta (Fixed)**

***I had a noisy problem with Ubuntu on my Toshiba laptop: the fan, once started, never stopped until I shutdown the computer.***
 ***I don't know since when Ubuntu has that problem but it is not new.  I had the same problem with Ubuntu 8.04 on my laptop and never found a way to fix it (or didn't try hard enough)...***
 ***Yesterday, I finally find a working fix.  Now my laptop fan starts only when the CPU is too hot... like it should!***
 ***So here is the recipe:***
 
[LIST]
[*]***Open a terminal (Applications | Accessories | Terminal)***
[*]***Type:***
[/LIST]
 ***sudo nano /etc/default/grub***
[LIST]
[*]***Find and Edit the following line:***
[/LIST]
 [B][I]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[/I][/B]
[LIST]
[*]***Add  [I]acpi_osi=Linux* to the end so it looks like this:[/I]**
[/LIST]
 [B][I]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
[/I][/B]
[LIST]
[*]***Exit Nano editor with Ctrl+X.  Answer "yes" when asked to save the file***
[*]***Update grub: ***
[/LIST]
 ***sudo update-grub***
[LIST]
[*]***Reboot to make changes effective***
[/LIST]
 ***Hope it helps you to have a quieter work environment!  [IMG]http://symbiosoft.net/modules/fckeditor/fckeditor/editor/images/smiley/msn/regular_smile.gif[/IMG]***
 ***[B]IMPORTANT:** That procedure will work only with Ubuntu 9.10 because it uses grub 2.  Therefore the default grub file was not present in previous versions of Ubuntu.*[/B]

---

### Post by Anonymousable on 2009-10-23
Hmm... Sounds good, I'll have to try that. However, nano is not a very newbie-friendly option... My suggestion for you is to replace nano with gedit and then follow the instructions.

Thanks!

EDIT: Oops... The file /etc/default/grub doesn't exist for me...

Does anyone know if I should make the same change to /boot/grub/menu.lst?

---

### Post by earthpigg on 2009-10-23
> **Anonymousable said:**
> EDIT: Oops... The file /etc/default/grub doesn't exist for me...

Does anyone know if I should make the same change to /boot/grub/menu.lst?

9.10 uses a ***completely different*** grub than 9.04 and previous.

grub2 is completely different. do not follow any directions intended for 9.04 or earlier.

beyond that... i have never worked with grub2, so cannot help you with that method :\

---

### Post by Anonymousable on 2009-10-23
Ok... Does grub1 get kept if I *upgraded* from ubuntu 9.04?
If yes, would I then have to edit menu.lst?

EDIT: OK, I've just tried it. I might not be back :D

EDIT: No difference. Still the " There are no pwm-capable sensor modules installed" error. :(

YET ANOTHER EDIT: Updated to grub2. I'll see what happens now.

---

### Post by earthpigg on 2009-10-23
i really don't think CPU fan speed could have a lot to do with grub, unless there is some serious sillyness going on.

---

### Post by Anonymousable on 2009-10-23
> **earthpigg said:**
> i really don't think CPU fan speed could have a lot to do with grub, unless there is some serious sillyness going on.
I am aware of that, but look at co0z's post. That should explain it ;)

Now, I've managed to semi-brick my PC and am writing from a live CD...

I didn't know not to run update-from-grub-legacy until later. How can I revert it? :(

---

### Post by Anonymousable on 2009-10-23
Sorry to bump so soon, but PLEASE can someone help me? I really need to have normal access to my computer again...

---

### Post by Anonymousable on 2009-10-23
Sorry I'm bumping so much, but I really need to know how to undo update-from-grub-legacy using the Live CD...

Oops, this has gone off-topic, this is the wrong place to ask. Sorry.
*asking in appropriate forum*

---

### Post by Anonymousable on 2009-10-23
Now, back on topic after my long post chain... I'm sorry about that.

Any ideas about how to solve this? I really want the fan running at proper speeds so that my CPU doesn't overheat...

---

### Post by Anonymousable on 2009-10-25
bump... again... sorry...

---

### Post by Anonymousable on 2009-10-27
Someone, please help... I still have to throttle...

---

### Post by Anonymousable on 2009-10-28
Bump

---

### Post by Anonymousable on 2009-10-29
Bump!

---

### Post by Anonymousable on 2009-10-30
bump...

---

### Post by rossmoore on 2009-10-30
I know that in theory you can use /proc/acpi/fans to control the fan speed. On my Dell XPS M1530 the bios doesn't give up control of the fans to the operating system, so I can't control them and never have been able to - but they seem to kick in at appropriate temperatures.
Do you have anything in acpi/fans to control?

---

### Post by Anonymousable on 2009-10-30
Nope, an empty directory named /proc/acpi/fan. That's all. As I said (before all my bumping >.<), I tried pwm-config too, but that didn't work.

Thanks for trying to help though.

---

### Post by Anonymousable on 2009-10-30
ARGH! bump.

---

### Post by Anonymousable on 2009-10-31
Not another... Bump.

---

### Post by Anonymousable on 2009-11-01
*yawn* bump.

---

### Post by infinities on 2009-11-02
yay, this solved the problem on my toshiba laptop

this is probably my first linux problem that i've actually resolved

---

### Post by Anonymousable on 2009-11-02
Hey, that's good to hear! :)

But my problem still hasn't been solved...

---

### Post by revilodraw on 2009-11-03
> **Anonymousable said:**
> Hey, that's good to hear! :)

But my problem still hasn't been solved...


If you updated from Jaunty then you will need to update your grub. 

"GRUB 2 will be installed by default on NEW installations of Karmic. If you have upgraded from Jaunty 9.04 to Karmic 9.10 you can follow the install instructions for Jaunty 9.04 below." 

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)


hope this helps.

---

### Post by Anonymousable on 2009-11-05
Sorry, looks like my original problem has been lost...

I've now installed GRUB 2 successfully, works like a dream. :)

The problem is, and remains, how can I keep my CPU cool without throttling? I'm missing out on a game I really love to play just because of my troubles with the fan.

Tried `pwmconfig': No pwm-capable sensor modules installed
/proc/acpi/fan is an empty directory.

---

### Post by M7S on 2009-11-08
What worked for me was adding acpi_enforce_resources=lax to that same line in grub. Hope it helps.

---

### Post by Anonymousable on 2009-11-08
Thanks, I'll try that...

---

### Post by Anonymousable on 2009-11-08
UPDATE: It just made it worse. I tried it with strict rather than lax afterwards, and it was better, but not much better. :(

Thanks for the help though, it has made it better. I still don't think the fan is on full power when I use ```
burnK7 & burnK7 & burnK7 & burnK7
``` though.
Any ideas?

---

### Post by Anonymousable on 2009-11-10
Anyone? Does anyone maybe know how to get the fan working with /proc/acpi/fans?

---

### Post by Anonymousable on 2009-11-10
Nobody? I really want to stop throttling and start playing my favourite game again... :(

---

### Post by ratcheer on 2009-11-10
This documentation is very thorough on installing, reinstalling, using, and fixing grub2. There is a section of booting from a LiveCD and fixing grub2 in cases like yours. I know - I had to do it a few days ago.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Tim

---

### Post by Anonymousable on 2009-11-10
Again, thanks, but IT'S NOT ABOUT GRUB2.

I'm trying (and failing) to directly control my CPU fan.

/proc/acpi/fan(s) is empty
pwmconfig says `there are no pwm-capable sensor modules installed.'[SIZE=1][/SIZE]

---

### Post by Anonymousable on 2009-11-11
A-bump.

I'm trying (and failing) to directly control my CPU fan.

/proc/acpi/fan(s) is empty
pwmconfig says `there are no pwm-capable sensor modules installed.'

I assume that it's an acpi problem, what with the /proc/acpi/fans folder being empty.

---

### Post by Anonymousable on 2009-11-11
PLEASE!

I'm forced to use windows when doing any heavier computing, which cuts performance by about 75%!

---

### Post by ethos101 on 2009-11-14
Bump.  You're not alone my friend.  I'm having the same problem.

Acer Aspire 5720z w/9.10 and the acpi grub2 fix.  Still no fan at all.

---

### Post by Anonymousable on 2009-11-14
No fan at all? O_O that sounds bad.
I at least have it running a little.

Please, any help?

---

### Post by bouil on 2009-11-14
I have the inverse problem, after upgrading from jaunty to karmic, my laptop fan is always on noisy.

I've read somewhere to add "acpi_enforce_resources=lax" on grub linux boot option, so i modified the /boot/grub/menu.lst :

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash **acpi_enforce_resources=lax**


(be aware you must NOT uncomment the line)

It worked for me.

---

### Post by Anonymousable on 2009-11-14
> **bouil said:**
> I have the inverse problem, after upgrading from jaunty to karmic, my laptop fan is always on noisy.

I've read somewhere to add "acpi_enforce_resources=lax" on grub linux boot option, so i modified the /boot/grub/menu.lst :

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash **acpi_enforce_resources=lax**


(be aware you must NOT uncomment the line)

It worked for me.
Thanks for trying to help. I've tried that with strict, which helped a little. But not enough - the CPUs still overheat when running burnK7 x 4.

---

### Post by moh980 on 2009-11-14
I am having the same problem with a new Toshiba laptop and fresh install of Karmic! 
my fan start at full speed only when the CPU overheated (80C) and when it cool down the fan never shuts off


any way to solve this????



Thanks

---

### Post by J-Buntu on 2009-11-14
Have you considered that it may be your proprietary driver ? When i first installed Karmic, i enabled the Nvidia v185 driver that was suggested to me (that i previously used in Jaunty) but on reboot, noticed that my fan was going seriously crazy. I rebooted several times, just to confirm the problem and it still persisted. Fortunately two proprietary drivers were available to me - the Nvidia v185 and Nvidia v173, so i uninstalled the v185 and installed the v173 and rebooted - and guess what, no more crazy fan.

It's just a suggestion.

---

### Post by steve161 on 2009-11-14
This worked for me.  Open /etc/default/grub as root.  Look for the line that ends with quiet splash.   Add acpi_osi=\\\"Linux\\\"" to the line so it looks like this

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""

Then run sudo update-grub from the terminal.

I saw a similar parameter posted earlier, but the problem is that grub2 does not honor quotation marks without the \\\  added.  Btw, I have a toshiba laptop and my fan now kicks in (quietly) at 56C and turns off at 42C.  I found this after googling and some trial and error so I can not explain the logic behind this.  Also, I am not sure this will give the user any direct fan control.

---

### Post by J-Buntu on 2009-11-14
> **steve161 said:**
> This worked for me.  Open /etc/default/grub as root.  Look for the line that ends with quiet splash.   Add acpi_osi=\\\"Linux\\\"" to the line so it looks like this

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""

Then run sudo update-grub from the terminal.

I saw a similar parameter posted earlier, but the problem is that grub2 does not honor quotation marks without the \\\  added.  Btw, I have a toshiba laptop and my fan now kicks in (quietly) at 56C and turns off at 42C.  I found this after googling and some trial and error so I can not explain the logic behind this.  Also, I am not sure this will give the user any direct fan control.
_____________________

This would be of no use to me i don't think, as it seems my lappy never really drops below 46c anyway if it has been on for any normal amount of time. I'd like to read the source of your post myself if you could leave a link. I wouldn't want to try that without knowing how to reverse it personally. I'm guessing you'd just remove what you added. But i'd still like to read it myself, as you said it's not obvious why it works.

---

### Post by steve161 on 2009-11-14
Sorry, I do not remember where I found it.  I used to have to add acpi_osi="Linux" to the kernel parameters of all my distros on my laptop.  However, it didn't work for grub2 and I came across this fix.  I may have found it in a reply to a bug report.  Changing it back though, is easy.  Just delete the line acpi_osi=\\\"Linux\\\"  and run sudo update-grub again.

 > as you said it's not obvious why it works. 		                   		  		  		  		  		 		 			 				

Not obvious to me.  I'll take a quick look to see if I can find it.

---

### Post by moh980 on 2009-11-14
> **J-Buntu said:**
> Have you considered that it may be your proprietary driver ? When i first installed Karmic, i enabled the Nvidia v185 driver that was suggested to me (that i previously used in Jaunty) but on reboot, noticed that my fan was going seriously crazy. I rebooted several times, just to confirm the problem and it still persisted. Fortunately two proprietary drivers were available to me - the Nvidia v185 and Nvidia v173, so i uninstalled the v185 and installed the v173 and rebooted - and guess what, no more crazy fan.

It's just a suggestion.

Thanks! but i am only offered one option for the ATI driver

---

### Post by moh980 on 2009-11-14
> **steve161 said:**
> This worked for me.  Open /etc/default/grub as root.  Look for the line that ends with quiet splash.   Add acpi_osi=\\\"Linux\\\"" to the line so it looks like this

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""

Then run sudo update-grub from the terminal.

I saw a similar parameter posted earlier, but the problem is that grub2 does not honor quotation marks without the \\\  added.  Btw, I have a toshiba laptop and my fan now kicks in (quietly) at 56C and turns off at 42C.  I found this after googling and some trial and error so I can not explain the logic behind this.  Also, I am not sure this will give the user any direct fan control.

Thank you for the suggestion...i just tried it and rebooted so far the fan is kicking off at 56C quietly :D ...but it didnt turn off yet! 
will keep monitering it and will report back later

Thanks again!

Cheers! 
Moh

---

### Post by ethos101 on 2009-11-15
It's working so far...

I feel quite alienated.  The past two releases (9.04 and 9.10) have left me and my Acer Aspire 5720z in the dark for various issues (Intel video for 9.04 and CPU overheating in 9.10).  I get what I pay for I guess.  Hell, even before that with 8.10 I had to compile the madwifi module to get my wireless to work.  I'll stop my rant here.  Thanks for listening.  :)

---

### Post by J-Buntu on 2009-11-15
> **steve161 said:**
> Sorry, I do not remember where I found it.  I used to have to add acpi_osi="Linux" to the kernel parameters of all my distros on my laptop.  However, it didn't work for grub2 and I came across this fix.  I may have found it in a reply to a bug report.  Changing it back though, is easy.  Just delete the line acpi_osi=\\\"Linux\\\"  and run sudo update-grub again.

 

Not obvious to me.  I'll take a quick look to see if I can find it.
_________________________________________________________

Thanks for taking the time to look for it, i'll check back here later.

---

### Post by moh980 on 2009-11-15
> **moh980 said:**
> Thank you for the suggestion...i just tried it and rebooted so far the fan is kicking off at 56C quietly :D ...but it didnt turn off yet! 
will keep monitering it and will report back later

Thanks again!

Cheers! 
Moh

just report back....so far everything is working the way it suppose to be :D

also i noticed the fan now kicking on high speed around 58C...and i guess its shutting down around 44C...

the temp now is so stable (range 44~55C / before applying this tweak it was 33~80C)


Cheers!
Moh

---

### Post by steve161 on 2009-11-15
> Thanks for taking the time to look for it, i'll check back here later.

I can't find the page where it discusses the reasoning behind the parameter, but here is a short explanation of the parameter and the change needed for grub2

[http://forums.linuxmint.com/viewtopic.php?f=60&t=18222]("http://forums.linuxmint.com/viewtopic.php?f=60&t=18222")

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/411597]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/411597")

---

### Post by Anonymousable on 2009-11-16
Thanks for all the attempts to help... Nothing has helped all the way though. cpuburn still makes my CPUs reach 90°C in seconds.

---

### Post by mivo on 2009-11-16
Have you tried the Live CD of another distro to see if they work? Fedora or SuSE are obvious choices since they are not Ubuntu-based. Not to switch, just to isolate the problem a little.

---

### Post by Anonymousable on 2009-11-17
What do you mean? I don't think I've understood you fully, but I'll repeat that this problem didn't occur on 9.04 (I am aware that you may have already seen that).

---

### Post by mivo on 2009-11-17
It may be a kernel issue, or could be caused by the update of another commonly used component. By burning and running the Live CD of [Fedora]("http://fedoraproject.org/en/") or [OpenSuSE]("http://www.opensuse.org/en/") you may be able to find out whether this is an Ubuntu-only problem or one that is shared by the new releases of other Linux distros, too. It may help a little with troubleshooting.

---

### Post by Anonymousable on 2009-11-17
OK, thanks, I'll try that and post updates soon.

Good thing I have a new internet connection since living in France xD

---

### Post by Anonymousable on 2009-11-19
So, here are the promised updates...

I tried BOTH Fedora and oSUSE, *both* didn't have drivers for my wireless dongle, making it impossible for me to get the (also unincluded) sensor drivers. :(

---

### Post by ethos101 on 2009-11-19
But did the cpu fan spin properly?

---

### Post by Anonymousable on 2009-11-19
It always spins, and I can never tell if it spins *enough* unless I have a CPU temperature monitor running or it overheats so much that the X server crashes.

Thanks for trying to help though.

---

### Post by Anonymousable on 2009-11-19
Any ideas how else I could test the fan + linux? :(

---

### Post by mivo on 2009-11-19
Hmm, you could give Puppy Linux a try. It can be installed to an USB stick and will create sort of a virtual /home directory there so that you can save your settings, packages, etc. It is also very good with wireless support out of the box, in my experience. What I don't know is whether it has sensor software in its limited repositories.

[Puppy Linux]("http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm")
[Download]("http://puppylinux.org/main/index.php?file=Download%20Latest%20Release.htm") (It's just about 100 MB.)
[USB flash installation guide]("http://puppylinux.com/flash-puppy.htm")

---

### Post by Anonymousable on 2009-11-20
Ah,  thanks. What software does it use for package management?

---

### Post by mivo on 2009-11-20
Puppy uses its own package manager. It does allow you to compile own stuff from source, too. They have a small but helpful forum. But see first if the wireless works out of the box. :) I'm surprised still that Fedora and OpenSuSE failed you.

---

### Post by ethos101 on 2009-11-20
CPU fan isn't working.  It was intermittent and now it's not spinning.  I can't understand why it was fine under 9.04 and previous but with 9.10 it's not spinning at all.  This will end up damaging my hardware beyond repair.  I'm gonna put windows back on my laptop until this is sorted out.

Thanks for your help anyways.

---

### Post by slumbergod on 2009-11-20
> **ethos101 said:**
> Bump.  You're not alone my friend.  I'm having the same problem.

Acer Aspire 5720z w/9.10 and the acpi grub2 fix.  Still no fan at all.

I am using the same system. My fan is hyper all the time. A week ago I managed to make my system shutdown by converted flac audio files to ogg. I can almost do the same playing certain mkv videos of HD content.

I've found both Jaunty and Karmic run my fan more than usual. I remember when I got the laptop Vista was so quiet. With Linux it is noisy and frustrating. I just accept that my *next* (new) laptop will work better with linux.

---

### Post by ladi on 2010-01-10
works great!!!!!!!!!


> **co0z said:**
> Hey,

Im also having the same problem - In fact it was one of the reasons i moved to ubuntu I found an answer to this question but im a total n00bee lol and i dont know how to execute the instructions...

If this answer works - can someone explain what to do once i open
[B][I][B][I]sudo nano /etc/default/grub
[/I][/B][/I][/B]
Heres what it said.. 

**Laptop fan runs constantly under Ubuntu 9.10 beta (Fixed)**

***I had a noisy problem with Ubuntu on my Toshiba laptop: the fan, once started, never stopped until I shutdown the computer.***
 ***I don't know since when Ubuntu has that problem but it is not new.  I had the same problem with Ubuntu 8.04 on my laptop and never found a way to fix it (or didn't try hard enough)...***
 ***Yesterday, I finally find a working fix.  Now my laptop fan starts only when the CPU is too hot... like it should!***
 ***So here is the recipe:***
 
[LIST]
[*]***Open a terminal (Applications | Accessories | Terminal)***
[*]***Type:***
[/LIST]
 ***sudo nano /etc/default/grub***
[LIST]
[*]***Find and Edit the following line:***
[/LIST]
 [B][I]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[/I][/B]
[LIST]
[*]***Add  [I]acpi_osi=Linux* to the end so it looks like this:[/I]**
[/LIST]
 [B][I]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
[/I][/B]
[LIST]
[*]***Exit Nano editor with Ctrl+X.  Answer "yes" when asked to save the file***
[*]***Update grub: ***
[/LIST]
 ***sudo update-grub***
[LIST]
[*]***Reboot to make changes effective***
[/LIST]
 ***Hope it helps you to have a quieter work environment!  [IMG]http://symbiosoft.net/modules/fckeditor/fckeditor/editor/images/smiley/msn/regular_smile.gif[/IMG]***
 ***[B]IMPORTANT:** That procedure will work only with Ubuntu 9.10 because it uses grub 2.  Therefore the default grub file was not present in previous versions of Ubuntu.*[/B]

---

