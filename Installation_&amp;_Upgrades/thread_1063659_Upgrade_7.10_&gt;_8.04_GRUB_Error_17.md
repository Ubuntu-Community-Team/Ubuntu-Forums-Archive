---
title: "Upgrade 7.10 &gt; 8.04: GRUB Error 17"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by schilduil on 2009-02-08
Hi,


Freshly installed 7.10 from a live CD a few days back. Did a apt-get update; apt-get dist-upgrade to get the latests fixes. It's a clean install, no other OS on there any more. It rebooted fine.

Then when I used the GUI, the upgrade manager told me I could upgrade to 8.04LTS, so I clicked it. Some downloading, installing, cleaning up later it prompted me for a reboot. I clicked it (I'm a 'click me'-button slave, just like Alice).

When it rebooted GRUB threw me an Error 17. I did notice that during the cleanup stage earlier it did say it was throwing away some, presumably old, kernel. So I guess the upgrade procedure is missing something?


Cheers,

Bert

---

### Post by Pumalite on 2009-02-08
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by caljohnsmith on 2009-02-08
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

