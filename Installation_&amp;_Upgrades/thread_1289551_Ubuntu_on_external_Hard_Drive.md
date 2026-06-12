---
title: "Ubuntu on external Hard Drive"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by Pacotaco90 on 2009-10-12
I recently bought an external hard drive for my laptop and decided to install ubuntu on it. My laptop has windows vista 64-bit pre-installed on it, and that is what I primarily use. The problem I'm having is that i have to take my external hard drive every where I go now, because even if i just want to boot into windows it gives me an error until I plug in my external HD. Is there a way around this so that when I want to run Ubuntu I can just plug in my HD and when I just want to run windows I can leave the HD at home?

---

### Post by louieb on 2009-10-12
The Ubuntu install by default will put its boot loader (GRUB) in the MBR of boot drive. 

1st) to get your laptop boot Vista on its own again get the [Vista Recovery Disc — NeoSmart]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") . You need to put Vista's boot loader back in the MBR Instructions are on the site. 

2nd) to get Ubuntu your pc needs to be able to boot from the USB drive. and GRUB needs to be installed in the MBR of the USB drive.  [Super Grub Disk]("http://linux.softpedia.com/progDownload/Super-Grub-Disk-Download-8071.html") can do it + it can boot your usb Ubuntu install too.

---

### Post by Pacotaco90 on 2009-10-12
Ok, I tried using the windows rrecovery cd that came with my computer and when I went in to repair boot, it told me that it found no problems. I tried this multiple time with and with out my External HD with Ubuntu plugged in. Any other ideas?

---

### Post by louieb on 2009-10-13
Thats a problem with the recovery disk that come with some computers - download, burn and boot the disk in the link.

---

### Post by Pacotaco90 on 2009-10-15
OK I downloaded the 64-bit (I have a 64 bit OS) version of the recovery disk and burnt the ISO to a disk and when I booted from the disk and clicked repair, i got the same message saying that nothing was wrong. So I then tried to download the regular version (X86) and it told me that I had an incompatible version of windows ( I figured that would happen but figured at least i should try) sorry to be a pain, but do you have any other suggestions or do you see anything else that I'm not doing right?

---

### Post by louieb on 2009-10-15
Though I'd seen the instructions for using the disk on the NeoSmart site. But I guess not. 
Anyway After booting to the CD, get to the Recovery Console (it differs for each recovery program, but generally is easily enough found). Once there type  
```

bootrec /fixmbr

```Probably not needed but may also may have to run 
```

bootrec /fixboot 

``` which will restore the Vista bootloader.

More here : [Restore XP,Vista or GRUB Bootloader]("http://ubuntuforums.org/showthread.php?t=740221")

---

### Post by Pacotaco90 on 2009-10-21
Ok, I finally got around to trying that and it worked beautifully, that you for all the time and effort you put into helping me.

---

