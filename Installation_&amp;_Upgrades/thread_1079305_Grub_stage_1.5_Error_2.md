---
title: "Grub stage 1.5 Error 2"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by mario s on 2009-02-24
Hi,

I´ve recently installed the ubuntu in my PC; no partitions for windows or anything, just the Ubuntu. The PC is a Celeron 1.6 with 1024Mb RAM.

One day I turned it on and a black screen appeared with the following message:

GRUB stage 1.5
error 2

and anything else happened. Not sure but it probably had something to do with an upgrade or some software I treid to install.

Then I downloaded the Ubuntu from the website, burnt a .iso copy and try to load it again; I get into the BIOS and changed the settings in order to try the CD first. A new installation happened then, but ever since, everytime I switch off the computer, the same screen appears with the same message:

GRUB stage 1.5
error 2

And the only way I´ve found to make it work is going through all the installation again.

Once Ubuntu is installed it works fine apart from the CD that don´t opens (I tried to install from an original disk: from canonical)

Can anyone help me to fix that GRUB thing?

I have downloaded a piece of software from here:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

and I´ve tried with the USB but I couldn´t manage to make it work...

Any (detailed) help will be appreciated.

Thank you in advance!

---

### Post by caljohnsmith on 2009-02-24
I'm confused by your description of the problem; when you reinstall Ubuntu from the Live CD, does it work right away, or do you immediately get a Grub error 2 when you try to boot the new install? If it does boot, when do you start getting the Grub error 2 again? I think it would help to get a clearer picture of your setup, so how about booting your Ubuntu Live CD, download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

