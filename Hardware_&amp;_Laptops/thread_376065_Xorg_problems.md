---
title: "Xorg problems"
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by davbren on 2007-03-04
I installed new ati drivers for xorg using the package manager. I now get as far as the splash screen for ubuntu and then nothing happens. Is there a solution to this problem. Also is there a way of accessing my files? Maybe using the ubuntu live CD?

---

### Post by taurus on 2007-03-04
Boot into recovery mode from the GRUB menu and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
Then, reboot.

```
shutdown -r now
```

---

### Post by davbren on 2007-03-04
Yh I tried that and still no luck, I can log into other accounts that aren't using beryl but mine is, i have some work that needs to be taken from my account but i cant access my files from the other accounts because of permissions. As long as i can get my files i can reinstall no probs but its getting the files that is the problem

---

### Post by taurus on 2007-03-04
What is your login name then?  Just have to change the permissions so others can access your old account.

---

### Post by davbren on 2007-03-04
my login name is dave...

---

### Post by taurus on 2007-03-04
Try this.

```
sudo chmod -R 777 /home/dave
```
Now, everybody can read and write to /home/dave.  So, backup whatever you need in /home/dave.

---

### Post by davbren on 2007-03-04
and how do would i be able to uninstall the xorg-ati-driver thingy?

---

