---
title: "How to get window transparency in Compiz in 8.10?"
date: 2008-10-31
forum: General Help
---

### Post by JerecDrak2 on 2008-10-31
So after upgrading to Intrepid today I went about customising everything to my liking as usual but I've encountered some problems with Compiz. First of all, in Hardy there used to be a setting under General Options in CompizConfig where you were able to set window opacity rules for certain types of windows, but this isn't there any more and I can't find similar functionality in any of the plugins. Can someone enlighten me? 

Also I'm using the zoom animation plugin for DropdownMenu items but it seems to have no effect on Gnome drop-down boxes? Ones on the internet in Firefox use the animation though, again does anyone have any ideas?:confused:
Thanks for any help guys

---

### Post by Forlong on 2008-10-31
> **JerecDrak2 said:**
> So after upgrading to Intrepid today I went about customising everything to my liking as usual but I've encountered some problems with Compiz. First of all, in Hardy there used to be a setting under General Options in CompizConfig where you were able to set window opacity rules for certain types of windows, but this isn't there any more and I can't find similar functionality in any of the plugins. Can someone enlighten me? 
There's a standalone plugin called **Opacity, Brightness and Saturation** now.

> **JerecDrak2 said:**
> Also I'm using the zoom animation plugin for DropdownMenu items but it seems to have no effect on Gnome drop-down boxes? Ones on the internet in Firefox use the animation though, again does anyone have any ideas?:confused:
If you use this for Window Match in the Animation plugin, it should work:
```
(type=Menu | PopupMenu | DropdownMenu | Dialog | ModalDialog | Normal)

```

---

### Post by JerecDrak2 on 2008-10-31
> **Forlong said:**
> There's a standalone plugin called **Opacity, Brightness and Saturation** now.

Thanks! Can't believe I missed that earlier, silly me:redface:

> **Forlong said:**
> 
If you use this for Window Match in the Animation plugin, it should work:
```
(type=Menu | PopupMenu | DropdownMenu | Dialog | ModalDialog | Normal)

```

I have ```
(type=Menu | PopupMenu | DropdownMenu | Dialog | ModalDialog | Normal | Tooltip | Notification | Utility | class=Gnome-panel) & !(name=compiz)
```in my animation plugin and it doesn't work....:(

---

### Post by Forlong on 2008-10-31
Well, all I can say is: works here.

So you must be doing something wrong there. No offence. :)
Try copying the exact same options I posted above.

---

### Post by JerecDrak2 on 2008-11-01
Hmm, I just noticed, with the theme I'm using the Appearance Preferences displays a message reading "This theme will not look as intended because the required GTK + theme engine 'ubuntulooks' is not installed" I don't really know anything about how themes work, could this have something to do with it? Like I said before this is all very confusing as the dropdown lists animate correctly in Firefox:confused:

---

### Post by ellalan on 2008-11-01
Hi
Go to synaptics and type"ubuntulooks" in the search, then tick the box to install the ubuntulooks. I think thats all you have to do. HTH.
But I have to warn you that this will remove Human themes.

---

### Post by JerecDrak2 on 2008-11-01
> **ellalan said:**
> Hi
Go to synaptics and type"ubuntulooks" in the search, then tick the box to install the ubuntulooks. I think thats all you have to do. HTH.
But I have to warn you that this will remove Human themes.
I had thought of that but then human-theme, ubuntu-artwork and ubuntu-desktop are marked for removal, is that not a bad thing?

---

### Post by ellalan on 2008-11-01
Yeah, I do agree with you,its not worth it. I allowed it to remove Human theme and reverted back.

---

### Post by xak on 2008-11-03
> **Forlong said:**
> There's a standalone plugin called **Opacity, Brightness and Saturation** now.

Well there's 10 minutes I'd like back looking for those options! #-o

So, I had quite a few (at least a dozen) window transparency rules on my Hardy install that didn't get carried over to this new plugin.  Any way to transfer them or even retrieve the old settings for manual input?

UPDATE: I found the values located at */apps/compiz/general/screen0/options/opacity_matches* and */apps/compiz/general/screen0/options/opacity_values* using **gconf-editor**.  Had to paste them manually into the new Opacity[...] plugin, but at least I found my expression strings!

---

### Post by ozzyprv on 2008-11-06
The problem I am experiencing (8.10) is that Alt + "+"/"-" does not increase/decrease the transparency....
Any idea why?

It was working with 8.04 before I did the fresh install of 8.10

Thanks.

---

### Post by Forlong on 2008-11-06
> **ozzyprv said:**
> The problem I am experiencing (8.10) is that Alt + "+"/"-" does not increase/decrease the transparency....
Any idea why?
Install ccsm ```
sudo apt-get install compizconfig-settings-manager
```
Go to *System &#8594; Preferences &#8594; CompizConfig Settings Manager* and simply enable the aforementioned **Opacity, Brightness and Saturation** plugin there.

---

