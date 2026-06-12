---
title: "Help - Ubuntu not installing on new laptop"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by niceguy123 on 2009-01-05
I just bought a new laptop Sony VGN-FW250J/H with windows vista pre installed. I've been trying to install Ubuntu 8.10 from a new disk that I downloaded from the main site. I turn on the computer with the disk in and get the ubuntu screens up till choose install on live etc. I choose install, the screen shows the bar filling up or moving and then the screen goes dead and I hear no movement from the hard disk and then nothing changes. I've tried this a couple of time with the same no results. 

I then tried installing an old xbuntu disk that I used a while back when too I was not successful in installing ubuntu on a laptop. This time I got an hour of error messages. I'm not sure if the disk is still good. 

Help.

Does ubuntu have issues with laptops? Is there a better way to do this? 

Would it be easier to install linux and add on ubuntu. I have no idea how to do that. Can it be done? 

I would appreciate some advice. 

Thanks.

---

### Post by Zimmer on 2009-01-05
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

and

[http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Should set you on the path to enlightenment.

Basically, to dual boot Vista and Ubuntu you are required to:

Use Vista to shrink your Vista partition and create an extra partition to install Ubuntu on.

Install Ubuntu to the new partition and install GRUB to that partition , not the MBR.

Install EasyBCD on Vista and edit Easy BCD to tell it where Ubuntu is....

Read the articles at the links above very carefully.

Helpful reading also at 
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
and
[http://www.psychocats.net/](http://www.psychocats.net/)

---

### Post by Zimmer on 2009-01-05
OOPs! double post, due to time out...

---

### Post by niceguy123 on 2009-01-05
> **Zimmer said:**
> [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

and

[http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Should set you on the path to enlightenment.

Basically, to dual boot Vista and Ubuntu you are required to:

Use Vista to shrink your Vista partition and create an extra partition to install Ubuntu on.

Install Ubuntu to the new partition and install GRUB to that partition , not the MBR.
QUOTE]




Thank you,

I am following this recipe and got stuck at  > Install Ubuntu to the new partition and install GRUB to that partition , not the MBR.


How do I get Ubuntu into the new partition?

It goes right in to instalation and doesn't show this message:

[QUOTE]Ubuntu will then load the disk partitioner to determine where it's going to be installed. Choose "Manual - use the largest continuous free space". This will automatically select the unpartitioned space we created earlier using the Shrink tool. Click Forward.

Is this something new with 8.10? The how to you gave me is for 8.04

---

### Post by Zimmer on 2009-01-06
Ok, I have seen the new install sequence here,
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

is that what you are seeing? It appears a bit different from 8.04 ..

I assume (sorry, but no actual experience here) that the choice at 'Select a Disk' should be the dangerous, and possibly catastrophic, 'Manually edit partition table' and to create a new partition from the free space which you have created by Using Vista to shrink your Vista partition... (you know much about creating partitions?)
See Step 3 here 
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Again, this assumes that 8.10 partitioning at install will behave in the same way as 8.04. 

If I were you I would search further for 8.10 Vista dual booting before trying again. And make sure you have the means to restore your Vista and any vital data in case of problems.

If you are unsure about partitioning, then maybe you would prefer to try the WUBI route to Ubuntu..  Not tried it myself, but it would appear to be a mostly risk free experience...

---

### Post by niceguy123 on 2009-01-06
> **Zimmer said:**
> Ok, I have seen the new install sequence here,
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

is that what you are seeing? It appears a bit different from 8.04 ..


At this point I don't think that its an 8.10 issue. I've tried older ubuntu disks that I have around. This is after shrinking the disk via vista as explained in the link you showed. 

In all of the Ubuntu installation I am getting a blank or unclear screen after choosing English as language.

I have not been able to reach the stage where I have the option to choose the partition. 

If this keeps up I will most likely just format the disk and can the vista all together. I am trying to avoid that because I paid for the license with the laptop and have had a couple of programs or website that require windows since I have migrated to Ubuntu. I wouldn't want to be stuck the other way around with vista and no Ubuntu. 

This laptop is going to be my main work station for the near future.

---

