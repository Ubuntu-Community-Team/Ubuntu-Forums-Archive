---
title: "black screen on wake up for acer 5535"
date: 2011-01-12
forum: Hardware
---

### Post by Yehonal on 2011-01-12
Hello Ubuntu community.
I have an acer aspire 5535. when it goes into suspension and after i try to wake up , it doesn't seem to show signs of life ( black screen)..
I did a search and found many other cases similar to mine, but none of the solutions / workarounds are compatible with my problem
(I tried to kill the xserver, change the screen mode with FN + F4, type the user password and press enter ..but nothing... the problem is that as soon as i press a button to wake up, it seems to read the harddisk for 2 seconds and then it doesn't responds to anything except forced poweroff, pressing power button for 3 secs)

---

### Post by issues on 2011-01-22
I've been having the same problem for a while. That also happens on another Ubuntu-based distro. I read extensively the forum, looking for clues of what might have been happening, but I haven't found anything.

Some people suggested alternative methods such as 'hibernate' and 'uswsusp', none of them worked. Some changes on grub didn't do a thing either.
All I get after waking up is a blank screen, I can't toggle function keys like Caps Lock and if I press Fn + F4 it just gives a loud beep and doesn't do a thing.

I'd be happy to help with logs, but I think enough logs have been spread around the forum. Something I heard might work was updating the kernel to 2.6.36, but I'm not confident I can do such thing without fucking up a few times first.

Oh, and I use the same laptop. Acer Aspire 5535. I guess specifically it's 5535-50, since it's the model without Bluetooth. It probably makes no difference, though.

---

### Post by Lupajz on 2011-04-09
Same notebook, and same problem here :( Guess we have to wait for 11.04 release :P

---

### Post by Lupajz on 2012-01-11
Hey, I'm back on ubuntu 10.04 ;) I still have this problem with suspend/hibernate on this acer :P I was wondering if it is possible to port something from fedora and openSuse to make this suspend/hibernate work ? 

As this guy says that something works, something does not : 
```
http://forums.opensuse.org/english/get-technical-help-here/laptop/457171-acer-aspire-5535-standby-issues.html
```

> standby works on fedora 14 but hibernation does not and hibernation works on opensuse but standby does not

---

### Post by Yehonal on 2012-10-08
I regret to bump an old post guys, but i still have this problem with acer 5535 laptop...but now i really need the suspension feature because i'm using it for the university

i've noticed there was also a bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/948573](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/948573)

but it expired for inactivity..

so, is it possible that the only way to get ubuntu suspension/ibernation is to change the laptop itself?

isn't there a fix/workaround solution?

---

