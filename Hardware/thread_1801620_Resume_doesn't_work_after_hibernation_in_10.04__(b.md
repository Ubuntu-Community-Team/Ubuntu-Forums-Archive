---
title: "Resume doesn't work after hibernation in 10.04  (but does w/suspend)"
date: 2011-07-10
forum: Hardware
---

### Post by mike-g2 on 2011-07-10
Hi,

I've got a ThinkPad X201 tablet that's running 10.04.  Everything works fine except resuming after hibernation.  I've tried the 'standard' hibernation via the menus and issuing s2disk from the command line.  Either way, the machine simply reboots.  Note it restarts from suspend to RAM without a hitch.

I've seen lots of discussion about hibernation issues, but they don't seem to address this issue. Does anyone have any suggestions on where to start diagnosing and/or solving this problem?

Mike

---

### Post by lmarmisa on 2011-07-10
I suppose the size of the swap partition will be correct. Your swap partition should be at least as big as your RAM size.

---

### Post by mike-g2 on 2011-07-10
Hi lmarmisa, 

Thanks for the reply. You suppose correctly
[INDENT]RAM = 8GB
SWAP = 19GB[/INDENT]

Mike

---

### Post by mike-g2 on 2011-07-15
Anyone have any suggestions?  I suspect that I may be able to solve this by setting the boot parameters correctly, but that's just a guess.

---

### Post by Toz on 2011-07-15
According to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577916]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577916"), make sure that the UUID of your swap partition matches the value in **/etc/initramfs-tools/conf.d/resume**. I don't have a 10.04 install to check, but in 11.04, that file doesn't exist (for me at least)

---

### Post by mike-g2 on 2011-07-17
Thanks for the suggestion.  I do have that file already in my system and the UUID matches the swap partition, so that's not the problem.  

I'm wondering if there's anything I should be looking for in /var/log/messages or using dmesg that might provide some insight.

---

### Post by Toz on 2011-07-17
Is your $HOME encrypted? (you would have choosen it during setup). Mine is and I can't hibernate because of that. See: [https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume#Failure_due_to_encrypted_swap]("https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume#Failure_due_to_encrypted_swap")

---

### Post by mike-g2 on 2011-07-18
Thanks for the link!  It seems useful. 

When I did the install I had my home encrypted but had some issues so I unencrypted it and removed the relevant libraries. But perhaps that's the root of the problem.   Will try to trouble shoot based on the info in the debug link.

Thanks!

---

### Post by Toz on 2011-07-18
Sorry, I wasn't totally accurate with my previous statement. Allow me to clarify. It is the encryption of the swap partition that causes the problems. The hibernation image is written to an encrypted swap partition and unfortunately, during the resume, the system cannot access the encrypted partition and the system reboots. In ubuntu, when you choose to enrypt your home parition/directory during setup, by default it also encrypts the swap partition.

---

### Post by mike-g2 on 2011-07-19
Thanks for the clarification. I don't believe that my swap is encrypted but I'm not sure how to determine this with 100% certainty.  

Here's my /etc/fstab entry for my swap
> UUID=98b...faf      none    swap    sw      0       0

Does this have the required info?

---

### Post by Toz on 2011-07-20
What does:
```
dmesg | grep swap
```return?

---

### Post by mike-g2 on 2011-07-23
I get
```
[    21.364899] Adding 18980756k swap on /dev/sda6.   Priority:-1 extents:1 across: 18980756k
```

---

### Post by Toz on 2011-07-23
No, your swap is not encrypted. Try another hibernate & resume. After it reboots, post back copies of **/var/log/pm-suspend.log** and **/var/log/dmesg.0** and the results of: ```
lspci -vnn
```Lets see if there's anything in there that helps.

EDIT: Another thing you could try is to remove the tpm module prior to hibernating to rule it out as a cause. Run a:
```
sudo modprobe -r tpm_tis
``` prior to hibernating.

---

### Post by mike-g2 on 2011-07-26
Hi Toz,

Thanks for your help with this.  

Removing the tpm module as you suggested had no effect.  I still could not resume from hibernate.  The system just rebooted.

I've attached copies of the files and output you've requested.  I see lots of 'success' notes and instances of failures when trying to activate the display in the lspci output. Pretty cryptic to me, overall.  I appreciate you taking a look.

Best, 

Mike

---

### Post by Toz on 2011-07-26
Maybe worth giving uswsusp a try.

1. Install the necessary packages:
```
sudo apt-get install hibernate uswsusp
```

2. Try the command:
```
sudo s2disk
```

If you get an error about the machine not being in a whitelist (or something like that), try the command:
```
sudo s2disk -f
```

---

### Post by mike-g2 on 2011-09-29
Hi Toz,

Excuse the long pause and thanks for the suggestions.

I had actually tried these options before posting here and they didn't help.

I have finally solved the problem which, like most solutions, is embarrassingly obvious in retrospect.  I modified my /etc/default/grub by adding "resume=UUID=89...." (where the UUID was for my swap partition) to the GRUB_CMDLINE_LINUX_DEFAULT option line.

I've tried it 3 times now and it seems to work fine. Yippie!

Thanks to everyone for their help and suggestions.

---

