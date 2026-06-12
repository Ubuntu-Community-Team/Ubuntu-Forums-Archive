---
title: "Virtualbox: Image file name????"
date: 2008-10-04
forum: General Help
---

### Post by Tex786 on 2008-10-04
Hi everyone,

Can someone tell me what i need to do when starting a new virtual harddissk in virtualbox.

Its asking for this ("Press the Select button to select the location and name of the file to store the virtual hard disk image or type a file name in the entry field.").

I have tryed to do this several ways but I don't seem to be getting it right.

How should I do this???

Thanks.

---

### Post by drs305 on 2008-10-04
This is for VirtualBox 2.0.2:

As you are setting up your new 'machine', when you get to the "Boot Hard Disk Primary Master" select New, Next, Dynamically expanding. In the Image File name window, type any name (don't add the .vdi extension). For the location, click on the folder icon to the right to choose where to create the .vdi file. Choose an image file size, Next and Finish.

That should do it. Once you have created the new .vdi, click on Settings and go through each of the categories to set them up. If you are running 64-bit, make sure you check General, Advanced, Enable VT-x/AMD-V. 

Under CD/DVD-ROM don't forget to point to an .iso or CD/DVD install disk if you are setting up a VM OS for the first time.

---

