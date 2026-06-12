---
title: "Secondary (non-OS) HDD recognition [n00b]"
date: 2009-04-05
forum: Hardware
---

### Post by cyberhood on 2009-04-05
Hello community-

I'm just starting my lengthy quest to expunge MS from my life so please keep in mind that my computer skills have been sufficiently truncated by Windows' over-emphasis on "user-friendliness" & that I have not had a computer class more advanced than keyboarding; so you're talking to a complete n00b who's been attempting to use Linux for a grand total of couple of weeks.

By just passively reading forums and Q&A's I've been able to get **Xubuntu** installed on my new computer without problems.  It is the one & only OS on this particular system & boots from a partitioned 4GB Compact Flash drive mounted in a **MSI Wind PC** (which is a desktop with laptop guts and a CF slot on the MB). Note: my system also includes a recognized SATA-mounted DVD burner.  

As I got a bit familiar with the Xubuntu GUI I decided it was time to make the move to a larger secondary HDD.  I chose a **Toshiba 2.5" (laptop) 500GB 5400rpm SATA** drive.  I picked it up bare (OEM) from the local computer store, opened the Wind PC case, plugged it into the remaining SATA wire & internal power source.  Turned on the computer, the HDD sounds & feels like it's running (quietly humming & slightly vibrating to the touch) yet I don't see it when I go into the File System.  
Using a Google search I found this: [http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/)
I typed "sudo fdisk" in the Terminal Window and I can see the CF and the DVD burner, but no Toshiba drive.
I restarted the computer and checked the BIOS and it's not recognized in there either. 

Sorry if this is a redundant question but I've been surfing the search engine of these forums for the past 3hrs to no avail.  Some have similar problems, but as soon as there's a difference with my problem the responses veer far away from the solution I need.

Other notes: This HDD has not been formatted by me, I assume it's been factory formatted but I have no idea what file system it's formatted as (assuming NTFS?).  Do I need to format it before it can be recognized?  If so, how would I go about doing that?  If not, what do I need to do to see this thing?

THANKS A BUNCH IN ADVANCE FOR ALL YOUR SUPPORT!

---

### Post by cariboo on 2009-04-05
OEM drives do not come preformatted. I would suggest installing gparted, then using it to partition and format your hard drive. Gparted can be installed using Add/Remove Programs or Synaptic Package Manager. Once you have installed it go TO System-->Administration-->Partition Editor, the rest is pretty obvious from there.

Jim

---

