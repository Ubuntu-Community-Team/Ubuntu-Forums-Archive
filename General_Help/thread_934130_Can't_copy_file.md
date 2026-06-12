---
title: "Can't copy file"
date: 2008-09-30
forum: General Help
---

### Post by Benniee on 2008-09-30
Hello,
I'm really hoping someone can help me with a problem I've got copying a file.

I have a 900MB .VOB file and I want to copy it to another spot on the hard drive. Using my file manager (Dolphin in Kubuntu) I select the file, then right-click and select copy. I go to paste it in the required spot and it copies ok up to the 250MB mark, then hangs there for a little while and eventually quits on an error message "Could not read file /<path>" where path is the full path to the source file.

It always bombs out at the same file size - 250MB. The drive isn't full, having about 20GB free space.

Now here is what has me beat - If I try and play the original .VOB file in my media player (kaffeine) it plays perfectly.

Any idea how I can get this thing to copy properly?

Thanks,
Benniee

---

### Post by 3rdalbum on 2008-09-30
The .vob file isn't, by any chance, actually on a DVD video?

If so, you'll need to use some sort of program to rip it without re-encoding it. I use a bug in Acidrip to do it:

Load the disc, start Acidrip, and click the "Load" button. Select the title you want to rip, set the name to anything with spaces in it, click Queue and then Start. The process will "end with an error" after the disc has been cached. The cache is a VOB file inside /tmp. Just drag that out into whatever directory you want it in, and bob's your uncle.

---

### Post by Benniee on 2008-09-30
Thanks for the reply. No, the .VOB file isn't on a DVD, it's on my hard drive (sda1).

I've tried restarting the system to see if it was some sort of problem with caching the file - but still no luck. Stops at 250MB every time,

I would have thought if it was some sort of problem with file corruption then the kaffeine player wouldn't be able to play it.

Benniee

---

### Post by leo3307 on 2008-09-30
you could try with 
gksudo nautilus and copy the file like as the root user with out restriction

---

