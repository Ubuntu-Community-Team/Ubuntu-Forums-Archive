---
title: "Ubuntu Won't boot from Vista"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by kb7ypf on 2009-02-12
Hi All-

I just installed Ubuntu 8.04 on a 30B USB hard drive connected to my VISTA OS.  The install went well as did all the 300 plus updates.  When I restarted my computer the "loader" stop working and would not load anything (VISTA or Ubuntu.)  

I used the old fix MBR with the Vista Repair Disk to get the computer back working.  Now I can boot into Vista.  

How can I boot into Ubuntu?  I looked around the web and did not find any working solutions.  

Really need your help.  Thanks in advance.

---

### Post by caljohnsmith on 2009-02-12
How did you install Ubuntu to the USB drive? Did you do it from a Live CD, or did you use something like UNetBootin in Windows? If you have a Live CD you can boot for troubleshooting, how about doing that, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by kb7ypf on 2009-02-13
Thanks for our response.  

I finally had to load Ubuntu in Vista OS and it works well.

Dick

---

### Post by Taemojitsu on 2009-02-13
question/tangent for the more experienced. This is the second thread listing problems when Linux was installed onto a second HD, whether external or internal. So I'm wondering: can Stage 1 Grub point to a separate hard drive? Or do you need to install Grub on the HD that /boot is on?

---

### Post by caljohnsmith on 2009-02-13
> **Taemojitsu said:**
> question/tangent for the more experienced. This is the second thread listing problems when Linux was installed onto a second HD, whether external or internal. So I'm wondering: can Stage 1 Grub point to a separate hard drive? Or do you need to install Grub on the HD that /boot is on?
Yes, you can certainly install Grub to the MBR of a different HDD than where Grub's boot files are. The problem with doing that is the drive that Grub looks on for its boot files is hard-coded when Grub is installed to the MBR, so if your BIOS boot order is different than how the drives are ordered in Ubuntu (sda, sdb, sdc, etc.), then Grub will look on the wrong drive for its boot files and return an error. Also, your drives are dependent on each other for booting in that situation. Therefore, it is much more ideal if you can install Grub to the MBR of the same drive that has its boot files, and then simply boot that drive.

---

### Post by Taemojitsu on 2009-02-13
ic, ty.

i suppose it would probably make a good suggestion for the Ubuntu installer to default Grub to the disk it's on instead of always the first disk..? It might not load by default if BIOS boot priority isn't changed, but at least it wouldn't give errors.

---

