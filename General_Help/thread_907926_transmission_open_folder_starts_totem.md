---
title: "transmission open folder starts totem"
date: 2008-09-02
forum: General Help
---

### Post by krsmit0 on 2008-09-02
when i click "open folder" on a torrent, it trys to open totem regardless of what the files are.

How do i fix this, i have searched and can't find anything.  i just want it to open the folder like it is supposed to.

Thanks
ken

---

### Post by matdombrock on 2008-09-02
Thats weird. Has it always done this?

---

### Post by krsmit0 on 2008-09-02
i just started using transmission, but i think ktorrent did the same thing.

---

### Post by krsmit0 on 2008-09-04
Any ideas anyone?

---

### Post by krsmit0 on 2008-09-07
???

---

### Post by krsmit0 on 2008-09-16
anyone?

---

### Post by cariboo on 2008-09-16
Have you tried right-click then, Open With Other Application?

Jim

---

### Post by krsmit0 on 2008-09-16
it transmission?  because that doesn't seem to be an option.

in nautilus?  because everything opens in the program it should.

---

### Post by krsmit0 on 2008-09-16
i take that back, using the directions at the bottom of this...

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/35463](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/35463)

> annot change the default action in Nautilus or GNome.
The precise steps are:
 Open a folder in Nautillus (for example with Places -> Computer);
 browse to the folder that does not behave properly (in my case file:///home/myuser)
 Select File -> Properties -> Open With; here one should be able to add and remove items. It is possible to Add items, but they cannot be selected. Two items cannot be removed: 'Open Folder' and 'Open Folder with Thunar', which is selected by the radio button. It is not possible to move the radio button and select any other option.

based on your suggestions, i found that my download folder was set to open with totem.  fixed it.



Thanks.

---

### Post by afrodeity on 2011-01-30
There doesn't appear to be an option to change the setting in Maverick 10:10.

If I try opening with places, my Downloads folder opens in Totem.

File > Properties > no open with option.

---

### Post by afrodeity on 2011-01-30
Ok, problem solved, a wee bit more complicated than the previous solution:

1. Open Home folder

2. Right click on problem folder

3 Choose Open With

4. Choose Other Application...

5. Make sure "remember this application for folder files" is clicked

Anybody out there know why we can't do this in three steps, via File > Properties?

---

