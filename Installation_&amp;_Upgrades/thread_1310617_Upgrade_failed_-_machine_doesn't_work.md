---
title: "Upgrade failed - machine doesn't work"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Papapapoute on 2009-11-01
Hi everybody,

I was on an installed XUbuntu 9.04 until october, 30. October 31 I downloaded the alternate install CD v9.10, verifyied and installed under the 9.04, using the new CD. When restarted the machine, I had a white mouse on the screen, then splash wrote two errors about the setting of the screen then it freezed flickering. After some minutes, I have the command line flickering too and I can not write anything.

Now I would like to know: what can I do to have my system still working as before?

Thanks to everyone will want to help me.

I am surfing now with my Ubuntu live CD 7.04...

---

### Post by KiLaHuRtZ on 2009-11-02
I am guessing you have an Nvidia graphics card.  If so, sounds like a driver/kernel problem.  I would do this.

1) Download the Nvidia drivers right from Nvidia (will need a GUI): [http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html")

2) SSH to your box if you cannot login and kill you desktop manager.  Assuming you have XDM since your tag is Xubuntu.

```
sudo /etc/init.d/xdm stop
```

3) Change the permissions on the file you downloaded from Nvidia to be executable.

```
chmod 744 [FILE]
```

4) Install the drivers and follow the on screen instructions.

```
sudo /path/to/[FILE]
```

5) Reboot after install and everything should work.

*) Note, everytime you install a new kernel (via APT) you'll need to repeat this process.  This also allows you to have the most recent drivers from Nvidia.

---

### Post by Sistershaft on 2009-11-04
I have a similar problem. After 9.10 from a live USB I can't get past the login in page. The prompt is flickering so much I can't enter the correct password! How do I get from the prompt into the desktop environment - can I start it in recovery mode?

When I checked out the live version I was immediately invited to change to the NVidia driver ... what went wrong?

---

