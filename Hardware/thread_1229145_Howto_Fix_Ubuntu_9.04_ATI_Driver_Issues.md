---
title: "Howto: Fix Ubuntu 9.04 ATI Driver Issues"
date: 2009-08-01
forum: Hardware
---

### Post by jonathank89 on 2009-08-01
My guide is pretty straight forward, basically what it does is roll back your xserver to version 1.5 which is supported by the ATI drivers.

Guide:
[http://friendlytechninja.com/2009/07/30/howto-fix-ubuntu-9-04-and-ati-driver-issues/]("http://friendlytechninja.com/2009/07/30/howto-fix-ubuntu-9-04-and-ati-driver-issues/")

You should be up and running with compiz and all that fun stuff in no time!

You'll also notice at the bottom of the guide a link to another guide, this is a follow up on how to fix the video playback issues

[http://friendlytechninja.com/2009/08/03/howto-fix-ati-video-playback/]("http://friendlytechninja.com/2009/08/03/howto-fix-ati-video-playback/") (I did an update to his article [here]("http://friendlytechninja.com/2009/08/05/howto-fix-ati-video-playback-update/"))

Hope this helps out some of your guys.

Jonathan

**Edit:** In the main article I've added an extra step seeing as some people may run into an issue whereby they can't shutdown or restart via there username in the top right.

**Edit:** I updated the article on fixing the video playback issues for all media players, see [here]("http://friendlytechninja.com/2009/08/05/howto-fix-ati-video-playback-update/").

**Edit:** You'll have some video playback issues if you're using Totem, this can be fixed if you follow this [guide]("http://friendlytechninja.com/2009/08/03/howto-fix-ati-video-playback/").

**Edit:** I was informed there was a typo in the command in Step 4, which has now been **fixed**. I have also gone back and made sure that each command was correct. The rest where fine. Thank you Jim March for telling me.

---

### Post by Jim March on 2009-08-02
Typos in commands make this article worthless.  DO NOT USE UNTIL FIXED, FOLKS!!!

I'm pretty sure there's no such thing as "sesseion" but worse, it means he hasn't tested these exact commands.  DO NOT USE!!!

---

### Post by jonathank89 on 2009-08-02
> **Jim March said:**
> Typos in commands make this article worthless.  DO NOT USE UNTIL FIXED, FOLKS!!!

I'm pretty sure there's no such thing as "sesseion" but worse, it means he hasn't tested these exact commands.  DO NOT USE!!!

I have edited the post above and guide, I ensure you I have tested this method myself. Unfortunately I made a mistake, however thank you for telling me.

Regards,

Jonathan

---

### Post by pastalavista on 2009-08-02
I've tried fixing my ATI drivers and xserver many times and always ended up having to reinstall xserver-xorg. I think I'll wait until somebody with a few more beans verifies this.

---

### Post by jonathank89 on 2009-08-02
> **pastalavista said:**
> I've tried fixing my ATI drivers and xserver many times and always ended up having to reinstall xserver-xorg. I think I'll wait until somebody with a few more beans verifies this.

As you can see from the [screenshot]("http://friendlytechninja.vndv.com/wordpress/wp-content/uploads/proof.png") my xserver-xorg-core version is  1.5 you can also see that it's locked along with others. I'm also showing you that my ATI drivers are installed and working, hence the transparency effects in the terminal window and gnome-do docky theme.

---

### Post by pastalavista on 2009-08-02
OK, you convinced me. I'm going to try this as soon as I finish watching Top Gear and if it screws me up, I will send Ninjas to decapitate you.

---

### Post by gemini6 on 2009-08-02
Thanks Jonathan, I tried this and it seems working fine. I don't have graphics demanding application to run so may not be able to tell the truth.
I see ATI CCC in your picture. Did you also install ATI's latest driver as well?

---

### Post by pastalavista on 2009-08-03
Thank-you jonathan! it worked perfectly. I'm going to BUMP this so the mods will check it out and maybe make it a sticky.

Good job! Instead of Nijas I'll send some Geishas ;) I never worried much about eye-candy but thanks very much for giving me Google-Earth back.

---

### Post by gemini6 on 2009-08-03
I found a problem. After enabling the visual effect, video playback is not working properly. The video flickers. Do you have this problem jonathan?

---

### Post by szczym on 2009-08-03
> **gemini6 said:**
> I found a problem. After enabling the visual effect, video playback is not working properly. The video flickers. Do you have this problem jonathan?

Me too after downgrading to xorg 1.5.2 head problems with video playback. Now, after upgrading xorg to 1.6 and kicking out fglrx  i cant get desktop effects to work, various modifications to xorg dont seem to change anything... 

I opened new thread of it here:
[http://ubuntuforums.org/showthread.php?t=1230317](http://ubuntuforums.org/showthread.php?t=1230317)

Thanks for any info

---

### Post by jeb800e on 2009-08-03
I can't even get my Ubuntu 9.04 running off the LiveCD. Is there a way I can get it running without removing my graphics card?

---

### Post by jonathank89 on 2009-08-03
> **gemini6 said:**
> I found a problem. After enabling the visual effect, video playback is not working properly. The video flickers. Do you have this problem jonathan?

I've updated my original post, you'll see at the bottom of the guide a link to a new one on how to fix the video playback issue. It's pretty simple to fix.

Here's how to [fix it]("http://friendlytechninja.com/2009/08/03/howto-fix-ati-video-playback/"):

[http://friendlytechninja.com/2009/08/03/howto-fix-ati-video-playback/]("http://friendlytechninja.com/2009/08/03/howto-fix-ati-video-playback/")

Everything should work fine now.

I'll be doing some more testing soon with the new 9.7 drivers (which were release on the 23rd july 09), I hope they fix the video playback issues.

Hope that sorts out your problems

Jonathan

---

### Post by gemini6 on 2009-08-03
> **jonathank89 said:**
> I've updated my original post, you'll see at the bottom of the guide a link to a new one on how to fix the video playback issue. It's pretty simple to fix.

Here's how to [fix it]("http://friendlytechninja.vndv.com/2009/08/03/howto-fix-ati-video-playback/"):

[http://friendlytechninja.vndv.com/2009/08/03/howto-fix-ati-video-playback/](http://friendlytechninja.vndv.com/2009/08/03/howto-fix-ati-video-playback/)

Everything should work fine now.

I'll be doing some more testing soon with the new 9.7 drivers (which were release on the 23rd july 09), I hope they fix the video playback issues.

Hope that sorts out your problems

Jonathan
Yes that fix the problem! Thanks a lot.
But what interest me is that not only video playback is fine now, but also sopcast. I only changed settings in vlc....

---

### Post by jonathank89 on 2009-08-03
> **gemini6 said:**
> Yes that fix the problem! Thanks a lot.
But what interest me is that not only video playback is fine now, but also sopcast. I only changed settings in vlc....

Glad it worked! Kinda strange that it fixed the other player...maybe they share settings somehow? Have a look in the settings and look for a similar option that you changed in vlc.

---

### Post by peakshysteria on 2009-08-03
> **pastalavista said:**
> Thank-you jonathan! it worked perfectly. I'm going to BUMP this so the mods will check it out and maybe make it a sticky.

Good job! Instead of Nijas I'll send some Geishas ;) I never worried much about eye-candy but thanks very much for giving me Google-Earth back.

Cross my fingers to once again see a working howto on how to enable the latest ATI drivers. As mentioned in more than one thread in the forums earlier my card worked out of the box. Full effects and Google earth working smooth. Some games (i'm not a hard gamer) seems to play bad though.

How about sending some Ninja-Geishas instead? :D

---

### Post by pastalavista on 2009-08-03
> **jeb800e said:**
> I can't even get my Ubuntu 9.04 running off the LiveCD. Is there a way I can get it running without removing my graphics card?jeb, you could boot/install the 8.10 Intrepid Distro, lock all the xorg/ati files in synaptic and then upgrade to jaunty.

It's strange, after jonathan's fix, I locked the xorg & ati versions in synaptic, restarted and there was the flgrx driver back in Hardware drivers. I activated it and things worked fine. I restored my jaunty resources.list file and there were updates for jaunty which upgraded the kernel and when I restarted, my flgrx driver was gone. I checked Synaptic and all the xorg/ati versions were still locked and graphics are working as good as they ever have. 

So, possibly, now if you change xorg to the older version, the kernel will update with the ati driver and you won't need the flgrx version of the ati driver any more.

Anyway, thank-you again jonathan. This kind of thing could never happen on Windows. Somebody would be making a lot of money for a fix like this.

---

### Post by BigWoop on 2009-08-05
I'm having a problem, I have carried out the steps exactly but after the second restart (after activating the driver), when next logging in the driver has not been activated.

It still says that the driver has not been activated, I've tried activating the driver and restarting like 6 times.

Another small thing, there is now no longer a shutdown option in the menu, and I have to log off and then shutdown or restart, how can I fix that?

I'm using Ubuntu Studio if that matters, and my GPU is an HD 4670.

I also wondered, how do we tell when ATI updates the drivers to be compatible, can we presume the next release?

---

### Post by two1stnamz on 2009-08-05
> **BigWoop said:**
> I'm having a problem, I have carried out the steps exactly but after the second restart (after activating the driver), when next logging in the driver has not been activated.

It still says that the driver has not been activated, I've tried activating the driver and restarting like 6 times.

Another small thing, there is now no longer a shutdown option in the menu, and I have to log off and then shutdown or restart, how can I fix that?


I'm having a similar issue where the driver will not activate. I still have all the shutdown, restart, etc options, but none of them work anymore. When I click on them, OS doesn't even seem to notice it at all. It's only when i hit my computer case's power switch does a shutdown menu appear that allows me to shutdown, restart, etc.

Ubuntu 9.04
Radeon 4830

---

### Post by jonathank89 on 2009-08-05
> **BigWoop said:**
> I'm having a problem, I have carried out the steps exactly but after the second restart (after activating the driver), when next logging in the driver has not been activated.

It still says that the driver has not been activated, I've tried activating the driver and restarting like 6 times.

Another small thing, there is now no longer a shutdown option in the menu, and I have to log off and then shutdown or restart, how can I fix that?

I'm using Ubuntu Studio if that matters, and my GPU is an HD 4670.

I also wondered, how do we tell when ATI updates the drivers to be compatible, can we presume the next release?

> **two1stnamz said:**
> I'm having a similar issue where the driver will not activate. I still have all the shutdown, restart, etc options, but none of them work anymore. When I click on them, OS doesn't even seem to notice it at all. It's only when i hit my computer case's power switch does a shutdown menu appear that allows me to shutdown, restart, etc.

Ubuntu 9.04
Radeon 4830

Go into your package manager and search for "gnome-session". It should be one of the locked packages. Unlock it via the "Package" menu in the toolbar and then run your update manager. That should fix the shutdown problem.

As for not being able to activate the driver, it might work after you do the above step. Another way to activate your ATI drivers would be to right click on your desktop, go to "Change Desktop Background" -> "Visual Effects" and select "Normal" this will load the drivers and get you to activate them. Select the ATI driver and then press activate a couple of times. Hopefully it'll work and you'll see a restart symbol.

Best of luck.

Jonathan

---

### Post by BigWoop on 2009-08-06
OK, updating gnome-session made the Shutdown option come back, but it didn't help activate the driver unfortunately, after updating gnome-session I tried doing it through Hardware drivers and restarting again and nothing really happened like before.

When trying to activate visual effects I get the error  "Desktop effects could not be enabled".

---

### Post by jonathank89 on 2009-08-06
> **BigWoop said:**
> OK, updating gnome-session made the Shutdown option come back, but it didn't help activate the driver unfortunately, after updating gnome-session I tried doing it through Hardware drivers and restarting again and nothing really happened like before.

When trying to activate visual effects I get the error  "Desktop effects could not be enabled".

I had that problem when I was first figuring out this work around and I put it down to the fact I had dicked around with so many different ATI drivers and config files I figured it would be easier for me to do a fresh install. Like I'd recommend partitioning your hard drive to have a separate "/home" partition, this means when you reinstall your OS you can just do a manual partition while installing and make sure you point the "/home" to that partition. Means you'll have all your data when you do a fresh install...or juts backup and do a normal install...whatever easier for you.

Note: You have to really make sure all traces of the ATI drivers are gone for the work around to work...so maybe find other ways other than in my guide to make sure it's all gone. Although starting new would be my recommendation...but that's just me.

Jonathan

---

### Post by BigWoop on 2009-08-06
I don't really have any data to backup really so that's not such an issue.

I had actually done this from a fresh installation already, as my previous attempt to install the drivers went totally messed up. But I guess I can try again.

By getting rid of the drivers, you mean specifically the proprietory ati drivers right? Or do I have to worry about removing the default open source driver?

---

### Post by jonathank89 on 2009-08-06
> **BigWoop said:**
> I don't really have any data to backup really so that's not such an issue.

I had actually done this from a fresh installation already, as my previous attempt to install the drivers went totally messed up. But I guess I can try again.

By getting rid of the drivers, you mean specifically the proprietory ati drivers right? Or do I have to worry about removing the default open source driver?

You don't need to worry about the default drivers. It's just important that the proprietary drivers are removed before hand.

Best of luck,

Jonathan

PS. My clan is starting a Game Club and our first game is going to be Half Life 1, if you anyone is interested please come join our little community and play with us, [here]("http://phxclan.6.forumer.com/viewforum.php?f=13").

---

### Post by BigWoop on 2009-08-07
OK I have re-installed from scratch and done the whole process again but it's still the same.

I'm not sure if I can read anything into it but after the first restart the graphics performance is still OK, after attempting to activate the driver and then restarting again it runs real crappy, windows don't even move smoothly. 

Before trying to activate the driver I get an error when trying to run the catalyst control center, after it's activated the control center runs but the driver is obviously not working properly.

While I was trying to find some info I read an article I think in the ubuntu wiki about the ati drivers and it mentions something like only basic 2D functionality is supported for 4000 cards, so maybe I will just have to handle the open source driver until that is fixed. I will try find the article again but so far haven't been able to. (Actually I was thinking of this, [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver), and it refers to the open source driver.)

I also remember reading about a different open source driver that has better 3D support, does anyone know what it is, as I can't find the page I saw that on either? (That was this, [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide), mentioning the edge driver.)

Sucks that it didn't just work, but thanks for the help anyway. I'll try the edge driver and see how that works. Otherwise AFAIK 8.10 should work fine with the ATI drivers, is that the case?

---

