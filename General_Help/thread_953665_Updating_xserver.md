---
title: "Updating xserver"
date: 2008-10-20
forum: General Help
---

### Post by Wickd on 2008-10-20
Hi there. 

I recently updated my kernel headers, but for some reason xserver keeps on crashing. So I will need to update it? How do I do that. Also after the update my cdemu icon on my panel dissapeared and I cant seem to find it.

Can someone please help?

Thanks

---

### Post by Fixman on 2008-10-20
> **Wickd said:**
> Hi there. 

I recently updated my kernel headers, but for some reason xserver keeps on crashing. So I will need to update it? How do I do that. Also after the update my cdemu icon on my panel dissapeared and I cant seem to find it.

Can someone please help?

Thanks

Are you sure xserver is crashing? Please describe your problem better (ie what is actually happenning). If you are VERY SURE you must update xserver, just do

```
 sudo dpkg-reconfigure xserver-xorg 
```

---

### Post by Wickd on 2008-10-20
Well where to start. I updated my kernel headers on Friday and everything went sour. I dont know exactly why, but my Nvidia driver kept on crashing, but I did reinstall it and it worked fine. Also I was able to run Quake 3 on Wine at a resoltion of 800x600 on my desktop resolution of 1024x768 without any issues in full screen, without any special effects turned on. Now it only opens a 800x600 window. And after checking my wine settings, it was set to run in fullscreen. Also after this when I start up nvidia-settings as root I keep on getting an error message in my console telling me that it cant apply changes to nvidia-settings-rc. I did try to delete the file nut nothing happens.

I am quite new to this so I think, maybe the xserver is crashing?

Also if I start compiz it starts at a small resolution and with only two workspaces? Also my Cdemu just ran away I suppose :)

Thanks

---

### Post by Wickd on 2008-10-20
> **Fixman said:**
> Are you sure xserver is crashing? Please describe your problem better (ie what is actually happenning). If you are VERY SURE you must update xserver, just do

```
 sudo dpkg-reconfigure xserver-xorg 
```

Well where to start. I updated my kernel headers on Friday and everything went sour. I dont know exactly why, but my Nvidia driver kept on crashing, but I did reinstall it and it worked fine. Also I was able to run Quake 3 on Wine at a resoltion of 800x600 on my desktop resolution of 1024x768 without any issues in full screen, without any special effects turned on. Now it only opens a 800x600 window. And after checking my wine settings, it was set to run Also after this when I start up nvidia-settings as root I keep on getting an error message in my console telling me that it cant apply changes to nvidia-settings-rc. I did try to delete the file nut nothing happens.

I am quite new to this so I think, maybe the xserver is crashing?

Also if I start compiz it starts at a small resolution and with only two workspaces? Also my Cdemu just ran away I suppose

Thanks

---

### Post by Wickd on 2008-10-23
bump

---

