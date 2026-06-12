---
title: "Dell 8600 suspend on lid close"
date: 2005-10-15
forum: Hardware &amp; Laptops
---

### Post by vulpes76 on 2005-10-15
I have just installed breezy I can suspend via the log out menu but i'd like to be able to suspend via lid close. Can anyone help me with how I do this?

I have installed Gnome Power Manager but the options seem very limited compared with the screenshots i've seen?

---

### Post by Hezekiah on 2005-10-15
As far as I know (I haven't used the Gnome Power Manager, as I've heard that it has many problems still...), one of the easiest ways to do this is with a little bit of console-action :-)

For my laptop (Sony VGN-S260), I setup suspend-on-lid-close by changing around some of the ACPI scripts in /etc/acpi :
```

# cd /etc/acpi
# sudo mv lid.sh lid.sh.ORIGINAL
# sudo ln -s sleep.sh lid.sh

```
Now, when you close the lid, the computer should go to sleep.  Pressing a key should wake it back up.

If there is a better way to do this, I'd love to hear it!  But that's what I've used for both Hoary and Breezy.

---

### Post by blawson327 on 2005-10-15
wow, after messing with  5.04 for a long time trying to make my 8600 do some type of suspend and failing.....i did what you posted with breezy and it comes back out of suspend nicely!! that was why i had to ditch hoary, can't beleive i finally have that!! thanks

---

### Post by vulpes76 on 2005-10-15
that didn't work with my 8600. Suspend works via the applet out of the box but I can't get it to work via the lid.

blawson327 did you only make the changes above and suspend now works on lid close on your 8600?

Has anyone got any suggestions/ideas?

---

### Post by Hezekiah on 2005-10-15
vulpes76 - can you post the output from:
```

# ls -l /etc/acpi

```
to the forum?  Maybe there is a symlink problem?  Also, you can take a look in /etc/default/acpi-support and try toying with some of the options in there.  After making a backup of the original file, of course :-)  I didn't have to tweak anything in there for Breezy (other than enabling Suspend to RAM), but I did under Hoary.

---

### Post by vulpes76 on 2005-10-15
here is the output:

```
david@cbanksii:~$ ls -l /etc/acpi
total 124
-rwxr-xr-x  1 root root  270 2005-10-12 22:42 asus-touchpad.sh
-rwxr-xr-x  1 root root  203 2005-10-12 22:42 asus-wireless.sh
-rwxr-xr-x  1 root root  152 2005-10-12 22:42 ejectbtn.sh
drwxr-xr-x  2 root root 4096 2005-10-16 06:36 events
-rwxr-xr-x  1 root root  611 2005-10-12 22:42 hibernate.sh
-rwxr-xr-x  1 root root  310 2005-10-12 22:42 ibm-wireless.sh
lrwxrwxrwx  1 root root    8 2005-10-16 06:25 lid.sh -> sleep.sh
-rwxr-xr-x  1 root root 1029 2005-10-12 22:42 lid.sh.ORIGINAL
-rwxr-xr-x  1 root root  153 2005-10-12 22:42 mailbtn.sh
-rwxr-xr-x  1 root root  156 2005-10-12 22:42 mediabtn.sh
-rwxr-xr-x  1 root root  152 2005-10-12 22:42 mutebtn.sh
-rwxr-xr-x  1 root root  151 2005-10-12 22:42 nextbtn.sh
-rwxr-xr-x  1 root root  817 2005-10-12 22:42 panabright.sh
-rwxr-xr-x  1 root root  287 2005-10-12 22:42 panapower.sh
-rwxr-xr-x  1 root root  150 2005-10-12 22:42 playbtn.sh
-rwxr-xr-x  1 root root  433 2005-08-31 03:33 powerbtn.sh
-rwxr-xr-x  1 root root 1630 2005-10-12 22:42 power.sh
-rwxr-xr-x  1 root root 2243 2005-10-12 22:42 prepare.sh
-rwxr-xr-x  1 root root  151 2005-10-12 22:42 prevbtn.sh
drwxr-xr-x  2 root root 4096 2005-10-14 06:20 resume.d
-rwxr-xr-x  1 root root 2889 2005-10-12 22:42 resume.sh
-rwxr-xr-x  1 root root  304 2005-10-12 22:42 screenblank.sh
-rwxr-xr-x  1 root root 1217 2005-10-12 22:42 sleep.sh
-rwxr-xr-x  1 root root  700 2005-10-12 22:42 sonybright.sh
-rwxr-xr-x  1 root root  152 2005-10-12 22:42 stopbtn.sh
drwxr-xr-x  2 root root 4096 2005-10-14 06:20 suspend.d
-rwxr-xr-x  1 root root  637 2005-10-12 22:42 toshbright.sh
-rwxr-xr-x  1 root root  172 2005-10-12 22:42 tosh-wireless.sh
-rwxr-xr-x  1 root root  151 2005-10-12 22:42 voldownbtn.sh
-rwxr-xr-x  1 root root  148 2005-10-12 22:42 volupbtn.sh
-rwxr-xr-x  1 root root  151 2005-10-12 22:42 webbtn.sh
-rwxr-xr-x  1 root root  442 2005-10-12 22:42 wireless.sh
```

---

### Post by vulpes76 on 2005-10-15
what do you mean by a symlink problem?
I have had a look at acpi-support and enabled suspend to RAM but still no luck, i've noticed that Fn + ESC that is meant to suspend doesn't do anything either.

---

### Post by Hezekiah on 2005-10-15
I'm sorry, I'd misread your earlier post.  The directory listing does look the same as it does on my laptop though, for what that's worth :-)

I'm running a Sony VAIO VGN-S260, so the details of this setup may be different.  You could try looking at /etc/default/acpi-support to see if ACPI_SLEEP=true is commented out.  I'm not sure if the menu Sleep option and the /etc/acpi/*.sh scripts both look at this, or if they check different places to see if Suspend-to-RAM is enabled.

---

### Post by vulpes76 on 2005-10-18
I have checked my acpi-support and it was commented out (although i still had the suspend option through the logout applet) so i uncommented it and still no luck with suspend via lid close or via Fn + ESC.

Does anyone know if both the applet and /etc/acpi/*.sh scripts both look at acpi-support ACPI_SLEEP=true or do i need to update something else for the lid and Fn + ESC suspends to work?

Any help would be greatly appreciated

---

### Post by ewinslow on 2005-10-18
I've also issues for sleeping for a Dell Inspiron 6000 on coming back from sleep. The machine seems to go to sleep OK with lid close or from the logout menu (I did do the suggestion of the previous poster with point lid.sh to sleep.sh), but the display never comes back. Power light comes back on full force, but the display remains blank. It doesn't appear that there are any useful entries in the syslog either.

This machine does have the ATI graphics card and I am not running 3d acceleration.

This did not work under Hoary either, but at least it goes to sleep. I'm getting closer!

If anyone knows of a thread that has a solution for this, please let me know. I'll keep on looking, course.

---

### Post by Ainvar on 2005-10-19
For the 8600 users do you have an ato card and if so what drivers are you using? The reason I am asking this is cause I have the 6000d (8600 blew up and they had no new ones to replace it with so I got bumped to a 6000d) and it has an ati x300 card. I use the fglrx drivers so I can have some 3d action goodness. I was wondering if suspend works for you if you are using the fglrx drivers.

---

### Post by Zinoc on 2005-10-19
Hello,
I am a inspiron 8500 user. Our laptops are very similars, except the video card: I have a nvidia 4200 go. 
I have the same problem, my laptop don't want to wake up form sleep (with or without nvidia proprietary drivers)
I'm very interested in resolving this problem.

---

### Post by vulpes76 on 2005-10-19
My 8600 has an ATI 9600. I tried the fglrx drivers under Hoary and it will goto sleep but won't resume from my understanding it's a known issue with ATI proprietry driver.

At the moment I only have the ubuntu driver installed under breezy as i'd like to get power management working, mine wakes without a problem i'd just like to get it to suspend via Fn + ESC and or via a lid close rather than having to use the logout menu.

---

### Post by awaldram on 2005-10-20
hi I have an s6010 for fujitsu siemens running ans 830m chipset.

I also have suspend and hibernate modes working.

To get suspend to resume properly I had to

1 Added acpisleep=s3bios in grub.conf 
2 remove all the fancy fixes for buggy video in acpi-support (breaks more than it fixes on my laptop)
3 add my prim54 network card for removal before suspend
4 move my embeded prism from  the orinoco_pci module to hostap.

Orinoco_pci seems to have serious issues with my chipset works fine until you put it under heavy load then falls over in a heap... hostap has been very stable and resumes cleanly. 


put "/etc/acpi/sleep.sh" into the lid.sh script (just after the lid detect stuff)

---

### Post by gmc on 2005-10-21
[QUOTE=Hezekiah]...one of the easiest ways to do this is with a little bit of console-action :-)

```

# cd /etc/acpi
# sudo mv lid.sh lid.sh.ORIGINAL
# sudo ln -s sleep.sh lid.sh

```
Now, when you close the lid, the computer should go to sleep.  Pressing a key should wake it back up.

If there is a better way to do this, I'd love to hear it!  But that's what I've used for both Hoary and Breezy.[/QUOTE]

Hi Hezekiah,

Thumbs up :)  here, this was just the ticket for my Toshiba Satellite Pro 4600. Thanks for the tip. 

It occured to me, that if you can get acpi suspend to work this way, why can't we get hibernating to work too. So I tried this:

```

# cd /etc/acpi
# sudo mv powerbtn.sh powerbtn.sh.ORIGINAL
# sudo ln -s hibernate.sh powerbtn.sh

```

This allows my laptop to sleep if I close the lid and hibernate when I hit the power button. Only problem with this is that this method of hibernating is not as quick as the suspend2 hibernation method (discribed in another howto in this forum). I tried to combine both Hezekiah sleep fix and suspend2 but wasn't successful.

G.

---

### Post by bbpackwood on 2005-10-26
Hi,

The above did not work for me, but after playing around I found the best way to do this is:

cd /etc/acpi
sudo mv lid.sh lid.sh.ORIGINAL
sudo gedit lid.sh

Then erase everything but:

#!/bin/sh

sudo /etc/acpi/sleep.sh sleep


The advantage of this method is that your notbook will wake up as soon as you open the lid.

-good luck

---

### Post by scotartt on 2006-01-04
[QUOTE=Zinoc]Hello,
I am a inspiron 8500 user. Our laptops are very similars, except the video card: I have a nvidia 4200 go. 
I have the same problem, my laptop don't want to wake up form sleep (with or without nvidia proprietary drivers)
I'm very interested in resolving this problem.[/QUOTE]

Has anyone ever actually solved this issue? I have an Inspiron 8500 with Breezy installed and with the following observed behaviour;

- Lid close does not suspend or hibernate computer - just blanks screen

- Choosing suspend from the Log Out dialog results in a machine whose screen cannot be woken back up.

- I've tried various solutions found in the forums, in the wiki, and on the net generally, to no real success.

I am not using the proprietry nvidia drivers, rather the "nv" ones.

---

### Post by pbv on 2006-01-05
I have an Inspiron 8500 with the Nvidia card and 1.0.7667 driver and I have managed to work around the blank screen on resume. What you have to do is disable LOCK_SCREEN on /etc/default/acpi-support so that the screen doesn't resume locked already.
Then if the screen doesn't come up on resume just hit the lid button again (which should blank and lock the screen). This is enough to "reset" it and it comes up most of the time. Occasionally this still doesn't work, thought.

BTW, I have done some changes to the config scripts which might or might not be required to get this working:

/etc/default/acpi-support:
ACPI_SLEEP=true
SAVE_VBE_STATE=false
LOCK_SCREEN=false
DISABLE_DMA=true
RESET_DRIVE=true
ENABLE_LAPTOP_MODE=true

/etc/X11/xorg.conf:
Add to the device section:
Option NvAGP "1"

/etc/hotplug/blacklist:
# disable intel agp - use nvidia's instead
intel_agp

---

### Post by pbv on 2006-01-05
Just some follow up on my own post: I've found out how to automatically restore the screen on resume. Edit /etc/acpi/resume.sh, look the line 
  su $user -c "xset dpms force on"
and add a line
  su $user -c "xset dpms force off" 
before that one (off then on). That's it - screen comes up all after resume all the time for me.

---

### Post by BrendanM on 2006-12-30
> **Hezekiah said:**
> 
For my laptop (Sony VGN-S260), I setup suspend-on-lid-close by changing around some of the ACPI scripts in /etc/acpi :
```

# cd /etc/acpi
# sudo mv lid.sh lid.sh.ORIGINAL
# sudo ln -s sleep.sh lid.sh

```
Now, when you close the lid, the computer should go to sleep.  Pressing a key should wake it back up.

This worked fantastically for me on a Dell Latitude c610 running Edgy, thanks.

---

### Post by kjur on 2008-02-03
Hi all,

I run Xubuntu 7.10 on Dell 6400.

The solution with a sym link works great for me.

The one problem I experience is when I open a lid the system wakes up, but then I have a text mode with a message
```
* Shutting down ALSA...
```
and it goes sleep again. I have to press Power button to wake it up, and then all is fine. All works great - wi-fi, usb, keyboard, etc.
The screen blink and pressing the power button is just annoying. Especially that my family uses the laptop and they are not very familiar with linux, so want to make all user friendly for them.

Any idea how to fix the isue? Is anyone experiencing the same?

Cheers,
Greg

---

