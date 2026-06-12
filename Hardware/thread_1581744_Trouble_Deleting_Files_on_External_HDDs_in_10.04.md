---
title: "Trouble Deleting Files on External HDDs in 10.04"
date: 2010-09-25
forum: Hardware
---

### Post by cynicalcylon on 2010-09-25
I've been having problems deleting .avi files on both of my external HDDs.

I keep getting the following error when deleting:
> Unable to move file to the wastebasket: No such file or directory

Can anyone help?

---

### Post by perspectoff on 2010-09-25
The Trash / wastebasket is specific to your user. 

The most reliable way to use the trashcan / wastebasket is through your File Manger (Nautilus / Dolphin / etc) where you will see the wastebasket for your user as a folder.

If you perform tasks as the root user, the relevant wastebasket will belong to the root user. To use the File Manager as the root user:

 sudo nautilus

or

 sudo dolphin

In general, the root user can delete anything on any drive (with the possible exception of NTFS drives, in some circumstances. On NTFS drives, sometimes only the user that created the folder / file can delete it.)

---

### Post by cynicalcylon on 2010-09-25
> Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Am a little confused now, as, surely, I'm the system admin?? :confused:

---

### Post by perspectoff on 2010-09-25
Samba may not be installed on your system.

You need Samba to access network folders / drives that use NTFS (Windows folders).

Try:
 sudo apt-get install samba

(Or install the samba package using the Synaptic Package Manager or KPackageKit).

---

### Post by cynicalcylon on 2010-09-25
Samba installed ok, but when the File Browser screen pops up, I get this when I click on the Deleted Items link on the left:

> Sorry, could not display all the contents of "trash": Operation not supported

---

### Post by colin.p on 2010-09-25
What happens when you do a "shift-delete"?

---

### Post by cynicalcylon on 2010-09-26
Same as plain old delete:

> Error removing file: No such file or directory

Admittedly, it's not for all files, but it's frustrating nonetheless.

---

