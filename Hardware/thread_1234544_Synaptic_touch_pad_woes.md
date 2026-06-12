---
title: "Synaptic touch pad woes"
date: 2009-08-08
forum: Hardware
---

### Post by gooddm on 2009-08-08
Lots of chatter about this hateful little bug spanning a couple of years, but no solid leads...

Got my kid a confuser, a Dell Inspiron Mini, and he wants Ubuntu like his old man... well of course says I, and set out to install it (im in to hour 6 now).  Gettin Ubuntu to behave on this laptop has been one rockety ride.

With Ubuntu runnin, the Synaptics Touchpad on this thing is one step from useless.  It is bouncing all over the place whenever you try to click a button, and trying to drag something on the screen will have you talkin like a sailor in no time.

First up, I found the thread which had me creating some .fdi config goodness buried down in /etc.  No glory there... so next I found a thread which had me installing gsynaptic.  Of course, that barfs sayin SHMconfig has to be set TRUE in xorg.conf.  No worries, added the offending bits to xorg, but 5 or 6 variants and reboots later, gsynaptic still refuses to load.

At present, I'm grouchy, stumped, and out of options.  If I tell my budding 10 year hacker old that his dad was defeated by Ubuntu, it'll ruin him on the whole linux eats windows thing... not to mention it'll give my windows adoring wife sumthin to crow about.  I could use a leg up if anyone had finally put this little annoyance to rest.

Thanks!

  --dave

---

### Post by RavanH on 2009-08-22
Sorry to hear you are facing this much trouble. Even more sorry i cannot give a clear solution, just a suggestion: did you follow these instructions for enabling SHMConfig or did you just paste "SHMConfig" "on" in the xorg.conf file like it used to be in previous versions of Ubuntu?

EDIT: [https://help.ubuntu.com/community/SynapticsTouchpad#Enabling SHMConfig]("https://help.ubuntu.com/community/SynapticsTouchpad#Enabling SHMConfig")

---

### Post by RavanH on 2009-08-22
> **RavanH said:**
> Sorry to hear you are facing this much trouble. Even more sorry i cannot give a clear solution, just a suggestion: did you follow these instructions for enabling SHMConfig or did you just paste "SHMConfig" "on" in the xorg.conf file like it used to be in previous versions of Ubuntu?

Forgot the link |-/ so here it is: [https://help.ubuntu.com/community/SynapticsTouchpad#Enabling SHMConfig]("https://help.ubuntu.com/community/SynapticsTouchpad#Enabling SHMConfig")

---

### Post by gooddm on 2009-08-31
Hi!

Thanks for responding to my plight :)

Sadly, I lost the battle of Dave vs. the Touchypad... my kid's confuser now has WinXP installed on it.  Under Win, the touchpad works as expected, so it is pretty certainly something amiss afoot alas with the linux driver.

Before calling no glory however, I was finally able to get gsynaptc stuff working.  This allowed me to watch the data-stream coming back from the touchpad.  The results were... interesting.

First up, the touchpad on this netbook is weird.  The buttons are integrated in to the touchy surface and not separate.  When you touch the area over the buttons, the driver reports the XY coordinates of the touch.

When you click the button, the driver reports the touch before the click occurs.  As you start to press on the button and before it clicks, you will see the XY coordinates of the touch moving a bit.  The mouse cursor responds by moving, thereby causing you to miss what you were tryin to click on more often than not.

As to the drag thing being a drag... process is, click and hold the button, then slide your finger over the surface.  As you run out of surface, pick up your finger and rinse/repeat.  Except... as soon as you lift your finger, the driver screams that the lower left corner is now being touched (tis where you are holding the button), and the rubber-band responds by jumping that way.  This is why dragging is hosed.

Seemed the obvious fix was to get the driver to stop reporting touches along the bottom edge of the pad.  I spent a good bit of time playing with xorg.conf setting trying to get the driver to ignore that area of the screen... I never could get then the settings to do what I was looking for.

Looking in the bug-lists, this problem is being reported in various places.  It appears that the smart folks are on the case.  Perhaps someone will crack this before too long.

  --Dave

---

### Post by bubuka on 2009-09-07
now I'm struggling with the same issue on a Samsung N310. It worked fine with 9.4 "vanilla" until i decided to apt-get update and upgrade... Bad move...
Yes, I played all those tricks with SHMConfig, set maxspeed=minspeed to avoid conflict of two acceleration processes, but it's still crappy. If I move the cursor gently it can follow but a normal drag causes loss of track, the cursor starts to jump or is stuck in one point. 

I see two options: upgrade to some dev synaptic drivers (I found something on packages.debian.org but it lacks the configure script, I don't know what to do)

The other option is to downgrade. I never done such thing so some help would be appreciated how to block the auto update of the relevant packages and files once I downgraded. Thanks in advance

---

