---
title: "no preview of .jpg files"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by wwuster on 2009-11-02
I just installed 9.10 and most things work, but I copied some .jpg files from the 9.04 drive into a folder and the .jpg previews don't show up and I
get a "wait cursor" that never stops. If I browse to the old drive the previews show up fine.

What's wrong?

William

---

### Post by Dragonbite on 2009-11-02
Is the drive you are trying to view them in a local directory or over the network?  Is it only JPEG or other image files too?

I know that pictures previews over my network do not work but once they are local I am able to view them.

---

### Post by wwuster on 2009-11-02
> **Dragonbite said:**
> Is the drive you are trying to view them in a local directory or over the network?  Is it only JPEG or other image files too?

I know that pictures previews over my network do not work but once they are local I am able to view them.

The 9.04 drive is on usb and the previews work. The previews don't work on the local sata drive. Just .jpg files, nothing else.

William

---

### Post by Dragonbite on 2009-11-02
> **wwuster said:**
> The 9.04 drive is on usb and the previews work. The previews don't work on the local sata drive. Just .jpg files, nothing else.

William

What are the size of those files? I think nautilus defaults to not show preview for files over 1MB or so, and you can change that to just about any number or to show all.

I doubt this is it, though, because it would be for everything and everywhere so if it shows up in one location and not the other then this can't be it.

Hmm....

---

### Post by wwuster on 2009-11-04
> **Dragonbite said:**
> What are the size of those files? I think nautilus defaults to not show preview for files over 1MB or so, and you can change that to just about any number or to show all.

I doubt this is it, though, because it would be for everything and everywhere so if it shows up in one location and not the other then this can't be it.

Hmm....

The files are way under 1MB. Interesting observation: if I rename the directory they are in with nautilus and then browse down into the newly renamed directory the preview works the first time. Then if I try to change the 'view' from icons to list it hangs forever again and won't work once again until I rename the directory a new unique name. Nautilus seems to have a memory of past names of the folder and I can't use those again to get the preview to work.

---

### Post by wwuster on 2009-11-12
Today's updates fixed it.

---

