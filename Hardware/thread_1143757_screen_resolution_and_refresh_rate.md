---
title: "screen resolution and refresh rate"
date: 2009-04-30
forum: Hardware
---

### Post by crabhunter on 2009-04-30
Hi,I have just installed 9.04 on my works pc.
I have enabled the nvidia driver under hardware drivers and it has set the screen resolution to the highest my monitor supports.
Unfortunately at this setting my crt monitor flickers badly and it needs to be set back to 1024*768@85 to work nicely.
When I try System->Preferences->Display I get

It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?


If I click yes I get to the nvidia x server settings.
In there I can set the resolution and refresh rate but cannot save the settings,I get

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.


Which file can I manualy edit to save my settings /etc/x11/xorg.conf doesent seem to have any relevent entries to change.
Mike

---

### Post by AlecJ on 2009-04-30
you have to do this in a terminal 
```

sudo cp xorg.conf xorg.conf.backwhatever

```Then you can edit xorg.conf with

```

sudo nano xorg.conf

```

or you could just

```

sudo nvidia-setting

```

---

### Post by crabhunter on 2009-04-30
Thanks,I took the easy option

sudo nvidia-settings

That did the trick,thank you very much,
Mike

---

### Post by crabhunter on 2009-11-26
I have just done a fresh install of 9.10 and have got the same problem as listed above.however this time sudo nvidia-settings dosen't work :(
I tried opening xorg.conf but there are no relevent lines to edit.I assume I will have to add some lines but don't know what to add.
Any help would be appreciated.
Mike

---

### Post by Chaos Punk on 2009-11-26
Please help, I have the same problem as crabhunter.

---

### Post by crabhunter on 2009-11-30
Ok, here's how I fixed it.
I installed 9.04 (which killed my windows) set up the graphics and made a copy of xorg.conf.
Did a clean install of 9.10 and swopped xorg.conf.
Mike

---

