---
title: "Success on HP Pavilion dv4-2145dx"
date: 2010-06-15
forum: Hardware
---

### Post by j.v.matthews on 2010-06-15
In case anyone else wants to pick up the HP Pavilion dv4-2145dx laptop (which was just $500 recently at Best Buy), I can report that Ubuntu 10.04 LTS works just fine on it.

Moreover, you can triple-boot the system into the QuickWeb interface, into Ubuntu, or into Windows 7.

Here is what I did:
[LIST]
[*]Boot up laptop for the first time, do the initial setup provided by HP.
[*]Once you're into Windows 7 proper, do all security updates and HP updates.
[*]Run the recovery manager to make recovery discs. This took 4 DVD-R discs on my system. (Note: It appears the recovery disc creation doesn't know how to use RW media, but does understand DVD+R and DVD-R.)
[*]When you're done you should delete the recovery partition (through the recovery manager program).
[*]Reboot and install system from Ubuntu 10.04 LTS. When partitioning, you can shrink the Windows 7 partition (I reduced mine to 60GB, containing 30GB of data) and this leaves a nice big slot for Ubuntu. I had something like 280GB left over. Leave the Windows boot partition (/dev/sda1 probably) alone. Also leave the HP Tools partition.
[*]Once the system reboots, it will probably bring up QuickWeb (a little Linux distro used for email/web/music/photos). Skip that to get to grub.
[*]From grub you can boot Ubuntu or Windows 7 (using the first entry for Windows 7, which corresponds to /dev/sda1 where the Windows boot partition is).
[/LIST]

Sound, video, hotkeys, DVD burner, webcam all work. I have had one hard lock when waking from suspend -- this appears to be fireglx driver related, but unless it happens again I'll chalk it up to my tapping the wireless on button while the system was still waking up.

I used the tips in this post on HP's forums for help.
["This is how I installed Ubuntu on HP Mini dm1-1120ez while preserving the options of booting also HP QuickWeb and Windows 7."]("http://h30434.www3.hp.com/t5/Operating-systems-and-software/HP-mini-210-quickweb-install/td-p/212868#M38015")

---

### Post by v1nsai on 2010-08-23
To clarify, I ended up using the megaupload link [from this thread]("http://myhpmini.com/forum/viewtopic.php?f=70&t=4092") to get Quickweb running, none of the other sp-whatever.exe's worked.  Quickweb is some damn cool linuxy goodness, hope this helps anyone having problems.

---

