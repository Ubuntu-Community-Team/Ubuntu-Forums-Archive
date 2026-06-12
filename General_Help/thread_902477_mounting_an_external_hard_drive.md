---
title: "mounting an external hard drive"
date: 2008-08-27
forum: General Help
---

### Post by rapattack1 on 2008-08-27
Hi this external hard drive is a Sarotech FHD-352 and the interface is USB(1) Firewire(2). As I don't have a firewire cable I am testing it with a USB one but I got the attached error when trying to mount it. I made the mistake of not waiting long enough for linux to see it and i went to remove the usb cable. Then I re attached and got this error. I tried one of the commands but didn't get anywhere. It wanted me to read mount 8 man and I didn't understand anything.
Oh I forgot to mention this is an item I found on the street and I have never used an external hard drive before.

---

### Post by vanadium on 2008-08-27
Have your ntfs volume checked and repaired under MS Windows. This is essentially what point 1) is advising in the dialog you attached.

---

### Post by rapattack1 on 2008-08-27
I am not sure what you mean about having the ntfs drive checked. Can you elaborate please. It is an external hard drive.

---

### Post by vanadium on 2008-08-28
Connect the drive to a system running Windows, and check/repair the drive using the Windows tools. After that, properly disconnect the drive or shut down that Windows system completely.

ntfs is a proprietary file system. Therefore, Linux does not have a 100% comprehensive repair tool, although ntfsfix can probably also help in many instances.

---

### Post by hessiess on 2008-08-28
> Oh I forgot to mention this is an item I found on the street and I have never used an external hard drive before.

If you found it on the street then the most responsible thing to do would be to take it to your local police station. Its lickly that someone lost the device, and also lickly that it has personal information on it.

---

### Post by rapattack1 on 2008-08-28
No it was just the case and it was in an area where we have what we call in Sydney 'Council cleanup'. People through their stuff out for the council to take to the dump. It was just the case and I put a hard drive in it.

---

