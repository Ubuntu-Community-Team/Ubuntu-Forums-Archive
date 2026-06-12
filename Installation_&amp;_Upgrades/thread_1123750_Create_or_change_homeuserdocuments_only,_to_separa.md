---
title: "Create or change /home/user/documents only, to separate drive/directory"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by 73ckn797 on 2009-04-12
I am about to attempt to get my wife to use Ubuntu and will be loading 8.10 on a second partition already created on the (hd0) drive.

I know that I can create a separate /home on another drive/partition either during or after installation. I would really only want to create a separate document directory on another drive and/or partition.

This will be a dual boot with XP. I have been able to designate the Windows "My Documents" to use the Linux directory on an earlier installation on another computer. 

Is there a way to designate a separate document directory alone? If both OS's can share this directory, what would you recommend? I feel ext3 format with a reader for XP to "see" this partiton/directory will work. I figure that I could also make 8.10 use the NTFS Document directory. I currently have that on a second drive for use with XP and as a secure way to not lose her documents. Regular back-ups to the (hd0) drive is another security measure to not lose data.

Does this make sense? Need any clarification?

---

### Post by ad_267 on 2009-04-12
Yes that's definitely possible. Using ntfs is probably the best idea. You can simply mount your Documents partition at /home/username/Documents in the same way you would mount a partition at /home.

---

### Post by 73ckn797 on 2009-04-14
> **ad_267 said:**
> Yes that's definitely possible. Using ntfs is probably the best idea. You can simply mount your Documents partition at /home/username/Documents in the same way you would mount a partition at /home.

I have designated Windows to use the Linux partition (/home/me/Documents) as the "My Documents" on my laptop since it only has a single HD and it works fine. Looking at the instructions ( [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/) ) for creating a separate /home, could I just edit fstab and insert info there pointing to the new /home/documents since I am not creating a completely new directory?

My desktop computer could go either way. I have 3 drives (250Gib & 2-160Gib) If I wanted to use the existing Windows document directory from Linux, where would I find the file to designate that in? I could repartition the 250 drive for use as the Document partition to share between all OS's.

---

### Post by 73ckn797 on 2009-04-15
Bump

---

### Post by ad_267 on 2009-04-15
I'm still not 100% sure what you want to do exactly. Do you want to just have the My Documents folder mounted at /home/user/documents?

I don't know if there's a way to do this directly, what I would do is mount your whole Windows partition at /windows or wherever you like, and then have a symbolic link to the My Documents directory in your user's home directory.

If you want a separate partition that only contains the documents and is shared between Windows and Linux then yes you can do that too. The procedure would be nearly exactly the same as having a separate home, but just replace the /home part with /home/user/Documents. You would also have to make sure you specified the file system correctly.

There's a good guide for using fstab at: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by 73ckn797 on 2009-04-17
Found the solution to make a separate Document directory. This is not a separate /home designation but just Documents.

Ubuntu Tweak has the ability to designate the Documents location change that I was looking for.

Here is the link to have Ubuntu Tweak available: [http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)
Ubuntu Tweak will then be available to install via Synaptic Package Manager.
Once you complete the iinstallation you will find the program in Applications/System Tools.

When in Ubuntu Tweak you will find the options under System/File Type Manager. There you can designate directories and file associations.

---

