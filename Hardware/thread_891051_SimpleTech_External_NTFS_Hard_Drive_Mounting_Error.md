---
title: "SimpleTech External NTFS Hard Drive Mounting Error"
date: 2008-08-15
forum: Hardware
---

### Post by Zerim on 2008-08-15
Hi, I am completely new to Linux and such, and I would like to know why my external hard drive with a NTFS Filesystem isn't working. I have tried to get it to work by looking at other posts, but I still have errors.
I am a big newbie to Linux, so I would appreciate a step-by-step guide on how to get it to work.
I have Ubuntu, and the message i get is
> $LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sda1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2:If uoi don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g/dec/sda1/media/Clinton's Drive -o force  or add the option to the relevant row in the /etc/fstab file: dev/sda1/media/Clinton's Drive ntfs-3g force 0 0
It is a 232 GB hot swappable drive.
I do have Windows, but I still need a step-by-step guide.
I also hear that other people with NTFS drives get other error messages, and when I get to those I would love to just jump right over them, because from what I understand Linux doesn't write to NTFS drives, just reads them. Mine isn't doing either.
Thank you in advance!

---

### Post by Zerim on 2008-08-15
Please help me.....
I really need this hard drive.

---

### Post by 12growon on 2008-08-26
Just one quick suggestion if you haven't nailed this one already.  The reason for the error mounting is that the last time the drive was used, it was probably on a windblows box and was unplugged without clicking the "safely remove usb devices" button on the toolbar.  This has happened to me a couple of times, it can also happen when a windows box is cut off with the power switch instead of the correct shutdown. Your ubuntu O/S knows that windows wasn't "finished" with the drive and won't mount until whatever flag M/S uses is cleared. This gives my dual-boot machine fits when my son plays games in windows and the system freezes, he powers off with the switch, tries to boot back into linux and it throws a tantrum until I log back into windows and then shut down properly. 

Long explanation, but quick solution.  Plug the drive into a windows box, let it get recognized, and then either power windows down completely or just "safely remove" this time. Then, boot into your 'buntu box and plug the drive back in, it should auto-recognize.  I've had this same problem myself once or twice.  Let me know if this works for you, this is my first post, so....

P.S.- Ubuntu will read and write to NTFS with no problem, people use it all the time now on dual-boot systems and portable drives.

---

### Post by Amzer zo on 2008-08-27
I had the same issue on a brand new SimpleTech 320GB that I plugged into my system (Kubuntu 8.04).  It refused to mount with the same message Zerim (original poster) got.

I then plugged the usb drive to a WinXP machine, then selected "Safely remove...", plugged the disk back to the Kubuntu machine and it worked (it automatically auto-mounted with no problem).

---

### Post by SallyBlue on 2008-11-29
This worked for me, too.

I just bought a brand-new SimpleTech 500GB (re)drive and was dismayed to have that same ntfs error pop up.  All I had to do was plug it into a windows laptop, safely disconnect it, and it opened properly on my computer.

Thanks all!

---

### Post by zachthejones on 2008-11-29
I just bought the same as SallyBlue. I found after "safe disconnect" in Windows I also had to 'restart' the drive by unplugging it and then plugging it back in.

Also, interestingly enough, I've found that I cannot boot my desktop up with the drive turned on - it freezes on the initial BIOS boot screen. weird...

---

### Post by Ranger3698 on 2008-12-26
I just bought a Comstar 640GB USB drive and also had the exact same error. All I had to do was plug it into a windows box, safely disconnect it, I powered it down and moved it to my Ubuntu 8.10 box. After plugging it in and powering up, it worked fine. Thank you for a great fix!!!!

---

### Post by albinootje on 2008-12-26
> **Zerim said:**
> 
I also hear that other people with NTFS drives get other error messages, and when I get to those I would love to just jump right over them, because from what I understand Linux doesn't write to NTFS drives, just reads them. Mine isn't doing either.


Since a few years it is safe to read/write to NTFS partitions with Linux.
Before there was an experimental read-only driver included with Linux, and some projects in development to make read/write stable and safe.

You have at least 3 options, where 1 option was already mentioned here :
1) Use MS-Windows, connect the drive, and use "safely remove".
2) Use the "force" mount option which was already mentioned in the 
   error-message that you've quoted.
3) Install ntfsprogs, and use the tool called ntfsfix

Try option 1) first. Use the other options later when you've become more comfortable with playing around in Linux.

---

