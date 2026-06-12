---
title: "How is the resolution picked by gnome?"
date: 2008-08-31
forum: General Help
---

### Post by dmakfan on 2008-08-31
Hello,

When I installed 8.04, I think the resolution got set to 1024x768 or something because now because that worked for my old display. I've now moved my computer to another monitor and want 1280x1024.  When I go to system->adniminstrator->nvidia x server settings, I can manually select 1280x1024, and it works fine.  When I tell it to save my xorg.conf file though, it says that it cannot create the backup file '/etc/X11/xorg.conf.backup'.  I'm not sure what's up with that yet, but I'm guessing that's why my resolution continues to come up as 1024x768, and right now, I have to change it everytime I startup.  

That being said, when I go to system->preferences->screen resolution, if I haven't done the whole nvidia x server thing first, then 1024x768 is the highest resolution that shows up in the list.  Why doesn't it offer me 1280x1024?  If I do the nvidia thing then launch the screen resolution app, 1280x1024 now shows up.  If I choose a resolution in this app, where does it save the settings? I'm guessing it's not xorg.conf either?

One curious thing about this install over other ones I had done in the past (based on 7.10 and earlier) is that my xorg.conf doesn't explicitly indicate any resolutions.  So I'm not sure how X is picking which resolution to use.  I'm guessing it's the same way as the screen-resolution app.

Can anyone shed some light on this?  It seems to me that this shouldn't be that complicated :)

Thanks!
Dave

---

### Post by jonian_g on 2008-08-31
You can try this:

Problems with the resolution mean that your monitor is not recognized. To solve this problem open a terminal and type:

```
sudo displayconfig-gtk
```

On the window that comes up look if your monitor model is next to "Model:". If its not, click on it and find it in the list.
If its not in the list, instert in the drive the disc that came with your monitor, click "add" and locate the .inf file in the disc. If you don't have the disc choose a generic model with the maximum res your monitor can handle.(1280x1024 in your case)

Also if settings are not saved in nvidia x server settings, try running it from the terminal as root:

```
sudo nvidia-settings
```

---

