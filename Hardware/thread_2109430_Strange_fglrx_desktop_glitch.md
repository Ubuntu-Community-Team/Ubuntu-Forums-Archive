---
title: "Strange fglrx desktop glitch"
date: 2013-01-27
forum: Hardware
---

### Post by craigcrawford114 on 2013-01-27
Hi,

I was wondering if anyone could help me with my issue. I know fglrx is proprietary, but this seems to be the only bug I have with the drivers, and the performance of the X.Org drivers is terrible (plus no CrossFireX).

I've uploaded a video to YouTube to show you what is happening, when I use the X.Org drives this doesn't happen but as I said earlier, the performance is terrible.

Since the performance was bad, I decided to install the "fglrx" driver, which worked good at first. Then I changed the CrossFireX mode, changed the display output to Full RGB and turned on the setting to remove desktop tearing and this problem appeared. I thought, no biggie, I'll just change it all back and find out the problematic setting. No dice, it stayed even though I changed everything back.

So I installed fglrx-updates and that is the same. I've also tried disabling various desktop effects and Googling to see if anyone else has this issue and nothing really matches mine.

Is there anything I can possibly try, or do to resolve this? Even if I lose a tiny bit of performance, it's better than having this annoying problem...

YouTube video: [http://www.youtube.com/watch?v=4Fp8rpKaMT4](http://www.youtube.com/watch?v=4Fp8rpKaMT4)

Many thanks.

---

### Post by Yellow Pasque on 2013-01-27
I would try Catalyst 13-1 first: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

If that doesn't help, try a different dekstop environment. It may be a Unity-specific issue.

---

### Post by craigcrawford114 on 2013-01-27
I have just tried it, same result :(.

---

### Post by Yellow Pasque on 2013-01-27
Tried the newer driver or a different DE? Both?

---

### Post by craigcrawford114 on 2013-01-27
Tried different driver, not Desktop Environment yet.

If it makes any difference, this glitching is also appearing on the login screen.

---

### Post by craigcrawford114 on 2013-01-28
So, does anyone have any idea apart from installing another desktop environment? I'd rather not try another because when I saw the sheer amount of packages aptitude wanted to install for gnome3, I shuddered.

Not that it's a problem, I just would rather try other possible things first.

Also, I thought the login screen was pre-DE... or am I wrong?

---

### Post by Yellow Pasque on 2013-01-28
You can try lxde. It's small and you can install it with minimal packages:
```
sudo apt-get install --no-install-recommends lxde-core
```

> Also, I thought the login screen was pre-DE... or am I wrong?
I don't understand what you mean here.. :\

---

### Post by craigcrawford114 on 2013-01-28
> **Temüjin said:**
> You can try lxde. It's small and you can install it with minimal packages:
```
sudo apt-get install --no-install-recommends lxde-core
```


I don't understand what you mean here.. :\

I mean, before you login you aren't in Unity right? I still get this issue before I've logged in.

---

### Post by craigcrawford114 on 2013-01-28
This looks as close as I have as similar to what I am experiencing:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1067320](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1067320)

Okay, I've been fiddling around with various stuff (removing old kernels, messing around with some compiz settings, and removed the load "dri" from xorg.conf) and the blinking cursors have moved up higher.

---

### Post by Yellow Pasque on 2013-01-28
The login manager can use different greeters to draw things and the default for Ubuntu is the unity greeter. So it is possible that the issue could manifest itself at login screen and not in lxde environment...

---

### Post by craigcrawford114 on 2013-01-28
Okay, currently posting from lxde and the problem has disappeared...

Edit: Actually, I restarted and went straight into lxde and it was there. I logged out and it was gone. Seems like logging in, and then out makes it disappear.

---

### Post by craigcrawford114 on 2013-01-28
Hooray! I found a viable temporary solution!

I decided to make it so **lightdm** is stopped, and then started upon boot by placing the following in **/etc/rc.local**:

```
service lightdm stop
sleep 1
service lightdm start
```

And the lines have disappeared!

---

