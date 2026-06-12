---
title: "lid acpi notify on acer aspire 2003wlmi (hoary)"
date: 2005-03-02
forum: Hardware &amp; Laptops
---

### Post by stcoulon on 2005-03-02
Like many others, acpi is the problem while running linux on a laptop, and the acer aspire 2003wlmi I own is no exception.

I currently have 2 problems (at least ;-) ):
- suspend to ram (no progress on this)
- acpi notifications with lid (I will discuss here)

it happens that the 2003wlmi does notify when the lid is closes, and the default acpi configuration correctly fires the /etc/acpi/lid.sh script, but will never notify the system when the lid is open again.

I discovered that, when the lid is open again, while reading the /proc/acpi/button/lid/LID/state file, the status will first appear 'closed' and then next read of this file will report 'open'.

So I changed the lid.sh script, to actively poll this file, waiting for the open status to appear. The script will only exit when the lid status will change. This is less elegant than a properly event driven solution, but here I didn't see any other clue. I had a look to the dsdt of this laptop, which appears to contain any error or warning, when you try to decompile/recompile with iasl. I located some parts of the code dealing with the lid, but without hardware specs, it seems very difficult to change the default behavior of the bios (which is version 1.07).

I also changed the screenblanking mechanism of lid.sh, using a simple "chvt 12; vbetool dpms off" then "vbetools dpms on; chvt to saved console". THe default mechanism appears a bit strange to me.

because the script will run for a long time in this solution, I introduced also a lock mechanism, to avoid multiple instances of the script to run.

any comment on this issue is welcome.

---

### Post by jerome bettis on 2005-03-02
would you mind posting the contents of the script?  i'm having similar problems ... it used to work but i did somethng stupid and now it doesn't.

---

### Post by stcoulon on 2005-03-02
Yes Jerome I'll post the script as soon as I'll come back home.

After some thoughts on this acer case I came to a possible conclusion that this design (notification only when lid is closed) could be a choice of the laptop designer, if they intend to suspend to ram or disk when the lid is closed. I'm also wondering if, when you have no support for S3/suspend to ram, like me on my acer, it's worth to use this script   :-k  

My business laptop, which is an HP nc6000 running XP pro, appears to only support S3/S4/S5 suspends, according to SpeedSwitchXP. This is reflected by what you're allowed to choose in win XP's power management when the lid is closed: either do nothing, or suspend to ram/S3 or suspend to disk/S4.

Suspend to disk/S4 is probably here not an option, unless you're short on battery power for example (and is probably only reserved for this kind of situation, when your battery runs to 5% and that the pc should be safely turned off, without loosing your work).  Resuming from S4 is generally too long.

So we remain with two choices, either do nothing or suspend to ram/S3

If you choose to do nothing, pressing the lid button to simulate the closed lid on my HP nc6000 appears to "mechanically" shut the backlight of the display off (not the display completely off, only the bakclight, this is why I thing this is a mechanicall process, but I maybe wrong on this). Global power saving in this situation relies on various other parameters: delay to spin down the disk ... 

The problem with the acer is that I don't know where's the lid button (that's silly, but that's true). I suspect that at least, the acer does the same thing, turning the backlight off.

Maybe turning the display completely off using dpms is a better power saving option ? (This is what I achieve in my script, and as far as I understand, what the original lid.sh script attemps to do, even if I do not completely understand the exact magic between the call to the screenblank script and the chvt 12, which always gave me strange results).

If it's not worth it, then unless you have a working S3 suspend to ram while running linux on your laptop, then we'd better in fact to do nothing when the lid is closed (of course, only if the backlight is mechanically turned off).

If you have a working S3/suspend to ram, then opening the lid and pressing the power button to resume the laptop doesn't appear to be a big issue in the end.

---

### Post by stcoulon on 2005-03-02
Here it is

---

