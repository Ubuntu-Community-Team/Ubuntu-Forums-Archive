---
title: "Vista won't let me switch to Linux"
date: 2008-04-17
forum: Hardware &amp; Laptops
---

### Post by TaylorHelferty on 2008-04-17
So, I just finished exams and am finally going to go back to Ubuntu on my new laptop - which is currently running Vista. I didn't want to make the switch during school in case there were problems, but now I'm done and ready - especially after Vista has been getting progressively worse, such as uninstalling it's own programs.

Anyway, I went to boot from the Ubuntu cd, and it didn't. So I checked setup, changed the boot order so the cd drive was first. Still nothing. So I hit F12 to manually select the cd drive, but the only options to boot from were the HDD and the LAN (and I know from past experience that it does normally have the option to boot from cd and flash drives). Now this is odd, and it wasn't just the Ubuntu cd that wouldn't boot. So I tried restoring the computer to factory settings, thinking Vista had done something in it's aforementioned uninstalling spree. This didn't fix the problem and it still won't let me boot from any cds. 

Any suggestions? I am sick of Windows and want to go back to Linux asap.

---

### Post by Perfex on 2008-04-17
Sounds like a bios issue, whats the make of the laptop.. model, etc?

---

### Post by El Rogueo on 2008-04-17
> **TaylorHelferty said:**
> 
Anyway, I went to boot from the Ubuntu cd, and it didn't. So I checked setup, changed the boot order so the cd drive was first. Still nothing. So I hit F12 to manually select the cd drive, but the only options to boot from were the HDD and the LAN (and I know from past experience that it does normally have the option to boot from cd and flash drives). Now this is odd, and it wasn't just the Ubuntu cd that wouldn't boot. So I tried restoring the computer to factory settings, thinking Vista had done something in it's aforementioned uninstalling spree. This didn't fix the problem and it still won't let me boot from any cds. 


**edit- it occurs to me you might not want to tear open a laptop unless it's taken heavy damage. Question retracted.

Also, what do you mean by restoring the computer to factory settings? Such as with a restore CD that came with Vista? I'm a little skeptical about the stability of your computer overall, particularly if you're having unexplained problems with vista enough that you even considered this could be vista related. Again, check the usual suspects, in your case resetting the BIOS by removing the CMOS battery, or swapping the reset jumper.

Lastly, please reestablish the chronology of incident: you describe the CD drive as being a boot option but the drive not booting initially, and then later say it's not even an option. Is this correct? If so, did anything change between those two problems? If not, can you still select to boot from CD first through the BIOS, but just not from F12?

Anything else you've done as far as troubleshooting is concerned since you made this post?

With those kinds of things checked, it should be simpler to narrow down the problem.

---

### Post by TaylorHelferty on 2008-04-17
It's a Toshiba A200-TJ9 laptop. As for the chronology, I restarted with the Ubuntu cd in the drive, and it booted into Vista. So I checked the BIOS settings and changed the cd drive to be the first boot option, and the HDD second. I rebooted, and it still went to Vista. So I restarted again and hit F12 to bring up the boot menu, and all that was there was the HDD and LAN. Now I haven't checked the boot option menu in a long time, so I don't know what went wrong and where. 

I restored the computer using the factory restore partition pre-installed on the computer. This didn't work. Now I notice that the Ubuntu 8.04 cd has an option to install something that allows you to boot from a cd. I might give that a try. Would flashing/updating the BIOS possibly work as well? I don't want to have to open this laptop up as it's new, expensive, and I'm not as familiar with laptops as I am desktops.

---

### Post by timcredible on 2008-04-17
as much as i like to blame microsoft, i kind of doubt it's vista's fault, unless it installed a new version of the bios.  most probably though, buried in the bios menus, is an option that has the cdrom as a bootable device deselected.  check around the bios menus and see if you can find that.

---

### Post by Jose Catre-Vandis on 2008-04-17
Could be the CD is not bootable? Try another bootable CD. Does that work? try your Ubuntu CD in another machine, will it boot?

If this is the case, try burning at a slower speed.

---

### Post by TaylorHelferty on 2008-04-17
The cd worked fine in other computers. It's bootable.

I just put the disc in while in Windows and let Ubuntu install a boot loader for the cd. It worked fine and Vista is now gone, with Linux in it's place. So far, 8.04 is kickenass. One more question though: this is probably an obvious answer, but I assume the beta version of 8.04 will get updates and work just like the full version when the full version comes out, right? As in, when the full release is out in a few days, I won't have to upgrade/re-install, the beta will just get the updates and stuff? Again, probably an obvious answer but I figured I'd ask anyway, as I know some betas you have to re-install when the next release comes out.

---

### Post by Jose Catre-Vandis on 2008-04-17
> **TaylorHelferty said:**
> The cd worked fine in other computers. It's bootable.

I just put the disc in while in Windows and let Ubuntu install a boot loader for the cd. It worked fine and Vista is now gone, with Linux in it's place. So far, 8.04 is kickenass. One more question though: this is probably an obvious answer, but I assume the beta version of 8.04 will get updates and work just like the full version when the full version comes out, right? As in, when the full release is out in a few days, I won't have to upgrade/re-install, the beta will just get the updates and stuff? Again, probably an obvious answer but I figured I'd ask anyway, as I know some betas you have to re-install when the next release comes out.

That's how it is supposed to work :) Most folk will either do as you suggest, or do a fresh install once the release comes out. It will still be Hardy beta underneath, and possibly a bit cluttered with some bugs lurking maybe. I did Dapper that way and had no problems. My Hardy isn't a very happy install so I will be waiting, wiping and reinstalling. Glad you got it all going :)

---

### Post by TaylorHelferty on 2008-04-17
Yeah, my Hardy isn't doing too well either. For once linux is working well with my video card (linux and video cards I've owned never got along well), but the DVD drive isn't recognized (HD-DVD drive, of course bought a month before it went obsolete). Always something. Ah well, this time I'm just going to stick with Ubuntu and make do with the bugs till they get worked out. I always switch back to Windows when I get all these problems and start missing Ubuntu.

---

