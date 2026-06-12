---
title: "Cannot find a way to adjust my screen refresh rate"
date: 2020-05-19
forum: Hardware
---

### Post by reptilou on 2020-05-19
Hello,

I work with a Dell XPS 15 running Ubuntu 18.04. The graphics card is a GeForce GTX 1050 4GB.

I recently got a new screen which can go up to QHD 2560 x 1440 at 144 Hz.

I can reach 144 Hz on my personal computer which is running Windows 10, everything is smooth and it's just pure enjoyment.

Now on my working laptop, I can see that the mouse pointer is somehow not refreshing ideally, and the screen is kind of flicking, it really hurts my eyes at the end of the day.

Here is what I have in "Displays" settings:
[IMG]https://ibb.co/68VXQ2g[/IMG][IMG]https://ibb.co/68VXQ2g[/IMG][ATTACH=CONFIG]285925[/ATTACH]

Here is what I get for the HDMI output that I use:
[ATTACH=CONFIG]285926[/ATTACH]
Does it mean I cannot go above 60 Hz whatever the resolution?

Here is what I have in nvidia-settings:
[ATTACH=CONFIG]285927[/ATTACH]
I read on some forum threads I googled that there was supposed to be a refresh rate option; it doesn't appear to exist... I'm lost.


What can I do to help you help me? Is this really a problem of refresh rate? I hope I'm clear enough, it's pretty hard to explain but it really feels like it.

Thanks a bunch!

---

### Post by DuckHook on 2020-05-19
Refresh rate is not just a function of your monitor but also of your GPU. If your desktop can refresh at high rates, it is because your desktop video card is powerful enough to match your monitor rate. Your laptop may not be likewise.

I'm surprised that 60 Hz refresh gives you eyestrain. Modern monitors are not like the old CRTs where the monitor constantly needs repainting. On LCD monitors, static pages shouldn't give you trouble even at 30Hz. Higher rates are useful only for ultra smooth movement, which is important in gaming and things like 3D modeling, but shouldn't cause problems in everyday use. Then again, different people have different sensitivities, so my statement is subjective.

Perhaps your eyestrain is caused by blue light, or inaccurate gamma, or the jumpy mouse, or a different problem altogether from refresh rate. Is your monitor capable of 60 Hz? I would be surprised if it wasn't, but you can experiment by trying a different resolution at pure 60Hz.

Unfortunately, I don't use nVidia. Hopefully, someone who does will jump in here. Are you using the nouveau driver or nVidia's proprietary one?

---

### Post by reptilou on 2020-05-19
I think I was using nvidia v390 driver. My monitor is able to go up to 144Hz. The graphics card was rather good 2 years ago when we got our laptops. I don’t know if it is able to go above 60 actually. 

But right now I have a bricked graphical interface. I tried to reboot and now, just after login and I enter my session password, the screen is empty and frozen. I just see the mouse pointer but cannot move it. 
I can switch to non graphical environment though. So I updated nvidia driver to v440. But still freezing... I don’t know where I went wrong, I don’t remember updating anything.

---

### Post by CatKiller on 2020-05-19
> **reptilou said:**
> Dell XPS 15... GeForce GTX 1050 4GB... 144 Hz.

You may be out of luck.

As you may know, there's been a transition underway for quite a while now from X11 to Wayland, and Optimus is a pain. Those are the biggies for the situation you're in.

You've got your laptop screen refreshing at 60 Hz and your monitor refreshing at 144 Hz. Mixed refresh rates *are* possible... on Wayland. The work could conceivably have also been done for X11 (since high-refresh rates became more popular during the X11&#8594;Wayland transition), but all the X11 devs moved to Wayland instead so there's no one to do it. Unfortunately, Wayland on Nvidia hardware is problematic since Nvidia don't want to do things the Wayland devs would prefer and the Wayland devs don't want to do things the way Nvidia would prefer and both sides just dug in their heels.

You *might* have some luck having your Intel graphics driving your laptop screen at 60 Hz and your Nvidia graphics driving your monitor at 144 Hz, but I have no experience of that kind of setup, and there may be big tradeoffs in doing things that way.

---

