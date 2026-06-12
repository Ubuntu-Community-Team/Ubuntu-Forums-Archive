---
title: "Slow boot, with dmesg output"
date: 2008-10-16
forum: General Help
---

### Post by Zeedok on 2008-10-16
My Hardy installation (Dell XPS, m1330, 2.4Ghzx2, 4GB HD) boots more slowly on Ubuntu than on Vista (tut, tut).

I know that the Intrepid release has attempted to improve boot times, and that boot times may be slower on laptops than on desktops, but I was wondering whether there were errors on boot that might be slowing me down.  First of all I see the error message:

```
[   26.606978] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:7670)
[   26.607345] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
```

and also some message about memory and 'not automatically fixing this' (sorry that's so vague, but I ran dmesg and couldn't find the exact message).

I'm sure that the splash of text on boot-up wasn't visible when I first upgraded to Hardy, but I can't remember when everything became so 'wordy'.

Will intrepid (when it comes out) fix my issues?

I enclose the output of dmesg for your consideration, any assistance would be gratefully accepted. Thanks.

---

### Post by Zeedok on 2008-10-16
I found a solution to the 'not automatically fixing this' error.

By following [this]("http://ubuntuforums.org/showthread.php?t=189238&highlight=SimonU&page=2") thread.

I found this solution:

```

sudo cp /etc/init.d/checkfs.sh /etc/init.d/checkfsbackup.sh
sudo rm /etc/init.d/checkfs.sh
```

I'm not sure if my boot time is that much faster, but that error doesn't show up anymore.

Now to tackle the other error . . .

---

