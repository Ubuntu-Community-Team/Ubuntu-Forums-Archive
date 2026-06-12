---
title: "Accessing My Documents (Windows) from Ubuntu"
date: 2008-10-07
forum: General Help
---

### Post by hrMeyer on 2008-10-07
Hi.

I have both Windows Vista and Ubuntu 8.04 installed. When I access my HDD hard drive (HDD is only the name of the Windows partition), I can see most files, but not the files in My Documents.

Is there a way to allow me to see them (and preferably edit them) in Ubuntu?

Thanks in advance.

---

### Post by secondstage on 2008-10-07
I beleive that you can access you documents, by opening the windows partition/drive (Places > Computer > Blank GB Media). Ubuntu will mount the windows partition, and you will have a window open. They should be under User > yourUserName > My Blank. If the documents are not there, then you will need to check in Windows, where you have 'My Documents' headed towards. To do so, Start Menu > Right-click the icon for My Documents, and see where it is pointed to. Boot into Ubuntu, and use that address to check if you can find your documents. If you once again cannot find your documents, then I am terrible sorry to say that my help was of no use, and that I do not know where to go next.

But if you do happen to find your documents, then I would suggest to make a dedicated partition for your documents. You can do so by following [this how to]("http://support.microsoft.com/kb/309000"). If you don't create a separate partition, Windows will do a system check every time that you edit something from the windows system partition in Ubuntu. This gets very annoying after the first, or second time.

---

### Post by PocketDog on 2008-10-07
That's how XP's laid out. With my Vista drive mounted 'Documents and Settings' is empty. My documents are under Users > Me > Desktop/Pictures/Documents/Music

---

### Post by secondstage on 2008-10-07
@PocketDog: True. Sorry for the mishap.
@hrMeyer: Use User > You > My Whatever

---

