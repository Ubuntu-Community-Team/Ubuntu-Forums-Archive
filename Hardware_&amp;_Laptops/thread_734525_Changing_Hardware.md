---
title: "Changing Hardware?"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by Mehashi on 2008-03-24
Hi guys!
I'm a new user to ubuntu and really enjoying windowless freedom!
I have been having endless problems with my ati radeon x1650 pro agp, seemingly driver related. Rather than wait for better ati drivers I have an nVidia 6600gt agp that I would like to install.

What I would like to know is how I do that in ubuntu? Is there an order to changing hardware/drivers to avoid conflicts? 

Also is there anywhere I can go to find information on changing hardware in general in ubuntu because I often test out new hardware and configurations and it seems linux is more particular than windows about how things are configured.
Sorry if this is a novice question! Hopefully I've posted in the right forum too!

Thanks to anyone with advice, much appreciated. I really like the community spirit so far seen in ubuntu!  Mehashi ^_^

---

### Post by overdrank on 2008-03-24
> **Mehashi said:**
> Hi guys!
I'm a new user to ubuntu and really enjoying windowless freedom!
I have been having endless problems with my ati radeon x1650 pro agp, seemingly driver related. Rather than wait for better ati drivers I have an nVidia 6600gt agp that I would like to install.

What I would like to know is how I do that in ubuntu? Is there an order to changing hardware/drivers to avoid conflicts? 

Also is there anywhere I can go to find information on changing hardware in general in ubuntu because I often test out new hardware and configurations and it seems linux is more particular than windows about how things are configured.
Sorry if this is a novice question! Hopefully I've posted in the right forum too!

Thanks to anyone with advice, much appreciated. I really like the community spirit so far seen in ubuntu!  Mehashi ^_^

Hi and welcome, on the graphics card you will have to uninstall the ATI drivers first. If you used Envy to install the uninstall with Envy. Then when you install the nvidia card you will have to reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
As for other hardware, I have install Ubuntu on a drive and move to a different system and that is the worst I had to do was reconfigure the xorg. Good luck!

---

### Post by Mehashi on 2008-03-24
Excellent, thank you! Thats encouraging news! Ill install the new card tonight and post a result, hopefully success!

It was one of my main worries about ubuntu being able to cope with hardware being different from its last boot without needing admistrative-level experience. As much as I hate windows it does stand up well to that!

Thanks for the feedback Overdrank!

---

