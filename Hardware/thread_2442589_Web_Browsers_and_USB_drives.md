---
title: "Web Browsers and USB drives"
date: 2020-05-05
forum: Hardware
---

### Post by ngilmour on 2020-05-05
I'm running Ubuntu 19.10 on a used HP laptop.

When I mount an external USB flash drive (Sandisk, 128 GB), I can open files, move them here and there, save files, and do everything one expects to be able to do with files.

But when I attempt to use a browser-based email client to attach a file, neither Firefox nor Chromium will allow me to do so.  I get a message that reads "Could not read the contents of [drive name]" and then "Error opening directory" and then "Permission denied."

I've figured out a workaround in which I save the files to a directory on the laptop's SSD and then to the flash drive, but since I use that flash drive when I move from classroom computer to classroom computer (I'm a professor at a small college), that often means that I forget a step somewhere in there and end up without the file I need in the classroom.

So here's my question: for someone with a little know-how but decidedly neither a programmer nor a power user, is there a relatively simple way to convince my browsers to recognize a USB flash drive?

---

### Post by TheFu on 2020-05-05
Chromium is a snap package and is constrained to allow file access to the HOME by default. There are some ways to relax that slightly.   [https://snapcraft.io/docs/removable-media-interface](https://snapcraft.io/docs/removable-media-interface)
```
$ snap connect chromium:removable-media
``` 

i don't know what the deal is with Firefox. it isn't a snap to my knowledge, but if it is, there's the answer.  

Or it could just be normal Unix permissions.   Can you please posts the **ls -al** for the directory and file?

---

