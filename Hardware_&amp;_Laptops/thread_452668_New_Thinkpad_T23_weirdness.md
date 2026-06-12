---
title: "New Thinkpad T23 weirdness"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by teripittman on 2007-05-23
I have had something strange happen. Feisty has been working fine on this Thinkpad. As of yesterday, it boots up okay and then the mouse exhibits odd behavior. It jumps around rather jerkily and the buttons won't work. When I try to bring up the Update Manager, it locks up and I have to reboot. I tried booting into restore, but that didn't seem to help. I also tried using xubuntu instead of the gnome desktop. The mouse behaves normally, until I bring up the Update Manager. Then things lock up. Any ideas?

I did try the fix mentioned in a previous thread but no go. It's behaving a bit better under XFCE, but still locks up when I open the update manager. Things do not look good at this point.

---

### Post by teripittman on 2007-05-28
I am going to try updating this one more time. It's getting to the point that I am tempted to uninstall ubuntu and try a different distro. Feisty was working fine for several weeks. Then I started getting the weird mouse behavior. I can bring up the desktop but can't use it for any real work. At some point, it will lock up. This is a dual boot with WinXP. There are no virus or spyware issues on the XP side. I have better luck bring up the XFCE desktop as Gnome seems to lock up quickly. So far, it locks up every time I try to bring up the Update manager. I use a Lucent wireless nic, which seems to be working okay. I just don't have any idea what caused this installation to go wrong.

---

### Post by maksei on 2007-05-28
perhaps try 
sudo dpkg-reconfigure xserver-xorg

---

### Post by bone43 on 2007-05-28
> **teripittman said:**
> I am going to try updating this one more time. It's getting to the point that I am tempted to uninstall ubuntu and try a different distro. Feisty was working fine for several weeks. Then I started getting the weird mouse behavior. I can bring up the desktop but can't use it for any real work. At some point, it will lock up. This is a dual boot with WinXP. There are no virus or spyware issues on the XP side. I have better luck bring up the XFCE desktop as Gnome seems to lock up quickly. So far, it locks up every time I try to bring up the Update manager. I use a Lucent wireless nic, which seems to be working okay. I just don't have any idea what caused this installation to go wrong.

Did you install the 2-6-20-16 kernel update with update manager?

if so there been some problems with it...

[http://ubuntuforums.org/showthread.php?t=456662](http://ubuntuforums.org/showthread.php?t=456662)

---

### Post by teripittman on 2007-05-29
Nope, I haven't been able to install that, although I did manage to download it the other day. (I did run the command mentioned in the other post at that time.) I tried booting into ubuntu with the wireless card out. Mouse worked fine and it seemed to be okay. I then put the card back in and things still seemed to go okay. I managed to download 11 updates. It locked up during the install at some point. 

Another thing I tried was booting up with a Dapper live CD. I can run update manager with that, which shows 248 programs to update. Did not update but at least things seemed to be working okay. I still have Edgy and Dapper installed, I believe. I've tried booting into the Edgy kernal but it seems to have the same problems. May try the older kernal too, to see how that one works.

---

### Post by teripittman on 2007-05-29
Here's an update: I had three kernels on this thinkpad: 6.17-10, 6.17-11, 6.20-15. I booted into the oldest kernel and things looked pretty good. I was able to get update manager to run and installed the latest kernel 6.20-16. Tried booting into that and noticed a few more things about this issue. When I use Gnome, I have two sets of ethernet icons at the top. One of these sets now vanishes and reappears on the upper toolbar. The hard drive is being accessed almost constantly. It's the sort of activity I see when it clears out the temp files after an install, only this doesn't stop. 

The oldest kernel seems to work just fine and I do not get that constant hard drive activity. The three newer kernels all show that activity. I guess I could just use the oldest kernel for now and wait to see if there are any new fixes that will make this work for me again.

---

### Post by teripittman on 2007-06-08
So here's my update. I've thrown in the towel, reinstalled Dapper from a live CD. I have a backup of my important files which I will reinstall. I might upgrade to Edgy again, but will not be trying Feisty any time soon. I feel bad in a way for the Feisty team. This upgrade seems to have a lot of issues. The bottom line for me is that I need a working system. Something in the upgrade made even my older kernels unreliable.

---

### Post by Talon2 on 2007-06-10
> **teripittman said:**
> So here's my update. I've thrown in the towel, reinstalled Dapper from a live CD. I have a backup of my important files which I will reinstall. I might upgrade to Edgy again, but will not be trying Feisty any time soon. I feel bad in a way for the Feisty team. This upgrade seems to have a lot of issues. The bottom line for me is that I need a working system. Something in the upgrade made even my older kernels unreliable.

You have plenty of company.  I've deemed Fiesty unacceptable on my T23 also.

The major problems I saw:

- The video driver is broken.  No direct rendering.

- Suspend is broken.

- Hibernate is broken.

- USB won't come back up if you happen to get suspend to work.

---

