---
title: "Ubuntu and Vista dual booting, GRUB error 22"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by valdemaras on 2009-02-17
Hello Community.
Recently I got my Ubuntu 8.10 CD shipped and I decided it's time to give it a chance. I have an ASUS F3E series laptop with Vista Home Basic installed, and I thought I won't erase it until I don't get used to Linux completely. Ok, so the installation went perfect. Since I have a hard disk of 280GB splitted to C: and D: (in windows) I gave Linux ~14GB of C:, the same where windows are. The installation went great, as I mentioned, it finished, restarted computer - voila, I have myself a fresh, shiny Ubuntu installed. Then I try to get to my Windows Vista. I restart the computer, GRUB menu appears, I choose "Windows Vista/Longhorn loader"... and it goes mad. It starts swearing and puking with errors, throws me a window with big red "ERROR" sign, and I turn off my laptop. I then try to turn it on again, it says "GRUB ERROR 22", or something along these lines, but something about Error 22. 

Okay, I heard something about Vista being not-too-friendly to other OS's, but c'mon, I've seen people dual booting Vista and other Linux's all the time, so that _IS_ possible. Please, if someone had this problem or at least similar, and knows how to solve it, help me. ;)

---

### Post by caljohnsmith on 2009-02-17
It sounds like you might have unintentionally booted your Vista recovery partition from Grub, and if that was the case, Vista would have reinstalled to that HDD and probably overwrote Ubuntu. In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD, download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by valdemaras on 2009-02-17
OKay, I'll do it as soon as I'll get home.

---

### Post by valdemaras on 2009-02-17
Now that I think of it, yesterday my friend helped me to get to fix it a bit. I loaded LiveCD and executed this line:
```
sudo lilo -M /dev/sda mbr
```

And I was able to boot my Vista again, not Linux though. I remembered a few minutes ago that then Vista crashed when I tried to boot it first time, it had a window called "RECDATA" or something along these lines, which had a big ERROR sign in it. Vista did crash at that moment.
What I'm going to do now, is install Ubuntu again, fix menu.lst file for GRUB and see what happens. If something, I'll report back here.

---

### Post by valdemaras on 2009-02-17
Thanks a lot **caljohnsmith**, you put me and my friend on tracks so we managed to pull this thing of. It was two options to load Windows in GRUB, sda1 and sda2, first one being the recovery partition, second - real Vista one. I opened /boot/grub/menu.lst file (sudo gedit menu.lst) and just erased the part about sda1. And it worked. ^_^

Thanks again, and *a&#269;i&#363;, Donatai*. :-)

---

### Post by caljohnsmith on 2009-02-17
I'm really glad to hear you figured it out and it's all working OK now; cheers and enjoy Ubuntu and Vista. :)

---

