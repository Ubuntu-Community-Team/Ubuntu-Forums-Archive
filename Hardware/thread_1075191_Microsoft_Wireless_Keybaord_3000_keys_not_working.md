---
title: "Microsoft Wireless Keybaord 3000 keys not working"
date: 2009-02-20
forum: Hardware
---

### Post by NexusZA on 2009-02-20
Hi there all,

I started using Ubuntu with Hardy and loved the OS. I went and bought a new Wireless keyboard/Mouse set, the Microsoft Wireless Laser Desktop 5000 mouse and the Microsoft Wireless Keyboard 3000. Each of these components have hotkeys, the ones on the keyboard specifically allow you to:

- Start/pause music
- Increase volume, Decrease volume, Mute Volume
- Back and Forward in browser
- Open browser
- Open mail client
- Open Search box
- Open Calculator

When I bought them and plugged them in no problems whatsoever. The keyboard and mouse worked without incident and all hotkeys responded as I expected.

Then I upgraded to Intrepid. Now not a single one of these hotkeys work. I use the same keyboard/mouse combo on two different systems. One system was an upgrade to 8.10 from 8.04 the other a fresh install of 8.10 and on both the keys do not work.

I have tried to find any solution I could on how to fix this but all of the suggested fixes don't seem to work. There was some guide about going to console and pressing the keys to see what codes they give me but even there they give no response.

This is bad enough to have me considering wiping out Intrepid and installing Hardy back on, which I don't really want to do as the improvements on Intrepid for me are brilliant apart from this ONE issue :S.

Any help will be greatly appreciated guys and feel free to ask me for any more info you may need as I am relatively new to Ubuntu so not exactly sure where I should be looking to fix this

---

### Post by NexusZA on 2009-02-20
Just as a bit of a bump. No one have any ideas how to fix this at all? Is it a bug that I just need to wait to get resolved or is there actually something I can try at all?

---

### Post by djriskyp on 2009-02-20
I would also like to know how to resolve this issue. I just got the Microsoft Wireless Laser Desktop 4000 keyboard and am having the same issues with each hotkey. Also running Ubuntu 8.10.

I have tried using [keyTouch]("http://keytouch.sourceforge.net/") and also [LinEAK]("http://lineak.sourceforge.net/index.php?nav=docs") to create a custom profile for this keyboard, but I can not get it to work with either keytouch-editor or the instructions given on the LinEAK website. After running 'xev' there is data output only for the "My Favorites" hotkeys, but not for any of the others.

Any help is greatly appreciated.

---

### Post by keibak on 2009-02-26
This is a known bug. Please see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/281993](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/281993)

---

### Post by dodongo on 2009-04-18
> **keibak said:**
> This is a known bug. Please see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/281993](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/281993)

Note that the fix for this issue has been committed for Intrepid (8.10) and Jaunty (9.04).

I also experienced this problem but as of today, things are working again as expected.  Media keys, calculator key, everything.  Good deal!

---

