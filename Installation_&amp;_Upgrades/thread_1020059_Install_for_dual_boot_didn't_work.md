---
title: "Install for dual boot didn't work"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by gregrjones on 2008-12-23
I just performed a dual boot install of Ubuntu on my Win XP system and upon reboots, I'm not getting the Grub menu options to pull up.

I know that the install must have worked because I have now lost NTFS space on the hard drive.

---

### Post by caljohnsmith on 2008-12-23
What exactly happens on start up? Do you get any errors? In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---

### Post by gregrjones on 2009-01-01
I receive no errors. Windows boots up as if I didn't even do the install. Again, the only way that I know that the install worked is that I lost NTFS disc space. I'll check out that results.txt file as you suggest and post a follow-up.

---

### Post by gregrjones on 2009-01-01
Ok, I tried executing the command to produce the results.txt file the URL path is unrecognized and can't execute. I think Ubuntu installed correctly but GRUB didn't complete. Can I somehow fix Grub to prompt me with my boot options?

---

### Post by caljohnsmith on 2009-01-01
It sounds like you may not have internet connectivity in Ubuntu; how about instead right-clicking [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the file, transfer it to your Ubuntu desktop, and run it by doing:
```
sudo bash ~/Desktop/boot*.txt
```
Let me know how that goes.

---

