---
title: "slow touchpad"
date: 2008-12-17
forum: Hardware
---

### Post by jacksonpollack on 2008-12-17
I just upgraded my sony laptop from Ubuntu 8.04 to 8.10 and now have a problem using my touchpad: the cursor moves terribly slow. I actually had the same problem in 8.04, but managed to edit the /etc/X11/xorg.conf file to increase the speed of cursor.

Now, however, those edits have been commented out:

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
etc., etc., etc.

If I uncomment them, the cursor moves fast again - but I can no longer tap to click or scroll by touching the sides of the pad. Is there a different file I can edit to increase the speed without losing the scolling and tapping abilities? 

Any help would be appreciated, thanks!

---

### Post by shane8002 on 2008-12-17
Download touchpad controller from your package manager and then you can change the settings to whatever you like. I know someone who had the same problem so you might try reinstalling the driver, that fixed it for him.

---

### Post by jacksonpollack on 2008-12-18
Thanks for the reply. I installed gsynaptics, if that was what you meant -  at first, however, it just told me that:
GSynaptics couldn't initialize. You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics.

So I did in the xorg.conf file, giving me access to touchpad settings in preferences. While I can enable tapping (and it works) now, the horizontal/vertical scrolling on the sides of the touchpad do not, even when they settings claim they are enabled (and I tried different speeds and restarted X each time). I have no clue why it doesn't work. 

Are there any other configuration files I can mess with somewhere?

---

### Post by shane8002 on 2008-12-18
You could try mouse under preferences if you havent tried that already,its under system-preferences-mouse, or you could try reinstalling your touchpad driver because it sounds like a driver problem to me. If that dosent work let me know.

---

### Post by Ayuthia on 2008-12-18
> **jacksonpollack said:**
> I just upgraded my sony laptop from Ubuntu 8.04 to 8.10 and now have a problem using my touchpad: the cursor moves terribly slow. I actually had the same problem in 8.04, but managed to edit the /etc/X11/xorg.conf file to increase the speed of cursor.

Now, however, those edits have been commented out:

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
etc., etc., etc.

If I uncomment them, the cursor moves fast again - but I can no longer tap to click or scroll by touching the sides of the pad. Is there a different file I can edit to increase the speed without losing the scolling and tapping abilities? 

Any help would be appreciated, thanks!

Not for sure if this will help, but from the informaiton that you posted, it looks like it is using HAL now.  If that is the case, Arch had something similar:
[http://bbs.archlinux.org/viewtopic.php?pid=456488#p456488](http://bbs.archlinux.org/viewtopic.php?pid=456488#p456488)

I had to make those changes to get my touchpad to work.  If you try that link, just try the portion for the synaptics touchpad in post #13 and go to this portion: /etc/hal/fdi/policy/11-x11-synaptics.fdi in the post.  Create that file and then paste that section into it.  You will need to make sure that the information in /etc/X11/xorg.conf has been commented out for your touchpad or else it will not work.  You can always remove the file if it does not work.

Hope that helps.

---

### Post by jacksonpollack on 2008-12-19
I uncommented the xorg.conf bits, added that 11-x11-synaptics.fdi file... but then hit the same problem as before: shmconfig was not found, so the touchpad reverted to how it worked at the beginning (scrolling working, but movement much too slow, as opposed to no scolling, but good speed). But I searched some other threads along those lines, and realized I had to add an shmconfig.fdi file. Which I did, and yay it works - both the scolling and fast movement.

Thanks for all your help everyone!

---

