---
title: "Volume Control not working"
date: 2008-09-01
forum: General Help
---

### Post by enderal on 2008-09-01
The Volume Control is not working. I get an error message that says...

"No volume control GStreamer plugins and/or devices found."

And in System > Preferences > Sound in the settings I get error message when testing...

"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument"

I did try unintslling and reinstalling gnome-volume-manager

Thanks for any help.

---

### Post by sayakb on 2008-09-01
At a terminal, type in:
```
sudo apt-get install linux-backports-modules-hardy
```
And if you are not using Hardy:
```
sudo apt-get install linux-backports-modules
```

---

### Post by enderal on 2008-09-01
Tried that and restarted. Still get the error messages...

---

### Post by enderal on 2008-09-01
Here is another message I just got...

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

Also I just noticed...
sudo apt-get install linux-backports-modules

"Couldn't find package linux-backports-modules"

---

