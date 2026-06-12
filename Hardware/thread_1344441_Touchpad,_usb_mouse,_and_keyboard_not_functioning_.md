---
title: "Touchpad, usb mouse, and keyboard not functioning after latest xorg update"
date: 2009-12-02
forum: Hardware
---

### Post by emackey3k on 2009-12-02
Hello,

I have an old Thinkpad r40.  After I installed the latest xorg update via the update manager and rebooted my usb mouse, keyboard, touchpad and red nub thing don't work. The keyboard works in recovery mode. 

Basically it will get to the login screen and I can't move the cursor and the keyboard does not work.  

Unfortunately I can't boot from cd because the cd drive is going bad or I would just do a fresh install. 

Any help would be appreciated thanks.

---

### Post by kh1116 on 2009-12-03
Same thing happened to me
[http://ubuntuforums.org/showthread.php?t=1343473](http://ubuntuforums.org/showthread.php?t=1343473)

---

### Post by lidex on 2009-12-03
What update was that? Have you tried booting into rescue mode with LiveCD? That will give options to fix your xserver.

---

### Post by emackey3k on 2009-12-03
> **lidex said:**
> What update was that? Have you tried booting into rescue mode with LiveCD? That will give options to fix your xserver.

Unfortunately the cd drive is bad and I can no longer boot from cd.  

I have gone in recovery mode and droped to roost shell and tried to edit the xorg.conf.  There was no section for inputs so I put one in.  Rebooted and still no luck.

---

### Post by emackey3k on 2009-12-03
I'm not sure what update it was for sure I just remember seeing xorg.  I normally don't think anything of running updates so I didn't keep a close eye on what it was.  It is possible it is just a coincidence that this started but it was working fine did the update rebooted and now it doesn't work.

---

### Post by lidex on 2009-12-03
Any way you can post the output of? 
```
sudo lshw -short
```
and
```
lspci
```

---

### Post by lidex on 2009-12-03
Here are some fixes:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8127237]("http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8127237")
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8346782]("http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8346782")
[https://bugs.launchpad.net/ubuntu/+bug/334249]("https://bugs.launchpad.net/ubuntu/+bug/334249")

---

### Post by emackey3k on 2009-12-03
I have no way to paste the results.  I will have to type it out.  What exactly should I be looking for so I can type that instead of the whole results?

---

### Post by efflandt on 2009-12-03
If you can get into the console in recovery mode, use **sudo less /var/log/apt/term.log** to see what last package(s) were installed at the end.  Also what version of Ubuntu are you currently running, and the output of **uname -a**?

The most recent X does not use xorg.conf unless you need to specify something special, so maybe something in your old one is mucking it up.

---

### Post by emackey3k on 2009-12-03
</entry>
<entry name="Update_handlers" mtime="1257196771" type="schema" stype="list" owner="gnome" gettext_domain="libgnomekbd" list_type="string">
<local_shema locale="C" short_desc="Keyboard Update Handlers">

---

