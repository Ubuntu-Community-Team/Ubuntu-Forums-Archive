---
title: "Please please tell me now... Server or Desktop?"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by peiklk on 2009-02-13
Sorry for the Duran Duran reference.  :)

Anyway, I have a desktop machine running Windows XP that right now is only used for file storage, hosting our two printers, and occasional web browsing.  That's it.

So I used to use Slackware and Red Hat about 14 years ago and have been out of the loop lately.  I downloaded the Ubuntu server and desktop installations but right now am unsure which one to install.

All our other machines are Windows based (Vista) and I want to still be able to the linux machine for development (web server, ruby, etc.)... so they need to interact.

So...

Which should I install to be able to...

1. Web browse from the ubuntu machine.
2. Have print spooling functions (both printers have linux drivers -- an HP PhotoSmart B8850 and a Minolta QMS PagePro)
3. Support shared directories that my Vista machines can map to and view files.  Are they any NTFS restrictions on the current drives or will I need to reformat?

The machine is way overdue for a OS reinstall anyway, so I was hoping to make this switch to linux.

Like I said, I am leaning toward server but the lack of a GUI for browsing make me nervous (my wife sometimes will use that machine as will I when we're in that room)

Also, can a linux server be a domain server for my network (userid, logins, etc.)?

Any other things I haven't thought of?

THANKS SO MUCH!

Kevin

---

### Post by theozzlives on 2009-02-13
You can setup a file & print share from the desktop edition. There is no GUI in the server edition.

---

### Post by peiklk on 2009-02-13
> **theozzlives said:**
> You can setup a file & print share from the desktop edition. There is no GUI in the server edition.

ok, cool.  So mapping to shares to/from Vista machines is no problem?

Can apache or a web server run on the Desktop?

---

### Post by Taemojitsu on 2009-02-13
yes, they'll run on the desktop they just might not have the packages installed by default.

Ubuntu can read NTFS. If you have a bad shutdown of Windows tho, NTFS will need to do that check thing, and to mount it in Ubuntu you'll have to force mount with a command line.. command, unless you start windows again to check it.

Note: might want to specify a mount point for the windows partitions at Ubuntu install, but you probably already know this

BUT, Vista won't read ext3 unless you install the drivers, which I think is as simple as Google 'ext3 Vista'

---

### Post by peiklk on 2009-02-13
> **Taemojitsu said:**
> yes, they'll run on the desktop they just might not have the packages installed by default.

Ubuntu can read NTFS. If you have a bad shutdown of Windows tho, NTFS will need to do that check thing, and to mount it in Ubuntu you'll have to force mount with a command line.. command, unless you start windows again to check it.

Note: might want to specify a mount point for the windows partitions at Ubuntu install, but you probably already know this

BUT, Vista won't read ext3 unless you install the drivers, which I think is as simple as Google 'ext3 Vista'

I just cleared all of the C drive of any data and documents I want to keep (moved them to D).

I plan to install ubuntu onto the c drive, repartioning and reformatting as necessary and leave my larger d drive for data, etc (currently NTFS, plan to keep it that way).

Sound like a plan?

---

### Post by Taemojitsu on 2009-02-13
-panics- I don't know, ask theozzlives 

I don't think there are any major differences between ext3 and ntfs from functionality. The main thing is journaling, and both have it. Ntfs will not copy permissions tho, and might not do some other stuff (inodes?). However it's probably best if you are trying to share it on your network. I've never shared a folder in ubuntu but ozz said it works, and if not then ofc just Google 'share folder ubuntu vista' or something, or find someone else here who knows more than I do

---

### Post by peiklk on 2009-02-13
> **Taemojitsu said:**
> -panics- I don't know, ask theozzlives 

I don't think there are any major differences between ext3 and ntfs from functionality. The main thing is journaling, and both have it. Ntfs will not copy permissions tho, and might not do some other stuff (inodes?). However it's probably best if you are trying to share it on your network. I've never shared a folder in ubuntu but ozz said it works, and if not then ofc just Google 'share folder ubuntu vista' or something, or find someone else here who knows more than I do


But hey... you know more than me!

Thanks to you both!

---

