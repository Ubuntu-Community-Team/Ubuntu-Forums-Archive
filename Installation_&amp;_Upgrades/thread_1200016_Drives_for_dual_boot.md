---
title: "Drives for dual boot"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by Heldrex on 2009-06-29
[FONT=Times New Roman][SIZE=2]I'm sort of new to dual booting vista and linux. I've been looking around on the internet for the past day or two and have a few questions before I purchase some drives.

I have read about using something called a boot drive that is 10k RPM. My question is do I put both systems on this drive? Are there issues of physical size and shape that I have to look into to make sure it goes into my tower? (Shell of an dell XPS)

If I am able to get both operating systems booting from the same drive can I assign them to store data on separate drives?

If this setup works I will have 2x 500GB 7200RPM SATA 3.0Gb/s and 1x[/SIZE][/FONT][FONT=Times New Roman][SIZE=2][COLOR=black]150GB 10000 RPM 16MB Cache SATA 3.0Gb/s[/COLOR][/SIZE][/FONT]

---

### Post by pytheas22 on 2009-06-29
> do I put both systems on this drive?

You don't have to put both systems on this drive, but if you want both systems to benefit from the higher performance drive, then you would want them both to be on the "boot drive."
> 
Are there issues of physical size and shape that I have to look into to make sure it goes into my tower?

I doubt this will be a problem--as far as I know, all internal hard disks are the same size and shape and should fit into any standard computer case--but you should check the product information just to be safe, I suppose.
> 
If I am able to get both operating systems booting from the same drive can I assign them to store data on separate drives?

Yes.  On Ubuntu, you would probably want to put your / (root) partition on the boot drive, and put /home on one of the secondary drives.  With this configuration, your system files, including configuration files and application executables, would be stored on the boot drive for fast access, while the bulk of your data and personal files (pictures, video, etc.) would go on a second drive.

There are lots of other possible configurations for Ubuntu, but I think this one would make the most sense if your goal is to increase overall system performance.

On Windows you would end up with your C drive on the boot disk, and then another partition (E or F or whichever letter gets assigned to it) on the second disk.  On Windows, this configuration could be a little messier than it would be on Linux, but it's still possible to do.

Finally, with all this said, the boot drive isn't likely to revolutionize performance, so if it adds a lot of extra expense or complication to your project, you may want to rethink it.  It might make things a little faster, especially during bootup, but I doubt that 10000 RPM vs. 7200 RPM is going to make that much of an impact compared to all the other factors that affect performance.

And Ubuntu has been dumping a lot of resources lately into improving boot speed, with the goal of a 10-second boot within the next few releases.  So the amount of time you have to wait for Ubuntu to boot should become less and less of an issue.  Windows Vista may be different; I don't know.

---

### Post by Heldrex on 2009-06-29
Thanks for the informative reply. I think I will go with 2x 500GB hard drives if there won't be a significant increase in performance, the boot drives are expensive for making a small difference. I definitly need a second drive, I'll just skip a third.

---

