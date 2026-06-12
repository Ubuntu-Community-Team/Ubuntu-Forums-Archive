---
title: "Aspire One upgrade experiences"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by JamesSmith on 2009-11-03
Hi all.

Wondering what others' experiences with the **upgrade **on an Acer Aspire One?

I've got Jaunty running well on my AOA150-Ab but I'm yet to pluck up the courage to do a distro upgrade to Karmic - I'm worried about things going wrong.  For a start I installed the UNR version of 9.04 but have ditched the remix desktop for the standard one, stopped 'maximus', installed emerald etc and I don't want these things to change, get lost or messed up.

Also, all of the hardware works (after a fashion), but having read around a bit people seem to have all sorts of little issues.

Any feedback greatly appreciated. Cheers, James

p.s. doing a backup right now, just incase I bite the bullet!

---

### Post by Toddy on 2009-11-03
Hi James.  I too have a AOA 150 and originally installed Hardy along side the native Linpus partition.  I've also installed Intrepid and Jaunty, but was never really satisfied with those two. Hardy always seemed more solid. However, I've been pleased with Karmic.  When Karmic GA'd, I decided to wipe all those partitions and install a clean install of Karmic. Everything is working out of the box for me. I have had no regrets.

---

### Post by JamesSmith on 2009-11-03
> **Toddy said:**
> When Karmic GA'd, I decided to wipe all those partitions and install a clean install of Karmic. Everything is working out of the box for me. I have had no regrets.

Hi Toddy.  I'm glad to hear everything works well on a clean install. The thought has crossed my mind but I don't know if I can remember how to do some of the tweaks again!  I did try Karmic out live from a usb stick, and everything seemed ok.

---

### Post by wilee-nilee on 2009-11-03
Well since you have the usb set up with Karmic do a clean install, I have a acer net-book and switched to the standard rather then the remix. I like the remix but it seemed to have some problems that may be worked out now.

---

### Post by skotos on 2009-11-04
I installed Karmic UNR on my Asus eeepc 900 and I am satisfied: 9/10.  :D

Just one note: [B]if you attach the second display and run it in non mirror mode but as a separate screen with its content and configuration, a mess comes out. 

[/B]No test has been done with this configuration before realeasing UNR: 2/10. [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

---

### Post by nevarDeath on 2009-11-04
I have an AOA150 running UNR 9.04. Before upgrading to 9.10, I imaged the HDD using the dd command. Sure glad I did because my touchpad does not work (plugging in a USB mouse does work), it rarely boots to the GUI login screen (have to login then type 'startx', bootup and general usage are super slow, and monitor mode no longer works with my madwifi drivers. I'm sure the madwifi drivers probably just need to be patched again, but the system was so slow, I have re-imaged my HDD with the 9.04 and will have to do a porper file backup, then do a clean install of 9.10 and see how that goes.

---

### Post by JamesSmith on 2009-11-06
Hmm. doesn't sound good. I think I'll test out the live usb for abit and eventually go for a fresh install to avoid any of those problems. Cheers

---

### Post by jwmuelle on 2009-11-06
I've been on Karmic with my AOA-150 since pre-RC.  Had initial problems with wireless (Atheros).  From prior experience I knew wireless worked with Jaunty.  I loaded Jaunty from alternate CD so I could get luks encryption, then did upgrade to Karmic and all has been well.  I'm using the ath5k modules instead of madwifi.

Except when taking it about town, I run dual-head with 22" 1680x1050 VGA monitor oriented "above" the laptop.

No real problems to speak of using gnome and even gnome-shell.  I've tried KDE, XFCE, and E16 but ran into significant display issues... like X crashing and constantly taking me back to the login screen.  As I think back... was trying those with dualhead... never tried only with the micro display.

I've kept away from the UNR due to the annoying way maximus functions when I'm dual-head and netbook-launcher insists on using the VGA rather than LVDS display.  

About 75% of my use is at home, so prefer everything working with dualhead and large display.

Overall, it's so nice it's replaced Fedora 11 as version of choice even before it went GA.

jw

---

### Post by Cowan283 on 2009-11-13
I upgraded my AAO to Karmic and it was a total failure. After about three minutes from booting it would start having serious kernel problems and slow massively down, also i'm not a fan of the new netbook remix. I backed up my files and got a list of my packages; then i did a clean install and everything now works fine. I ditched the netbook launcher but kept maximus and the window picker applet, i'm now happy with karmic.

---

### Post by JamesSmith on 2009-11-13
> **Cowan283 said:**
> I upgraded my AAO to Karmic and it was a total failure.

Hi Cowan, this is exactly what I'm concerned about, and having sparked up a [thread]("http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=18536&sid=b97f07ff87e5a26a749125edcd5dc6ce") on the AspireOneUser forum I've decided not to bother as it sounds too risky.  At some stage when I have a bit more time on my hands I will probably do a fresh install of Karmic, but until that day Jaunty will do me just fine as it is.

Cheers

---

