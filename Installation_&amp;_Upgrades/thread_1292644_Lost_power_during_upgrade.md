---
title: "Lost power during upgrade"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by jfwb on 2009-10-16
I tried to upgrade my system to 9.04.  All went well but after some hours of downloading and with just 15 minutes left of the installation process, I lost power!  Is there any way I can recover the situation - perhaps using a live boot dvd?

---

### Post by rob-ward on 2009-10-16
What is the current state of your install, does the computer boot? If not what does it do?

---

### Post by jfwb on 2009-10-16
> **rob-ward said:**
> What is the current state of your install, does the computer boot? If not what does it do?

I get the original boot menu but the system will not start in either regular or recovery mode.

---

### Post by prshah on 2009-10-16
> **jfwb said:**
> I get the original boot menu but the system will not start in either regular or recovery mode.

It should land up at the command prompt in recovery mode, otherwise there is something else wrong.  Once you reach the command prompt, you can follow [this post]("http://ubuntuforums.org/showthread.php?t=780531") for an easy solution.

Please post back with more details if you are unable to reach the command prompt in recovery mode.

---

### Post by jfwb on 2009-10-17
> **prshah said:**
> It should land up at the command prompt in recovery mode, otherwise there is something else wrong.  Once you reach the command prompt, you can follow [this post]("http://ubuntuforums.org/showthread.php?t=780531") for an easy solution.

Please post back with more details if you are unable to reach the command prompt in recovery mode.

When I select recovery mode, it quickly gets to a line saying
Begin:waiting for root file system
Then a fairly long wait ending with a few more lines on the screen then
(initramfs)
Then another lengthy wait and the screen goes blank although the machine is still runing.
Doesn't look good, does it?

---

### Post by prshah on 2009-10-17
> **jfwb said:**
> 
Then a fairly long wait ending with a few more lines on the screen then
(initramfs)
Doesn't look good, does it?

Ouch. No it doesn't. 

You can try a little risky solution; boot off a live CD, then run an fsck on your (unmounted) root partition. Post back if you want more details on how to do this.

Note that while it carries an element of risk, I don't think that you have much choice at this stage.

Even if the fsck completes successfully, you will still have to reboot to recovery console and use the "dpkg --configure -a" command as explained in the previously linked post.

---

### Post by jfwb on 2009-10-17
> **prshah said:**
> Ouch. No it doesn't. 

You can try a little risky solution; boot off a live CD, then run an fsck on your (unmounted) root partition. Post back if you want more details on how to do this.

Note that while it carries an element of risk, I don't think that you have much choice at this stage.

Even if the fsck completes successfully, you will still have to reboot to recovery console and use the "dpkg --configure -a" command as explained in the previously linked post.

Them "more details" would be very helpful. Thanks.

---

### Post by prshah on 2009-10-17
> **jfwb said:**
> Them "more details" would be very helpful.

Boot into the live CD, since you cannot use recovery console.

Open a terminal (Applications-Accessories-Terminal) and use the fdisk command to check which partition(s) are your linux partition.```
sudo fdisk -l
``` (Hint: Look for ID "83" and System "Linux"; others are not required, not even 82) Note the corresponding device entries (similar to /dev/sdx9).

By default, these partitions should not be mounted. However, when you run the fsck (filesystem checker) command, if you are alerted that the partition is mounted, DO NOT CONTINUE. Exit, and unmount with the command```
sudo umount /dev/sdx9
```

You can safely use the umount command even if the partition is not actually mounted, so you can issue the command just to be on the safe side.

Now comes the business part: to have the check run, issue the command```
sudo fsck -p /dev/sdx9
``` The "-p" (preen) will ask the filesystem to be fixed automatically. 

Sometimes, automatic fixing might fail with an error message stating that fsck should be run manually. In this case, and ONLY in this case, you can use```
sudo fsck -y /dev/sdx9
``` The "-y" tell fsck to agree to all suggested repairs, and continue automatically without the need for user interaction. [ObligatoryDisclaimer]This is a very dangerous and risky procedure and can potentially cause considerable file loss.[/ObligatoryDisclaimer] In actuality, I have used the "-y" switch quite a few times, without any data loss, but YMMV. I do not have enough knowledge of the file system to actually consider the best course for each repair action, so whenever asked by fsck "Fix? <y/n>" I just kept hitting "y". All "-y" does is bypass the question. 

If you feel you can better handle fsck interactively, then give the command```
sudo fsck -r /dev/sdx9
``` (or no switches), and you will be asked about every repair.

Don't forget to replace "/dev/sdx9" with the actual partition id as gained from the fdisk command. Run this command repeatedly (with reboot when asked) until no more errors are detected. Sometimes multiple fsck passes are required. Check all 83/Linux partitions. 

When you are finished, reboot without the live CD. Try recovery mode again; if it boots to a command prompt, you will still need to complete the interrupted upgrade with the "dpkg --configure -a" command (as per link in previous post). If recovery mode does not drop you at a command prompt, as a long shot, try the regular mode.

Please post back with results, errors, etc.

Note all activities at your own risk only. You could wait for some confirmation of the steps outlined here before you do anything, I will try mightily not to be offended.

---

### Post by jfwb on 2009-10-18
> **prshah said:**
> Boot into the live CD, since you cannot use recovery console.

Open a terminal (Applications-Accessories-Terminal) and use the fdisk command to check which partition(s) are your linux partition.```
sudo fdisk -l
``` (Hint: Look for ID "83" and System "Linux"; others are not required, not even 82) Note the corresponding device entries (similar to /dev/sdx9).

By default, these partitions should not be mounted. However, when you run the fsck (filesystem checker) command, if you are alerted that the partition is mounted, DO NOT CONTINUE. Exit, and unmount with the command```
sudo umount /dev/sdx9
```

You can safely use the umount command even if the partition is not actually mounted, so you can issue the command just to be on the safe side.

Now comes the business part: to have the check run, issue the command```
sudo fsck -p /dev/sdx9
``` The "-p" (preen) will ask the filesystem to be fixed automatically. 

Sometimes, automatic fixing might fail with an error message stating that fsck should be run manually. In this case, and ONLY in this case, you can use```
sudo fsck -y /dev/sdx9
``` The "-y" tell fsck to agree to all suggested repairs, and continue automatically without the need for user interaction. [ObligatoryDisclaimer]This is a very dangerous and risky procedure and can potentially cause considerable file loss.[/ObligatoryDisclaimer] In actuality, I have used the "-y" switch quite a few times, without any data loss, but YMMV. I do not have enough knowledge of the file system to actually consider the best course for each repair action, so whenever asked by fsck "Fix? <y/n>" I just kept hitting "y". All "-y" does is bypass the question. 

If you feel you can better handle fsck interactively, then give the command```
sudo fsck -r /dev/sdx9
``` (or no switches), and you will be asked about every repair.

Don't forget to replace "/dev/sdx9" with the actual partition id as gained from the fdisk command. Run this command repeatedly (with reboot when asked) until no more errors are detected. Sometimes multiple fsck passes are required. Check all 83/Linux partitions. 

When you are finished, reboot without the live CD. Try recovery mode again; if it boots to a command prompt, you will still need to complete the interrupted upgrade with the "dpkg --configure -a" command (as per link in previous post). If recovery mode does not drop you at a command prompt, as a long shot, try the regular mode.

Please post back with results, errors, etc.

Note all activities at your own risk only. You could wait for some confirmation of the steps outlined here before you do anything, I will try mightily not to be offended.

Thank you very much for your comprehensive suggestions.  Unfortunately I am no further forward. Fdisk found two 83/Linux partitions and after running fsck on these, both are now reported as clean.  Trying to boot in recovery mode produces the same result as before - no command prompt, just the same initramfs thing and eventually a blank screen.  I tried to boot in the regular mode - also the same as before.  I get a screen that advises me that 
[INDENT]Your session lasted less than 10 seconds. Try logging in with one of the failsafe sessions to see if you can fix this problem. Then View details (~/xsession-errors file).[/INDENT]
When I then press enter I get to a login page asking for user name and then to one requesting password.  The only user name and password I know have no effect and the system just hangs.
Thank you for your efforts but it looks like I will have to bite the bullet and just reinstall and start over. I have however enjoyed trying your various suggestions to try and fix the problem.
Regards,
John

---

