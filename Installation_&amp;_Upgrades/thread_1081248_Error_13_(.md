---
title: "Error 13 :("
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by beedub- on 2009-02-26
Hey guys, I thought I would try ubuntu 3 days ago, but I cannot get grub to work right.  My windows install is Windows XP x64 Professional Edition on fakeRAID 0, and a seperate 80gb drive.  I have both grub and ubuntu on this seperate 80gb drive, which is my primary drive in my BIOS.  I have the RAID array set to second, and it is completely untouched but won't boot.  I have read that grub doesn't like fakeRAID, so I was wondering if you guys had any idea what I should do to fix this.  If you have any additional questions just ask, thanks.

---

### Post by caljohnsmith on 2009-02-26
In order to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to boot Windows from the RAID array.

---

