---
title: "hd0 read error"
date: 2011-05-27
forum: Hardware
---

### Post by jamgood96 on 2011-05-27
I just built a computer to run as a small server in my living room. All has been going well, but I restarted it today and it gives me "error: hd0 read error.". It then puts me at the command prompt "grub rescue>" Obviously, something is messed up.

I checked settings in the BIOS to make sure nothing was funky, and also tried booting off an Ubuntu CD, but it just sat there for 10 minutes. I turned off the computer, played around a bit more, and now it won't even recognize a USB keyboard, so it's basically dead in the water.

All of the components were brand new, so it's hard to believe it's a hardware failure. Where do I go from here? This sucks...

Thanks,

James

---

### Post by Rubi1200 on 2011-05-28
Hi and welcome to the forums :-)

The next time you boot and get to the grub> prompt type ls and let us know what output you get please.

---

### Post by jamgood96 on 2011-05-28
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

The next time you boot and get to the grub> prompt type ls and let us know what output you get please.

It wont recognize a keyboard anymore. It did initially, but now, nothing :-( 

I've tried different usb ports as well as a different keyboard.

---

### Post by Rubi1200 on 2011-05-28
Try running either Slax, GParted Live, or Knoppix as LiveCDs and see if you can get the machine booted.

---

### Post by jamgood96 on 2011-05-28
> **Rubi1200 said:**
> Try running either Slax, GParted Live, or Knoppix as LiveCDs and see if you can get the machine booted.

How do I get I to boot from a CD without a keyboard?

---

### Post by Rubi1200 on 2011-05-28
If I understand the original problem, the first issue you encountered after discovering the problem was being unable to boot the machine with an Ubuntu CD correct?

I am suggesting trying some other LiveCD and see if the problem persists. I have seen people able to boot a machine which had similar issues simply by using another distro.

Also, when you say you > played around a bit more before the keyboard issue, what exactly did you do?

---

### Post by jamgood96 on 2011-05-28
> **Rubi1200 said:**
> If I understand the original problem, the first issue you encountered after discovering the problem was being unable to boot the machine with an Ubuntu CD correct?

I am suggesting trying some other LiveCD and see if the problem persists. I have seen people able to boot a machine which had similar issues simply by using another distro.

Also, when you say you  before the keyboard issue, what exactly did you do?

When this first happened and I booted up off the ubuntu cd the keyboard was working. After booting off the cd and having it sit there for 10 minutes I restarted the computer. The only playing I did was checking the BIOS settings and making sure things looked okay. I reset things to default settings.

I don't quite remember at what point I noticed the keyboard not working. Sometime after initially trying to boot off the cd. Now I cant hit f12 or del while booting, and it goes directly toward trying to boot from the ur, but fails.

---

### Post by jamgood96 on 2011-05-28
Okay, so I used a PS/2 adapter for my USB keyboard and now have a functioning keyboard again.

When I type 'ls' at the grub rescue prompt it prints the following:

(hd0) (hd0,msdos5) (hd0,msdos1)

---

### Post by Rubi1200 on 2011-05-28
Try and use the procedure here to boot:
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

If that doesn't work then you need to find a way to boot the machine and run the boot info script.

---

### Post by jamgood96 on 2011-05-28
> **Rubi1200 said:**
> Try and use the procedure here to boot:
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

If that doesn't work then you need to find a way to boot the machine and run the boot info script.

So, first off... stupid me turned of usb inside the bios, so that explains the keyboard issue. Used a ps2 adapter and got booted into the ubuntu disk. Disk utility showed bad sectors on the hd. Tried doing the smart disk scan and it failed. Running a badblocks scan currently. Should I mess with the link you posted after the scan is done?

If the ur has bad sectors, I should just return it, right? Its a week old.

---

### Post by Rubi1200 on 2011-05-28
> **jamgood96 said:**
> So, first off... stupid me turned of usb inside the bios, so that explains the keyboard issue. Used a ps2 adapter and got booted into the ubuntu disk. Disk utility showed bad sectors on the hd. Tried doing the smart disk scan and it failed. Running a badblocks scan currently. Should I mess with the link you posted after the scan is done?

If the ur has bad sectors, I should just return it, right? Its a week old.
If there are bad sectors, then this could explain the problems you first experienced. If the drive is under warranty, then for sure take it back and complain, get your money back, or get the drive replaced.

And to answer the question; no, I see little point attempting to boot if there are bad sectors or other failures going on.

---

### Post by jamgood96 on 2011-05-28
> **Rubi1200 said:**
> If there are bad sectors, then this could explain the problems you first experienced. If the drive is under warranty, then for sure take it back and complain, get your money back, or get the drive replaced.

And to answer the question; no, I see little point attempting to boot if there are bad sectors or other failures going on.

Thanks so much for your help! Ive already requested an email with newegg.

I did do quite a bit of tweaking things in the os, like ssh, lmsensors, etc. I assume its unlikely I could have done something to cause this issue? Anything I should do with the new drive before using it to ensure it is good?

---

