---
title: "Ubuntu hands when uninstalling programs"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by ORFisHome on 2008-12-24
I purchased a Dell Mini 9 for my wife, and I am a TOTAL Ubuntu novice.  I was trying to clean up some of the bloat last night and the computer hung up when I was uninstalling some programs.  Being the novice that I am, I had no clue how to reboot safely.  I simply turned off the machine and powered back up again after a minute or so.  When I next tried to uninstall a program, I received an error message instructing me to run 'dpkg --configure -a' to fix an interrupted process.  I finally figured out how to do that, but I don't know if it really worked.  Now whenever I try to uninstall a program, the cursor simply spins and hangs up.  I don't have the option to apply the changes.  I can only hit cancel.  What have I done and how can I resolve it?!  Thanks.

---

### Post by damis648 on 2008-12-24
What software were you trying to uninstall? Were you using Synaptic Package Manager or Add/Remove Programs? Try opening a terminal and issue that command like so:
```
sudo dpkg --configure -a
```

---

### Post by theozzlives on 2008-12-24
```
sudo dpkg -a --configure
```

```
sudo apt-get install -f
```

---

### Post by ORFisHome on 2008-12-24
I was trying to uninstall some of the utility and accessory programs like Accessibility options (Screen Magnifier) by using Add/Remove programs.  I tried sudo dpkg...  It prompted me for a password and then blinked like it did something but no change.

This is the base Mini model with a 4GB SSD, so I'm trying to free up space.

What does sudo apt-get install -f do?

Thanks for the quick reply.

---

### Post by damis648 on 2008-12-24
That command fixes broken packages, which might possibly work. Try it.

---

### Post by snova on 2008-12-24
> **ORFisHome said:**
> I purchased a Dell Mini 9 for my wife, and I am a TOTAL Ubuntu novice.  I was trying to clean up some of the bloat last night and the computer hung up when I was uninstalling some programs.  Being the novice that I am, I had no clue how to reboot safely.  I simply turned off the machine and powered back up again after a minute or so.  When I next tried to uninstall a program, I received an error message instructing me to run 'dpkg --configure -a' to fix an interrupted process.  I finally figured out how to do that, but I don't know if it really worked.  Now whenever I try to uninstall a program, the cursor simply spins and hangs up.  I don't have the option to apply the changes.  I can only hit cancel.  What have I done and how can I resolve it?!  Thanks.

If you haven't found it yet, it's System -> Shut Down.

Ubuntu doesn't really like being turned off like that...

---

