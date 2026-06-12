---
title: "Installing Ubuntu and windows: 7 and vista, configuring grub"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by enduser000 on 2009-03-13
Hello,
     So I have a friend that just installed ubuntu on his gateway.  He also installed windows vista and windows 7.  He wants to install grub and be able to boot into all three at will.  So he booted to a livecd (windows vista, windows 7, and ubuntu installed) and installed grub.  It made an entry for vista, but not 7.

     I think that the problem is when vista was installed over 7 it overwrote the MBR, then when grub was being installed, it looked at the MBR and decided to make an entry for vista, but not for 7.

     If anyone has any ideas we'll give em a shot, as we both are all out.

enduser

---

### Post by meierfra. on 2009-03-13
> I think that the problem is when vista was installed over 7  it overwrote the MBR,

Overwriting the MBR wouldn't be much of a problem. But Vista probably did not detect Win 7 and overwrote the Win 7 boot files. 

Give this  tutorial a try:

[http://ubuntuforums.org/showthread.php?t=813628#4](http://ubuntuforums.org/showthread.php?t=813628#4)

**If you need additional help:**

Boot from into  Ubuntu and download the Boot Info Script to the Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by enduser000 on 2009-03-14
Ok,
    I guess he tried to boot into vista and windows created two entries in it's MBR and he says it sort of looks like grub, so now it works.  Thanks for your help,

enduser000

---

### Post by meierfra. on 2009-03-14
> I guess he tried to boot into vista and windows created two entries in it's MBR 

That's the normal behavior. So Vista's did recognize Win 7 and added it to it's boot loader.  If he doesn't  want to go through two boot menus, he can use the  tutorial I linked in my last post. Or he can use EasyBCD to add Ubuntu to the Vista bootloader:

[http://neosmart.net/dl.php?id=1]("http://neosmart.net/dl.php?id=1")
[http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://neosmart.net/wiki/display/EBCD/Ubuntu")

---

### Post by enduser000 on 2009-03-16
Thank you.
I will point him to this post and we'll probably end up giving it a shot, I'll let you know if we do,

enduser

---

