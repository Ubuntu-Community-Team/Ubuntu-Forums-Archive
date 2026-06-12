---
title: "Ubuntu is killing your hdd!"
date: 2007-07-24
forum: Hardware &amp; Laptops
---

### Post by schultz on 2007-07-24
Yes, this is it. Ubuntu is killing my (and eventually yours) hard drive!

My machine is a HP ze4950 laptop. I have ran Kubuntu in it for a day only, since I noticed a very grave bug.

It happens Ubuntu (and Gentoo, as far as I can tell) kills your hdd's. This is because upon power off, the kernel sends the FLUSH CACHE message to the disk to flush the disk write cache, which cause it to spin up. Then it suddenly shuts down making no call to the STANDBY signal to make the disk stop. The result is that the hdd keeps spinning as the power is off. Modern hdd's (yours, if it works after rebooting), can prevent such damage by taking the head off the disk surface just after power down so it does not hurt the disk in such situation. This is called an emergency unload. Technical specifications say doing this instead of the regular standby can reduce the drive's life time by about a rate of thrity (30) times. The symptoms of this is a weird noise upon shutdown (power off). It is like a "pop"!

All of this is known, I believe. Windows XP is as bad, it does the same mistake. The problem, though, is that Windows came with a HP drives DVD which loaded some files in the system and, after that, the noise and the emergency unload stopped. This DVD has hardware drives which does the right thing with my disks.

I hate Microsoft and Bill Gates. The problem is that only XP can turn down my disk properly. As soon as this bug is fixed, I will use Ubuntu again. Linux (not exactly Ubuntu) is very high quality software and I really desire using it, but I can not afford paying my hdd's life as price.

The problem is that I began using Ubuntu because in the laptop team testing page it said that this laptop is well supported by feisty fawn. It is not, feisty kills my hdd. And that is not only in power off, but in suspend-to-ram and hibernate. Hibernate does three "pop"'s!

Such a serious bug must be fixed! It is thrashing hdd's all over the world!

Ok, it is true that as the software is free, the community fixes it if it wants and gives us no warranty. This is acceptable. What is not acceptable is the lie that Ubuntu Feisty Fawn is ok to use in laptops. Lying is not nice! And this is stamped in ubuntu.org.

(Sorry if mistaken.)

---

### Post by tschneiter on 2007-07-24
It sounds like you know quite a lot about the proper shutdown procedures... why not have a poke around on your own? 
This is something that, if it is confirmed, would be really nice to have fixed. I like my laptop's hdd :)

---

### Post by schultz on 2007-07-24
The knowledge I gathered is fruit of a 2 hours search in Google and in the development forums.

I know nothing about low-level linux or computing.

I am just listing my symptoms and performing a diagnosis.

The point is, that noise is not healthy and should be fixed.

---

### Post by LaRoza on 2007-07-24
My Ubuntu box doesn't do that, and I have rebooted, and shutdown the machine many times. 

No noise was noticed on any of those times. 

Are there any instances of Ubuntu killing an hdd? Or is it just speculation?

---

### Post by schultz on 2007-07-24
Apparently that only happens in laptops.

I do not know why. Perhaps it is because in PC's, the noise goes within the machine, so you can not listen.

---

### Post by jacob01 on 2007-07-24
then just dont use stand by then

---

### Post by Old Pink on 2007-07-24
Mine doesn't do that, on any of my systems. And if you think XP does this too, surely thousands of hard drives are doing it hundreds of times per day? There'd be a much higher destruction rate. I think you're reading up on FUD bullcrap. :)

---

### Post by kostkon on 2007-07-24
My friend, I want to thank you for your interest in Open Source, and in Ubuntu particularly. 

Thus, if you believe this is happening indeed, it would be very good if you could fill a bug report at Launchpad. It seems that this is a kernel bug, but maybe if you report it, the Ubuntu kernel team will try to research and fix it or at least send it upstream.

In case you want to know more about bug reporting, you can get info [here]("https://help.ubuntu.com/community/ReportingBugs").

To say my opinion, I am not sure I can believe that this problem is so widespread; maybe it is happening only in some cases.

---

### Post by schultz on 2007-07-24
I never said the problem is widespread, just that Ubuntu kills hdd's, like mine.

I heard that in Dapper this does not happen, it began in Edgy and Feisty Fawn.

I also heard it concerns mostly laptops.

WinXP does it only in laptops (my family's PC does not do it). But for those there is those driver DVD's. HP's DVD solve the problem in WinXP. So few people might come across this bug.

Nevertheless, I can not understand how the laptop testing team said my computer was ok with Ubuntu in spite of the loud noises.

I shall fill a bug report. I took Ubuntu out of the PC, but shall put it in again once the bug is fixed. Of course, if I can make Gentoo function properly then I shall go for Gentoo instead.

Thanks for the answers, although they do not solve the vicious problem.

---

### Post by schultz on 2007-07-24
Man, reporting bugs is so difficult, non intuitive!

Is not there a way to do it easier?

I also can not send debugging results because this happens in power off and I have taken Ubuntu off.

---

### Post by JonD25 on 2007-07-24
I think I might be having the same problem on my Dell D600. Ever since I upgraded to Feisty, I noticed whenever I shut down, it would make a weird sound. I recognized it as the same sound my hard drive makes when I need to do a hard shut down by holding down the power button, like it's spinning down unexpectedly. This never happens with my XP partition, only Ubuntu. I even remember it going away for a brief period of time, but then another kernel upgrade seemed to bring it back. I hope this isn't killing my HD. I really don't like using XP at all and don't want to have to switch if it is.

---

### Post by kostkon on 2007-07-24
> **schultz said:**
> Man, reporting bugs is so difficult, non intuitive!

Is not there a way to do it easier?

I also can not send debugging results because this happens in power off and I have taken Ubuntu off.

Why not visit the *#ubuntu-bugs* channel at * irc.freenode.net* and tell them your case. I believe they'll be more than happy to help you.

---

### Post by bapoumba on 2007-07-24
To the OP: would you consider sharing some of the links you found in google about this? Thanks.

---

### Post by srt4play on 2007-07-24
Yes please share the links to the info you found in your research.

I have a new Compaq laptop and it makes a "pop" when suspending, not sure if it does it on a shutdown.  I always thought it was the speakers.

---

### Post by schultz on 2007-07-24
Yes, I sure shall send some of the links.

More than anyone, I too want to have this fixed so that I can run Ubuntu again (I have removed it).

Those were found by typing **linux "emergency unload"**, **Ubuntu "emergency unload"** and **ubuntu hd noise power off** in Google.

[http://linux-ata.org/shutdown.html](http://linux-ata.org/shutdown.html)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/72765](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/72765)
[https://bugs.launchpad.net/linux/+bug/63937](https://bugs.launchpad.net/linux/+bug/63937)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/63937/comments/22](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/63937/comments/22)

They talk about Dell and Compaq laptops, but none talk about mine.

I really wish to install Ubuntu back, I really liked it, (kate was so nice). I just entered university vacation and need to program (then I just put XP). I really, again, wish that this bug is solved.

---

### Post by bapoumba on 2007-07-24
[http://bugzilla.kernel.org/show_bug.cgi?id=7674]("http://bugzilla.kernel.org/show_bug.cgi?id=7674")

I'm currently reading this. Be aware I do not know much about kernel and stuff like this...
(BTW, I have a 2 years old Acer and an old Fujitsu Siemens, and did not notice this problem myself from warty up to gutsy. I know, that does not mean much ^^).

Edit: looks like its been fixed in the 2.6.22 kernel. Can some one confirm it? See comment #16 in the above link.

Gutsy:
```
~ $ uname -a
Linux yeti 2.6.22-8-generic #1 SMP Thu Jul 12 15:59:45 GMT 2007 i686 GNU/Linux
```

---

### Post by asmoore82 on 2007-07-24
um... wow... 

thank goodness linux is Stable and doesn't need to shutdown all the time like some other OSes

---

### Post by fd9_ on 2007-07-24
This is pretty scary, actually, because my system always makes a strange noise right before it shuts off. Does it sound similar to a system beep? The best way to describe it is that it sounds like a short squeak. I have a ThinkPad T61 and I'm running the latest 2.6.22 kernel, too.

---

### Post by JonD25 on 2007-07-24
> **fd9_ said:**
> This is pretty scary, actually, because my system always makes a strange noise right before it shuts off. Does it sound similar to a system beep? I'm running the latest 2.6.22 kernel, too.

If mine is indeed doing what is mentioned here, it should sound like a click, then audibly hearing your hard drive spin down. It's the exact same sound as when you hold down your power button for 4 seconds.

---

### Post by schultz on 2007-07-24
Yes, it sounds much like when you do a hard reset.

Is it true that in kernel 2.6.22 the bug is fixed? Can someone with a laptop model as close to a HP Pavilion ze4950 confirm it?

If it is fixed, how do I install a new kernel in Ubuntu? In Gentoo it was quite easy, but how is it done under Ubuntu.

Additionaly, I see hibernating does three "clicks", have anyone noticed it?

So, ok, has anyone used Feisty Fawn with this 2.6.22 kernel in a SATA drive (sd) and did not hear the sound?

Let us help each other.

---

### Post by lisati on 2007-07-24
> **srt4play said:**
> Yes please share the links to the info you found in your research.

I have a new Compaq laptop and it makes a "pop" when suspending, not sure if it does it on a shutdown.  I always thought it was the speakers.

I've heard a "click" on startup on my Toshiba laptop that seems to come from the speakers. I wonder if this could be something to do with the sound drivers loading or unloading.

---

### Post by Depressed Man on 2007-07-24
Wow, appears to be a serious issue. If this is a bug, and it's fixed in .22 is there any idea when that update will come?

---

### Post by schultz on 2007-07-24
I hope soon.

Can some developer give us a clue?

---

### Post by hardKNOXbz on 2007-07-24
i noticed that sound the day i installed ubuntu, thought it was my fan or something

---

### Post by atlfalcons866 on 2007-07-24
here is a anthor bug report
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810)

---

### Post by schultz on 2007-07-24
In this bug report it is said that if the script

[B]#!/bin/sh
echo 1 > /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown
[/B]

is put in **/etc/rc0.d/S00hdd-shutdown-workaround**, it is executed upon startup and in reboot, the hdd turns off quietly.

Can anyone run that script and test if it works?

Remember, simply putting it there shall not do the job, it must be executed.

Any HP ze4950 or similar please give me feedback.

---

### Post by tombott on 2007-07-25
I get this noise on my laptop, and have had one HDD fail.

My laptop is an Acer Aspire 9500 and have been running Ubuntu on it since 4.10.

If I boot with an Windows XP CD and start the setup process then cancel and shutdown, I don't get the noise.
The same can be said if I use a Windows XP PE CD.

I don't however get these noises on any of my 4 Ubuntu workstations.

---

### Post by 3rdalbum on 2007-07-25
If I suspend-to-ram on Ubuntu, I get a sound that is like the hard drive spinning down with some object in contact with the platter. I have had that since Breezy, but never thought much of it (I don't get the same in Win XP SP2).

From now on, I won't suspend - I've no need to do that anyway.

---

### Post by weth on 2007-07-25
I have a Dell Inspiron 2200 and I can confirm that upon turning off the machine the same sound can be heard. I have always thought it to be not normal, but since I very rarely swich it off I haven't felt the urge to bother. 

I always type
# hdparm -B254 /dev/sda
in order to stop other, similar "click" sounds while running

Please let us know if there is a fix to this issue!

---

### Post by schultz on 2007-07-25
The other similar clicks are a result of the system flushing the write cache to the disk.

There are some programs, which are not polite, that periodically syncs the disk. Those are mainly system loggers.

For laptop users, they can be a pain in the back. I kill them both and tell them never to start at boot. Also, enable laptop-mode by editing the configuration file. Enable it both in AC power and when using batteries.

This should get rid of this softer noise, generated by cache flushs.

---------------------------------------------------------------------------

About the other problem, has anyone tested putting the script there. Do not forget to run chmod +x, otherwise it will not work.

Do post feedback.

---

### Post by Depressed Man on 2007-07-25
I'm still confused about this. How do you know if your laptop suffers from this problem? Or is it all Ubuntu installs on laptops? Is it a clicking sound that always happens?

---

### Post by Brachabre on 2007-07-25
On my Dell Inspiron 9400 laptop, the speakers make a pop at shutdown and the hdd makes a click then flushing sound at shutdown too. I hope that it isn't an ubuntu problem or else I think I would put XP back on (hoping XP wouldn't do it too).
 
1.) So the speaker pop isn't actually the hdd correct?
 
2.) Isn't it normal for the hdd to have a click and flush sound (after shutdown, isn't this sound just the hdd spinning down?)

---

### Post by georgeguitar on 2007-07-25
Hello friends, could you find an answer to this post?
It is true that Ubuntu kills your HHD?

---

### Post by ncc74656 on 2007-07-25
On both WinXP and Kubuntu i can hear scratching shortly before power off. My laptop is old centrino asus with new HDD Seagate Momentus ST980815A. Can anyone tell me if this hdd is affected? It has 5 years seagate warranty, i don't want it to die after that time.

Thanks Lukasz

---

### Post by Spam Banjo on 2007-07-25
> **asmoore82 said:**
> um... wow... 

thank goodness linux is Stable and doesn't need to shutdown all the time like some other OSes

He-he!!! Now now!!!

By the way, I think you meant O$s!!! :P

---

### Post by bapoumba on 2007-07-25
I've been following the thread, but I do not know much about kernels and hard drives.
I'm asking the staff if they have an idea about what to recommend.
In the mean time, have any of you posted in the LP bug reports? If so which ones? Thanks.

---

### Post by Depressed Man on 2007-07-25
Hmm I don't hear any clicking when I shutdown or start Ubuntu. But when I start my laptop up (as in I power it on) before it gets to the BIOS splash screen it does a hiccup type clicking noise. It sounds like three clicks though. But I think this has always been happening? It's been a while since I use GRUB as my boot loader.

---

### Post by schultz on 2007-07-25
I have heard those three clickings while hibernating.

What about the script?

---

### Post by Depressed Man on 2007-07-25
I haven't tried the script, since it doesn't seem to be related to Ubuntu. Since it only occurs when my laptop is booting itself up. It's the hiccup then it shows the BIOS splash, then it's grub 1.5 loading then it lists my OSes with a 30 second timer.

---

### Post by schultz on 2007-07-25
Which version of Ubuntu are you using? Which kernel? Is your machine a laptop?

This (usually) happens during turn off, not boot. The script will do no good for you, then.

---

### Post by Depressed Man on 2007-07-25
Ubuntu 7.04 Feisty Fawn 
2.6.20-16-generic

On a Sony VAIO (some VGN model). I'm going post a link to this thread in the Sony VAIO thread  to see if anyone else has this problem.

[http://ubuntuforums.org/showthread.php?p=3079299#post3079299](http://ubuntuforums.org/showthread.php?p=3079299#post3079299)

edit: Added a link to the VAIO thread.

---

### Post by Wiebelhaus on 2007-07-25
> **tombott said:**
> I get this noise on my laptop, and have had one HDD fail.

My laptop is an Acer Aspire 9500 and have been running Ubuntu on it since 4.10.

If I boot with an Windows XP CD and start the setup process then cancel and shutdown, I don't get the noise.
The same can be said if I use a Windows XP PE CD.

I don't however get these noises on any of my 4 Ubuntu workstations.

Many more of these stories like this guys and this could be disastrous when this hits the tech news.

---

### Post by schultz on 2007-07-25
Exactly, so we should fix that up instead of putting it away.

Hiding or forgetting about the fact will not do any good, we have to fix the problem.

It is a serious one, but it must not be difficult to solve.

---

### Post by schultz on 2007-07-25
You are not listening the bug, using an old kernel or having your hardware mapped as /hda instead of /sda. Or perhaps you have solved the bug or is a pretty lucky man.

(Although Gentoo recognised my hdd as /dev/hda, it still had that problem).

---

### Post by Depressed Man on 2007-07-25
err? Are you replying to mine? My harddrive was listed as sda2 (though I just renamed the folder to Vista since I was getting tired of seeing sda2 listed under media). Though I thought I was already on the latest kernal for Feisty?

---

### Post by schultz on 2007-07-25
Well, something I thought about right now is the testing the Ubuntu team made.

In the laptop testing team page, in which class is your machine?

---

### Post by Depressed Man on 2007-07-25
It's not listed here [https://wiki.ubuntu.com/LaptopTestingTeam/Sony](https://wiki.ubuntu.com/LaptopTestingTeam/Sony)

But it's model name is 

VGN-FE880E

I wonder if it's an issue with GRUB.. I could always remove GRUB and try Vista's BCD loader. But somehow I think it's been doing this since I got it back in March. Which was even before I installed Ubuntu, Grub, or even tried Wubi yet. Always thought it was normal behavior. 

Shame I can't record sound and send it.

---

### Post by IntuitiveNipple on 2007-07-25
I'm on the ACPI kernel-development team and am also developing a kernel driver for Sony Notebook Control. A reference to this issue was posted in the thread about the Vaio SNC.

I'm currently working on fixing various suspend/resume issues so I'll add this to my ToDo list.

Without doing more research, but based on what has been reported here about when the symptoms first started, I would suspect it is related to the switch to libata to manage parallel and serial ATA disks.

I'll do some digging into the libata source-code and see what I can find out.

---

### Post by atlfalcons866 on 2007-07-25
is this fixed in the gutsy kernel?

---

### Post by schultz on 2007-07-25
I hope so, I really do.

---

### Post by qamelian on 2007-07-25
> **schultz said:**
> Apparently that only happens in laptops.

I do not know why. Perhaps it is because in PC's, the noise goes within the machine, so you can not listen.

Doesn't happen on any of the laptops I use to run Ubuntu. I have several of variouos models in my test lab right now and they all power down cleanly. They all suspend and hibernate fine, as well.

It may be specific to certain hardware.

---

### Post by schultz on 2007-07-25
Can you post the their model, hardware and software version?

---

### Post by schultz on 2007-07-25
Perhaps you could help us.

What is it that you did?

---

### Post by IntuitiveNipple on 2007-07-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/67810](https://bugs.launchpad.net/ubuntu/+bug/67810) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I asked Ben Collins about this; here's what he said:
> <BenC> basically libata, because it uses the scsi disk driver, isn't sending this signal because some drives (especially real scsi ones) shouldn't always get them
<BenC> like disks in an enclosure connected to more than one machine
<BenC> I believe 2.6.22 resolves this issue though
<BenC> with the IDE disk drive, it's safer to assume to always send this signal
<BenC> *IDE disk driver

So the fix should be in the kernel used in Gutsy, and the current workaround scripts should be used for Feisty and Edgy.

---

### Post by Brachabre on 2007-07-25
I use a Dell Inspiron 9400 laptop. Could someone clarify if Dapper Drake is affected by this? I hear different HDD noises during shutdown and all mine sound exactly like the ones previously mentioned. Especially the final POP!!!

Thanks!

---

### Post by Depressed Man on 2007-07-25
> **IntuitiveNipple said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/67810](https://bugs.launchpad.net/ubuntu/+bug/67810) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I asked Ben Collins about this; here's what he said:

So the fix should be in the kernel used in Gutsy, and the current workaround scripts should be used for Feisty and Edgy.

Interesting. Still doesn't explain why my laptop makes the harddrive clicking noise at startup lol. I'm guessing because it's powering up. Then again I heard some people comparing it to the sound when you have to do a hard reboot (holding power) and it doesn't sound anything like that when I had to hard reboot my laptop one time. That sound sounds more like a laser to me lol.  So I'm likely worrying over nothing? But I'll apply the script anyway.

---

### Post by ThrobbingBrain66 on 2007-07-25
I don't mean in any way to diminish the importance of this problem, but does anyone else think the title of this thread is a bit alarmist?  Granted, I have not had this issue on my Toshiba laptop (from Breezy to Gutsy), but reading the first 3 pages and skimming the rest, I counted one person who had a laptop hard drive fail and there's no real evidence that this problem caused that.

I think everyone needs to take a deep breath, apply the workaround if you need/want to and move along.  As someone earlier in the thread mentioned, if this was such a widespread problem, the forums would be flooded with complaints about dead hard drives.

Such a sensationalist title gets a post read but can also lead to all sorts of unnecessary negative attention.

---

### Post by Tzalidar on 2007-07-25
I have also experienced this problem with 7.04 on my Fujitsu Siemens Amilo M1425.

The following workaround did the trick for me:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60)

---

### Post by Depressed Man on 2007-07-25
> **ThrobbingBrain66 said:**
> I don't mean in any way to diminish the importance of this problem, but does anyone else think the title of this thread is a bit alarmist?  Granted, I have not had this issue on my Toshiba laptop (from Breezy to Gutsy), but reading the first 3 pages and skimming the rest, I counted one person who had a laptop hard drive fail and there's no real evidence that this problem caused that.

I think everyone needs to take a deep breath, apply the workaround if you need/want to and move along.  As someone earlier in the thread mentioned, if this was such a widespread problem, the forums would be flooded with complaints about dead hard drives.

Such a sensationalist title gets a post read but can also lead to all sorts of unnecessary negative attention.

True, I'm just worried cause I'd hate to send my laptop back to Sony to get a HDD replaced. That and I've never worked with a laptop's internals yet. Then again if it happens, it happens.

---

### Post by stchman on 2007-07-25
> **schultz said:**
> Yes, this is it. Ubuntu is killing my (and eventually yours) hard drive!

My machine is a HP ze4950 laptop. I have ran Kubuntu in it for a day only, since I noticed a very grave bug.

It happens Ubuntu (and Gentoo, as far as I can tell) kills your hdd's. This is because upon power off, the kernel sends the FLUSH CACHE message to the disk to flush the disk write cache, which cause it to spin up. Then it suddenly shuts down making no call to the STANDBY signal to make the disk stop. The result is that the hdd keeps spinning as the power is off. Modern hdd's (yours, if it works after rebooting), can prevent such damage by taking the head off the disk surface just after power down so it does not hurt the disk in such situation. This is called an emergency unload. Technical specifications say doing this instead of the regular standby can reduce the drive's life time by about a rate of thrity (30) times. The symptoms of this is a weird noise upon shutdown (power off). It is like a "pop"!

All of this is known, I believe. Windows XP is as bad, it does the same mistake. The problem, though, is that Windows came with a HP drives DVD which loaded some files in the system and, after that, the noise and the emergency unload stopped. This DVD has hardware drives which does the right thing with my disks.

I hate Microsoft and Bill Gaytes. The problem is that only XP can turn down my disk properly. As soon as this bug is fixed, I will use Ubuntu again. Linux (not exactly Ubuntu) is very high quality software and I really desire using it, but I can not afford paying my hdd's life as price.

The problem is that I began using Ubuntu because in the laptop team testing page it said that this laptop is well supported by feisty fawn. It is not, feisty kills my hdd. And that is not only in power off, but in suspend-to-ram and hibernate. Hibernate does three "pop"'s!

Such a serious bug must be fixed! It is thrashing hdd's all over the world!

Ok, it is true that as the software is free, the community fixes it if it wants and gives us no warranty. This is acceptable. What is not acceptable is the lie that Ubuntu Feisty Fawn is ok to use in laptops. Lying is not nice! And this is stamped in ubuntu.org.

(Sorry if mistaken.)

So you are saying that when you shut your laptop off the hard drives keeps spinning away.  It does not do that.  Otherwise the next time I turn my laptop on the battery would be dead.  I think you are reading too much M$ propaganda.

---

### Post by schultz on 2007-07-25
I did not mean to make a sensacionalist title or whatever, specially because I hate sensacionalism.

What I did was to report a bug (a serious one) which indeed damages hdd's. Technical documents suggests a fall from 600.000 power off's to 20.000 power off's in the lifetime of the hdd, and that got me worried.

And to the last poster: You did not understand! The disk keeps spinning due to inertia. Yes, the disk was spinning and keeps spinning by inertia until friction (or some other factor) brings it down. Of course, it does not waste batteries because the power is off.

I still have another problem. How is it that I know that if I install Kubuntu once more, the problem shall stop. This is specially important, because a failure in the correction of the error shall have me installing an entire OS for nothing.

So can any HP ze4950 or similar tell me if those workarounds really work?

---

### Post by Rui Pais on 2007-07-25
> **schultz said:**
> I did not mean to make a sensacionalist title or whatever, specially because I hate sensacionalism.

What I did was to report a bug (a serious one) which indeed damages hdd's. Technical documents suggests a fall from 600.000 power off's to 20.000 power off's in the lifetime of the hdd, and that got me worried.

Well, i personally find it a little sensationalist too.
Killing hdd could be something like; *may* be harm hdd or reduce timelife of hdd... 
One hardly see threads on dead drives around (or any other forum).

Anyway if an HD has a lifetime shorted to 20 000 and user powers off twice a day, that make a a period of 27 years!! 
I doubt anyone will use an HD for more then 10 years.

But yes, it's something that should be look seriously anyway.

---

### Post by schultz on 2007-07-25
Ok, I apologise for the title. It was just because I was worried.

But anyway, can people test the script and give feedback.

Tzalidar told it was alright, anyone else?

---

### Post by ThrobbingBrain66 on 2007-07-25
> **stchman said:**
> So you are saying that when you shut your laptop off the hard drives keeps spinning away.  It does not do that.  Otherwise the next time I turn my laptop on the battery would be dead.  I think you are reading too much M$ propaganda.

I think what he was saying is that the cache flush never gets a chance to finish or stop itself before power is lost.  This causes some sort of hardware issue that severely shortens the life of a hard drive

---

### Post by IntuitiveNipple on 2007-07-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/67810/comments/49](https://bugs.launchpad.net/ubuntu/+bug/67810/comments/49) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The fix is already done in the mainline kernel. You can read about it starting from the launchpad link above. As far as I am aware there isn't a backport of the fix to 2.6.20 (Feisty) so far at least.

---

### Post by schultz on 2007-07-25
So basically what I have to do is to change some system files.

Is it possible to explain how to make my computer running under Kubuntu Feisty behave correctly in shutdown?

---

### Post by georgeguitar on 2007-07-25
Hi friends I found the solution to this problem trying the solution previously posted and published on this page: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810")

In this other page there is the same solution:
[http://www.weiqiang.info/2007/05/feisty-hdd-noise-and-tty-problem.html]("http://www.weiqiang.info/2007/05/feisty-hdd-noise-and-tty-problem.html")

And it works with my Acer Aspire 3680 with a very small modification, basically what I did was this:

[I]Make a file at /etc/init.d/ called hdd-shutdown-workaround

#!/bin/sh
echo 1 > /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown #list all the HDDs you have
#EOF

sudo chmod +x hdd-shutdown-workaround
sudo ln -s /etc/init.d/hdd-shutdown-workaround /etc/rc0.d/S00hdd-shutdown-workaround
[/I]
This is the solution from the page above but my stop_on_shutdown file was at /sys/class/scsi_disk/ instead of /sys/class/scsi_device/ and it works, the strange sound has gone.

---

### Post by Depressed Man on 2007-07-25
So I assume (base on that read on the launchpad bug) that if you run. /sys/modules/libata/parameters/spindown_compat

and get 

No such file or directory


Then you don't suffer from this problem?

---

### Post by qsr.nrwn on 2007-07-25
I just have read all the thread... 

I have been experimenting the same trouble under feisty... (runs in a Inspiron 9400 [MP061]) And I thought that that clicking noise came from the speakers... So I decided to try the workaround, and it fixed that clicking sound...

Thanks for the workaround

---

### Post by fredj on 2007-07-25
I don't think the title was too alarmist. If someone asked me to choose a hdd which would only last for an
average of 20000 shutdowns or one which would last for an average of 60000 then I know which one
I would choose. 
The workaround script works on my Samsung Q35 notebook, so thanks to the people who provided it.
I had noticed the noise myself because I dual boot with winxp and linux was obviously noisier
when shutting down the hard disk.

---

### Post by Depressed Man on 2007-07-26
I still haven't figured out if this effects everyone using the pre-patched kernal, or just certain computers. Because it seems some people aren't effected by it, (that or we can't tell that we have the problem).

---

### Post by schultz on 2007-07-26
I built courage and reinstalled kubuntu.

The installation was smooth (despite strange noises comming from the CD).

I then tried to set the flag in /sys/class/0\:0\:0\:0/stop_on_shutdown. The file was write-protected.

No problem, I managed somehow to remove it (even sudo was not working). Then I wrote 1 to it.

I tried only power off until now (the others will be tested in the afternoon). The power down was so smooth not even XP would do better. No emergency unload. Everything was excelent!

The workaround was a fix for me.

I  must thank everyone that helped me doing this.

The nicest thing about using linux rather than M$ is that you can ask for help and people will answer. You can also configure your system and customize it to your needs. Again, thanks to everyone.

I shall be here to help with my (short) experience. Let us make no hdd's be burnt and no emergency unloads done.

Now, its M$'s hdd's which shall burn faster, since M$ is so unstable hard resets are needed very often. Blue screens of death are what kills hdd's!

Thanks again, and best luck to everybody.

---

### Post by wotringmw on 2007-07-26
I used the patch at
[(https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60)"][https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60)]("[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60)
and I don't have a popping sound anymore.

Specs:
Dell Inspiron E1705
Kubuntu 7.04
Kernel 2.6.20-16-generic

---

### Post by JonD25 on 2007-07-26
> **georgeguitar said:**
> Hi friends I found the solution to this problem trying the solution previously posted and published on this page: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810")

In this other page there is the same solution:
[http://www.weiqiang.info/2007/05/feisty-hdd-noise-and-tty-problem.html]("http://www.weiqiang.info/2007/05/feisty-hdd-noise-and-tty-problem.html")

And it works with my Acer Aspire 3680 with a very small modification, basically what I did was this:

[I]Make a file at /etc/init.d/ called hdd-shutdown-workaround

#!/bin/sh
echo 1 > /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown #list all the HDDs you have
#EOF

sudo chmod +x hdd-shutdown-workaround
sudo ln -s /etc/init.d/hdd-shutdown-workaround /etc/rc0.d/S00hdd-shutdown-workaround
[/I]
This is the solution from the page above but my stop_on_shutdown file was at /sys/class/scsi_disk/ instead of /sys/class/scsi_device/ and it works, the strange sound has gone.

I used this and tested it once, and it seems to be working. Thanks! I'm using a Dell Latitude D600 with kernel 2.6.20-16-generic.

---

### Post by schultz on 2007-07-26
Actually, I tested suspending the computer and the noise is still there.

Guess no more suspends for me.

---

### Post by JonD25 on 2007-07-26
> **schultz said:**
> Actually, I tested suspending the computer and the noise is still there.

Guess no more suspends for me.

Oh, yeah, I don't ever suspend, so I don't even know if that was a problem for me to begin with. Just shutting down. I haven't tried suspending. My D600 always was kinda fickle about suspending, so I just usually never do it.

---

### Post by schultz on 2007-07-26
And just by the way, I am a Kubuntu user. I can not find any decent hard drive monitor. In windows I used to have hdd life monitoring my hdd. But now I can not find even one monitor.

Can someone help me with this?

---

### Post by schultz on 2007-07-26
Ah, and also by the way, I am having an issue with laptop-mode-tools.

In KMenu->System Setting->Advanced->System Services I can see laptop-mode-tools is default to begin on boot. Nevertheless it does not.

I tried editing /etc/laptop-mode/laptop-mode.conf but no success. Then I ran the script in /usr/sbin/laptop_mode and it started, since the result for cat /proc/sys/vm/laptop-mode is 2. But still the system services do not show it running. Can someone help?

I still get the frequent noises in the hdd, despite having killed syslogd and klogd,

---

### Post by dabl on 2007-07-26
> **Depressed Man said:**
> 
I still haven't figured out if this effects everyone using the pre-patched kernal, or just certain computers.


Yeah, I'm with the Depressed guy -- does this affect ALL sdxx hard drives, or some subset that are only in laptops?  I've got SATA drives running Feisty in a desktop/tower -- should I be installing the stop_on_shutdown fix?

---

### Post by hessiess on 2007-07-26
i dont hear any pops wen shuting down, becose of what i use the laptop for suspending is the only option. but i do ceep getting bad filesystem errors. however thay may be cased buy the ext3 windows drivers, and it dus tend to be after booting windows. although not alwase

---

### Post by schultz on 2007-07-26
I tried hibernating and the hdd did an emergency unload.

How come some of us can suspend correctly and other can not?

---

### Post by Depressed Man on 2007-07-26
> **hessiess said:**
> i dont hear any pops wen shuting down, becose of what i use the laptop for suspending is the only option. but i do ceep getting bad filesystem errors. however thay may be cased buy the ext3 windows drivers, and it dus tend to be after booting windows. although not alwase

It's likely caused by Windows not shutting down cleanly. I use to have the software/driver? to read my ext3 drive as an ext2 drive (they're similar, ext3 just has journaling). But whenever Windows didn't shutdown cleanly or Dr. Watson made it unusable and I went to load Ubuntu the file system had to be checked.

And suspend is a difficult issue. It took forever to figure out on my laptop, and I only got it fully working with Intuitive Nipple's help (since he's working with the Sony VAIO dsdt). But the first issue most people have is the swap size. Mine didn't work when it was 2 GBs (my RAM is 2 GBs in my VAIO). But once I set it to 3 GBs it worked. But the sound didn't (then that's where Intuitive Nipple helped me).

---

### Post by hessiess on 2007-07-26
suspend and hibonate work perfectly without any tweking on my computer hp dv2000, just need to fix this filesystem errors, i ceep loosing work:( windows never shuts down clenly, regulaly blue screens, often refuses to shut down. dont rilly need it anymore tho

---

### Post by Depressed Man on 2007-07-26
Just unmount the Linux harddrive (whatever format it is) from Windows. Then if Windows doesn't shut down cleanly then it shouldn't matter for the Linux one.

---

### Post by schultz on 2007-07-26
I will just give up suspending or hibernating. Guess turning on and off is enough.

I wish I could do that, though.

Windows used to do it cleanly and fast, without any issues in my laptop.

---

### Post by Depressed Man on 2007-07-26
You say used as in.. it use to do that? Because if Windows is having trouble too then we really have a serious issue on hand! 

I still don't think my laptop is making any noises. And it turns out the noise I thought I observed came from my disc drive. When I removed the Ubuntu disc I left in there it booted up silently (well there was some clicking as in access drive clicking which occurs in Windows or Linux).

---

### Post by atlfalcons866 on 2007-07-26
is an emergency unload really more stressful on the heads than a normal shutdown? cause that is what my wd1600jb sounds like its doing. It makes a popping sound when it shuts down. I would test this on windows but i dont want to delete my partion just to test it.

---

### Post by schultz on 2007-07-26
Ok, let me explain more clearly. There are five kinds of noises.

The first is the hdd doing an emergency unload, which is very bad, upon shutdown. This can be fixed as long as a 1 is written to the file /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown.

The second is the LiveCD booting. The sound is so horrible and comes from the CD drive. It is as if the disk is not spinning once, but spinning, stopping all the time.

The third is the noise fruit of constant disk activity often generated by system loggers. Kill them all or use laptop-mode-tools and enable write cache while putting a dash in front of the files they refer to in their .conf files.

The fourth is the suspend noise. This is a "pop" much louder than the emergency unload (perhaps comes from the speakers, but I am not so sure). Is there anyone who can suspend-to-ram quietly?

The fifth and last is the most terrible of all! It happens during hibernation (aka suspend-to-disk). Those are two "pop"'s like the suspend-to-ram ones followed by the hdd emergency unload. Is there anyone who knows how to have this fixed?

I was able to remove the first and third noises, can people help removing the remaining?

---

### Post by Spartan.II.117 on 2007-07-27
is there a similar file stop on hybernate/stop on suspend? if so, those would need to be edited as well.

---

### Post by dcstar on 2007-07-27
> **schultz said:**
> In this bug report it is said that if the script

[B]#!/bin/sh
echo 1 > /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown
[/B]

is put in **/etc/rc0.d/S00hdd-shutdown-workaround**, it is executed upon startup and in reboot, the hdd turns off quietly.


Actually anything in the rc0 (Run level 0) directory is executed on shutdown, not startup - but is should work anyway in this application.

---

### Post by ev5unleash1 on 2007-07-27
Seriously If your saying that Ubuntu is killing Hard Drives and Windows XP is doing the same thing then don't you know the Hard Drive manufact would of seen this problem by now. I've has a hard drive for a while and it's has not do you call it dead.

---

### Post by Spartan.II.117 on 2007-07-27
but on suspend and hybernate, it dos'nt actually go to run level 0, does it?

---

### Post by genbuntu on 2007-07-27


Hi 

I was about to post the same concern to the forum but found this post already , so thought I'd rather reply to it.

I'm a new user of Ubuntu (& Linux as well) and simply love the feel of this open-source system. 

However, I would like to confirm Schultz's report that the laptop hdd makes a weird pop sound when shutting down in Ubuntu. My laptop is Toshiba satellite M50 running on dual boot WinXp and Ubuntu Fiesty; but I notice this problem occurs only when shutting down in Ubuntu (and NOT in WinXP). I did not go into the details of searching what might be the reason behind this but felt uneasy and definitely not good for my laptop. So whenever I use Ubuntu now, I make sure to  go through the process of rebooting (and then shutting at dos prompt or windows login screen) instead of directly shutting it down from Ubuntu station. (The problem doesn't occur while rebooting).

I hope somebody can come up with some fix soon (because I have started leaning more towards Ubuntu now and I'm sure we all love our hours of precious data on hard-drives).

:)

---

### Post by ev5unleash1 on 2007-07-27
I really don't understand how to fix this problem. IT says create the file. Um i can't i have read access only privileges to the root file system,

Any step by stop instructions or is there away from doing it though terminal.

---

### Post by ev5unleash1 on 2007-07-27
I have a simple solution... Everyone user USB Flash Drives! Put all data on there and only operating systems on the HDD #@*($ the hard drives :)

But seriously I want to know how to fix this problem. I've heard it's a Ubuntu Problem not a linux kernal problem because Open SUS does not have this problem and uses the same linux Kernal where other Ubuntu Users using the kernal have a problem

---

### Post by robsan on 2007-07-27
This not a problem for Ubuntu only.

Check out the following links:

[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=243021](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=243021)

[http://linux-ata.org/shutdown.html](http://linux-ata.org/shutdown.html)

This is a very serious issue and so far i noticed it with some distros (Mandriva/Ubuntu/PCLOS) as i bought a Asus F5V and i'm having trouble getting any to work with it. After first reboot i get an error during boot stating that one partition is corrupted and cannot boot anymore. I will try to install Kubuntu and apply the fix mentioned here.

---

### Post by Depressed Man on 2007-07-27
> **ev5unleash1 said:**
> I really don't understand how to fix this problem. IT says create the file. Um i can't i have read access only privileges to the root file system,

Any step by stop instructions or is there away from doing it though terminal.

Try cd (change directory) to the directory the file is located in. Then sudo gedit nameofthefile.

---

### Post by schultz on 2007-07-27
Ok, some answers.

For genbuntu: Just make sure a 1 is written to that system file before you press the KDE's shutdown button. You can cat it in a terminal. I also had my problems with root access, but managed to do it through Konqueror and KWrite.

I shall check if indeed I hibernated/suspended with that 1 in the file, but I believe I did. Suspending and hibernation are buggy. I would appreciate really much to have them back, but not having to pay my hdd as a price.

I also had this issue with Gentoo Linux, which, for laboratories of many equal computers and standardised machines such as the PS3 is far better than Ubuntu, by the way. But Gentoo did not even manage to hibernate/suspend properly. 

They should keep a close eye in this problem, at least until they release the next version. Upgrading to the next Ubuntu version must solve this, an the developers should make this compromise public. Users of linux know it is superior to M$, but some bugs such as this takes away our pride. It is ok that M$ plays dirty and make some kind of deal with hardware enterprises to release technical documents in detail only to M$. That is why the HP drives DVD solves the problem and XP alone does not. They play dirty, those son of a $#@*!'s.

But this should be no problem to fix, I believe. The whole point is that the developers of the next version should pronounce in public the bug is fixed and guarantee us system stability, that would be very wise, and nice, of them. Then we should stop worrying about that and have a perfect linux system under the hood. It would be good for everyone, except for Bill Gaytes, of course.

---

### Post by schultz on 2007-07-27
Ah, a trick! There is a slight possibility to fix that.

There is some script sleep.sh somewhere in the system. It contains a instruction like echo -n x > somefile. This makes the system sleep.

We should add a magic instruction, which I do not know of, right before that one to make the hdd idle.

That should work, should it not?

---

### Post by sr20ve on 2007-07-27
I never really thought anything about the "click" noise I got when I shut down my laptop, but after reading this thread, it looks like it is a problem. I applied the fix and now I don't get the noise anymore.

Thanks for the useful info and pointing out this issue.

---

### Post by schultz on 2007-07-27
I appreciate the thanks, but it was not me who spotted the problem, it was in some launchpad bug list. Of course, I never found it nice when I heard those sounds, which is why I searched the bug list.

Do you get your laptop to suspend/hibernate correctly? If so, share some information (system configuration) with us. That would be helpful.

---

### Post by Espreon on 2007-07-27
Look, I have used Ubuntu since Edgy and did at least 30 installs (I reinstall if something goes horrible, all of them are caused by me) and nothing bad has happened to the HDD.

---

### Post by Espreon on 2007-07-27
> **ev5unleash1 said:**
> I have a simple solution... Everyone user USB Flash Drives! Put all data on there and only operating systems on the HDD #@*($ the hard drives :)

But seriously I want to know how to fix this problem. I've heard it's a Ubuntu Problem not a linux kernal problem because Open SUS does not have this problem and uses the same linux Kernal where other Ubuntu Users using the kernal have a problem

What other distros might have this prob, since I was considering switching to Sabayon or dual-booting it with Ubuntu.

---

### Post by ev5unleash1 on 2007-07-27
No one tells be a simple way to fix the problem. They should have an update on Ubuntu to fix it.

---

### Post by schultz on 2007-07-27
I am placing any criticism on the Ubuntu community, I am just giving an advice. I think they should give us feedback.

And another thing. Who originally said hdd were being destroyed was not me, but technical documentation. I even read a post which says the life shortening rate is 100, not 30.

Anyway, Ubuntu should (not must) do something about it.

---

### Post by Grayfox777 on 2007-07-27
Woah what?! This sounds extremely terrible! :(  Fortunately, it also seems like it's not very widespread.

---

### Post by schultz on 2007-07-27
I thought about something. Perhaps it is not suspending correctly because the hdd has to spin up to write something to the system state file.

We actually need a bash expert to analyse the sleep.sh script and give us some light.

---

### Post by dcstar on 2007-07-28
> **ev5unleash1 said:**
> No one tells be a simple way to fix the problem. They should have an update on Ubuntu to fix it.

It is apparently fixed in the 2.6.22 kernel, so when that is available as an update the problem should go away.

---

### Post by schultz on 2007-07-28
It is very nice to know that it has been fixed in the next kernel.

How is it I will know it is available? And when it does, how is it I will update the kernel? That was a piece of cake in Gentoo, but in Ubuntu I am not sure.

Ah, and one more question. I have heard the next kernel shall rename ATA drivers such as mine to /dev/hda (just like in Gentoo) once more. If it does that, will there be any incompatibilities? I mean, will I have to reinstall the Ubuntu?

---

### Post by bigboy_pdb on 2007-07-28
All updates are shown in the "Notification Area". If you can see an icon for the "Network Manager" on you top panel then the "Notification Area" is on the panel. Another way to tell is if you've already performed system updates.

The kernel update is just like any other update. You will be asked to select which updates you want and then you can install them. During startup, in the GRUB boot menu, you get to choose which kernel you want to use when booting Ubuntu. When the kernel update is installed, it will appear as the first choice in the GRUB boot menu.

With respect to how that update will affect the rest of your computer, I'm guessing that it will have been tested before being released, but there's always the possibility that some bug might not have have been found. I don't think that you need to worry too much about the new kernel update though.

**EDIT:**
If the notification area isn't visible on one of your panels then you can add one by right clicking on the panel, selecting "Add to Panel...", and scrolling down to the last section which is entitled "Utilities" and by selecting "Notification Area" and then clicking "Add".

---

### Post by schultz on 2007-07-28
Thanks for the hints, but I guess it is better to wait until October to reinstall everything. I am thinking of using Gentoo again or Ubuntu Gutsy from scratch.

---

### Post by schultz on 2007-07-28
I tested something today.

The "pop"'s that come out in suspend are not from the hdd, but from somewhere else, perhaps the speakers.

I tried muting the speakers, but no result. Anyone gets the same?

---

### Post by jamieh on 2007-07-29
What???

---

### Post by brocolli on 2007-07-29
I am also experiencing this in dell xps m1210. The clicking sound is due to improper head parking during shutdown.

I still haven't read any reports of a sata hard disk failure due to the improper head parking during shutdown. But the fact that it is an 'unusual' clicking noise, and that this problem is relatively new (for sata drives on newer laptops), there might come a time that it will damage the hard drive.

I have tried many suggestions to remove the clicking noise but I was not successful. I am still waiting for kernel version 2.6.20.16 or later. This kernel bug is already fixed in those versions. What I do to temporarily avoid this is to just restart the pc instead of shutting down. Let it reboot to grub and from there, shut it down. Restarting doesn't cause the hard disk to click...

---

### Post by erfahren on 2007-07-29
I could hear that noise at shutdown on my laptop as well. I did the workaround script fix mentioned earlier in this thread, which was basically:
sudo gedit /etc/init.d/hdd-shutdown-workaround

and in there:
#!/bin/sh
echo 1 > /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown #list all the HDDs you have
#EOF

and:
sudo chmod +x /etc/init.d/hdd-shutdown-workaround
sudo ln -s /etc/init.d/hdd-shutdown-workaround /etc/rc0.d/S00hdd-shutdown-workaround

and it seemed to work, didn't hear the pop sound shutting down Ubuntu again.

I just wanted to mentioned this; the title of this thread caught my attention as well, but after reading through it I became much less concerned. I rarely fully shutdown my laptop, just letting go into suspend and restarting occasionally. And since that script seems to work, it's completely a non-issue for me personally. I wouldn't see it as a reason not to install Ubuntu. 

One other note here; out of curiostity I booted into my Vista partition for a little while and then used the shutdown in it --- and there it was; the noticeable "pop".  I wonder when M$ will provide a workaround fix for it, maybe in Vista's SP1 if ever?  hmmm... food for thought

---

### Post by misfitpierce on 2007-07-29
I have an HP laptop and it makes no noises upon restart or shutdown and have owned compaq before that with ubuntu and had no sounds of probs or anything... I dont believe it.

---

### Post by robenroute on 2007-07-29
> **misfitpierce said:**
> I have an HP laptop and it makes no noises upon restart or shutdown and have owned compaq before that with ubuntu and had no sounds of probs or anything... I dont believe it.

Well, whether you believe it or not is entirely up to you. It just happens so that some people have noticed this issue, filed a report/bug, applied a fix and henceforth haven't noticed the popping sound again. Personally, I've never seen Mars with my own eyes; that doesn't mean the planet doesn't exist. But whether I believe it to be out there is up to me.

---

### Post by isaacj87 on 2007-07-29
I wonder how long my HDD would of lasted if I hadn't applied the fix. I always noticed a slight "click/pop" when I shut down, but didn't really think anything of it (always thought it to be normal).

Anywho, here's my status of the situation... I applied this fix:

[HDD NOISE FIX]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60")

and it works perfectly. It seems like everyone who has come across this thread is either in disbelief or concerned (rightfully so). Either way, it seems right to encourage everyone to at least check for the sound, and if it's there, apply the fix.

As for suspend and hibernate...My laptop suspends and hibernates perfectly (I've got an Acer Aspire 1642WLMi) and I hear the sound still (obviously)...Are we getting closer to a fix for suspend mode?

---

### Post by brocolli on 2007-07-29
> **misfitpierce said:**
> I have an HP laptop and it makes no noises upon restart or shutdown and have owned compaq before that with ubuntu and had no sounds of probs or anything... I dont believe it.

based on what I have read about this, this only happens in laptops with sata drives. Not all are experiencing it...

---

### Post by H.E. Pennypacker on 2007-07-29
You guys...this is hysteria.  A forum search on this would have produced an answer instead of causing alarm and turning everyone into a fearful Ubuntu user.  Also, this problem is hardly new, and has already been addressed.

Check this out:

[http://ubuntuforums.org/showthread.php?t=469596](http://ubuntuforums.org/showthread.php?t=469596)

There's no evidence to support the notion of Ubuntu destroying hard drives.  Making such a blanket claim is highly deceptive, and quite frankly a lie.  People have been using Ubuntu for years without their hard drives ever having died...could the OP explain why the Angel of Death hasn't met their hard drives?  

You could fairly claim that some hard drives are being negatively impacted (the very first place to mention something like this is Launchpad), but please be careful with the words you choose.  Sensationalism will not further your cause.

Thank you for sharing your knowledge, nevertheless.

---

### Post by schultz on 2007-07-29
My laptop has an ATA hard drive. The problem is that Ubuntu recognises it as a SATA drive. Gentoo did name it /dev/hda, but the sound was still there.

Anyway, Ubuntu is suspending/hibernating correctly in my laptop, but in suspend I still hear the sound (which, I am pretty sure, does not come from the hdd, not like to be an emergency unload) and in hibernate I hear three sounds, two like the suspend one and the hdd emergency unload.

Now, considering I am too afraid to suspend/hibernate because of the above, my laptop is limited to shutdown, which is not what I would call nice. Still Ubuntu + shutdown is better than M$ + shutdown + hibernate + suspend + sound LED.

Anyway, I still think Gutsy developers should focus on it, since laptop compatibility should be one of their highest priorities, since laptops are increasing in number.

---

### Post by cyke on 2007-07-29
i have a sony vaio VGN-SZ28GP laptop with winxp and ubuntu feisty installed.  Upon reading this thread, i tested shutting down on ubuntu and winxp. i dont hear any popping sound except for the disk spinning down.  can any sony laptop user confirm if they can hear weird noises on their hd on shutdown?  

i can only hear this pop sound during hard resets.  is it possible that the problem is specific to certain hardware only?

---

### Post by brocolli on 2007-07-29
> **cyke said:**
> i have a sony vaio VGN-SZ28GP laptop with winxp and ubuntu feisty installed.  Upon reading this thread, i tested shutting down on ubuntu and winxp. i dont hear any popping sound except for the disk spinning down.  can any sony laptop user confirm if they can hear weird noises on their hd on shutdown?  

i can only hear this pop sound during hard resets.  is it possible that the problem is specific to certain hardware only?

During your installation, was your hard disk recognized hda or sda? I have seen that this is a problem with sda...

---

### Post by Depressed Man on 2007-07-29
Dunno about his, but I have a Sony laptop that's recognized as sda but I don't hear the sounds. The noise I noticed before was coming from the disc drive (loading a disc in there silenced it)

---

### Post by schultz on 2007-07-29
Once more, this bug has not much to do with the /sda or /hda recognition. I am a live counter-example to the theory that the bug is only with /sda. A previous Gentoo installation of mine with suspend2-sources of the same version of the Feisty kernel recognised my drive as /hda and the sound actually was there.

---

### Post by isaacj87 on 2007-07-29
I'm not sure why there are post claiming this is sensationalism...I can assure you my laptop was making the same unpleasant "click" upon shutdown that it would on a hard reset...After applying the fix from LaunchPad I don't have that noise anymore...

True, I frequent the forums and I haven't found any threads related to HDD failure, but how long would a drive last if the fix wasn't applied? (For example, how many times can you do a forced shutoff before the hdd goes bye bye...)

And if this post really is sensationalism...what was the noise my hard drive was making? And why is it gone now? Is the "fix" doing more harm than before when I was hearing the sound, or is not....

---

### Post by schultz on 2007-07-29
Yes, at first I was worried about my hdd and did post this thinking it would die soon.

The initial intention was to fix my problem.

Then I saw many people already experienced this and I am glad the fix was spreaded a little more.

---

### Post by Depressed Man on 2007-07-29
Yep, the important thing is that people who are in a similar situation got their problem solved.

---

### Post by schultz on 2007-07-29
Yes, I agree.

But let us not forget a workaround is never a solution, just a workaround.

Also, not everyone (me, for instance) got their problem completely workarounded, since suspend and hibernation still behave badly in some cases.

---

### Post by sunra350 on 2007-07-29
> **schultz said:**
> In this bug report it is said that if the script

[B]#!/bin/sh
echo 1 > /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown
[/B]

is put in **/etc/rc0.d/S00hdd-shutdown-workaround**, it is executed upon startup and in reboot, the hdd turns off quietly.

Can anyone run that script and test if it works?

Remember, simply putting it there shall not do the job, it must be executed.

Any HP ze4950 or similar please give me feedback.

I was having the same issue with a thinkpad T20 the machine would not shutdown and I had to hold the power button and the pop sound would happen, I ran the script and now it shutdown / powers off properly.

Works For Me!

---

### Post by brocolli on 2007-07-30
This clicking sound was already reported as a kernel bug and a fix is already out. But the fix is only incorporated in the newer kernel and is still in the testing stage. One good thing, while waiting for the newer kernel we can use the work around. It should work for now...

Why is this thread sensationalized? The clicking sound is something that is uncommon. It is yet to be proven that this sound can damage hard disk. But come to think of it, the click is something not normal. And instinct will tell you when you hear the click that there is something wrong. The hard disk may not bug down immediately but I think if the clicking continues, it will shorten the life of your hard disk. If the issue has something to do with a software that can damage hardware, I think it should be sensationalized.

---

### Post by brocolli on 2007-07-30
> **erfahren said:**
> 
sudo gedit /etc/init.d/hdd-shutdown-workaround

and in there:
#!/bin/sh
echo 1 > /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown #list all the HDDs you have
#EOF

and:
sudo chmod +x /etc/init.d/hdd-shutdown-workaround
sudo ln -s /etc/init.d/hdd-shutdown-workaround /etc/rc0.d/S00hdd-shutdown-workaround



Please help me as I haven't got this to work for me. I don't have the hdd-shutdown-workaround and S00hdd-shutdown-workaround files. Shall I create them? What are their extension, .sh? Thanks..

---

### Post by schultz on 2007-07-30
Ok, let me explain. Those files have no extension. Just because one of them is a shell script, it does not mean it must end in .sh. Just make a file without extension written there, just like the C++ STL headers, if you use C++. The other file is a software link generated by ln -s and should not get an extension as well.

One thing that you might come across is that the file /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown may already exist (as it did in my kubuntu) and be write-protected. In my case, not even sudo could remove that file. Then the script commited an error once it tried to write in that file. What I did to solve this was to use Konqueror and to delete that file within the graphical environment. It made a few warnings, but the file was removed. Then I wrote the file with KWrite for the first time. This solved it for me.

If you do not have the files, things are easier for you, just create them.

For those whose blood is filled with hatred towards M$, good news is that my desktop does that. It is quite new and has a SATA hard drive. The WinXP is there because my family uses the computer and think I use Linux due to being rebel only. The noise of the hdd spinning down appears in each shutdown. Every once a blue screen of death or a bug appears I laugh at them and show them my stable bug-free eye-candy desktop. I really expect this hdd to de destroyed soon so they have to waste money to see how it does not pay to use those workaround oriented software (have you ever heard of WOP?).

So this is it. You see, if a problem such as this happens in M$, how will the users fix the bug? Suckers...

---

### Post by brocolli on 2007-07-30
It's my first time to hear about this clicking sound problem in windows. My xps m1210 is on a dual boot with linux and vista and I haven't experienced the click when I shut down on windows...

---

### Post by brocolli on 2007-07-30
> **schultz said:**
> Ok, let me explain. Those files have no extension. Just because one of them is a shell script, it does not mean it must end in .sh. Just make a file without extension written there, just like the C++ STL headers, if you use C++. The other file is a software link generated by ln -s and should not get an extension as well.

One thing that you might come across is that the file /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown may already exist (as it did in my kubuntu) and be write-protected. In my case, not even sudo could remove that file. Then the script commited an error once it tried to write in that file. What I did to solve this was to use Konqueror and to delete that file within the graphical environment. It made a few warnings, but the file was removed. Then I wrote the file with KWrite for the first time. This solved it for me.

If you do not have the files, things are easier for you, just create them.

For those whose blood is filled with hatred towards M$, good news is that my desktop does that. It is quite new and has a SATA hard drive. The WinXP is there because my family uses the computer and think I use Linux due to being rebel only. The noise of the hdd spinning down appears in each shutdown. Every once a blue screen of death or a bug appears I laugh at them and show them my stable bug-free eye-candy desktop. I really expect this hdd to de destroyed soon so they have to waste money to see how it does not pay to use those workaround oriented software (have you ever heard of WOP?).

So this is it. You see, if a problem such as this happens in M$, how will the users fix the bug? Suckers...

Thanks for explaining. I am going to try your work around. I'll keep you posted..

---

### Post by schultz on 2007-07-30
As I said before, the clicking in Microsoft Windows happened in my laptop until I installed the drives from HP. HP plays dirty and gives a fresh shot of tested and compatible drivers for Microsoft. Without those, Microsoft is worse than Ubuntu in clicking problems. This comes in a HP drives DVD.

That way around, it is easy to set up a laptop, since the drives comes from the enterprise which built the laptop.

Notice also windows does consume less battery power, but even with all those advantages, it is still worse than Linux.

If you never removed Vista from you notebook and bought it installed in your box, it is quite likely the drives from the DVD are already in. That is why Vista turns off quietly.

---

### Post by viking777 on 2007-07-30
As a long term sufferer with shutdown problems on my laptop I can confirm two things for you, firstly it is not a Ubuntu problem - I have installed a dozen different distros on my laptop and the only one that shuts down properly is Windows. Secondly having the latest kernel makes absolutely no difference whatsoever I am on 2.6.22-9 and it still does not work. 
I don't know if this is a serious problem or not in terms of hard drive life expectancy, but it is sure as hell an annoying one, and why resources are not directed at this sort of problem instead of trying to keep up with the latest eye candy from Redmond is a mystery to me.:mad:

---

### Post by hysteresis on 2007-07-30
I would worry more about the overheating problems that laptops seem to have in ubuntu then drive problems. You could swap out your laptop drive for this:

 [http://www.addonics.com/products/flash_memory_reader/ad44midecf.asp](http://www.addonics.com/products/flash_memory_reader/ad44midecf.asp)


We have laptop drives at work mounted on full motion flight simulators. They have been shaken for the last 10 years  and we have not had to replace any drives. If shaking a hard drive for ten years (when the instructor inputs turbulence it's like a paint shaker) doesn't kill them, I doubt that hard shutdowns will.

---

### Post by Depressed Man on 2007-07-30
> **schultz said:**
> As I said before, the clicking in Microsoft Windows happened in my laptop until I installed the drives from HP. HP plays dirty and gives a fresh shot of tested and compatible drivers for Microsoft. Without those, Microsoft is worse than Ubuntu in clicking problems. This comes in a HP drives DVD.

That way around, it is easy to set up a laptop, since the drives comes from the enterprise which built the laptop.

Notice also windows does consume less battery power, but even with all those advantages, it is still worse than Linux.

If you never removed Vista from you notebook and bought it installed in your box, it is quite likely the drives from the DVD are already in. That is why Vista turns off quietly.

That problem explains why I didn't experience the problem? Dunno.

Well anyway, there's a few tricks to save power that Windows uses. Most laptops come with CPU frequency scaling. So when the CPU isn't needed as much it runs at a slower clockspeed to conserve energy. I think you can also install that for Linux (but whether your laptop supports it...well it may vary, I've never tried it myself).

---

### Post by schultz on 2007-07-30
One thing is right about that issue. Laptops do waste more battery in linux.

The difference is not what I consider prohibitive. In my laptop, windows lasted 3 hours and linux do well for 2:10 hours.

I have frequency scaling and laptop_mode switched on, but the waste is still there.

But that comes with advantages, too, Ubuntu is at least 3 times more efficient than Windows and 6 times in kernel related issues (like memory allocation).

For users of Python, Java, etc... this can be quite an improvement, since there memory allocation is the bottleneck.

Anyway, the shutdown/suspend/hibernate is not what I would call ok in my machine but Ubuntu is still preferable.

Ah, and I agree on investing eye-candy resources in base system development.

---

### Post by cazimir on 2007-07-30
So...I have 2 hhd's..a 80gb Pata driver and a 200gb Sata driver.The click sound it's here too.The script is the same?...or because i have 2hdd's it's diferent because i follow the instructions from here and the click sound diddn't dissapear?Pls say me:)

---

### Post by ahchong on 2007-07-31
i can agree with you on the Windows XP does damage the HDD. cause i cant installed anymore installed WIndows in my laptop. WEIRD!!! 
BUT!!! i can installed ubuntu fiesty on my laptop. MORE WEIRD!!!
then i started to use ubuntu, ive instaled ubuntu, then i switch to kubuntu, then i switch again t ubuntu.. INSANE!!!
then i notice there is BUG!!!
it said on my screen when try to start.
wrote smething like MP-BIOS  bug cannot connect?
what that? but it feels ok n nothing more wierd, i do have the sound 'pop' when i shutdown my laptop long ago!!! when i install WIndows. maybe i have to change HDD after all....T_T!!!

---

### Post by brocolli on 2007-07-31
> **ahchong said:**
> i can agree with you on the Windows XP does damage the HDD. cause i cant installed anymore installed WIndows in my laptop. WEIRD!!! 
BUT!!! i can installed ubuntu fiesty on my laptop. MORE WEIRD!!!
then i started to use ubuntu, ive instaled ubuntu, then i switch to kubuntu, then i switch again t ubuntu.. INSANE!!!
then i notice there is BUG!!!
it said on my screen when try to start.
wrote smething like MP-BIOS  bug cannot connect?
what that? but it feels ok n nothing more wierd, i do have the sound 'pop' when i shutdown my laptop long ago!!! when i install WIndows. maybe i have to change HDD after all....T_T!!!

What file format do you have on your hard disk? Linux will install and can reformat ntfs partitions but windows cannot install and format ext3 (linux formatting). To be able to reinstall windows  xp after a linux install, you need to reformat your partition to fat32 or ntfs first.

Specifically, what does this MP-BIOS bug say?

---

### Post by cyke on 2007-07-31
> **brocolli said:**
> During your installation, was your hard disk recognized hda or sda? I have seen that this is a problem with sda...

sda.  still cant hear it, but i'll try the workaround anyway.  no harm in doing it i guess.

---

### Post by schultz on 2007-07-31
Cazimir: you can do a bash loop like this in the script. Someone please correct me if my syntax is wrong.

#!/bin/sh
for disk in /sys/class/scsi_disk/*; echo 1 > ${disk}/stop_on_shutdown; done

But check if the syntax is ok first.

---

### Post by brocolli on 2007-07-31
> **cyke said:**
> sda.  still cant hear it, but i'll try the workaround anyway.  no harm in doing it i guess.

It's a click not to loud (but noticeable) just immediately before power is cut off. It is usually followed by a fading humming sound, just like a spinning wheel coming to rest.. If it is not noticeable, then you are not experiencing it...

---

### Post by W. Irving on 2007-07-31
I haven't read the entire topic, but judging by the first and second page I'd say this is complete and utter rubbish.

The click is due to the drive heads 'parking' themselves when they are no longer energised. All hard drives feature this click! Laptop drives even more so, as they park their heads from time to time to avoid scratching the platters. They are meant to park their heads like this - there simply is no other way to do it.

The "spinning wheel coming to rest" is obviously the platters winding down. Not much to be done about that, if you really want the drive to stop. :rolleyes:

---

### Post by schultz on 2007-07-31
Yes, I would say you did not read the full topic. The reason for this is that you did not read that the fix does remove the sound.

Additionally, as said in the very first message, when your hdd is running and you cut off the power just like in a hard reset, the spindown/park heads procedure is far more stressful for the drive hardware than if done slowly and carefully while the power is on. That is called a emergency unload, it happens in critical shutdown conditions and can not be healthy for the hdd. The number of times they can be done multiplied by 30 should be around the number of proper shutdowns a hdd can do. I even read that ratio to be near 100.

Anyway, if you are skeptic, I think just removing the noise would be worthy reading the topic. For those who believe technical drive documentation, either by no reason or knowing technicians should know more about this than mere users do, the fix can put off our shoulders a very heavy worry.

Now, I, one of the believers in what you express as rubbish, ask you: will you do the workaround or keep the sound in your notebook?

---

### Post by isaacj87 on 2007-07-31
I would agree with you..only the problem is there actually was a difference for me after I performed the fix.

Obviously, there's going to be a click (heck, I still get a tiny one after the fix...normal) but the problem was before the fix, the drive would be spinning and come to a abrupt stop much like after holding down the power button for 4 secs. That was causing a much more noticeable and unpleasant sound click (almost kind of a grinding). Something about the heads not parking or something.

---

### Post by cazimir on 2007-07-31
So,after all,ubuntu will kill our hard drives?I just install ubuntu again a week ago and i'm fear will destroy my hard drives.Really i don't want to uninstall ubuntu to put windows again..but if it's dangerous for my hdd i will:(

---

### Post by W. Irving on 2007-07-31
> **schultz said:**
> Yes, I would say you did not read the full topic. The reason for this is that you did not read that the fix does remove the sound.

Additionally, as said in the very first message, when your hdd is running and you cut off the power just like in a hard reset, the spindown/park heads procedure is far more stressful for the drive hardware than if done slowly and carefully while the power is on. That is called a emergency unload, it happens in critical shutdown conditions and can not be healthy for the hdd. The number of times they can be done multiplied by 30 should be around the number of proper shutdowns a hdd can do. I even read that ratio to be near 100.

Anyway, if you are skeptic, I think just removing the noise would be worthy reading the topic. For those who believe technical drive documentation, either by no reason or knowing technicians should know more about this than mere users do, the fix can put off our shoulders a very heavy worry.

Now, I, one of the believers in what you express as rubbish, ask you: will you do the workaround or keep the sound in your notebook?

I'm not debating whether the fix removes the sound or not, only whether the sound is harmful or not. And I don't believe it is.

I've installed Ubuntu on five laptops so far. My main laptop has been running Ubuntu since version 5. They have all produced a loud click as they cut power to their drives, but this is no different from Windows XP, or cutting power manually. Either way they're designed to do this without any adverse effects, unless they're really really old. Anyway, I really don't see what the problem is - surely the net effect is the very same: the power to the drive is cut, and the heads are parked? Please explain wherein the difference lies, and if possible, produce two high quality sound samples of each shutdown procedure.
Even my desktop PC running Windows XP with two 3.5" Maxtor drives produce the same click when power is cut. They are 3 and 1 years old, and both are in excellent condition even though they run 15+ hours per day (along with my laptop drive, which actually sees even more usage).

I noted many of you with laptops have reported a loudish 'bang' or squeak as the computer powers up or down. This is most likely due to the speaker amplifier powering up, which sends a malicious DC pulse through the speakers. Every amplifier in the world does this, but those found in modern stereo systems disconnect the speakers until the amplifier has started (you can sometimes hear a subtle click as a relay performs this connection), hence protecting the speakers from this thump which was common in older amplifiers.
Another source of peculiar sounds when the computer starts is the CD/DVD drive. The drive in my laptop is one of them, and the sound is a quite indescribable scratchey sound as the lens assembly is run up and down.

All in all, I don't believe it's of any use to get hysterical over these kinds of things.

---

### Post by schultz on 2007-07-31
Thanks for the information. I suspected the sound I heard when suspending the laptop was coming from the speakers. And indeed it is. Do you know how to have the speakers silenced just before cutting the power?

That sound is, however, not the same I used to get in power down. That one came from the hdd, and it was kind of serious.

The whole point here is fixing this bugs. Windows shuts down quietly if the appropriate drivers are in. Why can not Linux do the same?

The whole thing is about politeness. Even if it does no shorten the drive's life, which some believe is true and some not, the system has to be polite and shutdown the PC softly. Making "pop"'s is kind of disrespect, or at least causes a bad impression. The point is: is the laptop better without or with the noise?

I shall not record the noise for an obvious reason: I do not want to make it again, and also because for me to do it, I would have to change scripts in system files.

Anyway, do you know a proper way to shutdown the speakers properly? I once tried muting the laptop before suspend, but the effect was the same.

---

### Post by W. Irving on 2007-07-31
I'm no expert at hardware/software interaction of a computer, but I can imagine that if Ubuntu can switch off the sound card a second before telling the motherboard to power down, then that might work (the sound card should implement such a function of gracefully powering down). But if the speakers pop on boot even before Grub has started, then such is the nature of the sound card. Beware though if you've got your 500W 5.1 system connected on the analogue outputs. The pop might turn into a terrifying, membrane blowing BANG.

I shall hibernate my laptop tonight, record the click, and publish it tomorrow if I have the time. I will even abuse my drive for a bit, I have nothing to fear. 2.5" drives are much more durable than bigger such in this respect.

The way the unloading works is by using the momentum of the platters to power the actuator arms back to their parking area, if power is lost. Listen to a pre-1995 drive and there ought to be a louder click as the drive powers down, as they use springs to park their heads. So whichever way the arms are parked, they are done so as gently as possible and necessary. The only reason behind the perceived louder click, as far as I can see, should be due to the fact that several heads are parked simultaneously.

---

### Post by schultz on 2007-07-31
Ok, I will try to turn off the sound and then suspend the laptop. I shall give feedback.

And I agree the emergency unload does the job correctly, without hdd harm. I am only saying doing it silently is even better. The hurry the drive sustains is stressful to its mechanism.

The point, once again, is that the noise worries many people like me that have no hardware expertise and should be removed.

---

### Post by Sayers on 2007-07-31
I think this is true.

---

### Post by fredj on 2007-08-01
This is a real problem so don't ignore it. Turn off your sound before making up your mind, then
listen to the hard disk at power off. If your disk drive is configured as a sd device rather than a
hd device then you will shorten the life of the disk unless you apply a fix. I noticed it because on
my dual boot machine the win XP shutdown is almost silent but on the Ubuntu shutdown there is
a noticeable click. This problem has been fixed in the .22 version of the kernel (not available for
Ubuntu yet) and it is listed as an official bug. The fixes detailed in this thread do work.

---

### Post by viking777 on 2007-08-01
> **fredj said:**
> This is a real problem so don't ignore it. The fixes detailed in this thread do work.

Not for me they don't:(

And I already have the 2.6.22 kernel it makes no difference.

---

### Post by Taum on 2007-08-01
My 2 cents:

All Hard Drives die.  It's not a matter of if, but when.  The only thing that will cause a Hard Drive to die faster is improper use.

---

### Post by genbuntu on 2007-08-01
The 'click' sound indeed comes from the hdd which is different from the one that we hear from the speakers. 

 This 'click', which I started hearing when I began using Ubuntu (fiesty) few weeks ago, is different and louder than the normal shutdown sound (which for me, doesn't occur in Windows XP). 

I applied the patch as described in:
[http://ubuntuforums.org/showthread.php?t=469596](http://ubuntuforums.org/showthread.php?t=469596)

and the hdd doent't make that click sound anymore.

Thanks to Schultz, Pennymaker and others for their solutions 

Of course some are right in saying that hdds can die anytime anywhere but why increase this probability. (Why don't we just turn off the power every time instead of waiting for the OS to turn off our computer?)

---

### Post by tombott on 2007-08-01
> **genbuntu said:**
> The 'click' sound indeed comes from the hdd which is different from the one that we hear from the speakers. 

 This 'click', which I started hearing when I began using Ubuntu (fiesty) few weeks ago, is different and louder than the normal shutdown sound (which for me, doesn't occur in Windows XP). 

I applied the patch as described in:
[http://ubuntuforums.org/showthread.php?t=469596](http://ubuntuforums.org/showthread.php?t=469596)

and the hdd doent't make that click sound anymore.

Thanks to Schultz, Pennymaker and others for their solutions 

Of course some are right in saying that hdds can die anytime anywhere but why increase this probability. (Why don't we just turn off the power every time instead of waiting for the OS to turn off our computer?)

cheers for this, have applied patch as per your link and this has resolved the issue.

---

### Post by schultz on 2007-08-01
I feel grateful others having the same problem as I did now have it solved. Nevertheless, I must say that unlike stated above, the fix is not mine, I merely passed it on.

Also, the problem is not totally solved just yet. Many of us still hear the emergency unload even with the fix and some others such as myself also hear sounds in hibernation and suspend, most likely from the speakers.

---

### Post by maestrobwh1 on 2007-08-02
Oddly, this does not seem to happen with my drives EXCEPT starting with Feisty, sometimes, more often than "not-commonly" I insert a USB HD (a real HD, not flash), I get a very loud, "zip, zip... ping" sound three times, it settles, then the drive is no longer readable in Feisty, even though it pops an icon for the device on my desktop.

However, if I plug it into my laptop with Edgy or any XP system, I can fix it using whatever disk tools the system has.  Knoppix actually saved me more than once as well.  

I have two different ide to usb converters, and I have tried several drives.  Whenever I HAVE to plug one in, I just sort of grit my teeth.  I was using it to shuffle my music between my desktop and laptop for things like amarok and such.

This happens in the KDE version of Feisty.  Not sure if anyone else experiences this.

---

### Post by schultz on 2007-08-02
Well I can not say I have since I own no USB or detachable hdd's.

Nevertheless, other USB storage devices such as pen drives work well in my Kubuntu Feisty Fawn,

---

### Post by Tyggna on 2007-08-02
I look forward to the day when there are solid-state hard drives.  They're starting to hit the market (Dell ships a 32 Gig solid state in a few PCs).  That'd make the problem not applicable if we had no moving parts.

---

### Post by schultz on 2007-08-02
Well, following that reasoning line I expect flash memory to get cheaper than hard drives while lasting more than those.

---

### Post by Depressed Man on 2007-08-02
> **Tyggna said:**
> I look forward to the day when there are solid-state hard drives.  They're starting to hit the market (Dell ships a 32 Gig solid state in a few PCs).  That'd make the problem not applicable if we had no moving parts.

My cousin was thinking about getting one of those since it also saves battery life. Though in the end the small space was a big negative.

---

### Post by schultz on 2007-08-02
I have just read about those drives and found them nice.

I have always believed in non mechanical memory (flash memory, mainly) and think that sometime in the future those shall replace medias even like the DVD or Blu-ray. Good was the time in which games were distributed in cartridges rather than discs.

Anyway, will Linux employ that distributed writing technique to improve the disk lifetime? And is Linux compatible with those?

---

### Post by fredj on 2007-08-02
If you want the fix to work then it is not enough to simply copy what others have posted here.
Go to the /sys/class directory and look at the contents of both the scsi_disk file and the scsi_device
file. Your hard disk could be 1:0:0:0 instead of 0:0:0:0 and in this case you will have to amend the
fix.

---

### Post by other on 2007-08-03
I have question that I hope is not too unrelated. I have an external harddrive that I always turn off with its power switch (after I unmount it of course). Would this also be an improper shutdown ('hard shutdown')? The manufacturer should've thought about it, unless the OS is supposed to handle the shutdown of the harddrive. I'll have to listen for that popping sound next time I turn it off.

---

### Post by schultz on 2007-08-03
Perhaps the hdd is shutdown properly, since you unmount it prior to power down. That is just a guess, though. I am basing this guess on the fact that my pen drives stop blinking once I unmount them.

So you can expect no noise.

---

### Post by Depressed Man on 2007-08-03
> **fredj said:**
> If you want the fix to work then it is not enough to simply copy what others have posted here.
Go to the /sys/class directory and look at the contents of both the scsi_disk file and the scsi_device
file. Your hard disk could be 1:0:0:0 instead of 0:0:0:0 and in this case you will have to amend the
fix.

What if you have 2:0:0:0 and 4:0:0:0 in the scsi_disk folder?

---

### Post by schultz on 2007-08-03
Do a bash "for" command over the directories which match the /sys/class/scsi_* pattern and, inside this, another "for" command over the directories which represent the disks.

---

### Post by aaaantoine on 2007-08-05
The workaround worked for me, but also, you can go ahead and install kernel v.2.6.22:

[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

---

### Post by Brachabre on 2007-08-06
I'm using Dapper drake still, but does Feisty come with 2.6.20 by default?

If I go ahead and install Feisty, will I need to update the kernel to 2.6.22? and will I have to apply any patch or is the kernel already officially patched up?

Thanks!

---

### Post by aaaantoine on 2007-08-06
From what I understand, 2.6.22 requires no workaround for the hard drive shutoff problem.  I can't advise you on the upgrade path from Dapper's kernel to Gutsy's kernel, since I'm relatively new to Linux, but the directions at that link might be able to help you.

---

### Post by vexorian on 2007-08-06
Can anyone explain what the sound is like? When I boot and shutdown I hear a sound that is like ... "fiuh" Until today I thought it was just something upstart-related, now I don't know what to think.

---

### Post by aaaantoine on 2007-08-08
The sound may vary from drive to drive.  Mine sounded like a click, similar to what it sounds like when I open the laptop's disc tray.

---

### Post by dje on 2007-08-08
I used this workaround:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60")
on my Dell Inspiron 1501 and it now shuts down silently. Before it made a 'click' just before power off.

Vexorian: My laptop also makes a 'fluh' noise on immediate boot up, does anyone know if this damages the drives or if it is normal, if it is normal i don't mind it. If it is damaging my drive is there another workaround?

---

### Post by Jhet on 2007-08-08
I've just read this, and many of you describe this as an issue on laptops.  I was wondering can't this also affect desktops with sATA (and pATA ) HDDs?

Am I wrong? Also does applying that patch/workaround without suffering the issue (knowingly suffering) going to cause any problems?

---

### Post by punkybouy on 2007-08-11
Sorry, I don't buy it.  I have Ubuntu running on four machines including a laptop and some SCSI too and don't see any of the activity you mention. When I shut down each of these the are OFF.

---

### Post by Rigit on 2007-08-12
I have a Toshiba M45-s331 and noticed mine does the same thing.  It also did it with Windows XP before I switched to Ubuntu.  I also have a Compac Laptop that my wife uses that is one of the first pentium M chips so it is pretty old.  It also has always done this with XP so I thought it was normal.  If the life of the hard drive is shortened then it must not be by much.  I am new to Linux and love Ubuntu much more than Windows and am not going to switch back.  I am a computer tech that has never touched any kind of Linux and was up and going with Ubuntu with connectivity to work in about 2-3 hours.  This rocks.

---

### Post by applegrew on 2007-08-12
I too have a Laptop. When turning off from Windows I always heard the pop sound, but after switching to Kubuntu, on shutdown I still hear the pop sound but it is much more louder than before. :(

---

### Post by applegrew on 2007-08-12
probably this is already reported at [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63937](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63937).

---

### Post by Unicast on 2007-08-12
Phew, just read this entire thread.......

Glad to see that this issue has (hopefully) been addressed in the next kernel update, and it's nice to see that my [non-technical walkthrough](http://ubuntuforums.org/showpost.php?p=2735968&postcount=12) of how to implement the shutdown script has helped so many.

It's interesting that even with the same hardware some folks experience this issue while others do not. I emailed the guy that runs the [Ubuntu on Dell Inspiron 1501](http://ubuntu1501.blogspot.com/index.html) blog about this issue a few months back and he said that none of his readers had reported any problem. On his blog he says he uses BIOS version 1.7, but I'm using 2.3 - so it looks like different BIOS versions can play a part in whether you experience this issue or not.

---

### Post by arkangel on 2007-08-12
well maybe i am lucky , i am using linux in this laptop since i bought it , like 2 years ago , and  so far the disk is OK ....

---

### Post by anv on 2007-08-12
it is not joke

[http://ubuntuforums.org/showthread.php?p=3176316#post3176316](http://ubuntuforums.org/showthread.php?p=3176316#post3176316)

---

### Post by schultz on 2007-08-12
After applying the workaround the sound goes off.

While suspending, I hear the same "pop" as you are hearing.

The shutdown sound if like a "fiuuuuh...." from the hdd, that is the emergency unload.

The suspend sound comes from the speakers and I do not know how to remove it.

---

### Post by macogw on 2007-08-12
I don't hear anything on mine, and I'm pretty sure it DOES send the "standby" signal, since during shutdown it prints out the word "standby"

---

### Post by jmate24 on 2007-08-12
ubuntu is killing your hard drive!

ubuntu kernel 2.6.22 is in the new distro of ubuntu 7.10 alpha(after a few upgrades)

you can get it at [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

but be warned it's still in alpha testing!

---

### Post by vexorian on 2007-08-13
My question is shouldn't critical bugs like this one be fixed like security issues? I think this one is bigger than any buffer overflow vuln.

I have figured out the sounds I am getting on boot / shutdown come from my screen (odd?)

jmate24: it is easier to just upgrade the kernel

---

### Post by applegrew on 2007-08-13
I agree. I have lots of data on it and it took around 3 days to configure my Kubuntu to my tatse. I can't get all the data back or configure it again.

---

### Post by conphara on 2007-08-17
I don't like reading this thread, makes me worry.

Although, my laptop doesnt seem to make this noise. If it did, I would probably have noticed it. I dualboot XP/Feisty, and they both shutdown in a similar way. The last noise the laptop makes before poweroff is a small rather normal sounding poweroff "peweeeuuu" kind of sound, nothing metallic sounding about it. Or else the "peweeeuuu" sound is the wrong noise you guys are talking about.
Mine is a Medion MD 97600, Intel915, Samsung hard drive and the updated kernel via Synaptic. 
The poweroff on my moms pc (AMD 1400mhz, running Ubuntu 6.06, IDE hard drive) makes an oldfashioned poweroff sound, and yes I also think that the hard drive is running on it's last breath.

Can I upgrade my kernel to 2.6.22 via Synaptic or any other way (Ubuntu repos)?

---

### Post by viking777 on 2007-08-17
I have had the 2.6.22 kernel for about a month now, it makes no difference whatsoever to the shutdown and power management problems on my laptop, so I wouldn't bust a gut to get it if I were you. However if you want it you just have to switch to using Gutsy (which although still Alpha is incredibly stable for me). There are plenty of posts on how to upgrade from one distro to another, not sure how successful they are though I have never tried it.

---

### Post by vexorian on 2007-08-17
> it makes no difference whatsoever to the shutdown and power management problems on my laptopIt doesn't matter, it fixes this one bug.

> However if you want it you just have to switch to using Gutsy (which although still Alpha is incredibly stable for me).I recognize it is very stable for you, but it I wouldn't recommend it to everyone, it is alpha so the results are expected to be mixed.

> Can I upgrade my kernel to 2.6.22 via Synaptic or any other way (Ubuntu repos)?
try this: [http://ubuntuforums.org/showthread.php?t=511974&highlight=gutsy+kernel](http://ubuntuforums.org/showthread.php?t=511974&highlight=gutsy+kernel)

---

### Post by phenest on 2007-08-17
> **conphara said:**
> I don't like reading this thread, makes me worry.

Quite right. This thread comes from lack of understanding. I have a brand new SATA Seagate Momentus 7,200 160Gb. It makes a ticking sound most of the time in both Linux and Windows. Nothing to worry about. Some makes/models are noisy compared to others. Perfectly normal. I don't see how Linux can kill a hard drive. If your hard drive fails prematurely, then perhaps it was a faulty drive. Perhaps if a list was made of makes/models from everyone here that has had a hard drive failure, you may see a pattern.

---

### Post by ukripper on 2007-08-17
I see not even single post on DIGG worrying about any HDD after kernel upgrade to 22 -
[http://digg.com/linux_unix/Linux_Kernel_2_6_22_Released_final](http://digg.com/linux_unix/Linux_Kernel_2_6_22_Released_final)

---

### Post by viking777 on 2007-08-17
> 
Quote:
it makes no difference whatsoever to the shutdown and power management problems on my laptop
It doesn't matter, it fixes this one bug.


No it doesn't that is the whole point of my post.

---

### Post by Sunflower1970 on 2007-08-17
> **vexorian said:**
> 
> 
Can I upgrade my kernel to 2.6.22 via Synaptic or any other way (Ubuntu repos)?

try this: [http://ubuntuforums.org/showthread.php?t=511974&highlight=gutsy+kernel](http://ubuntuforums.org/showthread.php?t=511974&highlight=gutsy+kernel)

I used those instructions, and now my laptop no longer makes the odd klunking, or popping noise when shutting it down any more (it didn't do it in Edgy, did it in Feisty, and no longer does it with the new kernel)

---

### Post by jongkind on 2007-08-18
I refer to the link below for those who don't want to install a new kernel. This thread summarizes another workaround,  diagnoses tools and the the relevance of this all. 

[http://ubuntuforums.org/showpost.php?p=3209849&postcount=1]("http://ubuntuforums.org/showpost.php?p=3209849&postcount=1")

(I did not realise that the current thread was here).

---

### Post by bapoumba on 2007-08-18
> **jongkind said:**
> I refer to the link below for those who don't want to install a new kernel. This thread summarizes another workaround,  diagnoses tools and the the relevance of this all. 

[http://ubuntuforums.org/showpost.php?p=3209849&postcount=1]("http://ubuntuforums.org/showpost.php?p=3209849&postcount=1")

(I did not realise that the current thread was here).
NP, I did not merge to leave some kind of redirect from the Cafe :)

---

### Post by EdThaSlayer on 2007-08-18
Seems I will have to transfer ownership of my laptop from me to the dumpster.*sighs*

---

### Post by apjone on 2007-08-18
> **applegrew said:**
> I agree. I have lots of data on it and it took around 3 days to configure my Kubuntu to my tatse. I can't get all the data back or configure it again.

My work colleagues and myself run ubuntu on laptops and desktops from 6.06 to gutsy. We have had no problems, even with old kit. 

And applegrew my friend you said > I can't get all the data back Where are your backups? You do have backups of your data correct? Hard drives will fail, this is natural. After all mechanical failure can happen at any time as the quality of components fall in order to increase profit and production . Also you could lose your system or have it stolen at any time.

It never stops to amaze me how many people cry when they lose their data, and even after the 5th time of happening they still dont have backups! Why dont people back up?

---

### Post by jf/ on 2007-08-18
could we **pleasse** have a summary for this issue pls? Is it resolved now? If i update whatever i have to update after installation, will this problem still affect me? thanks...

---

### Post by kaurman on 2007-08-18
[COLOR="Red"]EDIT:Ok, so this has already been discussed. Sorry.[/COLOR]


Hello,

I had the shutdown&hdd problem and the workground script did the trick for me. However I have noticed a new problem: the 'clicking sound' is the result of hibernating as well. And... The computer won't resume it just boots up. <= This is likely not related to the click sound, but it probably won't hurt to mention it.

During the hibernation process I get a lot of errors about some usb&ACPI stuff but as /var/log/messages doesn't seem to contain any of them I'm currently unable to post an example. If anyone could tell me where the log containing them might be found I'd be grateful.

Or even better if someone could post a thought or two about fixing the click&hibernating problem.


Kaur
(Feisty, 2.6.20-16-generic)

---

### Post by hugmenot on 2007-08-18
Boy, there&#8217;s so much speculation and confusion going on in this thread.

One thing from the first page, when you use "sudo echo foo > file" in a shell on a file write-only for root then the redirection is done by the shell before sudo kicks in, which will give you an access denied error. With the following all is done with elevated rights.

sudo sh -c "echo foo > bar"

---

### Post by freeflyer57 on 2007-08-18
I run 7.04 on my laptop with no side effects. Also, I haven't turned my computer off in two months. I have blown a powercord.

---

### Post by genbuntu on 2007-08-18
I was able to resolve the pop-sound problem by the script. But recently I noticed it occurs while Hibernating also and the computer reboots from scratch instead of just resuming (as kaurman mentioned) . 
If we can create a similar script/code for hibernation as well (or for that matter for all shutdowns, suspends etc) that should solve it at least for the time being. 

:)

---

### Post by fredj on 2007-08-19
There seems to be a lot of confusion here with some people posting things like 'I don't see how
Ubuntu can kil your hard drive'. They obviously can't read. If you read this thread carefully all
that is explained. However I will go through it again.
Hard drive manufacturers rate their drives in terms of how many NORMAL shutdowns they can
take and how many EMERGENCY shutdowns they can take. The difference is dramatic. A drive
than can take 600,000 NORMAL shutdowns may only be able to take 20,000 EMERGENCY 
shutdowns. Of course these are manufacturers figures and are therefore often very optimistic.
If Ubuntu detects your hard drive as an sda device rather than a hda device then it treats it as
a SCSI drive and is at present only capable of doing an emergency shutdown of the disk when
you power off or hibernate etc. 
The problem is a kernel problem and is (I have heard) fixed in .22 revisions of the kernel.
In the meantime Linux may be shortening the life of your hard disk drive.
Despite what some people are posting here Windows XP (service pack 2) doesn't have this
problem. If you read the posts in this forum properly then you will be able to implement a 
workaround for the problem.

---

### Post by kaurman on 2007-08-19
Hi

Many people here seem to say, that using Gutsy's kernel will fix the whole problem. I'd argue with that because while using Gutsy's kernel I had to:

1) Remove 'evms' to make the HDD calm. Otherwise the activity light was blinking all the time. 
2)Well... I had to admit that HDD was making a strange sound which it didn't do with other kernels. Those of you who are using Gutsy's kernel should listen to your laptop/pc very carefully. Put your ear against it if need be :)

Maybe I'm paranoid but I really heard a strange sound with Gutsy's kernel and that made me go back to Feisty's kernel.


Kaur

---

### Post by jf/ on 2007-08-19
ok, so i've executed "the script", but i'm just wondering, if this normal?

```

$ cat /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown 
0

```

seems like its value is still 0???

---

### Post by kaurman on 2007-08-19
> 
ok, so i've executed "the script", but i'm just wondering, if this normal?

Code:

$ cat /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown 
0

seems like its value is still 0??? 


The script is fine as long as it is working :)

You don't have to execute it. The system does it for you if you've copied it to //etc/rc0.c

---

### Post by jf/ on 2007-08-19
> **kaurman said:**
> The script is fine as long as it is working :)

You don't have to execute it. The system does it for you if you've copied it to //etc/rc0.c
oh sorry about that. I'm doing the code in rc.local instead (reference [https://bugs.launchpad.net/ubuntu/+bug/67810/comments/76](https://bugs.launchpad.net/ubuntu/+bug/67810/comments/76), [https://bugs.launchpad.net/ubuntu/+bug/67810/comments/82](https://bugs.launchpad.net/ubuntu/+bug/67810/comments/82)), so that the fix will work for all of shutdown/reboot/suspend/hibernate (supposedly, i assume!!!)

Anyway, i found the fix - i got a bit too creative with my 'echo' statement...

```

echo 1>/sys/class/...

```

should have left in that space after the '1'!!!

---

### Post by kaurman on 2007-08-19
Hi

> I'm doing the code in rc.local instead (reference [https://bugs.launchpad.net/ubuntu/+b...10/comments/76](https://bugs.launchpad.net/ubuntu/+b...10/comments/76), [https://bugs.launchpad.net/ubuntu/+b...10/comments/82](https://bugs.launchpad.net/ubuntu/+b...10/comments/82)), so that the fix will work for all of shutdown/reboot/suspend/hibernate (supposedly, i assume!!!)

Didn't you mean rcS.d? Should it fix suspend/hibernate ,click' problem as well then please let us know in this topic.


Kaur

---

### Post by kinematic on 2007-08-19
Removing the -h flag from /etc/init.d/halt has solved it for us.

```
# Don't shut down drives if we're using RAID.
	hddown="-h"
	if grep -qs '^md.*active' /proc/mdstat
	then
```

---

### Post by jf/ on 2007-08-19
> **kaurman said:**
> Hi



Didn't you mean rcS.d? Should it fix suspend/hibernate ,click' problem as well then please let us know in this topic.


Kaur
nope!!! i prefer doing it in rc.local - BSD init style... ;) I dont see why doing it in rcS.d would be any advantage, since others have already advocated doing it in rc0.d instead (ie. so long as the setting takes effect before shutdown, it should be ok). Or do u have some other ideas which i dont know about?

---

### Post by r_l on 2007-08-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Dell Inspiron 6000 here encounters the same problem.  Instead of using the workaround, I updated to the Gusty kernel last night (as noted in the Launchpad).  It seems to solve the problem.  The soft-shutdown through menu does not make the long disk spinning sound anymore (although the "suspend" fail to resume now).  However, if I press the shutdown button to switch off the machine, it still make a long spinning sound.

Another thing, though, after upgrading the kernel, external disk seems not to dismount properly.  External USB drives, after "unmount" and removed physically, cause the machine to make that same disk-spinning sound.

---

### Post by kaurman on 2007-08-20
> **jf/ said:**
> nope!!! i prefer doing it in rc.local - BSD init style... ;) I dont see why doing it in rcS.d would be any advantage, since others have already advocated doing it in rc0.d instead (ie. so long as the setting takes effect before shutdown, it should be ok). Or do u have some other ideas which i dont know about?

No I don't have a good reason for placing the script to rcS.d instead of rc.local I just read those launchpad bug reports and they confused me a bit.

PS As I understand there's no chance that one day I can download Gutsy's kernel to Feisty as an official update? Does anyone have a clue when will there be any kind of fix/update at all that a Feisty user can download as an update?

---

### Post by conphara on 2007-08-20
If you still had to use the Feisty kernel until Gutsy comes out, would there be much harm (to the HDD) in restarting the pc and then while it shows the bootup flash, before it goes to GRUB, holding down the powerroff button as an emergency solution?

---

### Post by conphara on 2007-08-21
I just upgraded to the Gutsy development kernel and now Ubuntu shuts down just like XP without any noise/sound. So it does work. 
As a sidenote, I also think that the new kernel saves more power, but maybe that's just my imagination. 
Any, in short, the new kernel solves the problem, atleast on my laptop.

---

### Post by theironyofitall on 2007-08-21
I have an issue with gutsy 7.10 alpha s (surrently on the latest)

My disk was constantly being damaged when rebooting, sometimes fsck would fix it (fsck -c -f -y usually)
Sometimes if comes up with a grub error - cant find any easy way to fix this.

I have swapped to a new HDD - still the same - seems more commmon after using nvidia-settings to go to 1440x900 resolution

The problem is worse on ubuntu than kbuntu.

Comments anyone ? 

GAry

---

### Post by Ashrael on 2007-08-21
I've been reading this post completely, and YES i do hear this sound when shutting down my laptop, but i don't feel like changing scripts etc. So i will wait for gutsy to become stable and upgrade then... In the mean time i hope my drive will survive, AND i wil back up my data regularly... If and when my drive fails i will just put i a new one and a bigger one at that... I just see it as an oppertunity to upgrade my drive... LOL!

---

### Post by kchang on 2007-08-21
Whew! Just finished reading all of the posts. I was wondering if anyone has pinpointed the cause of the hard shutdown. That is, what type of computer is more prone to this behavior? I noticed that someone mentioned that it might be BIOS related. Someone else also stated that it depends on whether Linux recognizes your hard drive as hda or sda. Does anyone else agree with either of these statements?

---

### Post by cheetaux on 2007-08-21
I just ordered one of the Dell Inspiron 1420N notebooks with Ubuntu 7.04 installed.  Can someone tell me if this problem exists on this notebook.

Thanks

---

### Post by kaurman on 2007-08-22
> **cheetaux said:**
> I just ordered one of the Dell Inspiron 1420N notebooks with Ubuntu 7.04 installed.  Can someone tell me if this problem exists on this notebook.

Thanks
I think you should post this question (with a reference to this topic) to  [[COLOR="DarkOrange"]_'Ubuntu Dell support' category._[/COLOR]](http://ubuntuforums.org/forumdisplay.php?f=256) Why? Because this thread has become so long that only a few people ever reach to the last posts :)

---

### Post by Qui on 2007-08-22
i am using feisty fawn 7.04 with a brand new Segate PATA/100 320GB HD, A WD 4013GB HD & A 2GB Segate HD  drive and whenever i shutdown, i hear this noise, i wondered about it but thought noting until now... i guess its time to crawl back to ms windows again... just when i was getting use to this switch. thank heavens i didn't delete the damn thing on that spare hard drive.
                                                                                                                         Qui

PS: does anyone know of a distribution that does not have this problem?

---

### Post by RJARRRPCGP on 2007-08-22
> **schultz said:**
> Yes, this is it. Ubuntu is killing my (and eventually yours) hard drive!

 


Sad, but true, Windows XP and Windows 2000 are known to shut down the HDD and spin it back up if Windows is furious with a stop error!

---

### Post by Dylnuge on 2007-08-22
Qui, as far as I know, the problem has been reported in spreadout cases on Ubuntu only. Try Mandriva Free Edition ([http://www.mandriva.com/en/download](http://www.mandriva.com/en/download)).

Also, the problem is not extremely widespread, although it is an issue. I do not have the problem. Either way, I would trust Linux more with my data then WIndows, regardless of whether or not the STANDBY signal was sent properly.

Anyone realized yet what causes it? Could kernel config or something fix it, since it seems to not be universal? Weird that some people have it, some don't.

---

### Post by jacob01 on 2007-08-22
and your killing other peoples valuable time poasting this. Just normal use of a hard drive can kill it and nothing lasts for ever if you are worried about waisting money on buying a hard drive then why are you waisting money on windows and the virus protection softare and all of the other stuff that goes along with it

---

### Post by Dylnuge on 2007-08-22
> **jacob01 said:**
> and your killing other peoples valuable time poasting this. Just normal use of a hard drive can kill it and nothing lasts for ever if you are worried about waisting money on buying a hard drive then why are you waisting money on windows and the virus protection softare and all of the other stuff that goes along with it

1. This is in no way an attack on Linux or support of Microsoft. This is just a friendly user pointing out a serious problem. 

2. This is a serious problem. Shutting off the computer without shutting down the hdd first (holding the power button, interrupting the power by disconnecting the computer from its power source(s), etc) is dangerous and impacts the life of your hard drive seriously.

3. Yes, hard drives, being the only moving part of the computer, are going to die (for a good hard drive) in 3 to 4 years with poor file management (Windows) or 5 to 6 years with proper file management (Linux/MacOS/BSD/Any JFS). However, even turning off a computer by pulling the plug or holding the power button one out of every 20 times is detrimental to its health. Imagine, if you will, doing that every single time. Saying that there is no need to worry because the hard drive will die anyway is like saying there should be no research on diseases because people will die anyway.

4. You are killing your own time, unless someone is currently holding a gun to your head and forcing you to browse Ubuntu Forums (in which case, that person is killing your time). If not, then you don't need to read/reply. I happen to enjoy it, so I am fine with wasting time to it.

PS: Your post reeks of the "I didn't even read the second post" smell. As you may see, a lot of people agree this is a serious problem. Fact of the matter is, I wouldn't give a hard drive with this problem two years to live (depending, of course, on how often it is shut down). If you were to wake up one morning and find all your data gone, you would not consider this issue trivial.

-Dylan

---

### Post by spier on 2007-08-22
> **jacob01 said:**
> and your killing other peoples valuable time poasting this. Just normal use of a hard drive can kill it and nothing lasts for ever if you are worried about waisting money on buying a hard drive then why are you waisting money on windows and the virus protection softare and all of the other stuff that goes along with it

Good point. I`m running ubuntu for 2 years now, since Breezy Badger, without problems. The money I saved by not renewing anti-virus subscriptions will allow a nice upgrade!

---

### Post by Trenchbroom on 2007-08-23
I'm posting this as a coping mechanism.  

Please be aware that although my opinion is that this problem is very real and I am convinced that it is the cause of my personal woe, I will provide the whole story and you may draw your own conclusions of course.

I've been using (K)Ubuntu on my old desktop computer (circa 2002 hardware, same two original IDE drives inside the machine that I built the computer with) since 2005.  I love the program, never had a real issue with Ubuntu at all.  In October 2006 I purchased a new Dell Inspiron E1505 that I custom built around the idea of it being a Linux machine--Intel everything inside including video card, wireless, etc.  SATA 60GB hard drive included.  As I expected Ubuntu LTS and then Edgy installed and ran without problem one.  Thought it was funny that 8 months later Dell is selling my EXACT computer with Ubuntu pre-installed....

Everything runs great EXCEPT...worrisome clicking sound that occurs from the hard drive whenever I shut down Ubuntu.  This is a dual boot system with XP media edition and when I booted and shut down XP, no click sound.  Click sound occurs every time with Ubuntu.

April 2007 the hard drive completely fails.  Ubuntu had started making the clicking sound sporadically during routine usage of the computer while the OS was running, normally when I was listening to MP3's.  Then Ubuntu started occasionally "freezing" sometimes with more and more frequency as the weeks wore on.  Then one day--nothing.  Hard drive is frozen, no clicks, it's dead.   Do the chat thing with a Dell tech, they send me out a replacement drive (refurbished).  I install it, install Ubuntu, everything is as it was before. 

Now I didn't really put it together that the clicks that came after shutting down the laptop would be the cause of the first drive failure.  Drives are complicated things, right?  Failure could be from anything.  Also, it seemed to me that my desktop shut down a little more "loudly" with Ubuntu then with XP and those hard drives are still spinning after years of use.  I figured that it was a normal thing for the OS to do.  Having Dell decide to install the exact SAME OS on the exact SAME computer as mine allayed any fears that I may have that it was a software issue.  Defective hardware, case closed, move on.

Fast forward to today--using the laptop as normal, all of a sudden Ubuntu freezes on me...and I hear a faint rhythmic "clicking" sound from the hard drive.  Over and over.  Can't log out or anything so I push the button to turn the power off.  Try to reboot---"click click", error 16 on GRUB.  Dead in the water again!

Back to Dell chat room, they are sending me another replacement today.  NOW I go online and find this thread.

Is it coincidence that I've had two drives fail me within a year?  Could be.  However, since the machine always clicked upon shutoff in Ubuntu, never occurred in XP, clicked at me in the same manner before the first one froze up and clicked at me now that the 2nd one is dead, I suspect that this issue is a reality. 

If only I had looked for this thread before the zip drive-like "click of death" came to visit me the 2nd time... ;(

---

### Post by fredj on 2007-08-24
It is a software issue and more than that it is a kernel issue so it has been found in all Linux
distributions. Apparently it's been fixed in the .22 revisions of the kernel. You were unlucky to
have more than one hard disk failure but I think this is probably the cause. 
Its interesting to see how furious some people get when you suggest that there is a serious
bug in Linux and to see their insistence that the same bug exists in windows, it doesn't.
Windows has its own bugs.

---

### Post by fredj on 2007-08-24
Spier 
What a depressing person you are!
Hope they don't make many more like you!

---

### Post by schultz on 2007-08-25
GNU Linux is the best OS I have ever used. It is efficient, secure, well designed and respects the user. And do you know why? It is because it was made by "people like us" to "people like us", not by a billionare dirty marketeer and his money sucking team.

In history there is something I would change: the World War the first should have been won by either Germany or Russia (WW I, not WW II). US has thrown upon the world the idea that possessing is more important than studying, knowing or even being. Capitalism in its most pure form is the source of all this evil. It makes a rich guy (even if evil) be worth more than a hundred dedicated people with not so much money.

Mathematics, on the other hand, has always been free for 3000 years or more (definetly before linux or FSF). The computers we all use is a fruit of more than 3 milleniums of intense work in the area. All the results in mathematics are free for anyone to know. Those guys are really nice, they look to another person as a friend, a brother, a human being, not as an idiot animal to take money from, like MS does.

Pursuing having profit above all, Microsoft makes dirty deals with PC manufactures so that they close their hardware specs to the world except for Microsoft. This occurs mostly on laptops, a powerful market. And they do it to eliminate rivals. But they forget: linux is not a rival of Microsoft, we are in another business. Linux has nothing to do with M$, it is another thing. But pursuing maximum profit, they hurt our drives, computers and freedom every single day, those bastards. They do not seek to develop the world, as we from the free comunity or the mathematicians, they seek to have it for themselves because they think they are superior to us.

Linux is well designed and bugs like this are not kernel's fault. The kernel is good, it just has not enough info to behave correctly. And this is a fruit of making mathematics (and knowledge) private. Think well, Bill Gaytes sell us Windows, which uses mathematics,  computing theory results, open programming languages (C++) and many free knowledge, but he sells it as if he had discovered it all, as if it was all his, he pays no "royalties" to the billions of people worldwide along those 3000 years which have done most of Windows (if you think about it). He just packed most of the public knowledge and sells it to the same public as if we were retarded. And many of us are, but as we live in democracy (source of much evil, too), those retardeds dictate the laws.

World is too complicated, let me go back to my mathematics...

---

### Post by joewilliams on 2007-08-25
> ...let me go back to my mathematics...


please do.

---

### Post by dabl on 2007-08-25
> **joewilliams said:**
> please do.

Second the motion ... one can only shudder at the notion of the Soviet Union prevailing in the early 20th century ..... I might have nightmares tonight!  :lolflag:

---

### Post by jernau on 2007-08-26
I was reading through this thread, and wanted to mention something that I believe will fully resolve this problem --

Seagate is going to start offering solid-state drives in 08, so as long as your HDD can hang on for that long, you can solve the problem AND be bleeding edge.

:guitar:

---

### Post by Johnsie on 2007-08-26
I had one hp pavillion ze4400 laptop hdd burn out. It had ubuntu installed and the hard disk eventually stopped working.

---

### Post by schultz on 2007-08-26
Now that you said that I am worried.

I have a hpze4950 laptop with Kubuntu installed.

Can you tell me how much time it took to Ubuntu to kill your drive?

---

### Post by Liolikas on 2007-08-26
I used ubuntu for more than two years and my PC still working fine now.

---

### Post by Liolikas on 2007-08-26
On other pc I used windowsXP and hdd was replaced one year ago.

---

### Post by viking777 on 2007-08-27
Attention all clickers and poppers out there, I do believe (for me at least) that the problem has been solved. The script mentioned in this thread made no difference whatsoever to my 'popping' problem and neither did kernel 2.6.22-9, however I recently upgraded to 2.6.22-10 and this does cure the popping problem 100%.

I should say that I still can't shut down normally (ie it still hangs and I have to hold down the power button), but at least I am not presented with this sickening popping sound when I do so. 

Who knows, another couple of kernel upgrades and I might be able to shut down linux normally for the first time ever on this machine! 

Fingers crossed.

---

### Post by jso2897 on 2007-08-27
I wouldn't worry about this guy and his FUD. The first paragraph of his post reveals him to be so far out of touch with reality that one would be extremely foolish to listen to anything he has to say about anything. He's probably a paid shill for Redmond anyway.:lolflag:

---

### Post by DarkN00b on 2007-08-27
You're hard drive is fine. The control arm on all modern hard drives is designed to aerodynamically "float" on a cushion of air turbulence created by the spinning disc. If power is lost before the arm can be parked, it is snapped to the rest position by the built-in magnets on the pivot end of the arm.

Read about it on [Wikipedia's hard drive entry]("http://en.wikipedia.org/wiki/Hard_drive"). See section 5.1 which explains this process.

That's what you're hearing, the read/write heads are never making contact with your disc. If it were, the disc would not last very long at all and I have been using mine for over a year. FSCK has never found a problem with my disc.

---

### Post by schultz on 2007-08-27
The whole point is, again (perhaps for the fourth time), that whether damage is caused to the drive is not important. The sound is ugly and must be removed.

---

### Post by devi on 2007-08-27
Thanks for this thread. I had a HDD die in a refurb laptop after Xubuntu install... figured I got a lemon. Got a new drive two weeks ago. Just ran this script... silent shutdown, when before I got the click. I was totally unaware of the issue and ran across this thread searching for something else!

---

### Post by rrastogi85 on 2007-08-28
hi ...I am realy new to Ubuntu and this is my first post here in the forum.....

i am working as a student lab asisstant ....I have been asked to take server backup and to keep that in a hard disk attached to that.

I tried installing the graphics mode but it was really not a successful attempt, so I have to do the backup process by textual commands. I have read the command to take backup here.

But i dont know how to reach the one empty hard disk in the server (i am on server only) to put the TAR file  of the backup.

I am looking for suggestions on taking backups ; commands for detecting hard disks in the system and how to finally transfer the backup file to that purposely kept hard disk.

thank u !!

---

### Post by nick_h on 2007-08-29
You would be much better starting a new thead for this. Perhaps in *Absolute beginner talk* or *General Help*.

[Howto: Backup and restore your system!](http://ubuntuforums.org/showthread.php?t=35087) may be of interest.

---

### Post by KurtReidar on 2007-08-31
I'm not sure this is such a wide spread problem, but i does happen with my USB hd. A little eMagic box with 2,5" HD. When I use sleep in Feisty it's still spinning (using all my battery :mad:). But windows on the other hand shuts it down when going to sleep mode.:)

---

### Post by rzrgenesys187 on 2007-08-31
> **Tzalidar said:**
> I have also experienced this problem with 7.04 on my Fujitsu Siemens Amilo M1425.

The following workaround did the trick for me:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60)

This worked for me as well

---

### Post by mgpower0 on 2007-09-01
[http://linux-ata.org/shutdown.html](http://linux-ata.org/shutdown.html)
[https://bugs.launchpad.net/ubuntu/+s....20/+bug/72765]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/72765")
[https://bugs.launchpad.net/linux/+bug/63937](https://bugs.launchpad.net/linux/+bug/63937)
[https://bugs.launchpad.net/ubuntu/+s...37/comments/22]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/63937/comments/22")

You could have at least read the first 2 pages:???:

---

### Post by Zef_ on 2007-09-01
> **JonD25 said:**
> I think I might be having the same problem on my Dell D600. Ever since I upgraded to Feisty, I noticed whenever I shut down, it would make a weird sound. I recognized it as the same sound my hard drive makes when I need to do a hard shut down by holding down the power button, like it's spinning down unexpectedly.

Yes I have noticed this too with my laptop every time I shutdown. With XP on this laptop that never happened. When is this issue going to be addressed? I can't afford to have my hard drive running a risk of being damaged.

---

### Post by Vorian on 2007-09-01
thread closed for a cooling off period

---

