---
title: "2nd HD permission issues"
date: 2005-06-24
forum: Hardware &amp; Laptops
---

### Post by Uta on 2005-06-24
I am running Kubuntu as a stand alone OS on my Dell C800 laptop, I now have everything working great but...
I added a 2nd HD (40G) in the modular media bay, formatted half FAT32 and the other half EXT3, mounted without issue but I am having permission problems which are: root owns the drives (hdc1 and hdc2) and when I the 'user' tries to write to either drive it doesn't allow it. I have tried as 'root' to change the permissions but it won't accept the changes? I can only write to these 2nd HD as 'root' . Where did I go wrong and how can I get write permissions for these drives? Thanks in advance!

---

### Post by -TayloR- on 2005-06-24
This is the EXT3 partition your trying to write to right? as i dont think ubuntu, or any other distro for that matter supports fat32 or NTFS writing. 

First have you tried changing the ownership of the HD from root to normal user?
Also have you tried to actually change the permissions using chmod?

If you have and already know about these commands (chmod, chown) then i apologise for ranting on and just ignore this whole post lmao, im just insinuating that you dont know just so i can cover the basic things you may need to do :).

Im not entirely certain if this is correct but to change the ownership of the HD do the following:

(say your normal username is 'fred', obviously replace fred with your actual username)

```

chown -R fred /dev/hda 

```
(change the 'a' after hd to that of the other drive, so your second drive (being the EXT3 partition you've created) most likely will be hdb or hdc depending on the partition table)

Then to change the permissions to give you write / read access you should do:

```

chmod -R +rw /dev/hda 

```
(again change hda to that of your partition label)

Im not entirely sure on if you need to change the permissions on the linked directory that you have created so that you can access the drive. If you do just do the same commands but on the linked directory themselves e.g.

```

chown -R fred /mnt/storagedrive
chmod -R +rw /mnt/storagedrive

```

Depending on what you called the folder linked to that drive.

**NOTE:**I wouldnt advise you do this until someone else more experienced on these forums have commented on what ive said because im not 100% sure this is correct. In the console just type **man chmod** and **man chown** to get the definition / information on each command. Just man'ing the commands wont do any harm what so ever, but actually carrying out the commands like ive wrote on the code could possibly change things, so as i said, DONT follow this until someone else has commented on what ive wrote and said its correct / incorrect etc. But at least you have the idea of what you need to do :).

Hope this helps.

**:: Edit ::**

Information on Chmod: [http://www.mkssoftware.com/docs/man1/chmod.1.asp](http://www.mkssoftware.com/docs/man1/chmod.1.asp)

Information on Chown: [http://www.mkssoftware.com/docs/man1/chown.1.asp](http://www.mkssoftware.com/docs/man1/chown.1.asp)

---

### Post by Uta on 2005-06-24
Thanks for your reply, but yes I have tried to change the permission both the GUI and line command way as 'root'
Just for a sanity check on my part I reran chown and chmod and the error message is "Operation not allow" same as before. You can write to FAT32 (as root) with Kubuntu, FYI. As I said before it's writing as me the main user that is forbidden. Again thanks for your input.
Additionally
Ok, this is possible to chmod 770 the EXT3 partition of the 2nd HD but not the FAT32 partition. mmm, wonder why you can't chmod a FAT32 partition?

---

### Post by Alexander Kirillov on 2005-06-24
[QUOTE=Uta]Thanks for your reply, but yes I have tried to change the permission both the GUI and line command way as 'root'
Just for a sanity check on my part I reran chown and chmod and the error message is "Operation not allow" same as before. You can write to FAT32 (as root) with Kubuntu, FYI. As I said before it's writing as me the main user that is forbidden. Again thanks for your input.
Additionally
Ok, this is possible to chmod 770 the EXT2 partition of the 2nd HD but not the FAT32 partition. mmm, wonder why you can't chmod a FAT32 partition?[/QUOTE]
 Change mount options in /etc/fstab as decribed in 
[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

---

### Post by Uta on 2005-06-24
[QUOTE=Alexander Kirillov]Change mount options in /etc/fstab as decribed in 
[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)[/QUOTE]

Thank you, right direction, problem solved, again thanks!

---

### Post by -TayloR- on 2005-06-26
Lol apologies for me not being of much help :). Glad you got it sorted !

---

