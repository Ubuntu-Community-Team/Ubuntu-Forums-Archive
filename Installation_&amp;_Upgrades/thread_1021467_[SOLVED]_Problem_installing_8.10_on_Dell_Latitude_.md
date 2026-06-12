---
title: "[SOLVED] Problem installing 8.10 on Dell Latitude E4300"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by Monroc on 2008-12-25
Hello.

I am trying to set up a dual boot environment with Windows XP and Ubuntu on my new laptop - a Dell Latitude E4300. The Windows XP installation was a breeze. I expected the Ubuntu-installation to be just as easy, but I must admit it up until now has failed.

I have done this kind of setup on other laptops, but I am in no way experienced in Linux.

When I boot from the CD I can get into the initial screen, but when I move on from there (regardless of what I choose), the installation goes into a loop spitting out this block of messages over and over until it finally hangs:

[129.068626] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current]
[129.068759] sr 1:0:0:0: [sr0] Add. Sense: Timout on logical unit
[129.068864] end_request: I/O error, dev sr0, sector 1431184
[129.068911] Buffer I/O error on device sr0, logical block 178898
[129.577685] sr 1:0:0:0: [sr0] Result: hostbyte: DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

The numbers in bracets alterate between the blocks of messages, but the sector- and block-numbers do not. Furthermore the last one of the messages does not occur when the system hangs.

Hardware-problems are ruled out. It is a completely new laptop, and Windows installs fine (After I changed the interface to the HDD in the BIOS from IRRT to ATA).

I managed to get into Linux on the very first try despite the huge amount of errors, and listed out what sr0 was with lshw. It seems it is the CD/DVD-Burner.

From what I can google, it is an unresolvable problem regarding the kernel which 8.10 (2.6.27?) is built upon. I would however like to get some confirmation on this as I would really like to stick with Ubuntu.

In my persuit to solve the problem I have tried a lot of different boot-parameters, but to no avail. Install fails with the previously mentioned error regardless.

---

### Post by lemming465 on 2008-12-27
Does the CD pass the self-test?  Does it work on other computers?  You might try burning another copy, maybe on different color media, maybe at a slower speed.  The error messages look like it's having trouble reading that CD.

---

### Post by Monroc on 2008-12-28
> **lemming465 said:**
> Does the CD pass the self-test?  Does it work on other computers?  You might try burning another copy, maybe on different color media, maybe at a slower speed.  The error messages look like it's having trouble reading that CD.

Thank you for replying.

I figured it was reading the CD it had trouble with, but the strange thing is that the CD should work. I've redownloaded the ISO, despite the old ISO had the correct MD5-hash. I've burned like 6 CD's at 1x speed - same error. I have - however - not tried installing Ubuntu on another computer. Might try that out to verify the CD/DVD-drive is working. It should be though. Works perfectly under Windows...

Would it perhaps help trying with the Alternate CD? I've seen other people resorting to this, but nobody reported any success with it...

---

### Post by Coder543 on 2008-12-28
Try the alternate cd if the other is not working. However, *have you done the self-check on the cd*? (as was suggested earlier)

---

### Post by Monroc on 2008-12-28
> **Coder543 said:**
> Try the alternate cd if the other is not working. However, *have you done the self-check on the cd*? (as was suggested earlier)

My appologies for not touching that matter. I have tried, yes. But it fails with a black screen. I suspect it is the same error as mentioned before, as the error only shows up when i remove **splash** and **quiet** from the boot-options, which I suppose is not possible to turn off during self-test?

---

### Post by lemming465 on 2008-12-28
Can you try any different versions with different kernels, such as 8.04.1 or 9.04-alpha2?

---

### Post by Monroc on 2008-12-31
I have tried the Alternate CD, and it fails with the same error. Furthermore both CD's fail in my girlfriends laptop (Dell XPS M1530) as well. I doubt it is my CD-burder which is faulty, as I had enabled "Verify Data", and it evaluated the CD's with success.

I will try with the 8.04 image. If that fails too, I will give up on Ubuntu and move on to another distribution :/

---

### Post by lemming465 on 2008-12-31
If CD media are failing on multiple computers, you really ought to see whether or not they pass the "Check CD for defects" test boot.  Those of us on the sidelines are betting the answer is no, which tends to indicate some kind of hardware problem related to either burning or download, even if windows appears to run OK.  It would be a good idea to try the "Test memory" / memtest86+ boot for at least 20 minutes on the computer you are using to burn the CD's, for example.

If you give up on Ubuntu, my personal next choice to try would be Fedora, but obviously there are hundreds of other possibilities.

Good luck with it!

---

### Post by Monroc on 2009-01-02
> **lemming465 said:**
> If CD media are failing on multiple computers, you really ought to see whether or not they pass the "Check CD for defects" test boot.  Those of us on the sidelines are betting the answer is no, which tends to indicate some kind of hardware problem related to either burning or download, even if windows appears to run OK.  It would be a good idea to try the "Test memory" / memtest86+ boot for at least 20 minutes on the computer you are using to burn the CD's, for example.

If you give up on Ubuntu, my personal next choice to try would be Fedora, but obviously there are hundreds of other possibilities.

Good luck with it!

I've had the computer run memory tests for a bit over 20 hours now - no errors, 22 passes. Memory defect ruled out.

One of my friends asked me to try using the DVD instead. I'm trying to get the DVD-image over to another computer with a CD-burner as of now, but packing it takes ages (Packing I must do, as the external HDD is formatted with FAT32 - stupid 4GB filesize-limit!).


I will let you know how it works out :)

---

### Post by Monroc on 2009-01-02
The DVD did the trick. No errors and Ubuntu is installing now...

Perhaps someone needs to take a look for flaws in the ISO's for the CD's...

To all of you: Thanks for your help - it helped narrowing down the problem.

Happy ubuntuing :)

---

### Post by avilella on 2009-01-25
Hi,

I took the liberty of creating a launchpad team for the people who own or develop for the Dell Latitude E4200/E4300 laptops, so that we can have more visibility upstream when having to ask for patches or support.

[https://launchpad.net/~e4200-e4300](https://launchpad.net/~e4200-e4300)

I'll be sending a couple of messages to ubuntuforums and notebookreview forums to gather the ~15 users I've identified so far.

Cheers,

Albert.


> **Monroc said:**
> Hello.

I am trying to set up a dual boot environment with Windows XP and Ubuntu on my new laptop - a Dell Latitude E4300. The Windows XP installation was a breeze. I expected the Ubuntu-installation to be just as easy, but I must admit it up until now has failed.

I have done this kind of setup on other laptops, but I am in no way experienced in Linux.

When I boot from the CD I can get into the initial screen, but when I move on from there (regardless of what I choose), the installation goes into a loop spitting out this block of messages over and over until it finally hangs:

[129.068626] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current]
[129.068759] sr 1:0:0:0: [sr0] Add. Sense: Timout on logical unit
[129.068864] end_request: I/O error, dev sr0, sector 1431184
[129.068911] Buffer I/O error on device sr0, logical block 178898
[129.577685] sr 1:0:0:0: [sr0] Result: hostbyte: DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

The numbers in bracets alterate between the blocks of messages, but the sector- and block-numbers do not. Furthermore the last one of the messages does not occur when the system hangs.

Hardware-problems are ruled out. It is a completely new laptop, and Windows installs fine (After I changed the interface to the HDD in the BIOS from IRRT to ATA).

I managed to get into Linux on the very first try despite the huge amount of errors, and listed out what sr0 was with lshw. It seems it is the CD/DVD-Burner.

From what I can google, it is an unresolvable problem regarding the kernel which 8.10 (2.6.27?) is built upon. I would however like to get some confirmation on this as I would really like to stick with Ubuntu.

In my persuit to solve the problem I have tried a lot of different boot-parameters, but to no avail. Install fails with the previously mentioned error regardless.

---

### Post by Nanday on 2009-02-20
Does everything work out-of-the-box? I'm considering getting this exact laptop (looks great, and nice spec'd), but people on Dell's chat can't assure that K/Ubuntu will work nice with everything...

---

### Post by vigyani on 2009-03-08
Hi

I am planning to buy Dell E4300N that is with FreeDOS (no MS Windows) and plan to install Ubuntu 8.04 or 8.10.

Please share your experience. How does it work under Ubuntu.

thanks
Vig

---

### Post by bigbri9 on 2009-04-14
I also have the E4300, and I just installed the 9.04 beta to dual boot with Vista Business and it was cakework.  Everything critical works out of the box.  I ordered a refurb model with the 128 GB SSD and once I get past grub, it boots in under twenty seconds.  I love it so far.

---

