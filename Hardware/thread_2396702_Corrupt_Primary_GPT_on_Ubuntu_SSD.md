---
title: "Corrupt Primary GPT on Ubuntu SSD"
date: 2018-07-19
forum: Hardware
---

### Post by Ronco Pizatto on 2018-07-19
Can anyone suggest software that might fix my Ubuntu desktop 120 GB SSD.

I ran boot repair and got info but no repair. (See link and line 127 of bott repair info)

[http://paste.ubuntu.com/p/74rmhzrrB8/](http://paste.ubuntu.com/p/74rmhzrrB8/)

217 The primary GPT table is corrupt, but the backup appears OK, so that will be used.

I don't know much about boot repair software. Are there commands or options that might help?

Any help is appreciated and I will supply any other info desired.

In addition to ubuntu, I also have ntfs data partition on this drive. All is backed up but I just want my ubuntu setup restored.

---

### Post by oldfred on 2018-07-19
Boot-Repair does not fix partition issues.

You need gdisk and perhaps a fsck.
lets see what this says:
sudo gdisk -l /dev/sda
I expect it to give same error, but offer to write updates to primary table if structure looks ok.
You may need to run this and then use the commands:
sudo gdisk /dev/sda
       GPT fdisk Tutorial 
[URL="http://www.rodsbooks.com/gdisk/walkthrough.html"]http://www.rodsbooks.com/gdisk/walkthrough.html
      [/URL]
 Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR. Details:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html) 
    [URL="http://www.rodsbooks.com/gdisk/walkthrough.html"]
[/URL]        
 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by Ronco Pizatto on 2018-07-19
I used sudo gdisk -l /dev/sda and did get a similar error message.

Then I used the w command with gdisk (not for the faint of heart) and wrote to the primary since my backup partition info was intact.

I ran boot-repair and found no more error. But system wouldn't boot yet.

I had to go to bios and set boot options to UEFI only instead of UEFI first and Legacy second.

Poof! All is back just like before.


THANK-YOU TONS AND TONS. You've done a really good thing here!:KS

---

