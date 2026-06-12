---
title: "nvidia settings - I can't change them"
date: 2011-01-13
forum: Hardware
---

### Post by CP2 on 2011-01-13
Good morning all. I have a problem. When I try to change my monitor resolution it ask me something like "would you like to use your vendor software to change the settings?" So I click yes. The nvidia box comes up and then there is another box saying something like, "You must restart the X server. run nvidia-config and restart the x server using root" 

Problem is I can't do it. I tried with sudo, and it said that it didn't recognize the command "nvidia-xconfig"  and when I do a su - then when I type in my password it wont authenticate. 

I'm using Lucid Lynx and I had to download the nvidia drivers and what not. It's not showing up with the proprietary drivers int he "hardware drivers" section. Matter of fact there is nothing in that section.  And some of you might say "WHY???" but this particular card was working almost perfectly in Maverick. The only problem is I couldn't use DVI for some reason and didn't know how to enable DVI.  

If you are going to say, "Why not use Maverick then" well, for some reason it wont boot up. Thats another issue I'll address in another thread.

---

### Post by BbUiDgZ on 2011-01-13
> **CP2 said:**
> Good morning all. I have a problem. When I try to change my monitor resolution it ask me something like "would you like to use your vendor software to change the settings?" So I click yes. The nvidia box comes up and then there is another box saying something like, "You must restart the X server. run nvidia-config and restart the x server using root" 

Problem is I can't do it. I tried with sudo, and it said that it didn't recognize the command "nvidia-xconfig"  and when I do a su - then when I type in my password it wont authenticate. 

I'm using Lucid Lynx and I had to download the nvidia drivers and what not. It's not showing up with the proprietary drivers int he "hardware drivers" section. Matter of fact there is nothing in that section.  And some of you might say "WHY???" but this particular card was working almost perfectly in Maverick. The only problem is I couldn't use DVI for some reason and didn't know how to enable DVI.  

If you are going to say, "Why not use Maverick then" well, for some reason it wont boot up. Thats another issue I'll address in another thread.

run "nvidia-settings"

---

### Post by CP2 on 2011-01-13
> **BbUiDgZ said:**
> run "nvidia-settings"

I did that and all it did was bring up the window that eventually told me I need to reset the X server.

---

### Post by IcarusR on 2011-01-13
I think you need to run with root privileges, like this

```
gksudo nvidia-settings
```

---

### Post by efflandt on 2011-01-14
What video card do you have (output of **sudo lspci -v** related to it)?  Did you install Ubuntu nvidia drivers or something directly from nvidia.com?

To run nvidia-xconfig (assuming that you actually have nvidia drivers installed), you have to go to a console (like Ctrl+Alt+F1) do **sudo stop gdm**, then **sudo nvidia-xconfig** (note the x), then **sudo start gdm**.  Although, that ends up with a much bigger /etc/X11/xorg.conf than if you just "activate" nvidia from Hardware Drivers in Lucid, or Additional Drivers in Maverick.

But without knowing which nvidia card or drivers you are trying to use, it is difficult to tell you how to proceed.  There are newer Ubuntu nvidia drivers available from x-swat ppa for Lucid or Maverick if nvidia-current is not new enough.  They work with my nvidia card that is new enough yet that Linux kernels in Natty development do not recognize its model.

---

