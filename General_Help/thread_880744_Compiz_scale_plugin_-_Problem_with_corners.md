---
title: "Compiz scale plugin - Problem with corners"
date: 2008-08-05
forum: General Help
---

### Post by lunatico on 2008-08-05
Hello,

I have the scale plugin and I have it configured to Initiate Window Picker with corners. It will run fine normally, but sometimes the corners just stop responding. Restarting the computer, or just X fixes it. Or going into CompizConfig and untick, tick the scale plugin also works. I have played around a lot with the settings but nothing I do seems to fix this.

Does anyone experience something like this?
Any help is much appreciated.

---

### Post by sayakb on 2008-08-05
Try this: Disable the Scale Plugin and download **Ubuntu Tweak** from [http://getdeb.net](http://getdeb.net)
Goto Applications->System Tools->Ubuntu Tweak, expand *Desktop* and click on *Compiz Fusion* and set the corners to **Pick Windows** (which is the same scale plugin)
See if this works.

---

### Post by lunatico on 2008-08-05
> **LinuxIsInnovation said:**
> Try this: Disable the Scale Plugin and download **Ubuntu Tweak** from [http://getdeb.net](http://getdeb.net)
Goto Applications->System Tools->Ubuntu Tweak, expand *Desktop* and click on *Compiz Fusion* and set the corners to **Pick Windows** (which is the same scale plugin)
See if this works.

I did this. Then I went into CompizConfig and it seems like Ubuntu Tweak just enabled the scale plugin again. I'll monitor and post if it is a successful solution.

---

### Post by lunatico on 2008-08-06
Update. This didn't work. After some time the corners just stop responding. It is just the corners because I also have Super+A to Initiate Window Picker and in that way it keeps working, which means the plugin is still running I suppose. I also went through all CompizConfig setting to make sure there was nothing else mapped to those corners thinking that there might be something else causing like a collision.

Any other ideas anyone? Someone experienced this or is it just me?

---

### Post by Vadi on 2008-08-06
Yeah I experience this issue too at times. Not sure why does it happen.

---

### Post by tuxxy on 2008-08-06
Is this running on ATI video card?

---

### Post by lunatico on 2008-08-06
Not in my case. I have a IBM ThinkPad T61 with Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller.

---

### Post by lunatico on 2008-08-08
Anyone, any ideas?
Is there a way to dump into a file everything that happens in compiz? Like a log of everything compiz is doing... that would be a good way to debug and find what is causing this...

---

### Post by Vadi on 2008-08-08
Try starting compiz with "compiz --replace > log.txt" in the terminal.

---

### Post by lunatico on 2008-08-09
> **Vadi said:**
> Try starting compiz with "compiz --replace > log.txt" in the terminal.

No useful output prom this, just compiz startup info.
And it still happens. I have the Scale and the Scale Adons plugins enabled. Disabling the Adons one makes no difference. On the Bindings I only have for the corners Initiate Window Picker on TopRight and Initiate Window Picker For All Windows on BottomRight. And keyboard I have Initiate Window Picker For All Windows on <super>a
I had this problem back when I was using 7.10 (Gutsy Gibbon) also, and upgrading to 8.04.1 didn't fix it.
Would something like this be related to hardware? Someone has any ideas on the best way to debug it?

---

### Post by Vadi on 2008-08-09
Joining #compiz on the IRC I guess would be the best way.

---

### Post by lunatico on 2008-08-11
I think I have identified something interesting. If I don't use the corners right after turning the computer on then they stop working. For example, this morning I turned my computer on, didn't used the corners life for 45 minutes and then when I tried to use them they where not responding.
Does this help? Weird!

---

### Post by luctor on 2008-08-11
Same issue on my box

Ubuntu Hardy 8.04
nVidia GeForce 8300 GS

---

### Post by lunatico on 2008-08-11
Good to know I'm not the only one. I also have a thread at [http://forum.compiz-fusion.org/showthread.php?t=9437](http://forum.compiz-fusion.org/showthread.php?t=9437) about this. We'll see where it gets resolved first!

---

### Post by lunatico on 2008-08-13
As a temporary fix I was wondering if it is possible to control the enable/disable of plugins from the command line. That way I could write a little script to restart the scale plugin when it fails. Easier than having to go into CompizCongig, scroll down, un-tick and tick...

Thanks!

---

### Post by lunatico on 2008-08-21
I installed fusion-icon. So there is an icon in the Notification Area that you can right click and Reload the Window Manager. Quick fix for when this problem happens. Which is still there btw.

---

### Post by figure002 on 2011-07-20
I have the same problem for quite some time now (I don't remember when it started happening though). But it's quite annoying.

If found that it mostly happens when I have Firefox maximized. Sometimes when Firefox is maximized, the corner initialization doesn't work. When I unmaximize the Firefox window, the corner suddenly works again. But when I maximize it again, corner doesn't work, and so on.

Sometimes even unmaximizing the Firefox window doesn't solve it either. All I have to do then to get it working again, is to left-mouse-click on the GNOME desktop once. Then all of a sudden corners work again (until I maximize that Firefox window again).

I don't believe it's just with Firefox. I think it happens with other maximized windows as well, but I can't test this right now as it's not happening at the moment.

I got a NVIDIA card by the way.

EDIT: Yep, it happens with all maximized windows, not just Firefox.

---

### Post by jensbo on 2011-10-18
An old thread, but I have the same problem on 11.10 now too (running on my eeepc)

---

