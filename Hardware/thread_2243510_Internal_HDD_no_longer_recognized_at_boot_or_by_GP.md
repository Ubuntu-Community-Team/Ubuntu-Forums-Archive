---
title: "Internal HDD no longer recognized at boot or by GParted, shows in BIOS &amp; Disk Utility"
date: 2014-09-09
forum: Hardware
---

### Post by IzziSixx on 2014-09-09
I apologize if this is long winded, I just really want to make sure I have all the info I can give! I've spent a few hours Googling and haven't found anything that's helped. I had Windows 7 and Ubuntu 12.04 that I upgraded to Studio by adding the extra files later dual booted on my only hard drive in my Toshiba Satellite C655-S5132, mainly using Ubuntu. I've had it this way since 12.04 came out. Yesterday I was on Ubuntu, just using Firefox for Facebook and whatnot, and left to go get something from another room. I came back shortly and my laptop froze and I think (I can't really remember) went black, so I turned it off using the power button. I took out the battery and unplugged everything and held the power button for a while before replacing the battery, as this has helped in the past when I had random little problems. When I went to turn it on again, it hung at the first Toshiba screen for longer than normal, and then went black with a flashing white underscore in the top left corner, then showed an error ultimately saying "No bootable device -- insert boot disk and press any key." I pressed a key, it tried again, and gave the same error. I tried restarting, still the same thing. The hard drive shows when I go into the BIOS Setup from the first screen, but doesn't recognize it as having anything bootable when I try to boot from it. I put in the Ubuntu 12.04 live disk I had laying around and it worked fine, it's what I'm using now to type this. The hard drive doesn't show on in the left panel of the Home folder and when I try to see it with GParted it says no devices found. I opened Disk Utility and it shows up here, but it says that all 250 GB are not partitioned. 

What I'm thinking is that for whatever reason my hard drive failed and erased all of my stuff, but I really want to know if there's a way to recover what I had on it. I didn't have anything 'important' on it exactly, just pictures, songs, and projects from when I was in recording school that I'd really hate to lose. Is there any way to get my stuff back, and do you think I can still use this hard drive to reinstall Ubuntu on, or is it totally dead? If there's any other info I can give to help, let me know and I'll do my best. Thank you in advance! :)

---

### Post by weatherman2 on 2014-09-09
Could be a failed hard drive.  Check the drive's S.M.A.R.T. status.  You can do this from the live boot - install "smartmontools" and run the "smartctl" command in the terminal:

```
sudo smartctl -a /dev/sda
```

You could also install GSmartControl in the live session - that's a graphical interface to smartmontools and easier to use.

In the Attributes (most of which are just status and not necessarily bad at all even if you see the world "failure" in the name), look for attributes with "sectors" in the name like "Pending Sector Count" and "Reallocated Sector Count."  Any raw values > 0?  Or just post the list of Attributes you find with smartctl.

You can even run tests with smartmontools (GSmartControl is easier).  Run the short test which should take only about two minutes.

If the drive itself hasn't failed or isn't failing, perhaps there is some other hardware problem - why did the laptop freeze? - and when you did the hard shutdown, you corrupted the drive's partition table or something.  Hard shutdown usually can be done without worry on Ubuntu but is still dangerous and should be done only as a last resort, of course.  

If the drive isn't bad, you could try using file and partition recovery tools like Testdisk.  If you grab the Parted Magic boot disk - find the last free download on MajorGeeks I believe - you can run GSmartControl ("Disk Health" I think they call it) directly and also a version of Testdisk, I think, to try to recover files.

---

### Post by IzziSixx on 2014-09-09
Thank you so much for your response!

I installed GSmartControl, and it says the SMART status is unsupported, and when I right click the drive the option to run tests isn't selectable. 
[IMG]http://i.imgur.com/8o0M4qp.png?1[/IMG]

I tried running the "smartctl" command in the terminal, and got this: 
[IMG]http://i.imgur.com/ferj5eg.png?1[/IMG]

I don't see any Attributes anywhere, but I'm guessing I didn't look in the right place or maybe it's something I don't know how to do?

Does this mean the drive has failed or is bad? Thank you again for your reply and trying to help me out, I really appreciate it!

Edit: I've found Parted Magic on MajorGeeks. If using this does end up being an option for me, would I have to have another drive to extract the recovered files to, or could I somehow swing it with just the one hard drive I have?

---

### Post by oldfred on 2014-09-09
If drive is bad, there is no way to copy backups to it. Backups should always be to another hard drive, flash drive or DVD(s) or as I do all of those.

Sometimes failure can be fixed with chkdsk in Windows for NTFS and fsck from Ubuntu live installer. But drive & partitions have to be seen to mount them to fix them. That gparted does not show them may not be the end of the world but that smartmonitor cannot even load is not a good sign.

Generally best not to power off with power switch except as last resort. And removing battery the way you did is often required to totally reset configuration if otherwise ok.

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[xhttp://kember.net/articles/reisub-the-gentle-linux-restart/](xhttp://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by weatherman2 on 2014-09-09
As the end of the output shows, the command failed.  As it suggests, try adding "-T permissive" to the command, so it might look like:

```
sudo smartctl -T permissive -a /dev/sda
```

However, I have never seen this kind of issue with an internal hard drive (often with USB/external drives though).  It looks a lot like a pretty bad failure - but do try the command above.  There may be other smartctl options you can try, but I've never needed them for an internal drive.

Parted Magic should have the same S.M.A.R.T. tools built in (albeit with different names sometimes).  It may be smart enough (sorry for the pun) to add some of these options automatically.

But I wouldn't be too hopeful about recovering data from this drive.  Hard drives do fail, sometimes without warning, sometimes catastrophically.  I've replaced lots of them.

---

### Post by Mark Phelps on 2014-09-09
The (possibly) good news is that the drive most likely did not actually "erase" anything but instead, corrupted the partition table(s) -- which looks the same to the OS.

You might be able to use Testdisk to recover Linux files.

I've found that Windows data recovery apps do a better job of recovering Windows files and folders.  But ... you would need to install them on a working Windows PC and be able to connect this drive to that PC.  You could start by using Recuva -- to see what it finds.  If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.  IF it finds the files and folders you want to recover, you'll have to go online and buy a license to do the actual data recovery.

Good Luck

---

### Post by IzziSixx on 2014-09-12
Well, I've tried just about everything I could here, and nothing worked. I think I may have done something to make it worse, because now my computer won't even boot from any live disk. Argh. Oh well. Thank you all for your help!

---

### Post by weatherman2 on 2014-09-12
If the drive was failing and has now completely failed, it may make the computer freeze when trying to boot from it, if the drive is now no longer responding.

You might try physically unplugging the drive and see if you can boot a live disk.  If you can - just replace the hard drive.

---

