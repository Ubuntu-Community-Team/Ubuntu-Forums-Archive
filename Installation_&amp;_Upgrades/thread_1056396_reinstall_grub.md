---
title: "reinstall grub"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by davidtuti on 2009-01-31
Hi,

I have to reinstall windows xp and I lose Grub. When I reboot only windows is visible.

I boot with system-rescue-cd and I do:

grup
find /boot/grup/stage1
root (hdx,y)
setup (hdx)

But when I boot, another time only load Windows and doesn't appears me the grub menu.

Any help?

thanks a lot and sorry for my english!

---

### Post by caljohnsmith on 2009-01-31
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your System Rescue CD desktop and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

