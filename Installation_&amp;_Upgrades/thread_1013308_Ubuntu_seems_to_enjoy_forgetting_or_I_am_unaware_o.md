---
title: "Ubuntu seems to enjoy forgetting or I am unaware of proper settings"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by Demios101 on 2008-12-16
I used xubuntu (Hardy) for a while and decided do do a complete system wipe and install vanilla (regular) 8.10. Upon use for a few days I seem to have run into a few problems. It seems II enjoys forgetting my settings. First on the list. Networking.

1. I prefer for all my devices (pc, laptop, media center, consoles etc.) to have static IP addresses, and I port forward as needed to these devices. I cannot seem for the life of me to be able to get II to remember the settings I put into the NetworkManager app. I've tried disabling, changing settings and rebooting. Despite my disabling it, it auto connects upon reboot and forgets whatever settings I tell it to remember.

2. Does Ubuntu automount my extra HDDs, if not, i can perceive where my other problem could come from. I have a wallpaper on another drive, and it seems after every reboot. I have to go back into my settings and change my wallpaper back to whatever it was. If it does not, is there a way to make ubuntu automount my devices on startup?

3. This could be a VLC problem and not ubuntu. I always set my output in VLC to go through my logitech headset. Upon reboot however, it is also forgotten, and I have to go set it up again.

4. Is there a way for me to make it so all of my hidden files are visible al the time? it seems the show hidden files only works for the specific foler I select it on and even then, only as long as I keep it open.

---

### Post by fubbleskag on 2008-12-16
it's not clear to me - are you now using ubuntu/gnome, or still xubuntu?

---

### Post by oedipuss on 2008-12-16
> **Demios101 said:**
> I used xubuntu (Hardy) for a while and decided do do a complete system wipe and install vanilla (regular) 8.10. Upon use for a few days I seem to have run into a few problems. It seems II enjoys forgetting my settings. First on the list. Networking.

1. I prefer for all my devices (pc, laptop, media center, consoles etc.) to have static IP addresses, and I port forward as needed to these devices. I cannot seem for the life of me to be able to get II to remember the settings I put into the NetworkManager app. I've tried disabling, changing settings and rebooting. Despite my disabling it, it auto connects upon reboot and forgets whatever settings I tell it to remember.


This is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/259214") with network-manager 0.7. There are some workarounds mentioned in that thread, but I expect a fix is coming soon.
Right now, the easiest thing I've found that works with a compromise, is to create a new connection with your static IP settings, and switch to it after each reboot. At least you won't have to re-enter all the settings.
There was a comment mentioning that unchecking 'system setting' (for the static connection) , applying, and checking it again (it should ask for your password the second time) works, but I haven't rebooted yet to test it. 

> 
2. Does Ubuntu automount my extra HDDs, if not, i can perceive where my other problem could come from. I have a wallpaper on another drive, and it seems after every reboot. I have to go back into my settings and change my wallpaper back to whatever it was. If it does not, is there a way to make ubuntu automount my devices on startup?


I believe gnome-volume-manager is the thing you're looking for. It's available through synaptic, and then in System/Administration menu, as 'Disk Manager'. The alternative is messing about with fstab, I've never got the hang of it though, kind of confusing :P

> 
4. Is there a way for me to make it so all of my hidden files are visible al the time? it seems the show hidden files only works for the specific foler I select it on and even then, only as long as I keep it open.
 
Run gconf-editor in a terminal (install it with synaptic if it isn't there), and then in /desktop/gnome/file-views tick the 'hidden files' entry. It should enable it everywhere, except perhaps open file dialogs. 

EDIT again : Hah, it's in nautilus, menu Edit/Preferences, tab Views :P I completely missed it ... I suppose the menu item for hidden files applies only to the specific folder . 

> 
3. This could be a VLC problem and not ubuntu. I always set my output in VLC to go through my logitech headset. Upon reboot however, it is also forgotten, and I have to go set it up again.


I don't know about this one  , sorry =(
I'm assuming you're setting it with pulseaudio, and it *should* remember the preferred output ...

EDIT : added #4

---

### Post by Demios101 on 2008-12-16
Very informative oedipuss. I'll give all of those a shot as soon as I get home. Another one I wanted to add. When I used xubuntu, at bootup, it would auto load everything I had open when at shutdown (xchat, firefox, pidgin etc) can I do this as well in ubuntu?

---

### Post by robert shearer on 2008-12-16
> 2. Does Ubuntu automount my extra HDDs, if not, i can perceive where my other problem could come from. I have a wallpaper on another drive, and it seems after every reboot. I have to go back into my settings and change my wallpaper back to whatever it was. If it does not, is there a way to make ubuntu automount my devices on startup?

Move your wallpaper to the 'pictures' folder in your home folder on the main ubuntu drive then go to system=>appearence=>background and 'add' then select the wallpaper in your pictures folder.

---

### Post by oedipuss on 2008-12-16
> **Demios101 said:**
> Very informative oedipuss. I'll give all of those a shot as soon as I get home. Another one I wanted to add. When I used xubuntu, at bootup, it would auto load everything I had open when at shutdown (xchat, firefox, pidgin etc) can I do this as well in ubuntu?

I think that's in System/Preferences/Sessions , tab Options. 
You can also add custom startup apps from there for things that should always run, even if closed in the previous session.

---

### Post by Demios101 on 2008-12-17
> **robert shearer said:**
> Move your wallpaper to the 'pictures' folder in your home folder on the main ubuntu drive then go to system=>appearence=>background and 'add' then select the wallpaper in your pictures folder.

I am aware of that option, but there has to be another way, hence why i asked. I'd prefer to it exactly where it is.

> **oedipuss said:**
> I think that's in System/Preferences/Sessions , tab Options. 
You can also add custom startup apps from there for things that should always run, even if closed in the previous session.

Thanks, that works.

---

