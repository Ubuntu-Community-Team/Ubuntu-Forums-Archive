---
title: "Kubuntu 9.04 power management all whacky"
date: 2009-04-30
forum: Hardware
---

### Post by deadtom on 2009-04-30
So I go into System Settings -> Power Management and I set up my profiles and when to use them but it seems to do what ever it feels like.

For example:

I've got it set, when plugged into AC, to lock the screen when I close the lid. It doesn't lock the screen. It's also set to bring up the logout/shutdown dialogue when I hit the power button, it just shuts down, no dialogue.

I've got it set, when on battery power, to suspend to RAM when I close the lid. When I open the lid I have to hit the power button to wake it up, which I never had to do before and when it does wake up it has kicked me completely out of KDE and I'm looking at the KDM login prompt.

I can manually suspend it to RAM and wake it up fine with no problems.

Any ideas?

---

### Post by deadtom on 2009-05-01
*Bump me*

---

### Post by bottleman on 2009-05-13
I was having similar issues (it would wake up and then immediately hibernate again, then wake up properly), and started wondering if two different power managers were installed.  I found this in the Kubuntu 9.04 release notes at [http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904) :

<quote>The kubuntu upgrade may leave the no longer needed packages "kde-guidance-powermanager" or "guidance-power-manager" installed. Those can be removed. </quote>

I'm going to uninstall the guidance manager and see what happens...

....

It seems to have worked for me.

---

### Post by deadtom on 2009-11-18
I was also having issues with it locking the mouse and keyboard when waking up. I could log in remotely with ssh and restart it but could do nothing locally.
Then there was another random problem of it restarting if I plug it in or unplug it but I assumed this was more of a hardware problem.
Lo and behold, I upgrade to 9.10 and all of these problems have gone away. Everything is working great!

Marking this thread as solved... more or less.

---

