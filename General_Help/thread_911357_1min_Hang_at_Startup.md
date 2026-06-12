---
title: "1min Hang at Startup?"
date: 2008-09-05
forum: General Help
---

### Post by sandman3838 on 2008-09-05
Hello

I have a quick question here!
Is there some file or program that I can look into or install that would give me a better understanding of what's loading during the UBUNTU SPLASH SCREEN?

In the past UBUNTU 804 booted just fine but now during the Splash Screen while the BAR is moving back and forth it pauses for about a minute before continuing.  There are no errors, it's just dam aggravating!  Is there perhaps a file that shows what loads and how long it took for each item?  Anything?

Thanks for your help.

---

### Post by snowpine on 2008-09-05
> **sandman3838 said:**
> Hello

I have a quick question here!
Is there some file or program that I can look into or install that would give me a better understanding of what's loading during the UBUNTU SPLASH SCREEN?

In the past UBUNTU 804 booted just fine but now during the Splash Screen while the BAR is moving back and forth it pauses for about a minute before continuing.  There are no errors, it's just dam aggravating!  Is there perhaps a file that shows what loads and how long it took for each item?  Anything?

Thanks for your help.

Yes, there is an easy solution. When you boot up and get to Grub, press 'e' to edit your boot command. You'll see a longer line of code--it's usually the 2nd one down--that ends with 'quiet splash'. If you delete 'quiet splash' and then press Enter, then 'b' to boot, it will give you a "verbose" display instead of the splash screen.

Make a note of where the boot process is getting bogged down, then post back here!

---

### Post by sandman3838 on 2008-09-05
I'm back!  :)

I tried to do as you suggested but I was doing something wrong.  
Perhaps it was because my GRUB menu also holds WINXP?  I don't know?

However I did go into SYSTEM/ADMINISTRATION/STARTUP-MANAGER there I turned off the splash screen and I CHECKED "SHOW TEXT"!

I hope the results listed on the next reboot were what you were trying to archive?  The long pause is happening on LOADING HARDWARE DRIVERS.

Suggestions?

Thanks

---

