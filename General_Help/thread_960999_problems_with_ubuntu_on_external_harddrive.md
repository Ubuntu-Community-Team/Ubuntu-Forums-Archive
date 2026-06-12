---
title: "problems with ubuntu on external harddrive"
date: 2008-10-27
forum: General Help
---

### Post by moses73 on 2008-10-27
So I installed Ubuntu on an external harddrive with XP installed on my laptop. I can boot both Ubuntu and XP, but only with the harddrive plugged in. Is there a way to make XP run without the harddrive plugged in? I realize now that the boot is running from the external and that was a mistake, how do I remedy it?

---

### Post by dcstar on 2008-10-28
> **moses73 said:**
> So I installed Ubuntu on an external harddrive with XP installed on my laptop. I can boot both Ubuntu and XP, but only with the harddrive plugged in. Is there a way to make XP run without the harddrive plugged in? I realize now that the boot is running from the external and that was a mistake, how do I remedy it?

You need to restore the Windows boot partition on the internal drive, do a search for instructions on this.

You then need to reinstall Grub on the external drive, also search out these instructions.

Once both of those are done, you then need to get into your BIOS and set it to boot off the USB drive when it is plugged in, and boot the internal drive when the external is not plugged in.

---

### Post by Vindaumba on 2008-10-28
Hey dcstar, maybe you can please help me.
Basically wondering the benefits of running ubuntu off an external hard drive?

[http://ubuntuforums.org/showthread.php?p=6048380#post6048380](http://ubuntuforums.org/showthread.php?p=6048380#post6048380)

Thanks mate

---

### Post by caljohnsmith on 2008-10-28
Your problem is quite common; what happened is Grub was installed to the MBR (Master Boot Record) of your Windows drive so that you could boot into Grub on start up, but Grub's boot files are located on your external drive; thus you can't boot when you disconnect your external drive. 

So if you can set your BIOS to boot the external drive on start up instead of the internal drive, then you can install Grub to the MBR of the external drive and boot either Ubuntu or Windows from the Grub menu; also you can restore the Windows MBR to your internal drive so you can boot into Windows when your external drive is disconnected. 

If that sounds good to you, go ahead and boot into Ubuntu, and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Next open up your Grub's menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change the "#groot=(hdX,Y)" where X and Y are numbers to:
```
#groot=(hd0,Y)
```
At the end of the file, change your Windows entry (if you have one) to:
```
title	   Windows XP 
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Save the file, and run:
```
sudo update-grub
```
And let me know if you can boot the external drive OK. The last step would be to restore the Windows MBR to your Windows drive, which if you have a Windows Install CD, you can do by going to the "recovery console" and run:
```
fixmbr
```
Anyway, let me know how it goes. :)

---

### Post by timcredible on 2008-10-28
> **Vindaumba said:**
> 
Basically wondering the benefits of running ubuntu off an external hard drive?

lets you run ubuntu without touching the internal hard drive - useful when it's not your computer and you're not supposed to modify the computer.

---

### Post by Radioman991 on 2008-10-28
> **timcredible said:**
> lets you run ubuntu without touching the internal hard drive - useful when it's not your computer and you're not supposed to modify the computer.

+1

Especially when your company laptop is using an encrypted drive, and I don't want to think about resizing that partition.

For the OP benefit, when I did my install to my 100g LACIE, I removed the internal hard drive and did the install with only the USB connected.  This is easy on a Thinkpad T43p.....YMMV.  This way, Windows isn't touched, and with first boot being the USB, the Windows drive is not even recognized when the Ubuntu drive is plugged in...just the way I like it.

---

### Post by moses73 on 2008-10-29
Thanks Johnsmith, I put in the code to Ubuntu and I can still boot from the external. I still need to find a XP Pro live CD though, I'll let you know how it goes once I get that.

---

### Post by moses73 on 2008-10-29
and I got the MBR fixed, thanks again.

---

### Post by caljohnsmith on 2008-10-29
That's great news it's all working now, and you're certainly welcome. Cheers and have fun. :)

---

