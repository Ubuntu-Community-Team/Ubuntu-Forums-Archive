---
title: "Configuring a Creative Zen Xtra w/ Amarok"
date: 2006-09-28
forum: Hardware &amp; Laptops
---

### Post by raublekick on 2006-09-28
Anyone know what pre-connect and post-connect commands to use? The wiki says to use "mount %d" and "eject %d" where %d is the device node for your device. Huh!?

---

### Post by mitch.c on 2006-09-28
> **raublekick said:**
> Anyone know what pre-connect and post-connect commands to use? The wiki says to use "mount %d" and "eject %d" where %d is the device node for your device. Huh!?
I have a Dell DJ, which is essentially the same device (same driver). I use it with Amarok with no pre/post-connect scripts. Works fine!!

---

### Post by raublekick on 2006-09-28
> **mitch.c said:**
> I have a Dell DJ, which is essentially the same device (same driver). I use it with Amarok with no pre/post-connect scripts. Works fine!!

How did you go about getting it to work? I can't figure this out at all! I have normally use Gnomad2, and it works, but I'd like to try something else.

---

### Post by mitch.c on 2006-09-28
> **raublekick said:**
> How did you go about getting it to work? I can't figure this out at all! I have normally use Gnomad2, and it works, but I'd like to try something else.
I realized after I posted this that I rebuilt the ubuntu package to include libnjb (creative nomad/zen) support. That's why it works for me... I'm not mounting anything.

If you don't know how to do it, let me know and I'll see if I can write up a quick howto.

---

### Post by robgue on 2006-09-29
could you write up a quick how to? I would appreciate it too.(zen vision m user)

---

### Post by raublekick on 2006-09-29
yes i would very much appreciate that!

---

### Post by mitch.c on 2006-09-29
> **raublekick said:**
> yes i would very much appreciate that!

I just noticed amarok-2:1.4.3-0ubuntu8~dapper1 is in the dapper backports repository and has included libnjb support since 2:1.4.3-0ubuntu4.

Just upgrade to the backports version (if you haven't already done so). Plug in your zen, and you should be good to go.

To configure (mine wasn't autodetected):
[LIST=1]
[*]Start Amarok
[*]On the **Settings** menu, click **Configure Amarok**
[*]On the Configure sidebar, click **Media Devices**
[*]Click **Add Device**
[*]Select **Creative Nomad Jukebox Media Device** from the **Select the plugin to use** list
[*]Type a name in the **Enter a name for this device (required)** box. I called mine Dell_DJ.
[*]Click **OK**
[*]Click **OK** to close Configure
[/LIST]

To use:
[LIST=1]
[*]Plug in your media player
[*]On the Amarok sidebar, click **Media Device**
[*]Select **NJB Media Device** from the device list (top of Media Device sidebar)
[*]Click **Connect.**
[/LIST]

After a couple of seconds, you should see your Zen library listed.

Let me know if you have any trouble. Good luck!

---

### Post by raublekick on 2006-09-29
sweet, i can't remember if i have the backports repos enabled or not, so i'll check that when i get home. i tried what you said last night and the Creative Nomad Jukebox Media Device was missing from the driver selection.

---

### Post by MarzoRules on 2006-10-16
I also have a Creative Zen Jukebox Xtra which is picked up easily by Gnomad2 but I wanted to see if I liked it better in AmaroK. I'm running AmaroK 1.4.3 but when I plug the Zen in I don't see the right plug-in in the device settings.

I believe I have all the latest libraries installed but I am very new to both Linux and Ubuntu. Am I missing something obvious?

---

### Post by mishranurag on 2006-10-25
Great! I didn't know it was so simple. I will not have to bother with Gnomad2 or Kzenexplorer now!
Sweeet

---

### Post by romana on 2006-10-30
> **mitch.c said:**
> I just noticed amarok-2:1.4.3-0ubuntu8~dapper1 is in the dapper backports repository and has included libnjb support since 2:1.4.3-0ubuntu4.

Just upgrade to the backports version (if you haven't already done so). Plug in your zen, and you should be good to go.

To configure (mine wasn't autodetected):
[LIST=1]
[*]Start Amarok
[*]On the **Settings** menu, click **Configure Amarok**
[*]On the Configure sidebar, click **Media Devices**
[*]Click **Add Device**
[*]Select **Creative Nomad Jukebox Media Device** from the **Select the plugin to use** list
[*]Type a name in the **Enter a name for this device (required)** box. I called mine Dell_DJ.
[*]Click **OK**
[*]Click **OK** to close Configure
[/LIST]

To use:
[LIST=1]
[*]Plug in your media player
[*]On the Amarok sidebar, click **Media Device**
[*]Select **NJB Media Device** from the device list (top of Media Device sidebar)
[*]Click **Connect.**
[/LIST]

After a couple of seconds, you should see your Zen library listed.

Let me know if you have any trouble. Good luck!

Doesnt work on Edgy with a Creative Zen Vision:M. Gnmad2 continues to be only option, sadly. Choice is better.

---

### Post by stopsatgreen on 2006-11-03
I've followed the suggestions above, and at first my Zen Xtra shows the 'connected' icon, then quickly reverts to 'no connection' and Amarok freezes. I also can use Gnomad 2, but want to sync with Amarok.

BTW, I get the same problem with Banshee.

Also, how do I stop Rhythmbox launching every time I connect my Zen?

---

### Post by naholyr on 2006-11-19
> **mitch.c said:**
> I just noticed amarok-2:1.4.3-0ubuntu8~dapper1 is in the dapper backports repository and has included libnjb support since 2:1.4.3-0ubuntu4.

Just upgrade to the backports version (if you haven't already done so). Plug in your zen, and you should be good to go.

To configure (mine wasn't autodetected):
[LIST=1]
[*]Start Amarok
[*]On the **Settings** menu, click **Configure Amarok**
[*]On the Configure sidebar, click **Media Devices**
[*]Click **Add Device**
[*]Select **Creative Nomad Jukebox Media Device** from the **Select the plugin to use** list
[*]Type a name in the **Enter a name for this device (required)** box. I called mine Dell_DJ.
[*]Click **OK**
[*]Click **OK** to close Configure
[/LIST]

To use:
[LIST=1]
[*]Plug in your media player
[*]On the Amarok sidebar, click **Media Device**
[*]Select **NJB Media Device** from the device list (top of Media Device sidebar)
[*]Click **Connect.**
[/LIST]

After a couple of seconds, you should see your Zen library listed.

Let me know if you have any trouble. Good luck!

I did exactly that, and it didn't work.
Gnomad2 2.8.9 detects my device without any problem, mtp-detect returns well-formed information.
But Amarok says there is no device connected, and so does kzenexplorer.

It's a Zen Vision:M, is there a plan about supporting it ? Is there a reason it works in gnomad and not in amarok even if i tell what driver use ? :(

---

### Post by cloakable on 2006-11-19
How did anyone get Amarok working with a Creative device? I'm running Amarok 1.4.3 (latest), but it doesn't come up in the media devices section.

---

### Post by cloakable on 2006-11-19
I would now like to point out [http://evolvedlight.co.uk/?p=13](http://evolvedlight.co.uk/?p=13) as a good solution.

---

### Post by stopsatgreen on 2006-11-20
I followed all the steps given before I posted here, and I tried again now; still gets stuck. I'm on Ubuntu 6.10, Amarok 1.4.4, by the way.

I'm going to try again with that eveolvedlight.co.uk tutorial.

---

### Post by stopsatgreen on 2006-11-20
Just did what someone suggested and left Amarok for 5 minutes after it appeared to be frozen, and it worked! There's a heck of a long pause, but it does connect.

---

### Post by bsalt on 2007-02-06
Hey guys, I wrote a how-to for installing and configuring Amarok with MTP, iPod, and NJB support. I hope it helps somebody.

[http://thecrosstalk.blogspot.com/2007/01/amarok-music-manager.html](http://thecrosstalk.blogspot.com/2007/01/amarok-music-manager.html)

---

### Post by Wayno-san on 2007-10-25
Will Amarok play files directly from a Creative Nomad Jukebox Xtra or do you have to transfer them to the PC first?

---

### Post by Wayno-san on 2007-12-01
Is there a Linux program that will play mp3 files from a Creative Labs Zen Xtra directly without having to copy them to a PC hard drive first?

I'd also like to be able to change ID tags on the Xtra itself....

Thanks,
Wayne

---

