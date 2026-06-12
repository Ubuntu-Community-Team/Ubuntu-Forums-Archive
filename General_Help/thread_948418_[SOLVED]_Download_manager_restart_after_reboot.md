---
title: "[SOLVED] Download manager restart after reboot"
date: 2008-10-15
forum: General Help
---

### Post by Kevbert on 2008-10-15
Using Hardy Heron and I'm trying to download the Ultimate (Harty Hotrod) version of Ubuntu.  The download looks like it's going to take days and I normally turn the PC off at night. If I download something from the web a new Download (manager?) window opens. I'm able to pause the Ultimate download at night, prior to turning off, but in able to open it I have to download something else from the web prior to restarting the Ultimate download in the morning. Is there an easier way to do this ? (autostart or shortcut?)

---

### Post by kpkeerthi on 2008-10-15
How are you downloading? firefox?
Try this addon: [https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)

Or use a bittorrent client like deluge or transmission (included in Hardy)

---

### Post by Kevbert on 2008-10-15
I thought I selected a torrent but the download was very slow and couldn't see any seeds.  I've now tried a different link and now Transmission is working as expected (and working a lot faster...).  Thanks for the link.
It still looks like the download won't finish today, so I'm in a similar situation with Transmission. If I pause it to shut down, how do I restart it tomorrow ?

---

### Post by kpkeerthi on 2008-10-16
> **Kevbert said:**
> 
It still looks like the download won't finish today, so I'm in a similar situation with Transmission. If I pause it to shut down, how do I restart it tomorrow ?
Transmission can resume torrents so can deluge. Just launch transmission when you come back and it should resume the download.

---

### Post by Malac on 2008-10-16
> **Kevbert said:**
> .....how do I restart it tomorrow ?

You can create a "temporary" launcher on your desktop by right-clicking transmission and choosing add to Desktop.
Just click this and away you go.
Or:
Go to System->Preferences->Session and on the "Startup Programs" Tab choose Add then create an entry for transmission. It will now restart when you login.
You can do this with virtually any program you want to start when you login.
If you are unsure of the command right-click the menu entry and choose add to desktop then choose Properties of that file from it's right-click menu and select the Launcher tab.

Hope this helps.

---

