---
title: "Ubuntu on OQO Model 2 Installation Help"
date: 2011-05-06
forum: Hardware
---

### Post by Fualtycannon on 2011-05-06
Hello Ubuntu community, I am in need of a lot of help. I have looked around a lot in regards to finding a Linux distribution that would work for my UMPC, the OQO Model 2. I have downloaded and tried to install many flavors and versions, but have yielded no results. I do not know what is wrong, or why my installations don't work. I am really new to Linux, but I know enough to get around. This is the machine I am trying to get running with Ubuntu (Any Version is okay) or any other flavor.

Computer: OQO Model 2
Processor: VIA C7-M (aka: Esther) [Tech: 90 nm] [Socket: nanoBGA2] @ 1600MHz
Motherboard: OQO Model 2 [Board Revision: C] [Chipset: CX700/VX700 Series SP] [Graphics Interface: AGP]
Memory: DDR2 1024MB  @ 266MHz
GPU: VIA/S3G UniChrome Pro II IGP.

It comes with a dock that adds a DVD Drive, extra USB Ports, VGA output, Audio Line Out, and an Ethernet Port.

The only Operating System I've tested that work is Windows XP, Windows Vista, and Damn Small Linux.

After reading on the internet for a long time, I am convinced that maybe the issue with the Ubuntu on the OQO Model 2 has something to do with the graphics.

Any support anyone has that will help me find or make a flavor that can work for my computer and take advantage of all it's features is welcomed. If you want more information on the computer, I can install and upload more information if you know of any programs that can offer more then CPU-Z.

---

### Post by varunendra on 2011-05-07
Welcome to the community and the forums!

I think you've provided sufficient info above. Type and connection mode of HDD could have been additional help. Just to make sure, is this your system? :-

Images:
[http://www.laptopmag.com/review/newgallery.aspx?id=9625](http://www.laptopmag.com/review/newgallery.aspx?id=9625)

Specs:
[http://www.laptopmag.com/review/laptops/oqo-model-02.aspx?mode=specs](http://www.laptopmag.com/review/laptops/oqo-model-02.aspx?mode=specs)

Now let us know a bit more about your experience so far:

[LIST=1]
[*]Please mention the flavours you have tried so far (with their versions if possible). Since DSL (Damn Small Linux) is a debian based distro, I think Ubuntu, maybe with some required tweaking, should work. Besides, I'd give these a try: SLAX (just for testing), Lubuntu, Mint 9 lxde, Open Suse, Fedora (with gnome).
[*]What kind of media (Live CD/USB) and methods you've tried and what were the errors (if any) you got?
[*]Have you tried Alternate CDs yet?
[*]Have you tried advanced boot options in Live CD? (Press "shift" during boot up, then F6 to select "acpi=off, noapic, nomodeset" etc.)
[/LIST]
You said: > I do not know what is wrong, or why [COLOR=Red]**my installations don't work**[/COLOR]. so I assume that you probably succeeded in installations at least a few times, and then didn't get screen (or some other problem) after restart.

If this is the case, did you try "Failsafe Graphics mode" in 'Recovery Mode'?

**Bottomline is:** literally and specifically stating what you tried and errors you got would help narrowing down a solution for you. Since DSL worked, ubuntu should too.

---

### Post by Fualtycannon on 2011-05-07
I am pretty sure the hard drive is a SATA, but I do not know its RPM's.

The image is correct, my OQO looks exactly like that. The hardware is correct as well, except my clock speed of my processor is @ 1.6GHz.

I have tried Ubuntu 8.04, 9.04, and 10.04. I have not tried the recent 11.04. When the installations did finish, the OQO would boot, make it to GRUB, and then hang at a black screen shortly after I selected the OS of choice.

My method of installation is the Linux Live USB Creator, with a 4GB flash drive or a 1GB Flash Drive.

I have never tried alternative installations, I have only tried the primary choice when you download Ubuntu from the main website.

I have not tried booting with the shift option. However, I will ready a flavor and begin trying. I did not know you could use these options by pushing the shift key on boot.

Thank-you for your time and help, it is MUCH appreciated! And the quick response was great :D I will post any errors in a while after I try installing again within the next few hours.

---

### Post by Fualtycannon on 2011-05-07
]Here are the results:

I tried installing Ubuntu 10.04.2 Lucid Linux with a 4GB flash that was prepared by Linux Live USB Creator.

I just tried normally to see what would occur. Like usual, it didn't work. One time it hung at a green screen, the second time it got stuck and hung at some code.

This is the last thing that looked correct:

> [   8.012921] Linux agppart interface v0.103

And then is displayed this:

> Busybox v1.13.3 (Ubunutu 1:1.13.3-iubuntu11) built in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs) Unable to find a medium containing a live file system

I noticed that in order to scroll down, I had to keep hitting return until the code flowed up to my section. So that means it isn't fitting my screen size either.

I then tried holding shift and typing in the commands you said and got this error:
 > SYSLINUX 3.86 2010-04-01 EBIOS copyright (C) 1994-2010 H. Peter Anvin et al
Unknown Keyboard in configuration file: gfxboot
boot: acpi=off
Could not find kernal image: acpi=off

I received the same errors when trying to install 11.04. When the installation menu finally got up and running, it was just a load of wavy tearing lines, and I could not distinguish anything I saw.

---

### Post by varunendra on 2011-05-08
Oh no! Looks like I badly confused too many things in that previous post of mine, and worse even, I seem a bit too late to catch up with you.

Alright, I'll try to put up things as clearly as I can this time..

> **Fualtycannon said:**
> 
I then tried holding shift and [COLOR=Red]**typing in the commands**[/COLOR] you said and got this error:....
 
The "hold shift key, then press F6" trick was meant to be used in the live mode, not in the native installation.
That is, when you boot from a Live CD or a Live USB, it by default takes you (in a few minutes) directly to the screen where it asks you to "Try" or "Install" the OS. BUT.... if you press and hold "shift" key much before that screen, when the booting (from CD or USB) had just started, then those advanced options would appear where you are first asked to select a language to proceed with, and then occurs the menu where "Try, Install,...etc." options are listed, and in the bottom of the screen are the different options associated with F1, F2,..... F6 keys.

In that screen, if you press F6, a menu will pop-up with those options I mentioned (acpi=off, noapic,..... etc.). You just have to select desired options (by highlighting them using up/down arrow keys, then pressing 'spacebar' to put a cross mark before it as an indication of selection), no need to type them anywhere (it automatically happens in the background, in appropriate manner). I suggest to select acpi=off, noapic and nomodeset altogether. Although you may try other options also.

Now here's the catch (that is making me look utter stupid for making that unnecessary explanation above)! You mentioned that
> When the installations did finish, the OQO would boot, make it to GRUB,  and then hang at a black screen shortly after I selected the OS of  choice.which means you had no problems while being in the live mode. All the trouble begins only after installing it to the hard disk! Right?[B]

Please confirm this:-[/B]
Does the OS work flawlessly in the Live mode? (when you are using it from the USB/CD)
If so, then you don't need any of the above exercise at all!! All the above stuff (choosing advance F6 options, or installation from alternate CD) is meant for those who don't even get to the GUI in the Live mode, and hence can not proceed for installation.

Now if you are able to make it to the Grub menu where a list of OS/Options is presented to choose from, there is an option to boot in (recovery mode). Select that option and then, in the subsequent menu, select "failsafeX" (Safe graphics mode). This is not a guaranteed way to get GUI, but does work most often when the problem is caused due to wrong driver/graphics configuration. If this doesn't work, try "dpkg" option in the same list while you are connected to internet and reboot.

Bottomline is: if you are able to use GUI in Live mode, then there is no reason why it should not work after installation.

Sorry if I made it too long (my worst habit perhaps). We can try one step a time if you wish.

---

### Post by Fualtycannon on 2011-05-08
I do not successfully boot into the live mode. If I get anywhere close to booting, I get the screen tears. When I push F6 at the installer menu that says live mode, install, File Integrity check, it does nothing, and the advanced options selection doesn't have anything in it.

---

### Post by varunendra on 2011-05-09
> **Fualtycannon said:**
> I do not successfully boot into the live mode. If I get anywhere close to booting, I get the screen tears. When I push F6 at the installer menu that says live mode, install, File Integrity check, it does nothing, and the advanced options selection doesn't have anything in it.

Then how did you manage to install it? And are "Live Mode", "File Integrity check",.... the exact words that the menu displays?

I know it shouldn't matter what words are used but it makes me believe that perhaps you used some version much older than 10.04, because all the Live ISOs I have (9.10 to 11.04) display these options as "Try Ubuntu....", "Check Disc...." like in the screenshot below:
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/UbuntuStudioMaverick-2011-05-09-16-47-12.png[/IMG]


And did you try the Recovery mode options from Grub menu of installed version? (if you are still able to get there of course):
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/UbuntuStudioMaverick-2011-05-09-17-03-41.png[/IMG]

I thought if we can anyhow get to a working mode (Installed, Live, GUI, CLI,.. whatever) then we could get more info about X configuration and driver modules in use, and could also change them as required. Such as following these tricks suggested in another forum ([http://www.oqotalk.com/index.php?topic=3287.45](http://www.oqotalk.com/index.php?topic=3287.45))
> Make sure you have a line like:
blacklist via_agp 
in the file /etc/modprobe.d/blacklist
or you can try switching to the "vesa" driver in your /etc/X11/xorg.conf

Hope you're not too frustrated to try ahead! :)

---

### Post by Fualtycannon on 2011-05-09
I installed it a long time ago with an old friends installation drive. I don't remember anything about it except the fact that it didn't have a GUI.

My installation method does have those terms for options.

Well, I am making Live USB drives with Linux Live Creator. My image is downloaded directly from the Ubuntu Page. Where do you get your image, and how do you create your installation?

Also, I am really eager to learn, so I think my patience can uphold. Thank-you for taking the time to help me with this!

Also, the OQO did come with a docking station that allows me to have access to a DVD Drive.

---

### Post by varunendra on 2011-05-13
Sorry for a late response, but some of your replies have got me pretty confused. So unless you make facts absolutely clear now, I'm unable to conclude anything about your problem or a possible solution. I may get even more busy from now on, possibly not being able to reply soon again, so I'll put all my questions and suggestions in this one post (and you'll have a plenty of time to read & understand it).

Your summary so far:
> **Fualtycannon said:**
> I have tried Ubuntu 8.04, 9.04, and 10.04..... [COLOR=Red]**When the installations did finish**[/COLOR], the OQO would boot, make it to GRUB, and then hang at a black screen shortly after I selected the OS of choice.
> **Fualtycannon said:**
> [COLOR=DarkRed]**I do not successfully boot into the live mode**[/COLOR]. If I get anywhere close to booting, I get the screen tears.
> **Fualtycannon said:**
> [COLOR=Red]**I installed it a long time ago**[/COLOR] with an old friends installation drive. I don't remember anything about it except the fact that it didn't have a GUI.
To me, the statements - "[COLOR=Red]**When the installations did finish**[/COLOR]",[COLOR=Red][/COLOR]"[COLOR=DarkRed]**I do not successfully boot into the live mode**[/COLOR]"[COLOR=DarkRed][/COLOR]and "[COLOR=Red]**I installed it a long time ago**[/COLOR]"....[COLOR=Red][/COLOR]seem contradictory. First I had impression that your current attempts to install 8.04, 9.04, 10.04 did succeed somehow. And since you had not tried alternate CDs, so you must have had GUI in live mode to do so.:-k

But now it seems that you successfully installed it only once 'a long time ago' without GUI (and you didn't make clear which version it was). Because if you didn't have GUI in the live mode, and didn't try alternate CDs either, then you simply can not finish (even start!) installation as far as I know. But I may be missing some other aspect which you may bring to my notice.

Perhaps I'm failing to ask correct questions or in a correct way, so please consider stating 'everything' again, from start upto now (except hardware details as this one is absolutely clear), providing all the details in the order they occurred.

For now I'm assuming that none of your current installation attempts succeeded to even start the installation process, nor did you ever have GUI beyond startup menu in the live mode so far. Please do not try to confirm or correct me. Instead, you'd be better off stating everything clearly and systematically again - from beginning upto now - as I said before.

Umm.. I think I should also make clear that it is not a frustrated reply and I'm absolutely cool with it. It's just that I'm not able to make any conclusions from your statements so far as they seem confusing to me.](*,)


Now let's make my post a bit productive now....
> **Fualtycannon said:**
> Well, I am making Live USB drives with Linux Live Creator. My image is downloaded directly from the Ubuntu Page. Where do you get your image, and how do you create your installation?
I also download from their official page, but from alternate methods, using torrents:
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download) (for currently supported versions)
and..
[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/) (all available versions)

I always use a CD/DVD to install it on a physical computer (most often I install them on virtual machines, directly booting the downloaded ISOs). I prefer Live USB only for Live mode, although I've also used them for installation a few times and had no problems (except in Mint KDE once). I use "Live USB Creator" provided in the Live CD to create Live USB flash drives.


> **Fualtycannon said:**
> And then is displayed this:
> Busybox v1.13.3 (Ubunutu 1:1.13.3-iubuntu11) built in shell (ash)
 Enter 'help' for a list of built in commands.
 
 (initramfs) Unable to find a medium containing a live file system
It seems the boot process is unable to detect the flash drive. It happens sometimes. Solution ranges from altering BIOS USB settings to changing flash drive itself (different brand), or using different methods to create the Live USB. But I think trying a CD should be easier. Sometimes (especially in OQO models) it may require changing IDE settings in BIOS.

> **Fualtycannon said:**
> The only Operating System I've tested that work is Windows XP, Windows Vista, and [COLOR=DarkRed]**Damn Small Linux**[/COLOR].

Do you get GUI in DSL? Is it fully functional? If yes, then it may help in further troubleshooting. But first, clear and complete statements please.... [-o<

What is the current status of your OQO? Does it have any working OS that we need to be careful about while trying things? If not, then give 10.04 alternate CD (not USB) a try before posting this time. First we need a working installation of a desired version even if it is without GUI. We can try GUI solutions later on top of it.

---

### Post by Fualtycannon on 2011-05-13
Hey, I'm really sorry about the confusion. This should help straighten my installation history.

The Installations that worked were text based installers. Some of them only worked as a text based OS, while some did not boot at all. These were installations my friend prepared and gave to me to try. They should have been of the Ubuntu family in accordance with whichever one was recent. I did not know if they were alternate installers, if they are, because my friend prepared him, since he knew his way around Linux. Normally if I had trouble I talked to him. But, he isn't around anymore, so that why I am in the forums asking for help.

The above is my only installation history.

The not booting into Live mode is recent, with my own downloaded copies of Linux, from the page, using my own installation methods. These are all based on my own experiences without someone holding my hand showing me how to make a CD and everything. Like I said, I know enough, but Im still new to this.

11.04, 10.04, 9.04 and 8.04 have been attempted all from a Live USB. These installers never made it through. They displayed the errors I quoted in the text, and some of the others made it to a screen tear or solid color screen with nothing on it.

So from this point down, were just going off the fact I can't get into live mode using a flash drive.

Here is some recent information attempts. I will post anything else I try until you return, if you return. I am really sorry about the confusion. 

Here is another attempt. I burned 11.04 to a disc. I installed on another computer to make sure the disc worked at all. After it worked, I tried the instllation on the OQO Model 2. It didn't even go to a grub screen. It just started loading with the Ubuntu name and the dots underneath it that load by changing colors. Then is took me to a terminal I presume. And I walked away for a bit, and now I'm screen tearing again. So I turned it off. What I am going to do, is run the installers again, with an external monitor plugged in. Maybe I wont get screen tears if I'm on a decent resolution. If the installer makes it through, I can try to optimize it for the small screen. 
 
If I fix it before you get back, then I will edit my first post and put the answer to making it work under the problem, and figure out how to mark it solved.

Again, really sorry about the confusion, and thank-you for the help. If it is a screen size problem, the monitor is a good start.

[Edit]

Yes, Damn Small Linux gave me a gui. But I didm't have Wifi, so I couldnt get on the internet. I also didn't know what I could accomplish with it, without internet, so thats why I decided to try Ubuntu, because It has an interface I am familiar with, and more supported hardware, a great support team, and hopefully some WiFi features.

---

### Post by varunendra on 2011-05-13
Hi,

Good that we both are online now.

No problem with the confusion, I truly believe that it was my incorrect way of asking questions. :)

Now given that the performance of a UMPC is limited, I'd suggest to try  10.04-desktop (32 bit) alternate CD. Download it using torrent from the  link I provided. It is also LTS (Long term support) and much more stable than 11.04 currently is.

Alternate CD is not a Live CD, and does not use GUI for installation,  but after installation, it is same as installing from a Live CD (with GUI and  everything). But try this only if you have nothing to lose on your  UMPC, else be careful while selecting destination for installation (if  you reach to that stage at all!!) ;)

Lastly, I'm no expert, just a learner like you with maybe slightly more experience with  Ubuntu, so will try things with you, but can't assure anything.

And yeah, the separate monitor sounds good!

Cheers!

**PS:**
From DSL, we may confirm which driver module and display mode it is using. Applying the same on Ubuntu may provide a usable GUI.

---

### Post by Fualtycannon on 2011-05-13
I'm downloading the alternate installers right now. I am getting the i386 and amd64 to see if either version will work. They will both be burned to discs. I made sure is was the 10.04 LTS edition. I will be burning the copies right now, while testing the external monitor idea.

This will definitely be a good learning experience for me!

---

### Post by cjcardinal on 2011-09-20
> **Fualtycannon said:**
> I'm downloading the alternate installers right now. I am getting the i386 and amd64 to see if either version will work. They will both be burned to discs. I made sure is was the 10.04 LTS edition. I will be burning the copies right now, while testing the external monitor idea.

This will definitely be a good learning experience for me!

I hate to revive this, but on the off chance you are subscribed, or still dealing with these issues, I succeeded today in a fresh, stable 10.04 LTS install and wrote up a how-to as well

good luck Fualty

[http://ubuntuforums.org/showthread.php?t=1847296](http://ubuntuforums.org/showthread.php?t=1847296)

---

### Post by stevencook17 on 2012-10-28
This is awesome! I looked and looked on here for an answer and no one had one, now I found your awesome post, thank you!!

---

### Post by overdrank on 2012-10-28
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

