---
title: "Thinkpad T60 volume buttons in 9.04 and 9.10"
date: 2009-11-16
forum: Hardware
---

### Post by juhaszjozsef on 2009-11-16
Hi all.
I've a thinkpad T60 and 9.10 installed. I did some search on the forums and found the workaround with tpb package to fix thinkpad volume buttons issue.
My problems with that fix are:
-tbp package depens on xosd (or whatever like that, NOT Notify-OSD) so the result is not the best... :(
-tpb package is not neccessary at all, because thinkpad_acpi module can take care about volume buttons as well, you just have to enable the hotkey mask! [http://www.thinkwiki.org/wiki/Thinkpad-acpi]("http://www.thinkwiki.org/wiki/Thinkpad-acpi")

So my workaround on T60 (in terminal):
9.04 jaunty: 
```
sudo echo enable,0x00ffffff > /proc/acpi/ibm/hotkey 
```
9.10 karmic: (using sysfs): (also works on 10.04 and 10.10 as well...)
```
sudo cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask
```

[B]Update:
The solutions only works till next reboot or suspend/resume cycle.
you should put the commands in:
/etc/rc.local
without sudo of course, to make it permanent.[/B]

Please confirm if the solution works on other thikpad models.

As soon as I find solution for all the things I need on my T60 I will put it up on Thinkwiki and paste the link here.
(Active protection - hdaps) 
(Trackpoint additional functions - you just have to install the: gpointing-device-settings package)
(fingerprint reader - thinkfinger)

Hope it helped for someone.

---

### Post by rCXer on 2009-11-16
Hmm... the sound buttons worked out of the box on my t43p (maybe because I'm lucky ;) ) This should help others though.  Maybe you should post this in the Linux section of the [Thinkpad Forums](http://forum.thinkpads.com/).  Make sure you you edit the wiki page as well.

---

### Post by juhaszjozsef on 2009-11-17
Hi!
The buttons worked for me as well. (Since they are hw buttons on thinkpads)
But only wwithout notification. The workaroud above is to fix the notification only!.

---

### Post by rCXer on 2009-11-17
Wow that's brilliant!  The notification wasn't working for me and your method worked \\:D/ I had to become root by "sudo -i". Otherwise I got "permission denied"...

```

sudo -i
sudo echo enable,0x00ffffff > /proc/acpi/ibm/hotkey

```

This has been a [long-standing bug](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357673?comments=all) on thinkpads and this might be the workaround needed.  Since you discovered this, could you post your solution in the bug report in the link?  I'm sure they'll appreciate it. Thanks!

---

### Post by Forlong on 2009-11-18
> **juhaszjozsef said:**
> 
```
sudo echo enable,0x00ffffff > /proc/acpi/ibm/hotkey 
```

This won't work, since you are using sudo only for 'echo'

I'm at work but I think this should be working as expected:
```
echo enable,0x00ffffff | sudo tee /proc/acpi/ibm/hotkey
```

---

### Post by Denbert on 2009-11-26
> **Forlong said:**
> 

I'm at work but I think this should be working as expected:
```
echo enable,0x00ffffff | sudo tee /proc/acpi/ibm/hotkey
```

Worked Perfect on Lenovo T60 Type: 2007-63G :guitar:

---

### Post by apastuszak on 2009-11-27
Awesome!  Thanks for fixing my problem so easily!

---

### Post by mrufino1 on 2009-11-27
Cool! Just worked for me too. I found this while looking for something else, now I'm glad I did. I have a t41 that is being traded to someone else tomorrow that koala just went on yesterday, I'll try this and report back.

---

### Post by mrufino1 on 2009-11-27
Works on the t41 running 9.10!

---

### Post by sjpn on 2009-11-30
thanks! this works for me on my t60. it was annoying me for a long time!

---

### Post by gardel999 on 2009-12-02
> **rCXer said:**
> Wow that's brilliant!  The notification wasn't working for me and your method worked \\:D/ I had to become root by "sudo -i". Otherwise I got "permission denied"...

```

sudo -i
sudo echo enable,0x00ffffff > /proc/acpi/ibm/hotkey

```This has been a [long-standing bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357673?comments=all") on thinkpads and this might be the workaround needed.  Since you discovered this, could you post your solution in the bug report in the link?  I'm sure they'll appreciate it. Thanks!

This workaround works on my T43p / Ubuntu 9.10 too. Thanks!

---

### Post by drorata on 2009-12-06
For me, the following worked:

```
cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask

```

That is, once running this I got the controls and the indications. Both for the audio and for the brightness. But, once I restart I have to re-run the line above. How can I add it into the load sequence of the system, so I won't have to do it manually every time?

I'm running 9.10 on thinkpad R50e.

Thanks in advance,
Dror

---

### Post by shone.huang on 2009-12-20
> **juhaszjozsef said:**
> Hi all.
9.10 karmic: (using sysfs):
```
sudo cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask
```

This doesn't completely working on Karmic.
After reboot, the default hotkey_mask is restored and the screen indication is not working again.

---

### Post by pabc on 2009-12-29
ditto. the fix works until reboot - how do you set this command to passively run during startup?

---

### Post by zine92 on 2009-12-30
Hi, i am new to this Ubuntu and anyway, i am using a Lenovo w500, quite a lot of things not working in place. And yes, the mute button for me isn't working properly, firstly when i press mute, it mutes but the notifications doesn't indicate that and when i press mute the second time, still no sound untill i press vol up or vol down then i get my sound bad.

---

### Post by scoot1212 on 2009-12-30
This probably isn't the best way to accomplish this but I added 

cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask

to /etc/rc.local

This works for me on my T60 running 9.10.

Good luck and thanks to juhaszjozsef for figuring out the solution.

Scott

---

### Post by drorata on 2009-12-31
I can confirm - Seems like scoot1212's solutions works for me as well - for Thinkpad R50e.

UPDATE: I'm afraid that after reboot, things went wrong again.

---

### Post by ubsky on 2009-12-31
Seems unlikely that the volume buttons wouldn't work on such a relatively new  Thinkpad. But downloading the Thinkpad special button program through the  repository should do the trick. (tpb-0.6.4-2.3ubuntu1).

---

### Post by lrisan on 2010-01-17
> **juhaszjozsef said:**
> Hi all.

```
sudo cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask
```

Please confirm if the solution works on other thikpad models.



Hi!

Just want to confirm that that exactly this code worked on my Thinkpad T43p, running 9.10.

Thanks!

-lars

---

### Post by drorata on 2010-01-18
When applied manually it works perfectly. By manually, I mean invoking the command in console.

I tried to use the solution suggested by scoot1212, but it doesn't work.

How can one add such a line to the loading-up sequence of the system so it will be a default. Without the need to run it manually.

Thanks and have a nice day,
Dror

---

### Post by jimmyUT on 2010-01-18
Yes, I have the same problem.  It works great except I have to put it in the terminal every time I reboot.  I know there is a way of making it load somehow, but I am a newbie.

I  bought my T60 last week and before I reformatted the HDD, it was working every time it rebooted.  Now that I have reinstalled ubuntu it does not.

Does anyone have a permanent fix?

T60 with Karmic

---

### Post by jimmyUT on 2010-01-19
> **ubsky said:**
> Seems unlikely that the volume buttons wouldn't work on such a relatively new  Thinkpad. But downloading the Thinkpad special button program through the  repository should do the trick. (tpb-0.6.4-2.3ubuntu1).


OK, so how do I do that ???  It is not in the repository

---

### Post by jimmyUT on 2010-01-19
Ok, so I have the .deb file to make the Thinkpad buttons work, but how do I install it?

---

### Post by jimmyUT on 2010-01-19
Install this deb file and it will work... Apparently its a regression issue and this is from 9.04

Hope it works for all of you thinkpad users.[B]

hotkey-setup_0.1-23ubuntu7_i386.deb[/B]

---

### Post by juhaszjozsef on 2010-01-21
> **scoot1212 said:**
> This probably isn't the best way to accomplish this but I added 

cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask

to /etc/rc.local

This works for me on my T60 running 9.10.

Good luck and thanks to juhaszjozsef for figuring out the solution.

Scott

Thanks, updated the main post.

---

### Post by juhaszjozsef on 2010-01-21
> **ubsky said:**
> Seems unlikely that the volume buttons wouldn't work on such a relatively new  Thinkpad. But downloading the Thinkpad special button program through the  repository should do the trick. (tpb-0.6.4-2.3ubuntu1).

The buttons just work out-of the box.
I've probably forgot to mention it at the beginning of the thread.
We're trying to fix the notification issue (with notify-osd because of ubuntu)

---

### Post by [A]madeus on 2010-01-23
First of all, since below command gives solely a temporary solution
*cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask*
The volume notification will disappear after reboot your laptop.

Then Scoot1212 posted sth interesting;
> **scoot1212 said:**
> This probably isn't the best way to accomplish this but I added 

cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask

to /etc/rc.local

This works for me on my T60 running 9.10.

Good luck and thanks to juhaszjozsef for figuring out the solution.

Scott

It took me for awhile to understand what he meant.
sudo gedit /etc/rc.local
(for me it is freshly created.)
copy below line and paste to it.
*cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask*

now save and exit.
After reboot you will still get volume notification works as usual.

Let me know how's your result.
[i'm using IBM T60]

---

### Post by bartlby on 2010-01-25
works perfect with my x41t! on xubuntu/ 9.10!

tbp for me, tbp was needed to get the buttons - function, this workaround to get the buttons - work as visual-signal....

thanks!!!!

---

### Post by bartlby on 2010-01-25
> **bartlby said:**
> works perfect with my x41t! on xubuntu/ 9.10!

tbp was needed to get the buttons - function; this workaround to get the output of the buttons work as visual display signal....:P

thanks!!!!


Edit: bad englishskills sry

---

### Post by juhaszjozsef on 2010-03-16
I can also confirm the workaround on Debian Squeeze as well.

---

### Post by matt! on 2010-03-28
Works for me on my X31 from /etc/rc.local

Thanks!

---

### Post by juhaszjozsef on 2010-04-07
Solution also confirmed to work on Ubuntu 10.04 beta1

---

### Post by kolinab on 2010-04-15
> **'[A]madeus said:**
> First of all, since below command gives solely a temporary solution
*cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask*
The volume notification will disappear after reboot your laptop.

Then Scoot1212 posted sth interesting;


It took me for awhile to understand what he meant.
sudo gedit /etc/rc.local
(for me it is freshly created.)
copy below line and paste to it.
*cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask*

now save and exit.
After reboot you will still get volume notification works as usual.

Let me know how's your result.
[i'm using IBM T60]

Thanks so much for that post. I was close to getting the command right but needed someone to spell it out. Worked great, on my T60. Much better looking solution than the tpb solution that didn't stick after a reboot.

K

[edit] Now having tested some of my music files I find that I have to decrease the volume to somewhere in the 70 percent range to avoid distortion on my external speaker system. I discovered in alsamixer that the volume buttons affect PCM and master volume channels. Is this the normal behaviour for these buttons? I wonder if there is a way to lock an artificial maximum at 74% or whatever to prevent me from going into the 'distortion range' when I max the volume. 

Don't mean to derail the thread - sorry if this branches off topic. In any case it's nice to have the buttons working.

---

### Post by davidovp on 2010-07-15
A cleaner way to make this change survive reboot is to use the 'sysfsutils' package.

1) Install 'sysfsutils'

*sudo apt-get install sysfsutils*

2) Edit the file '/etc/sysfs.conf'

*sudo vi /etc/sysfs.conf*

3) Add the following line:

*devices/platform/thinkpad_acpi/hotkey_mask = 0x00ffffff*

To test it out, simply reboot the machine and the volume/mute  hotkeys should now work.

[Tested on a Thinkpad T60 w/ Ubuntu Lucid 10.04]

---

### Post by kirschjoghurt on 2010-09-08
davidop! it's worging great!

---

### Post by juhaszjozsef on 2010-10-01
Same issue on 10.10... :(
**Solution works on 10.10 as well!**

---

### Post by ibcrusn on 2010-10-24
I recently purchased a Thinkpad T60p and my volume buttons don't function as several have noted. I was able to get to the 2nd step in davidovp's post but I'm unable to edit or add anything. I realize this may be getting off topic but I'm having issues with the CLI, any assistance would be appreciated.

---

### Post by Denbert on 2010-10-24
> **ibcrusn said:**
> I recently purchased a Thinkpad T60p and my volume buttons don't function as several have noted. I was able to get to the 2nd step in davidovp's post but I'm unable to edit or add anything. I realize this may be getting off topic but I'm having issues with the CLI, any assistance would be appreciated.

I have a T60 - type 2007-63G - I installed Ubuntu 32-bit Desktop 10.10 and Everything works - even the Mobile Broadband USB Key I have from Huewei :guitar:

Try make a clean install of this version.

---

### Post by ibcrusn on 2010-10-24
I'll give it a whirl. At some point in the near future I plan to set it up as a dual boot but I'd like to make sure it'll all work on its own.

mine is a 8742-BB4 (wide screen)

---

### Post by Denbert on 2010-10-24
> **ibcrusn said:**
> I'll give it a whirl. At some point in the near future I plan to set it up as a dual boot but I'd like to make sure it'll all work on its own.

Why use Dualboot, when you have Ubuntu 10.10?

If you need Windows try Virtualbox, It runs better than direct on the Hardware. Make an ISO of your windows install CD and you will be impressed over the installation speed.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by ibcrusn on 2010-10-26
I tried a clean re-installation an still no change on the sound buttons. I do get a fatal message during boot up that I'll post up for guidance.

I'll read up on virtualbox, we'll see.

---

### Post by Denbert on 2010-10-26
> **ibcrusn said:**
> I tried a clean re-installation an still no change on the sound buttons. I do get a fatal message during boot up that I'll post up for guidance.


Hmm - strange, as Ubuntu since 9.10 has worked out of the box on my Lenovo T60 type 2007-63G

Have you tried the alternate installer? Some are reporting better and more stable installation with the alternate installer.

---

### Post by ibcrusn on 2010-10-26
Well after the second install of 10.10 and no change I elected to install a known clean copy of 9.10 with the same result.

I tried davidovp's steps and it returned:
> E: Couldn't find package sysfsutils

For now I'll reinstall Maverick and deal with it as it doesn't effect any other portion of the OS so far that I've noticed.

---

### Post by Karut on 2010-11-07
When I unmute I have to press either the higher or lower volume button to have sound on again. Any fix for that? Thanks a lot :)

---

### Post by Karut on 2010-11-11
your volume notification works fine except when I unmute I have to press  either the higher or lower volume button to have sound on again. Any  fix for that? Thanks a lot :smile:

Ubuntu 10.04 
T60

---

### Post by 47_MasoN_47 on 2010-11-20
Davidovp's fix worked on my Thinkpad G41 also.  The buttons worked out of the box just fine on 10.04, but for whatever reason they stopped working on 10.10.  With that simple fix I now have my volume buttons working on 10.10 :D

Thanks Davidovp!

---

### Post by vtdstein95 on 2010-12-09
The davidovp method confirmed working on an X60 running 10.10

---

### Post by gilbertoiki2 on 2011-01-09
> **matt! said:**
> Works for me on my X31 from /etc/rc.local[[COLOR=#000000]Thanks[/COLOR]](http://www.****************.com/zen-video-format/convert-wmp-video-to-zen-format.html)!Thanks for your reply! I'll follow what you said to take a try, I've got the same problem.

---

