---
title: "The panel encountered a problem...."
date: 2008-08-20
forum: General Help
---

### Post by ooolongT on 2008-08-20
Let me first say that I am a noob, but have been trying for some time to get Ubuntu working on various machines and can never seem to get it to work.  I go back to Windows, but I always come back since I can't stand using it!  

Therefore, I recently installed 8.04, and things were looking good.  It recognized my network card (finally) and I was off to the races. I did a few things to customize the look of it, but only simple things; changed the location, size, and contents of some of the panels, changed the background, etc.  Just want it to feel like home.  But now I have run into a problem when I start Ubuntu.  I get pop-up messages that say:

Panel encounterd a problem while loading "OAFID: GNOME_NetstatusApplet"

Panel encounterd a problem while loading "OAFID: GNOME_MixerApplet"

There is another one as well that comes up sometimes, but I don't remember that one right now. 

A few things about this issue, it seems to be an intermittent problem in that it does not occur every time I boot the machine, however, I just tried three times and I got those  messages each time.  The result of this is that I have no network connectivity, and I am sure that if I tried to use the mixer(whatever that is), I would have problems with it as well. :confused:

After trying a few things I found this bug from a while back: [https://lists.ubuntu.com/archives/desktop-bugs/2006-April/025864.html]("https://lists.ubuntu.com/archives/desktop-bugs/2006-April/025864.html")
Unfortunately, it doesn't offer a solution.

So, I decide since restarts are not solving mt problem (nor should I have to restart to solve problems, this is supposed to be BETTER than Windows, no?) I will try to shutdown completely, and  when I do I get this:

Network Manager: <WARN> nm_signal_handler():Caught signal 15, shutting down normally

Network Manager: <info> caught termination signal

Network Manager: <debug> [121954209.073846] nm_print_open_socks(): Open Sockets List:

Network Manager: <debug> [121954209.074040] nm_print_open_socks(): Open Sockets List: Done

Network Manager: <WARN> nm_hal_deinit():libhal shutdown failed - Did not receive a reply possible causes include: The remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired or the network connection was broken

I realize I may be including details from more than one problem here, but I am not sure what is related to what, so I tried to be comprehensive.  If there is more information you need to help me solve this, please tell me where to find it, as I said, I am something of a noob, so I can probably get to it, but I will also probably not know where to look!

Thanks in advance!

One last thing, I considered just using KDE instead and could not get Synaptic to launch from a menu, but was able to open it from the command line.  Necessary detail?  You tell me :)  Anyway, I have decided I want gnome to work, and not use KDE.

---

### Post by ooolongT on 2008-08-20
I realize my post may have been a bit verbose, but as I said I was trying to be comprehensive. 

Can anyone help me with any part of my problem?  You don't have to have all the answers, any suggestions are welcome!!!

---

### Post by mb_webguy on 2008-08-20
> **ooolongT said:**
> Panel encounterd a problem while loading "OAFID: GNOME_NetstatusApplet"

Panel encounterd a problem while loading "OAFID: GNOME_MixerApplet"
This looks like you've either uninstalled a couple of the applets (the packages gnome-netstatus-applet and gnome-applets_ that are on the panel, or something's gone wrong with the applets.  Try reinstalling the applets using Synaptic.

As for your network manager problem, I'm not terribly sure.  You may want to repost that part with a more descriptive subject.

HOWEVER, if you've done as little to your installation as you've said, it could be that there were problems with the installation disc.  Since you probably wouldn't lose much at this point except 30 minutes of your time, you could try reinstalling Ubuntu.  Try downloading and burning a new copy of the installation disc (and make sure you get 8.04.1, and not 8.04), and make sure that you check for disc errors at the LiveCD menu before you reinstall Ubuntu.

---

### Post by ooolongT on 2008-08-20
Whew!  Thanks for replying MB!  I will try suggestion 1 first - reinstalling, then option 2 If I have no luck.  Regarding option 2 do I need to uninstall Ubuntu before using the new disk?  If so, how do I go about that?

Oh, and I found the MixerApplet but I am not sure which package the NetstatusApplet is, any insight?

---

### Post by ooolongT on 2008-08-20
OK, well the good news is that I did not get the same error messages this time!  YEAH!  Thanks MB.  

However, I still have no connectivity even though the little yellow light on the nic card is blinking...

---

### Post by ooolongT on 2008-08-21
Ok, hated to do it, and forgot to move a few files, but I just reinstalled Ubuntu.  I am a much happier person for it.  Since the reinstall, no problems whatsoever, except one that I think is a Firefox issue.

---

