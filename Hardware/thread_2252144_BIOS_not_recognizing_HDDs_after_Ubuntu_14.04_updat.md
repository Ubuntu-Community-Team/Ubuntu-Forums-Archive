---
title: "BIOS not recognizing HDDs after Ubuntu 14.04 update"
date: 2014-11-09
forum: Hardware
---

### Post by Yamil_Tactuk on 2014-11-09
Hello,

I installed Ubuntu 14.04 in my laptop (Dell M1730) on my second HDD. I have an SSD where windows is at. everything was ok when I decided to update Ubuntu. I was watching some old videos from an external HDD when the update said that It was completed and I needed to restart the computer. So I tried to do that but Ubuntu froze and I had to force shutdown it. Then when I turned it on, for my surprise the BIOS said that it didn't find a bootable drive. Then I tried to boot with the live USB I have, the BIOS detected it fine and I booted to live Ubuntu and my HDDs and my SSD where there with all it's content and the installation detected windows and Ubuntu as normal.

I don't know what's the problem.
Just in case my laptop is 6 years old and maybe that Ubuntu converted the HDDs into UEFI when the BIOS only supports EFI. (Just guessing here)

Please help.

Thanks in advance.

---

### Post by weatherman2 on 2014-11-09
No, Ubuntu won't convert anything to UEFI - your 6 year old laptop most likely doesn't even have UEFI. In fact, even if you did have UEFI, "converting" to boot that way is not easy from a legacy installation.

Are you saying you have two separate hard drives, one with Windows one with Ubuntu, and your laptop can no longer boot from either one?  Using the F12 key to get a boot menu and choose?

I'd check the hard drive health - might as well check both.  Check S.M.A.R.T. Attributes using GSmartControl and see if any are highlighted in red or pink.  (An attributed that is simply labeled "pre-failure" is just a type of attribute, not an indication of failure.)  GSmartControl can be installed from a live Ubuntu session.  There's also a nice boot Linux disk called Parted Magic (still a free version on Major Geeks) that has GSmartControl built in - but it's an icon called "Disk Health."  You can also run S.M.A.R.T. tests from GSmartControl.  I'd run the short test on both of your drives, should take only a minute or so each, tops.  If they pass and no Attributes are highlighted pink for either drive, the drives are probably not failing.

If you can boot from Windows but not Ubuntu, you can try re-installing/repairing Grub from your live boot session.  Do a web search for "ubuntu grub chroot" - the "chroot" method has always worked well for me.

Sometimes your BIOS will "forget" boot drives in my experience.  Or you have USB drives plugged in and it is confused/trying to boot from them.  It may simply start working again - or you can try things like resetting the BIOS to default settings, pulling out your laptop battery (and power plug) and holding down the power button for 60 seconds, etc.  Double check boot priority in the BIOS, too, though I'm not sure why that would suddenly change just after an Ubuntu update.  Some sort of hardware failure is possible, too, unrelated to the Ubuntu update you did.

---

### Post by Yamil_Tactuk on 2014-11-09
Thanks a lot for your reply weatherman2. But I'm sure that the hard drives are ok because I remembered that when u but u froze it appeared like it was a live USB and I disconnected the USB. And I removed the drives and put them back on. Restared several times between reconnection and trying with only one drive. And when I use the live USB it has all the drives, reads all of them perfectly. 
So my question is if I format both drives and reinstall the OSs, is there a possibility that it will work again? I tried to reinstall ubuntu only but continued the same problem.
in the mean while I'll look on how the BIOS recognizes the drives and what could have change for it no to read them properly. 

Thanks a lot again Weatherman2

---

### Post by oldfred on 2014-11-09
Re-install is the brute force way to fix things. And sometimes that is the quickest and easiest way to fix major issues.

But we prefer to spend time & effort to fix things. :)

Post the link to the summary report, with multiple drives do not run autofix as that will install grub everywhere and you only want grub installed to MBR of Ubuntu drive.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Yamil_Tactuk on 2014-11-09
Thanks a lot oldfred for your reply.
I'll give this a shot.
I'll post the result as soon as possible.

---

### Post by Yamil_Tactuk on 2014-11-09
Well, couldn't boot from that image, my bios said that it didn't have a boot partition.
Then I downloaded Fedora, just to try and installed it on the ubuntu HDD. It is working now. but I really want to know what was the problem, why both of my drives lost their boot capability.
But thanks a lot for your support guys, really appreciated!

---

