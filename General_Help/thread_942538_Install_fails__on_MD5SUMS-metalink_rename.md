---
title: "Install fails  on MD5SUMS-metalink rename"
date: 2008-10-09
forum: General Help
---

### Post by Whinging_pom on 2008-10-09
I am an absolute begineer with all things Ubuntu/Wubi and  would be grateful of any assistance you can provide. 

I have a fairly old PC that runs badly under XP. I've therefore decided to try Ubuntu on it. 

I've successfully downloaded to a CD and booted from this and Ubuntu runs fine, all hardware seems to work, no problems accessing the internet. 

I've therefore decided to take the next step and install it alongside Windows. However the installation is failing consistently and repeatedly at

"Rename c:\ubuntu\install\MD5SUM-metalink.gpg->c:\ubuntu\install\MD5SUM-metalink.asc"

with the error:

"The download was interrupted with the error:" 
([sic] - there is no further text - just an incomplete error message)"

I've tried installing to different disks,altering the size of the install, but nothing seems to make any difference.

Checking in c:\ubuntu\install shows that both files are present. Deleting them makes no difference.

Some details to assist:
[LIST]
[*]Ubuntu-8.04 i386
[*]Wubi 8.4.0.495
[*]c: drive 21GB free
[*]d: drive 37GB free
[*]Windows XP SP2
[*]Logiq P3 996MHz, 512MB of RAM
[*]Intel 82815 Graphics Controller
[*]LG CD ROM CRD-8522B
[*]Cable connection to internet via Dlink Airplus G DWL-G510 Wireless PCI card
[/LIST]

---

### Post by ago on 2008-10-09
There should be a log under your user temp folder (type %temp% in windows explorer). Also there should be another log in the /ubuntu folder. Please attach them here.

---

### Post by Whinging_pom on 2008-10-11
Can't find anything in my temp directory. This is what is in my ubuntu directory on c: and d: (I've tried to install to both locations)

Thanks

WP

---

### Post by ago on 2008-10-12
type %temp% in windows explorer

---

### Post by Whinging_pom on 2008-10-13
Ok found it now thanks. I've attached the file (had to zi[p it to get it to the max size) but the lines with an error read:

[I]gpgv: Signature made 10/11/08 15:19:11 W. Australia Standard Time using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
; ; ; 
      Parsing C:\ubuntu\install\MD5SUMS-metalink
Could not find any md5
The download was interrupted with the error:[/I]

---

### Post by ago on 2008-10-13
Why are you using Wubi 8.04 beta? You should use either Wubi 8.04.1 rev 506 (available on the website), or Wubi 8.10 rev 510.

---

### Post by Whinging_pom on 2008-10-13
Ah - never even noticed. It was the version I was directed to on the Bigpond (my ISP) downloads section (free for me to download) as the latest avaialble - it just says v8.04 no mention that it is beta. I'll try the versions you mention instead. I'll post a note on how I get on - if the other version works I'll drop Bigpond support an email asking them to update the download.

Thanks

WP

---

### Post by Whinging_pom on 2008-10-14
Okay, progress but still no joy.

Firstly, I couldn't get the installer to recognise the files from the CD or from a download directory. It insisted on downloading them again. Great. That said everything then went smoothly until...

When booting I choose Ubuntu  and get the error:

"Error 1: Filename must be either an absolute pathname or blocklist."

I haven't altered anything by hand - this is exactly how the installer set things up. 

Typing e gives

find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel Normal mode
initrd /ubuntu/install/boot/initrfigz
boot

I've attached the log file again.

Thanks

WP

---

### Post by Whinging_pom on 2008-10-14
Ok - I did abit of digging about what grub is and made a little progress. I can now get a partial boot with the following command sequence but then the computer hangs just after detecting all my drives etc. 

root (hd1,0)
kernel /ubuntu/install/boot/vmlinuz
initrd /ubuntu/install/boot/initrd.gz
boot

I've also tried the various modes - all give the same result. I.e. lots of detecting of drives, USB devices etc. then nothing.

Perversely it boots with no problems from the CD image - this message has been posted from ubuntu.

So far Ubuntu looks fine but my impressions of the installer are not great - I certainly don't have the confidence to try a full install even though I like the look of Ubuntu.

---

### Post by Whinging_pom on 2008-10-14
I left it overnight and the boot completed with an error. What I see on screen is:
[I]
[140.610569]sr0:scsi3-mmc drive:52x/52x cd/rw xm/form2 cdda tray
[140.610650]Uniform CD-ROM driver Revision 3.20
Done
check root=bootarg cat /proc/cmdline or missing module devices: cat /proc/modules ls /dev
ALERT! does not exist. Droppping to a shell!
BusyBox v1.1.3(Debian 1:1.1.3-5 ubuntu12)
Built in shell (ash)
Enter 'help' for a list of built in commands.
(initramfs)
[/I]

---

### Post by ago on 2008-10-15
> **Whinging_pom said:**
> Okay, progress but still no joy.

Firstly, I couldn't get the installer to recognise the files from the CD or from a download directory. It insisted on downloading them again. Great. That said everything then went smoothly until...

When booting I choose Ubuntu  and get the error:

"Error 1: Filename must be either an absolute pathname or blocklist."

I haven't altered anything by hand - this is exactly how the installer set things up. 

Typing e gives

find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel Normal mode
initrd /ubuntu/install/boot/initrfigz
boot

I've attached the log file again.

Thanks

WP

No that is not correct, uninstall remove also manually any c:\wubildr* or c:\menu.lst you might have around (in any drive) as well as old ISOs. Then reinstall again.

---

### Post by Whinging_pom on 2008-10-16
Many thanks for your help. However I've now given up on Ubuntu/Linux for now. I'll give it another look in a year or two since, when running from the CD, it looks interesting. 

I've retried the install eight times in various combinations and still haven't had a clean install. I've tried it coexisting with Windows, repartioned my disks and tried it as dual boot, blown Windows away and tried on a blank PC; in total I've now downloaded it 4 times.

I'm not by any means thick and understand something about computers (albeit not Linux). Heck, I spent 10+ successful years as a developer prior to moving into consultancy and PM. Simply put - it shouldn't be this difficult. Especially given the bootable CD works fine! If I had a piece of hardware that was unsupported I'd understand but it works a dream - it just won't install! 

If I can't get it working after spending my entire spare time over a week, then I'm sorry, it's not fit for purpose as an end-consumer product. In contrast I just reinstalled XP: it just worked; first time.

---

