---
title: "[SOLVED] sudo segmentation fault errors after today's updates"
date: 2008-11-27
forum: General Help
---

### Post by rshnike on 2008-11-27
Hey everyone.

I'm running ubuntu 8.10, newly installed maybe 2 weeks ago or so. Everything was working fine until earlier today when I got a notice for a couple of critical updates (which I installed). Now every time I try to run a sudo command I get segmentation fault errors. I've been trying to run gedit to fix my netatalk (which also broke when the updates were installed) but even when I try apt-get update I get an error. I can run the program as a regular user but then obviously I can't save the file.

Also, I can't open synaptic any more after the update either. It'll ask me for a password in the gksudo window then I'll enter it, it'll close, but nothing will happen. I don't know where the log would be as to what is happening but I can probably safely assume that there is a segmentation fault there too. Don't quite know what these are (this is my first linux install since I was a toddler...) but I'd appreciate it a lot if anyone had any advice.

I'm running the AMD 64 version of 8.10 as I've said.

Thanks a lot!

---

### Post by akudewan on 2008-11-28
Hi,

I was facing the same problem today. After you run a sudo command (and it fails), run this command: ```
tail /var/log/messages
```

If you see a like like *[ 89.789908] sudo[4669]: segfault at 0 ip b7b98adb sp bfce50f0 error 4 in pam_smbpass.so[b7b3c000+12a000]* then the problem is the same as mine.

There's a bug report filed [here]("https://bugs.launchpad.net/ubuntu/+bug/260687").

Here's what I did to fix my problem:
Reboot the PC and start it in Recovery mode.
Choose root terminal from the list that comes up.
Run "apt-get remove --purge libpam-smbpass"
Exit the terminal and continue with normal boot

After this, I noticed that my smbd was not running, and it wouldn't start. So I purged all the packages with 'samba' in it, and reinstalled them. Note that you'll lose all your shares and samba users if you do this, but that was not a problem for me.

Hope this helps

---

### Post by rshnike on 2008-11-28
That did it. Thanks a lot.

Figures, the one thing (samba that is) that I installed but didn't really need for lack of any windows computers heh, is the thing that randomly bugs. I probably wouldn't have found that bug report either seeing as everyone in that thread abbreviated to segfault (gotta learn the abbreviations...).


Thanks again!

---

### Post by sceptre0 on 2009-01-04
Thanks akudewan.  I was having the same problem with sudo and gtksu.  I ran the following commands in recovery mode and everything worked again.

```
apt-get remove --purge libpam-smbpass
apt-get remove --purge samba
```

---

### Post by brookie on 2009-08-25
Hello akudewan and everybody,

I know this is an old thread but I just spent the last few hours trying in vain to fix system running intrepid from an external usb hdd. 

apt-get and sudo commands all resulted in Segmentation fault. 

After trying virtually every apt-get fix in the forums, I ran across this and the samba purges above fixed my machine. I can now get updates again. 

Thanks so much. It was driving me nuts, I almost re-installed, and now it's time for a cold one. :)

Cheers, 
brook

---

### Post by yorgabr on 2009-10-05
Hi all!

I use Intrepid and also confirm the problem and the helpful solution Sceptre0 give us.

Thanks a lot! :)

---

