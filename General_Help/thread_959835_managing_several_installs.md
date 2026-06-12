---
title: "managing several installs"
date: 2008-10-26
forum: General Help
---

### Post by quizzelsnatch on 2008-10-26
I was wondering how people managed several installs with their user accounts. I have three partitions for operating systems, arch, gentoo, ubuntu, and I want to have access to all of my files (music, video, documents, pictures, etc) from all of those accounts, but I don't want to mix my user settings (e.g. having the same username for each installation and sharing the same home folder). Anybody have any suggestions for this?

---

### Post by ciscosurfer on 2008-10-26
You could mount each distro's appropriate partition and selectively choose which files you'd like to use.  You don't need to bother with mixing/matching user accounts.  That would probably get crazy quickly.

---

### Post by utnubuuser on 2008-10-26
yeah, but how? Exact commands?

---

### Post by ciscosurfer on 2008-10-26
> **utnubuuser said:**
> yeah, but how? Exact commands?They've been documented for you already in the [community docs]("https://help.ubuntu.com/community/UserDocumentation?action=fullsearch&context=180&value=mount&titlesearch=Titles") as well as these forums.[]("https://help.ubuntu.com/community/UserDocumentation?action=fullsearch&context=180&value=mount&titlesearch=Titles")

---

### Post by quizzelsnatch on 2008-10-29
I'm not sure if I follow what you are saying. Do you mean I could do like a mount /path/to/music to ~/Music etc. for my folders to EACH user account and have separate user accounts? That doesn't seem right from what you say later in the post... could you explain a little more in depth. I went to the link you posted, but didn't really see anything that caught my eye as to what you are talking about.

---

### Post by ciscosurfer on 2008-10-29
> **quizzelsnatch said:**
> I'm not sure if I follow what you are saying. Do you mean I could do like a mount /path/to/music to ~/Music etc. for my folders to EACH user account and have separate user accounts? That doesn't seem right from what you say later in the post... could you explain a little more in depth. I went to the link you posted, but didn't really see anything that caught my eye as to what you are talking about.Perhaps I'm the one who's not following you.  My understanding from your original post was that you wanted access to your personal files from each of the other distributions (Arch and Gentoo) that you say are each on their own partition.  Is this correct?  If so, then you can mount each partition to a location of your choosing, say /media/Arch and /media/Gentoo and you'll then have access to those distro's and by extension, the files you want to work with. If you run fdisk you can find out the device locations each distro is associated with.

Take the following for example```
sudo fdisk -l

[FONT=monospace]
[/FONT]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00056ea5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         974     7823623+  83  Linux
/dev/sda2             975        1948     7823655   83  Linux
/dev/sda3            1949        2192     1959930   82  Linux swap
/dev/sda4            2193        5598    27358695    5  Extended
/dev/sda5            2193        4625    19543041   83  Linux
/dev/sda6            4626        5598     7815591   83  Linux
```For the sake of example, let's say that **/dev/sda1** is your **Ubuntu partition** that you boot from, **/dev/sda2** is your **Arch partition**, and **/dev/sda5** is your **Gentoo partition** (this is just an example, remember yours will differ). So armed with this new information, you can now make new directories to temporarily (or permanently) house these partitions for viewing and modification from within Ubuntu.```
sudo mkdir /media/Arch
sudo mkdir /media/Gentoo

sudo mount /dev/sda2 /media/Arch
sudo mount /dev/sda5 /media/Gentoo
```If you now browse to each directory, **/media/Arch** and **/media/Gentoo**, your files from each respective distro will now show up there. At this point, you could certainly symlink /media/Arch/home/quizzelsnatch/Music to your Ubuntu music directory, and so on, as you alluded to before.

Does this help?

---

### Post by quizzelsnatch on 2008-10-30
Aw. I see, I haven't made myself clear. The way my partitioning scheme works is I have a partition with all of my personal data, aka /home. And I have another 4 partitions reserved for different operating systems I wish to install. What I want to do is have access to all of my files on my home partition with each user on each of my operating system installs, in such a way that each user does not share config files (i.e. gentoo, arch, ubuntu all sharing the same username and therefore having access to all of the files but also sharing all of the config files, which isn't optimal). Do you see what I am saying now?

And thank you for taking time to explain all of that, even though it was not quite what I was trying to get at.

---

### Post by fsmithred on 2008-10-30
The basic method that ciscosurfer described should work for you. If all your files in /home are on a separate partition, then that partition should be mounted at /home in only one of the operating systems. In the others, you'll have to mount it someplace else. If you have the same username, uid and gid in all three installations, then you will have full control of your files.

---

