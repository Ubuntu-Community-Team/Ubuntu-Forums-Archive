---
title: "1 gig SD card containing 8 gig unremovable files"
date: 2008-11-23
forum: Hardware
---

### Post by zeekaart on 2008-11-23
Hiya guys, got myself a 1 gigabyte SD card, containing absolutly nothing. The problem is, my laptop show it as an Filestorage on my desktop, calling it "KODAK_". If i open it it shows several really weird file types and names. And the properties say its a 1 gig card, using 800mb of it, but containing 128 files wich takes up 7,1 gig space..
I cant trow  the files away, saying its not there. I really have no clue, this is my weirdest thing i have ever seen in Ubuntu.

Any help?

Links to screenshots of my problem:
1 [http://i5.photobucket.com/albums/y181/zeekaart/1gigcardcontaining8gig.png](http://i5.photobucket.com/albums/y181/zeekaart/1gigcardcontaining8gig.png)
2 [http://i5.photobucket.com/albums/y181/zeekaart/properties1gigcard.png](http://i5.photobucket.com/albums/y181/zeekaart/properties1gigcard.png)

---

### Post by Mewshi on 2008-11-23
Try formatting it?

I would recommend using GParted, since it is a GUI.

Just make sure you format the card, not your hard drive ^-^

---

### Post by zeekaart on 2008-11-23
Yeah i formated the card now, the card is clean now.
But there is an another problem now, even with the card not plugged in it still shows on my desktop, stil containing those files.
Cant unmount it, cant delete it. I have no idea what to do with it.

---

### Post by Mewshi on 2008-11-23
Ok.

Do you have another operating system/computer you can try this on?

If so, test it there; if it works on windows, it's an Ubuntu problem; if it works on a different machine running Ubuntu, it's a hardware problem.

Is this an internal card reader, such as I have on my laptop?

---

### Post by zeekaart on 2008-11-23
I have been succesfull in formating the card, thats no problem anymore. But there now is a files system on my dekstop that says its my SD card.

---

### Post by Mewshi on 2008-11-23
It's supposed to, I think

---

### Post by damis648 on 2008-11-23
> **Mewshi said:**
> It's supposed to, I think

Nope. That is very wierd. Try inserting the card, then do
```
sudo umount /dev/xxxx
```
replacing xxxx with the card device. If it unmounts, the icon will go away.

---

### Post by Mewshi on 2008-11-23
Oh, wait, he meant the icon was there after he pulled it out... just like at the movie theater...

---

### Post by Neostar on 2008-11-23
You can just right-click and select eject to unmount the card.

---

### Post by zeekaart on 2008-11-23
I already unmounted the orignal card. So even without a card in, theres still that icon on my desktop. If i open it it says its a 1 gig card, with 800 mb used out of 900 something. But the properties also say that there are 128 items on it with a total size of 7,1 gigs. (see screenshots first post).

---

### Post by Neostar on 2008-11-23
Try rebooting your machine, it's most likely a bug that disappears after a reboot.

---

### Post by cariboo on 2008-11-23
Have you tried Ctrl-Alt-Backspace to restart X and the desktop. If that doesn't work, Press Alt-F2 and type:

```
gksu nautilus
```

This will start nautilus as root, you will have to navigate back to /home/<user>/Desktop then try and elete the icon.

Jim

---

### Post by zeekaart on 2008-11-24
Thanks Neostar and Cariboo, the restart got away the icon on my desktop and the use of the command got the file gone from /Media.

Problem solved!

---

