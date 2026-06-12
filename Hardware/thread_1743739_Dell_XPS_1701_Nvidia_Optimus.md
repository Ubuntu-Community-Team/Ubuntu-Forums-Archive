---
title: "Dell XPS 1701 Nvidia Optimus"
date: 2011-04-29
forum: Hardware
---

### Post by Dreamer Zero on 2011-04-29
i bought this laptop a few months back without checking the compatibility on the video card because Nvidia was spot-on with the drivers before, and the past few months have been okay because i haven't really needed a power graphics card and used my desktop for my other needs...

but now that i've updated to 11.04, my laptop that i spent an arm and leg that now looks like Windows 95, i recall that in the beginning i read something that said with the Nouveau driver and a switching program (switcheroo?) the Nvidia card can be enabled and be able to use it.

any truth to this or did i make it up in a dream:?:

---

### Post by Finalfantasykid on 2011-05-04
I'm bumping this because I am in the same boat.

I was able to turn off my gfx card at least to save batter power(about dooubled the life).

---

### Post by beew on 2011-05-04
Someone claims he has a solution to the Optimnus problem on Nvidia's Linux forum.

[http://www.nvnews.net/vbulletin/showthread.php?t=162171](http://www.nvnews.net/vbulletin/showthread.php?t=162171)

Don't know if it works or how well it works. In the mean time you may want to write to Nvidia and Dell (for the BIOS switch to turn off Optimus)
[http://ubuntuforums.org/showthread.php?t=1712278](http://ubuntuforums.org/showthread.php?t=1712278)

[]("http://www.nvnews.net/vbulletin/showthread.php?t=162171")

---

### Post by asn_knight on 2011-05-07
> **Finalfantasykid said:**
> I'm bumping this because I am in the same boat.

I was able to turn off my gfx card at least to save batter power(about dooubled the life).

Can u please explain how you managed to turn it off (for Ubuntu 11.04 that is)...I have been tired searching for it! 
I hav a XPS 15 laptop with hybrid graphics - Intel HD and Nvidia GT 525M...
I wouldnt mind switching it off for Ubuntu as a whole coz any games I play is in Windows.

---

### Post by Dreamer Zero on 2011-06-01
for some reason i wasn't emailed for the last 2 replies... but i checked out Bumblebee, looks promising however i'm having issues with it.

[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

i got it installed and it required start and stop scripts and pointed to the examples, i tried using the XPS15 scripts wishing the hardware would be close enough to work, but this is what i get:

> ~$ optirun64 gxlgears
 * Starting Bumblebee X server bumblebee                                        _PS0 Enabling nVidia Card failed (Error: AE_NOT_FOUND).
                                                                         [ OK ]
exec: 301: gxlgears: not found
 * Stopping Bumblebee X server bumblebee                                         * .                                                                             * .                                                                             * .                                         

anyone else have any luck with this? i assume my issue is that it can't really figure out what kind of card i have... not sure if i'm suppose to install the Nvidia driver, very confused.

---

