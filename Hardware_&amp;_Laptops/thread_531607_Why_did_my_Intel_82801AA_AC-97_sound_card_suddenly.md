---
title: "Why did my Intel 82801AA AC-97 sound card suddenly stop working?"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by dnbozss on 2007-08-21
I've searched everywhere for this, even here.

I just installed Ubuntu on my old Intel about a month ago, the sound worked fine. About a week or two ago, I messed with some stuff and screwed a few things up (such as the sudoers list) but I got it all fixed as far as I know. But now my sound card suddenly stopped working.

When trying to open the sound control in the top right corner, I get "No volume control GStreamer plugins and/or devices found." 

When I go to Device Manager, it shows it and alot of ALSA and OSS stuff below it. 

When I go to System>Preferences>Sound, under all the pull downs, I can select 82801AA-ICH, but if I hit "Test", I get "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing." 

And under "Default mixer tracks, if I click the drop down, it's empty. 

If I run alsamixer in Terminal, I get "alsamixer: function snd_ctl_open failed for default: No such device"

If I go to Applications>Sound & Video> GNOME Alsa mixer, the entire screen is blank, and the only thing under File is Exit. If I click Edit>Sound card Properties, it closes the window.

I also get alot of junk filled with stuff followed by "The field ipc_gid must be a valid group (create group audio)".

HELP!

---

