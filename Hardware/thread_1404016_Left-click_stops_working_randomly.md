---
title: "Left-click stops working randomly"
date: 2010-02-10
forum: Hardware
---

### Post by oiler920 on 2010-02-10
I've got a rather annoying problem on my hands here. I'm running Ubuntu 9.10 on my Dell Latitude D600, and sometimes, at seemingly random intervals, the left-click will stop working. I know it's not a issue of the button being physically broken, because the touchpad clicking stops working as well, and I never experienced this issue on Windows XP or 7. Searching Google turned up nothing. Any ideas on what to do?

EDIT: Based on later reports, this appears to be due to a bug in the Synaptics touchpad driver, and not hardware-specific.

---

### Post by Sef on 2010-02-11
When does this happen?  After you have been on for a while or shortly after booting up or either?   How soon does the left click start working again?

---

### Post by oiler920 on 2010-02-11
Usually happens after I've been using it for a while. It lasts about one to two minutes each time before it starts working again.

---

### Post by oiler920 on 2010-02-16
bump

---

### Post by nocnokneo on 2010-03-01
I'm having the same really annoying problem on a Dell XPS M1330. Help!

---

### Post by shae on 2010-03-02
I also have the problem on my Inspiron 1420.  Perhaps it is related to the USB from santa rosa chipsets?

---

### Post by JlyGrnMigt on 2010-03-02
I am having the same problem on my Zareason Terra.  This is the 2nd time it's happened, and it definitely lasts longer than 20 minutes for me.

The first time, I was downloading some large updates and walked away for about an hour.  It was malfunctioning when I came back, and stayed that way through multiple reboots.  It was working again the next morning.

Now, two days later it's happened again.  I was watching a video and the click wasn't working when the video ended.  It's been a few hours, I've rebooted twice, and no luck.  I'm stuck using a bizarre combination of keyboard commands, right-clicking, and hitting enter.

---

### Post by JlyGrnMigt on 2010-03-03
For the last 24-hours, my tap-click has been working, but the left touchpad button is still dead.  Anyone else having any luck fixing this or are we stuck waiting until April?

---

### Post by Elango Mani on 2010-03-04
I am using Hp Mini 210 ...with  Ubuntu 9.10...even i am facing problem with my left and right click in my touch pad.. Is any driver software need to installed to make it work.. Please help... Were can i get the drivers for this

---

### Post by JlyGrnMigt on 2010-03-06
I have a new clue.  When I reboot (which is often because things are freezing like crazy in addition to this click thing), the BIOS screen has a line that says "no tpm or tpm has problem".  Pages found whilst googling indicate that people running windows with this issue can't boot at all.  The solution seems to be a BIOS update which, quite honestly, sounds a little scary.  The forums here seem to have no trace of this error, unless I searched with a typo.

Others with the click issue, do you see this error when you're booting as well?

---

### Post by dazzakoh on 2010-03-06
I am having this problem as well.  Acer Extensa 5620. Ubuntu 9.10

Everything ran perfectly well till about a week ago.  Then after an update on synaptic, this problem appeared.

I dual-booted back into Windows Vista, and there's no problem.

I had thought it was due to some incompatibility with the Linux kernel, but don't know how to downgrade it back to an earlier version.  Then again, the fact that it starts off working after a reboot makes me wonder if it is a  hardware problem - but I have no issues running under Vista/

Let's keep logging this issue in case it's more than just a few random people.

---

### Post by JlyGrnMigt on 2010-03-06
I didn't set up dual boot this time because I'm trying to force myself to use linux :)  When I would run into problems with dual boot machines before, I'd just stop using the linux side...

Unfortunately for me, the problem does not go away when I reboot.  For a short amount of time, my ability to tap and click came back, but that is gone now as well and I am left with only my right click.  The mouse pointer itself moves around just as expected, though it's picked up some occasional new errors as well.

I'm using UNR, and with a screen full of icons, the mouse will sometimes pick up the first icon it hits as if I were trying to drag it somewhere.

Lack of left click is more than a simple annoyance.  I've found that some sites become more difficult and lose some functionality (google reader...can't comment) and others lose a large amount of function (ravelry...browsing functions requires clicking to use tags).  If I wanted to live like this, I'd still be using lynx.  On my computer itself, I can't even use network manager.  To get online, I have to use a dsl workaround in a terminal which doesn't allow the use of my vpn.

Do you have the TPM message on startup?

---

### Post by mhakali on 2010-03-10
Problem confirmed Ubuntu 9.10 64-bit & Sony Vaio SZ5.

Do we have any status on this?

---

### Post by oiler920 on 2010-03-10
It seems that this is not hardware-specific, but rather a bug in the Synaptics touchpad driver. Updated first post accordingly.

---

### Post by andretav on 2010-03-11
I have the same problem on a HP mini 1033cl, running UNR 9.10. The left click fails all the time, when I change windows, like from a program for another. I can't open file/program clicking the icon, neither drag them. It's very odd.

---

### Post by JlyGrnMigt on 2010-03-11
> **oiler920 said:**
> It seems that this is not hardware-specific, but rather a bug in the Synaptics touchpad driver. Updated first post accordingly.

If there is a fix, can you give us a link or tell us what you did?

---

