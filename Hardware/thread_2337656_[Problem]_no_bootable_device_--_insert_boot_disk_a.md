---
title: "[Problem] no bootable device -- insert boot disk and press any key"
date: 2016-09-20
forum: Hardware
---

### Post by zasypiam on 2016-09-20
Hello Guys,

I have problem with my laptop. I used it and I had a problem with start LibreOffice (it doesn't start). Then I decided to restart Ubuntu.
After restart i showed only black screen with Lenovo logo and after that some lines of text ended "No bootable device -- insert boot disk and press any key".
I run my computer from live cd but it looks like that gparted doesnt see my hybrid hdd disc.
Should I send my computer to warranty service or could I make something with it by myself?
Under photo from gparted and df -h (and and of fdisk -l).
Thank You for any information.
[http://s17.postimg.org/vah5kiyzz/Screenshot_from_2016_09_20_11_55_34_1.png](http://s17.postimg.org/vah5kiyzz/Screenshot_from_2016_09_20_11_55_34_1.png)

---

### Post by oldfred on 2016-09-20
You are only showing /dev/sr0, which is mounted as the cdrom.
And it looks like that is all that is shown.

Does gparted in upper right corner show another drive?
Does going into BIOS/UEFI show a hard drive?

---

