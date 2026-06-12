---
title: "Fixing my reinstall"
date: 2008-08-27
forum: General Help
---

### Post by Sequences on 2008-08-27
So I happily reinstalled my Ubuntu to 8.04 this morning and things went quite well, no problems at all. when I tried to go back to my Windows XP I get an error involving ntoskrnl.exe in the windows/system32 folder. I wasn't too phased, so I went along and tried to fix the problem.

I booted up the Windows XP disk and copied ntoskrnl.ex_ from the disk to the location on the windows. alas it did not work. and after more poking around on the windows bootup, my GRUB was deleted, and now I can use neither my windows nor my Ubuntu. 

This has happened to me before, so I went along to try to reinstall the GRUB and it does not work, so it seems. I tried to do root (hd?,?) stuff and it all does not work. How do I get it to work now? 

Thanks

---

### Post by tuxxy on 2008-08-27
Heres how to reinstall GRUB

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by Elfy on 2008-08-27
If reinstalling grub from the livecd isn't working - what errors do you actually get?

---

### Post by Sequences on 2008-08-27
> **forestpixie said:**
> If reinstalling grub from the livecd isn't working - what errors do you actually get?

Everything went smoothly, no errors at all. But GRUB was not installed because right after i rebooted the system, it went back to the Windows boot and the GRUB that was supposed to have been just installed did not appear anywhere.

---

### Post by Elfy on 2008-08-27
Maybe download and use supergrub to reinstall it; it's worth having as a tool anyway.

[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

---

### Post by Sequences on 2008-08-27
Well, I got tired of trying everything else, and just reinstalled Ubuntu (it was a fresh install anyways). but the problem with the windows XP boot still persists. any idea how to fix it?

---

### Post by Elfy on 2008-08-28
About the only thing I could say is did you expand the ntoskrnl.ex_ file after you copied it. But I've no idea of why you get a ntoskrnl.ex_ problem.

---

