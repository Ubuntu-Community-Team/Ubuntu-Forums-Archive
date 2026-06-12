---
title: "Ubuntu 22 in &quot;try&quot; mode: video is greyed"
date: 2022-05-27
forum: Hardware
---

### Post by ibobak on 2022-05-27
There is a bug in the video driver or in Gnome in Ubuntu 22:  I launched in the "try ubuntu" mode and here is what I see:



[URL="https://ibb.co/GPVqQBK"]
[/URL]





I have Ubuntu 20 for more than a year, and everything is good with it. 
CPU: AMD Ryzen Threadripper 3990X (128) @ 2.900GHz


Parameters of the video card:[URL="https://ibb.co/DCGFZm1"]
[/URL]

---

### Post by QIII on 2022-05-27
This forum allows you to use the attachment facility (the paperclip icon) to attach an expandable thumbnail image in your text when you make a post.

Please edit your original post to do so.  You will need to click Edit and then Go Advanced since you have already posted.

---

### Post by zebra2 on 2022-05-28
I booted kinetic ISO May 27th into "try" mode and I get full color and what I would normally expect to see. I have been using kinetic since day one with no problems at all. Incidentally if a person wanted to download the 3.7G kinetic installer and is limited on bandwidth you can save 1.3G by zsyncing over the Jammy ISO if you happen to have a copy. FYI.

---

### Post by ibobak on 2022-06-03
I have no idea what is "kinetic ISO".  I just downloaded the image which is official, launched and got this. 
The goal of this post was to make so that maybe someone from Canonical will see this and will react somehow.

I've got an idea to switch on Fedora after getting this. Sadly, but if I try the 1st service release and will get the same - I will switch.

---

### Post by coffeecat on 2022-06-03
> **ibobak said:**
> I have no idea what is "kinetic ISO".  

Kinetic Kudu is the code name for the next version of Ubuntu, 22.10, which is still in very early development. You wouldn't want to use Kinetic for routine use, but zebra2's is an interesting observation. You will have an earlier kernel in the 22.04 live session, which will probably have an earlier version of the open source driver for nvidia cards. You appear to be using a fairly recently released nvisia card, so it's quite possible the nouveau driver in the 22.04 ISO doesn't properly support that card, whereas the driver in the 22.10 ISO as of 27th May does. Rather than a "bug" as you assume, it's possible that your card is just too new for the version of the driver in the ISO that you are using. If you were to install from your 22.04 ISO and upgrade the kernel, or install the proprietary driver, you would probably get better performance. I'll stop there because I have no recent experience of nvidia - I avoid nvidia now - so perhaps someone more versed in nvidia may be able to comment.  

> **ibobak said:**
> The goal of this post was to make so that maybe someone from Canonical will see this and will react somehow.

They won't. This is a peer to peer support forum consisting entirely of volunteers, end users all, forum staff included. We are not employed by Canonical. If you want to report a bug, you would need to do so on Launchpad although, as I've already impied, I personally wouldn't think of this as a bug.

---

### Post by sudodus on 2022-06-03
Please tell us more about your computer. It will help us help you.

One good way is to download and run the [system-info script](https://github.com/UbuntuForums/system-info/) of the Ubuntu Forums in your working version of Ubuntu and let it upload the result to a pastebin. After that you can post a link to the pastebin in a new reply of this thread.

Edit: As a first attempt, try to boot your live Ubuntu system with the boot option 'nomodeset' that might help with the nvidia graphic card. There is help for it in [this link](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808).

---

### Post by zebra2 on 2022-06-03
Re: Kinetic
Since this thread was created in the Development section of the forum I presumed that the discussion regarded 22.10. I reported on the my test boot of the 22.10 ISO which worked just fine.  In addition, if there was a problem with the 22.04 ISO i am certain it would have been reported by now.  The current release seems to be pretty popular. I used 22.04 for the entire cycle and had no problems whatever. I have no experience with Nvidia so missed that completely.  But Nvidia is a continuous problem here, and it usually gets fixed somehow. It makes sense to me to run the installation and get the drivers installed.

---

### Post by coffeecat on 2022-06-03
> **zebra2 said:**
> Since this thread was created in the Development section of the forum 

You're quite right - thanks for pointing that out. For some reason I thought this was in General Help when I posted and assumed the OP meant 22.04 when they specifided "22". Lack of attention on my part - my apologies.

I note, though, that on April 24th, the OP stated that they were using 22.04.

@ibobak, please clarify whether you are referring to 22.04, or to 22.10 in this thread. Also, I notice in your [earlier thread]("https://ubuntuforums.org/showthread.php?t=2474209") you asked for your observation to be forwarded to the developers. As I implied before in this thread, it's not the responsibility of the volunteer members of the forum to do that for others. If you find a reportworthy bug, please report this yourself. Member sudodus provided a useful relevant link in your earlier thread.

---

### Post by ibobak on 2022-06-16
I was referring 22.04.  

system information:    [URL="https://paste.ubuntu.com/p/j6mMNrGjyx/"]https://paste.ubuntu.com/p/j6mMNrGjyx/

[/URL]Please, note:  currently I am running Ubuntu 20.04, and system-info was launched under 20.04.   
But the problem which I am reporting is in the 22.04 - when launched via USB in "Try" mode.

---

### Post by ibobak on 2022-06-16
I'd be also happy to know how and where to report for bugs to developers of Ubuntu?  
What is the correct place (forum, e-mail, bug tracking system)?

---

### Post by sudodus on 2022-06-16
Thanks for showing the result of the system-info script :-)

It is a powerful computer. I was impressed by the amount of RAM.

I think we can conclude that the problems are related to the nvidia card, that the driver in Ubuntu 22.04 LTS does not cooperate well with the card and or with the desktop system.

- Have you tested (in the live Ubuntu 22.04 booted from USB) with the boot option **[FONT=Courier New]nomodeset[/FONT]**? It can be a first test.

- If/when you get better graphics, you can try installing Ubuntu (into a separate partition or separate drive), apply **[FONT=Courier New]nomodeset[/FONT]** also to the installed 22.04 system, and as a **next step try with an nvidia proprietary driver**.

- If still problems, **switch from Wayland to Xorg**, because I know of several cases where nvidia graphics have problems with Wayland.

---

### Post by sudodus on 2022-06-16
> **ibobak said:**
> I'd be also happy to know how and where to report for bugs to developers of Ubuntu?  
What is the correct place (forum, e-mail, bug tracking system)?

[Launchpad](https://launchpad.net/) is the correct place for bug reports. Get a member account at Launchpad, and then you can run the command

```

ubuntu-bug

```

---

### Post by coffeecat on 2022-06-16
> **ibobak said:**
> Please, note:  currently I am running Ubuntu 20.04, and system-info was launched under 20.04.   
But the problem which I am reporting is in the 22.04 - when launched via USB in "Try" mode.

Both 20.04 and 22.04 are current non-development releases, and therefore this thread does not belong in the *Ubuntu Development Version* sub-forum. Sudodus' suggestion that this is a video card/driver issue in 22.04 seems a good one, so I've moved this thread to the *Hardware* sub-forum, which is the appropriate place for video card problems in released versions of Ubuntu.

Good luck with finding a solution.

---

